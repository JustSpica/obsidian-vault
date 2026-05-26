# Roteamento IPv4, Gateway e NAT

## Gateway e decisão local vs remoto

Um host usa a própria [[CIDR e Mascara de Rede (IPv4)|máscara/prefixo]] para decidir se o destino está na mesma rede:

- Se `destino` está na mesma rede, ele envia direto no enlace.
- Se não está, ele envia para o **gateway** (rota default), que encaminha para outras redes.

Na prática, enviar direto no enlace significa: descobrir o **MAC** do destino (ou do gateway) e encapsular o pacote IP em um quadro (ex.: [[Padrão Ethernet|Ethernet]]). Tipicamente isso envolve ARP em [[IPv4]].

Quando a máscara está errada, o comportamento fica confuso. O host pode tentar usar o gateway sem precisar, ou tentar falar direto com um IP que na verdade está em outra rede.

**Exemplo de uma rede com IPs públicos:**

O provedor me vende a faixa `143.54.11.64/28` para uso pessoal, e diz que devo usar o IP `143.54.0.20/24` na interface que conecta com ele e o gateway deve ser `143.54.0.1`. Na minha infra local eu tenho a seguinte situação:

- **Rede A:** Tem 4 máquinas e dois gateways (router 1-eth1 e router 2-eth0).
- **Rede B:** Tem 3 máquinas e um gateway (router 2-eth1)

A solução é dividir o `/28` que o provedor me forneceu em dois `29`, assim respeitando o [[Topologias e Segmentação de redes LAN|domínio de broadcast]] de cada rede: ![[exemplo_roteamento_estático.png]]

- **Rede A:** Todos os IPs para a rede está sendo usados.
- **Rede B:** Sobraria 2 IPs para usar como bem quiser.

*OBS: Para o provedor, não importa como foi dividido a minha faixa de IPs. Ele vai rotear tudo que for `143.54.11.64/28` para `143.54.0.20`*.

## Tabelas de roteamento

Roteadores tomam decisões com base em uma tabela de rotas (`destino/prefixo -> saída/next-hop`):

- **Rotas locais:** Redes diretamente conectadas a uma interface.
- **Rotas para redes específicas:** Encaminham para um próximo gateway.
- **Rota default:** `0.0.0.0/0` (o que não casar com nada vai para ela).

**Tabela Roteamento do roteador 1:**

| **Rede**          | **Destino**    | **Observação**                                                                                                                                                                                                            |
| ----------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `143.54.11.64/29` | `Local eth1`   |                                                                                                                                                                                                                           |
| `143.54.0.20/24`  | `Local eth0`   | O roteador não sabe o que tem nessa rede e nem precisa saber, só sabe que a `eth0` faz parte e que é nela que acha o gateway (`143.54.0.1`) informado pelo provedor.                                                      |
| `143.54.11.72/29` | `143.54.11.66` | As máquinas da rede B não estão acessíveis por este roteador. Para chegar nelas é necessário passar o pacote para o Router 2, pelo *MAC Address* de router 2-eth0. Para obter esse *MAC* precisa-se do IP para fazer ARP. |
| `Default`         | `143.54.0.1`   | Tudo que não casar com as regras anteriores será repassado para ele.                                                                                                                                                      |

**Tabela Roteamento do roteador 2:**

| **Rede**          | **Destino**    | **Observação**                                                                                                                                                |
| ----------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `143.54.11.72/29` | `Local eth1`   | Indica que uma máquina com este IP está na rede local da interface `eth1`.                                                                                    |
| `143.54.11.64/29` | `Local eth0`   | Se o roteador precisar conversar com alguma máquina na rede A, deve saber que ela está localmente na sua interface `eth0`                                     |
| `Default`         | `143.54.11.65` | Tudo que não casar com as regras anteriores será repassado para ele, ou seja, se não é rede A e nem B, então manda para ele que ele deverá saber o que fazer. |

Tanenbaum diz que o roteador escolhe a rota mais específica, isto é, com maior prefixo (*longest prefix match*). A rota default só entra quando não existe nada mais específico.

Se uma rota está faltando ou errada, pode acontecer **loop** entre roteadores, isso só para quando o **TTL** expira.

**Exemplo de loop por rota errada/ausente, baseado na figura anterior:**

O Router 1 não tem rota direta para a rede B. Se um pacote para `143.54.11.76` não casa com nenhuma rota específica em Router 1, ele manda para a rota default (`143.54.0.20`).

O provedor, por sua tabela, manda de volta para o Router 1 (porque a faixa agregada é da infra dele). Nesse caso o pacote fica indo e voltando até o TTL expirar.

Esse exemplo é o motivo do TTL existir. Ele transforma “loop infinito” em “falha com limite”.

## Interfaces vs placa de rede

Quem recebe IP é a interface. Em uso comum, “1 placa = 1 interface”, mas com [[VLANs e Protocolo IEEE 802.1q|VLAN (802.1q)]] é possível ter uma placa com **várias interfaces lógicas**.

Isso aparece muito em roteadores. Uma única NIC (ex.: `eth0`) pode carregar várias VLANs e virar várias interfaces lógicas (ex.: `eth0.10`, `eth0.20`), cada uma com seu `IP/prefixo`.

## NAT (Network Address Translation)

NAT traduz endereços entre uma rede privada e a Internet. Ele aparece como solução prática quando você usa [[CIDR e Mascara de Rede (IPv4)|IPs privados]] internamente e precisa sair para a Internet com IP(s) público(s).

No caso **NAT estático** (RFC 1631), a tradução é uma associação fixa:

- **Ao sair:** Troca IP de origem privado por um IP público.
- **Ao entrar:** Troca IP de destino público pelo IP privado.

**Exemplo de uma rede com NAT estático:** ![[exemplo_roteamento_nat_1_to_1.png]]

**Tabela NAT 1:1**

| **IPs públicos** | **IPs privados** | **IPs públicos** | **IPs privados** |
| ---------------- | ---------------- | ---------------- | ---------------- |
| `143.54.11.64`   | `10.0.0.3`       | `143.54.11.68`   | `10.0.1.2`       |
| `143.54.11.65`   | `10.0.0.4`       | `143.54.11.69`   | `10.0.1.3`       |
| `143.54.11.66`   | `10.0.0.5`       | `143.54.11.70`   | `10.0.1.4`       |
| `143.54.11.67`   | `10.0.0.6`       | `143.54.11.71`   | `10.0.1.5`       |
|                  |                  | `143.54.11.72`   | `10.0.1.6`       |

Como o NAT altera o cabeçalho IPv4, ele precisa recalcular o checksum do cabeçalho.

*OBS: Em implementações reais, NAT geralmente precisa atualizar também checksums de TCP/UDP, pois esses protocolos usam um pseudo-cabeçalho que inclui endereços IP.*

## NAT dinâmico e mascaramento

No **NAT dinâmico** com mascaramento, a tradução não é uma associação fixa `1:1`. A ideia é permitir que vários hosts privados saiam para a Internet usando **um único IP público**, ou um conjunto pequeno de IPs públicos.

Esse caso é chamado de **NAT 1:N** e normalmente usa **PAT** (*Port Address Translation*), porque a tradução passa a envolver também as portas de [[TCP]] ou [[UDP]].

Na prática, o roteador NAT mantém uma tabela temporária de traduções, como no exemplo abaixo:

| Interno         | Externo após NAT    | Destino       |
| --------------- | ------------------- | ------------- |
| `10.0.0.5:2000` | `143.54.0.20:45000` | `8.8.8.8:443` |

Nesse caso, o funcionamento básico é dado como:

1. Cliente interno (`10.0.0.5:2000`) inicia uma comunicação para fora da rede.
2. O NAT troca o IP privado de origem pelo IP público.
3. O NAT troca ou reserva uma porta externa (como `45000`).
4. A tabela associa `143.54.0.20:45000` a `10.0.0.5:2000`.
5. Quando a resposta volta para `143.54.0.20:45000`, o NAT consulta a tabela e entrega para `10.0.0.5:2000`.

Isso funciona porque fluxos TCP/UDP podem ser diferenciados pela combinação de IPs e portas.

Como o NAT altera IP e porta, ele precisa recalcular checksums. No caso de TCP e UDP, isso é especialmente importante porque o checksum usa um pseudo-cabeçalho com IP de origem e destino.

*OBS: Mascaramento atrapalha uso como servidor. Se uma conexão vem de fora sem existir mapeamento prévio na tabela NAT, o roteador não sabe automaticamente para qual máquina interna entregar. Para isso, normalmente precisa de redirecionamento de porta, regra estática ou outro mecanismo.*

## CGNAT

O **CGNAT** (*Carrier-Grade NAT*) é o NAT dinâmico feito pelo provedor. Em vez de só a rede de casa ou da empresa compartilhar um IP público internamente, vários clientes do provedor também compartilham IPs públicos na rede do próprio provedor, criando um **duplo NAT**.

O problema é que o provedor não deveria simplesmente usar uma faixa privada comum, como `10.0.0.0/8`, entre ele e os clientes. Isso poderia conflitar com redes privadas que o próprio cliente já usa.

Por isso existe o bloco `100.64.0.0/10`, reservado para esse espaço compartilhado entre provedor e cliente em cenários de CGNAT.

Tanenbaum trata NAT como uma solução prática para a escassez de IPv4, mas também aponta custos importantes:

- Mantém estado de conexões/traduções no meio da rede.
- Dificulta hospedar serviços atrás do NAT.
- Complica protocolos que carregam IPs ou portas dentro do payload.
- Pode exigir regras extras, ALG, hairpin NAT ou redirecionamento manual de portas.

*OBS: NAT é útil, mas quebra o “fim a fim” da Internet. Vale lembrar disso quando algo “misteriosamente” não funciona.*

## Referências

- Baseado no PDF do La salle [[redes-aula-07.pdf|Redes - Aula 07]] e [[redes-aula-13.pdf|Redes - Aula 13]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].

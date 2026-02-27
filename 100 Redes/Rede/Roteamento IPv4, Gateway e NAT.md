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

*OBS: NAT é útil, mas quebra o “fim a fim” da Internet. Complica protocolos que carregam IPs no payload e pode exigir hairpins, ALG, etc. (Vale lembrar disso quando algo “misteriosamente” não funciona).* 
## Referências

- Baseado no PDF do La salle [[redes-aula-07.pdf|Redes - Aula 07]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].

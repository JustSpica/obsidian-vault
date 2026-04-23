# CIDR e Máscara de Rede (IPv4)

No IPv4, um endereço IP só vira rede quando você define um prefixo (CIDR) ou uma máscara. O CIDR substitui o esquema por [[Classes de IPv4|classes (A/B/C)]] e permite usar qualquer quantidade de bits para identificar a rede.

O esquema por classes facilitava roteamento no início, mas desperdiçava endereços e não acompanhou o crescimento da Internet.

O CIDR usa a notação `IP/prefixo` (ex.: `192.168.10.50/24`). Esse `/24` é a máscara em decimal, dizendo quais bits pertencem a rede e quais ao host, ou seja, `n` bits 1 (rede) e `32-n` bits 0 (host).

Com um IP e uma máscara, dois cálculos básicos resolvem quase tudo:

- **Número da rede:** `rede = ip & mascara`, ou seja, IP AND Masc
- **Broadcast:** `broadcast = ip | (~mascara)`, ou seja, IP OR Mas Inv.

**Exemplo de operações:**

Qual rede pertence o IP `192.168.10.50/24`, ou seja, os **24 bits** iniciais designam a rede:
![[exemplo_ip_mascara_and.png]]

E para encontrar o broadcast é só fazer a operação OR pela máscara invertida:
![[exemplo_ip_mascara_or.png]]

Alguns problemas típicos de usar máscara errada para as operações são:

- **Mesmo domínio, máscaras diferentes:** Máquina A está com `/24` e máquina B com `/25`.
  - B pode achar que parte da rede está “fora” e tentar falar via gateway sem necessidade.
- **Domínios diferentes, máscara “larga” demais:** Máquina A está com `/24` e máquina B com `/25` em outra rede.
  - Máquina A pode achar que máquina B é local e tentar ARP/enlace (falha).
  - Máquina B pode até enviar para máquina A, mas a resposta de A morre pelo mesmo motivo.

Regras:

- Em uma rede, o endereço com bits de host todos 0 é o número da rede.
- Em uma rede, o endereço com bits de host todos 1 é o broadcast.
- Em um mesmo [[Topologias e Segmentação de redes LAN|domínio de broadcast]], todos precisam usar a mesma máscara, senão cada host calcula rede e [[Transmissão de dados|broadcast]] diferentes.

*OBS: Em geral, o primeiro e o último endereço da sub-rede não são atribuídos a hosts (rede e broadcast). Por isso, uma regra prática é: hosts utilizáveis = `2^(bits_host) - 2`.*
## IPs privados

Faixas reservadas para intranet:

- `0.0.0.0/8`: reservado
- `10.0.0.0/8`
- `127.0.0.0/8`: loopback (uso local)
- `172.16.0.0/12`
- `192.168.0.0/16`

Elas são válidas para uso interno, mas não são roteadas na Internet pública (para acessar a Internet, normalmente entra [[Roteamento IPv4, Gateway e NAT|NAT]]).

*OBS: “Privado” não significa “inválido”. Significa “não roteado na Internet pública”.*
## Sub-redes

Dividir uma rede significa aumentar o prefixo (mais bits para rede), criando redes menores.

**Exemplo usando um IP `10.1.0.0/24`: **

Um `/24` tem 256 endereços. Tipicamente 254 hosts utilizáveis (ex.: `10.1.0.1` até `10.1.0.254` já que `10.1.0.0` é rede e `10.1.0.255` é broadcast).

Se eu dividir esse `/24` em 2 `/25`, terei duas redes:
- `10.1.0.0/25` (broadcast `10.1.0.127`)
- `10.1.0.128/25` (broadcast `10.1.0.255`)

Uma forma rápida de achar o tamanho do bloco no octeto do corte é:

- `bloco = 256 - valor_do_octeto_da_mascara`

Ex.: Um `/26`, a máscara é `255.255.255.192`, então `bloco = 256 - 192 = 64`.

O início de cada sub-rede precisa ser múltiplo do tamanho do bloco no octeto onde ocorreu o corte (ex.: em `/26` (bloco 64), as redes são `X.X.X.0`, `X.X.X.64`, `X.X.X.128`, `X.X.X.192`).
## Problemas típicos de máscara errada

- **Mesmo domínio, máscaras diferentes:** A está com `/24` (certa) e B com `/25`.
  - B pode achar que parte da rede está “fora” e tentar falar via gateway sem necessidade.
- **Domínios diferentes, máscara “larga” demais:** A está com `/24` e B com `/25` em outra rede.
  - A pode achar que B é local e tentar ARP/enlace (falha).
  - B pode até enviar para A, mas a resposta de A morre pelo mesmo motivo.

Em um mesmo domínio, todos precisam calcular o mesmo número de rede e broadcast.
## Referências

- Baseado no PDF do La salle [[redes-aula-05.pdf|Redes - Aula 05]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]]

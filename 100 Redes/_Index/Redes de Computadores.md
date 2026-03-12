---
node_size: 32
---
# Redes de Computadores

Esta nota funciona como um **mapa de conteúdo** para os assuntos de redes de computadores deste vault. A ideia é servir como ponto de entrada para revisar os conceitos principais e navegar entre as notas mais específicas.

Em geral, redes podem ser estudadas em camadas: primeiro os **modelos de referência**, depois os conceitos de **enlace** (como quadros circulam em uma rede local) e por fim os conceitos de **rede** (como pacotes são endereçados e roteados entre redes diferentes).
## Modelos e visão geral

- [[Modelos OSI e TCP IP]]: Visão geral das camadas, comparação entre OSI e TCP/IP e encapsulamento.
## Camada de enlace

Assuntos ligados à comunicação dentro de uma rede local (LAN), quadros, MAC address, switches e VLANs:

- [[Topologias e Segmentação de redes LAN]]: Topologias físicas/lógicas, domínio de broadcast, domínio de colisão, hubs, bridges e switches.
- [[Transmissão de dados]]: Unicast, multicast, broadcast, simplex, half-duplex e full-duplex.
- [[Padrão Ethernet]]: Família IEEE 802.x, quadro Ethernet, EtherType e relação com IPv4/IPv6.
- [[VLANs e Protocolo IEEE 802.1q]]: Segmentação lógica em switches e tagging 802.1Q.
## Camada de rede

Assuntos ligados a endereçamento lógico, roteamento e entrega de pacotes entre redes.

- [[IPv4]]: Visão geral do protocolo IPv4, datagrama, cabeçalho e fragmentação.
- [[IPv6]]: Evolução do IPv4, endereçamento de 128 bits, cabeçalho fixo, extensões e fragmentação só na origem.
- [[ICMP]]: Mensagens de controle e erro usadas junto do IP.

## Endereçamento IPv4 e subnetting

Essas notas focam em como um endereço IPv4 vira rede, host, broadcast e como isso impacta a comunicação.

- [[Classes de IPv4]]: Visão histórica do endereçamento por classes.
- [[CIDR e Mascara de Rede (IPv4)]]: Prefixo, máscara, rede, broadcast e sub-redes.
- [[Roteamento IPv4, Gateway e NAT]]: Decisão local vs remoto, gateway, tabelas de roteamento e NAT.

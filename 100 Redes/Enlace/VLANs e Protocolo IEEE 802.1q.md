# VLANs e Protocolo IEEE 802.1q

VLAN (*Virtual LAN*) é uma forma de segmentar uma LAN na [[Modelos OSI e TCP IP|camada de enlace]], criando dois ou mais [[Topologias e Segmentação de redes LAN|domínios de broadcast]] dentro de um, ou mais [[Topologias e Segmentação de redes LAN|switches]] gerenciáveis.

Cada VLAN se comporta como uma [[Topologias e Segmentação de redes LAN|bridge]] separada e tem sua própria tabela de comutação.

VLANs existe por um motivo principal: **Evitar desperdício de portas**.

Em um [[Topologias e Segmentação de redes LAN|switch]] nunca antes configurado, ele possui apenas a VLAN 1 com todas as portas, ou seja, uma [[Topologias e Segmentação de redes LAN|bridge]]:

- Sem criar outras VLANs, eu precisaria usar mais de um [[Topologias e Segmentação de redes LAN|switch]] para suportar duas redes sem quebrar o [[Topologias e Segmentação de redes LAN|domínio de broadcast]].
- VLANs me permitem criar [[Topologias e Segmentação de redes LAN|domínios de broadcast]] em um mesmo [[Topologias e Segmentação de redes LAN|switch]] (ex: rede A = VLAN 2, rede B = VLAN 3...).
- Eu posso ter VLANs dividas em `n` switches (ex: rede A = VLAN 2, no switch A e no switch B).
- Para poderem se comunicar (sem 802.1q) precisa ter um cabo ligando cada VLAN de um switch, na sua VLAN correspondente no outro switch.

VLANs são identificadas por números e não existe ligação entre uma VLAN e outro nível de enlance, logo um [[Topologias e Segmentação de redes LAN|domínio de broadcast]] não consegue se comunicar com outro na [[Modelos OSI e TCP IP|camada de enlace]].

**Exemplo de como uma VLAN funcionária em comparação com bridges:**![[exemplo_bridges_vlan.png]]

Para VLANs funcionarem, o [[Topologias e Segmentação de redes LAN|switch]] precisa de tabelas de configuração dizendo quais VLANs existem em cada porta. Quando um quadro chega na VLAN 1, ele deve ser encaminhado somente para portas marcadas com aquela VLAN, isso vale para [[Transmissão de dados|unicast, multicast e broadcast]].

De acordo com Tanenbaum, o [[Topologias e Segmentação de redes LAN|switch]] descobre de qual VLAN é o quadro a partir de 3 métodos mais comuns:

1. **Por porta:** Cada porta é associada a uma VLAN.
2. **Por MAC address:** Cada MAC address é associado a uma VLAN.
3. **Por IP:** Classificar olhando a carga útil.

***OBS:** O método 3 quebra a independência das camadas (camada de enlace decidindo pelo conteúdo da camada de rede) e é pedir dor de cabeça em migrações tipo IPv4 → IPv6.*

O 802.1q aparece justamente pra resolver isso.
## Protocolo IEEE 802.1q

O protocolo IEEE 802.1q (ou dot1q) é o padrão da indústria para marcação (tagging) de VLANs em redes [[Padrão Ethernet|Ethernet]].

A ideia do IEEE 802.1Q é carregar a identificação da VLAN no próprio quadro, evitando depender de heurísticas como “olhar o IP” (o que quebra a independência das camadas).

O 802.1q altera o quadro [[Padrão Ethernet|Ethernet]] adicionando 4 bytes entre o MAC de origem e o antigo campo EtherType/Length.

**Exemplo do cabeçalho 802.1q:**![[exemplo_cabecalho_802.1q.png]]

- **TPID (Tag Protocol Identifier, 16 bits):** Valor fixo `0x8100`, indicando que há uma tag 802.1Q.
- **TCI (Tag Control Information, 16 bits):** Controles da tag:
	- **PCP:** 3 bits que determinam a prioridade de acordo com o protocolo 802.1p.
	- **CFI:** Um único bit que identifica o formato do MAC address. Serve apenas para diferenciar Ethernet (0) de token ring (1).
	- **VLAN ID:** O número da VLAN em 12 bits, podendo ser de 1 até 4094 (0 e 4095 são reservados).

O antigo campo Type/Length do quadro [[Padrão Ethernet|Ethernet]] continua existindo, mas após a inserção da tag, ele passa a representar o tipo original do quadro (ex.: IPv4 `0x0800`, ARP `0x0806`, etc.).

***OBS:** O 802.1Q aumenta o tamanho máximo do quadro Ethernet de 1522 para 1526 bytes (por causa dos 4 bytes extras da tag).*

Além disso, o protocolo permite interligar [[Topologias e Segmentação de redes LAN|switches]] (ou um [[Topologias e Segmentação de redes LAN|switch]] e um roteador) transportando várias VLANs pelo mesmo meio físico, sem precisar de um cabo por VLAN.

**Exemplo de 802.1q por um único meio físico:**![[exemplo_802.1q_switches.png]]
### Trunk vs Access (tagged vs untagged)

Na prática, as portas de um [[Topologias e Segmentação de redes LAN|switch]] ficam em um destes papéis:

- **Porta access:** Associada a uma única VLAN. Entrega/recebe quadros sem a tag para hosts finais.
- **Porta trunk (802.1q):** Transporta múltiplas VLANs no mesmo meio físico (tipicamente entre [[Topologias e Segmentação de redes LAN|switches]]). Os quadros trafegam marcados.

Tanenbaum diz que: *"As tags só precisam existir onde switches/bridges precisam delas"*.

Por isso é comum o [[Topologias e Segmentação de redes LAN|switch]] inserir a tag ao encaminhar para um trunk e remover a tag ao entregar em access.

***OBS:** Se um host “legado” receber um quadro com `0x8100` no campo Type, pode descartar o quadro (não entende o EtherType). Por isso, em geral, quadros marcados não devem sair em portas access para máquinas que não suportam VLAN tagging.*
### Encaminhamento e tabelas por VLAN

Com tagging, o [[Topologias e Segmentação de redes LAN|switch]] consegue tratar cada VLAN como uma bridge lógica separada:

- Mantém uma tabela(s) de comutação por VLAN.
- Quando um quadro chega, o switch identifica a VLAN (pela porta access ou pela tag 802.1q) e encaminha apenas para as portas daquela VLAN.

Tanenbaum destaca que, para não voltar ao problema de configuração manual de bridges, o 802.1q descreve como construir essas tabelas dinamicamente, reaproveitando conceitos do 802.1D (Perlman / Spanning Tree).
## Referências

- Baseado no PDF do La salle [[redes-aula-03.pdf|Redes - Aula 03]] e [[redes-aula-04.pdf|Redes - Aula 04]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].
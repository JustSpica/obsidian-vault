# VLANs e IEEE 802.1Q
## VLANs

VLAN (*Virtual LAN*) é uma forma de segmentar uma LAN na [[Modelos OSI e TCP IP|camada de enlace]], criando dois ou mais [[Topologias e Segmentação de redes LAN|domínios de broadcast]] dentro de um, ou mais [[Topologias e Segmentação de redes LAN|switches]] gerenciáveis.

Cada VLAN se comporta como uma [[Topologias e Segmentação de redes LAN|bridge]] separada e tem sua própria tabela de comutação.

VLANs existe por um motivo principal: **Evitar desperdício de portas**.

Em um [[Topologias e Segmentação de redes LAN|switch]] nunca antes configurado, ele possui apenas a VLAN 1 com todas as portas, ou seja, uma [[Topologias e Segmentação de redes LAN|bridge]]:

- Sem criar outras VLANs, eu precisaria usar mais de um switch para suportar duas redes sem quebrar o [[Topologias e Segmentação de redes LAN|domínio de broadcast]].
- VLANs me permitem criar [[Topologias e Segmentação de redes LAN|domínios de broadcast]] em um mesmo switch (ex: rede A = VLAN 2, rede B = VLAN 3...).

VLANs são identificadas por números e não existe ligação entre uma VLAN e outro nível de enlance, logo um [[Topologias e Segmentação de redes LAN|domínio de broadcast]] não consegue se comunicar com outro na [[Modelos OSI e TCP IP|camada de enlace]].

**Exemplo de como uma VLAN funcionária em comparação com bridges:**![[exemplo_bridges_vlan.png]]

Para VLAN funcionar, o switch/bridge precisa de tabelas de configuração dizendo quais VLANs existem em cada porta. Quando um quadro chega na VLAN 1, ele deve ser encaminhado somente para portas marcadas com aquela VLAN, isso vale para [[Transmissão de dados|unicast, multicast e broadcast]].

De acordo com Tanenbaum, o [[Topologias e Segmentação de redes LAN|switch]] descobre de qual VLAN é o quadro a partir de 3 métodos mais comuns:

1. **Por porta:** Cada porta é associada a uma VLAN.
2. **Por MAC address:** Cada MAC address é associado a uma VLAN.
3. **Por IP:** Classificar olhando a carga útil.

***OBS:** O método 3 quebra a independência das camadas (camada de enlace decidindo pelo conteúdo da camada de rede) e é pedir dor de cabeça em migrações tipo IPv4 → IPv6.*

O 802.1Q aparece justamente pra resolver isso.

## IEEE 802.1Q (VLAN tagging)

### IEEE 802.1Q

Padrão para tagged VLANs (trunking):

- Campo VLAN ID: 12 bits (4094 VLANs possíveis)
- EtherType: `8100` (identifica quadro 802.1Q)
- PCP: 3 bits para prioridade (802.1p)
- CFI: 1 bit (Canonical Format Identifier)

### Como funciona

1. Switch insere tag VLAN no quadro antes de enviar pela porta trunk
2. Switch destinatário remove a tag e repassa para portas da VLAN correspondente
3. Máquinas comuns não reconhecem 802.1Q e descartam os quadros

### Tipos de Portas

- **Access:** Pertence a uma única VLAN, não espera tag
- **Trunk (802.1Q):** Transporta múltiplas VLANs, espera tag


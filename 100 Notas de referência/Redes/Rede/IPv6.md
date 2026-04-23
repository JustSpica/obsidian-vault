# IPv6

O IPv6 (Internet Protocol v6) é a evolução do [[IPv4]] na [[Modelos OSI e TCP IP|camada de rede]] da pilha TCP/IP. Ele mantém o modelo **sem conexão** e **best-effort**, mas tenta corrigir gargalos do IPv4, como espaço de endereçamento, eficiência de roteamento e processamento em roteadores.

Em redes [[Padrão Ethernet|Ethernet]], o IPv6 costuma aparecer no campo EtherType como `0x86DD`.

Tanenbaum resume a ideia como: Endereços muito maiores + cabeçalho mais simples + extensões opcionais.

Um endereço IPv6 tem no total **128 bits** (16 bytes) e é escrito como 8 grupos de 16 bits em **hexadecimal**, separados por `:` (ex.: `2000:4556:1010:1F30:1234:4560:00FF:DE02`).

Existem alternativas para minimizar a representação do hexadecimal, como:

- **Suprimir zeros à esquerda** em cada grupo (ex.: `00FF` -> `FF`).
- **Comprimir uma sequência contínua de grupos** `0000` com `::` (ex.: `0000:0000:0000:0000:0034:4560:00FF:DE02` -> `::34:4560:FF:DE02`)

No IPv6 existem três formas principais de comunicação:

- **[[Transmissão de dados|Unicast]]:** Um emissor para um único destino.
- **[[Transmissão de dados|Multicast]]:** Um emissor para um grupo de dispositivos.
- **Anycast:** Um emissor para “um de vários” destinos que compartilham o mesmo endereço (em geral, o mais próximo/mais bem roteado).

*OBS: IPv6 não tem [[Transmissão de dados|broadcast]]. Quando você precisa do “efeito broadcast”, usa multicast.*
## Cabeçalho IPv6

O IPv6 tem cabeçalho fixo de **40 bytes** (10 words de 32 bits). A simplificação existe para o roteador encaminhar mais rápido. 

Não há tamanho variável no cabeçalho base e não existe checksum no cabeçalho.

**Exemplo cabeçalho IPv6:** ![[exemplo_cabeçalho_ipv6.png]]

- **Versão:** `0110 = 6`.
- **Prioridade:** Similar ao ToS/DS no [[IPv4]] (priorização/QoS).
- **Rótulo de fluxo:** Identifica um fluxo que pode receber tratamento especial (ex.: áudio/vídeo em tempo real).
- **Comprimento dos dados:** Tamanho do payload (exclui os 40 bytes do cabeçalho base).
- **Próximo cabeçalho:** Indica o próximo cabeçalho (um cabeçalho de extensão ou um protocolo de transporte como TCP/UDP).
- **Limite de saltos:** Equivalente ao TTL (decrementado a cada roteador).
- **IP origem/destino:** 128 bits cada.

Opções/funcionalidades que eram “campos fixos” no IPv4 viraram **cabeçalhos de extensão** no IPv6. A ideia é, só paga o custo quando precisa.

Tanenbaum lista extensões típicas como: *hop-by-hop options*, *destination options*, *routing*, *fragment*, *authentication* e *encrypted security payload*.

*OBS: em geral, roteadores não precisam processar extensões (exceto as do tipo hop-by-hop, quando presentes).* 
## Hierarquia IPv6

O espaço IPv6 foi pensado para ser mais hierárquico (ex.: `<TIPO> <ID Provedor> <ID Assinante> <ID Sub-rede> <HOST>`), facilitando sumarização e roteamento, sendo que os 8 bits iniciais sempre dirá o tipo. O endereçamento IPv6 favorece mais hierarquia/agregação, o que tende a reduzir tabelas de roteamento e simplificar encaminhamento.

Uma sugestão comum (histórica) é separar **64 bits para o identificador de interface (host)**, o que permite formar esse identificador a partir do *MAC Address* no formato **EUI-64**.

Além disso pode ser definido um formato de compatibilidade comum em transição do IPv4 para o IPv6 (IPv4-mapped):

- Os 80 bits inicias em `0`.
- Os 32 bits finais com o endereço [[IPv4]]:
	- **IPv4:** `143.54.11.5`.
	- **IPv6:** `::FFFF:143.54.11.5`

*OBS: em redes reais, é comum evitar expor MAC diretamente e usar identificadores aleatórios/temporários (privacy extensions).* 

## Fragmentação e MTU (fim a fim)

No IPv6, **roteador nunca fragmenta** datagramas. Se um pacote for grande demais para algum enlace, o roteador descarta e retorna um erro (ICMPv6), e a origem ajusta o tamanho (descoberta de MTU do caminho).

Tanenbaum destaca duas consequências importantes:

- Fragmentação passa a ser **fim a fim** (apenas na origem, via cabeçalho de extensão de fragmento).
- O **MTU mínimo** aceito no IPv6 é **1280 bytes** (no IPv4 historicamente aparecia 576 bytes como referência).
## ARP e ICMPv6

O papel que o ARP tinha no IPv4 é absorvido no IPv6 por mecanismos do **ICMPv6** (Neighbor Discovery). Na prática, “descobrir vizinhos” e resolver endereço de enlace acontece via mensagens ICMPv6, sem um protocolo ARP separado.
## Referências

- Baseado no PDF do La salle [[redes-aula-14.pdf|Redes - Aula 14]] e [[redes-aula-15.pdf|Redes - Aula 15]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].

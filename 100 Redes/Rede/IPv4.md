# IPv4

O IPv4 (Internet Protocol v4) é o protocolo da [[Modelos OSI e TCP IP|camada de rede da pilha TCP/IP]]. Ele é sem conexão e fornece entrega de datagramas **best-effort** (não garante entrega, ordem, latência ou ausência de duplicação).

Tanenbaum comenta que a camada IP é o “serviço postal” da Internet. Você coloca um datagrama com um endereço de destino e a rede tenta entregá-lo, possivelmente passando por vários roteadores.

Um endereço IPv4 tem **32 bits** e normalmente é escrito em decimal pontuado (ex.: `192.168.0.10`). Internamente, é comum ser tratado como um *unsigned lont int* do C (`11000000 10101000 00000000 00001010` = `192.168.0.10`).

*OBS: A parte “rede” vs “host” não vem do número IP por [[Classes de IPv4|classe]], vem do [[CIDR e Mascara de Rede (IPv4)|CIDR]]*

*OBS: Classes (A/B/C/D/E) aparecem em material antigo e ainda em alguns exercícios. Para contexto, veja [[Classes de IPv4]].*
## Datagrama e cabeçalho IPv4

O IPv4 encapsula dados em um **datagrama** composto por cabeçalho + payload. O tamanho mínimo do cabeçalho é de **20 bytes** (5 words) e máximo **60 bytes** (com opções).

**Exemplo cabeçalho IPV4:** ![[exemplo_cabecalho_ipv4.png]]

- **Versão (4 bits):** `0100 = 4` no IPv4.
- **IHL (4 bits):** tamanho do cabeçalho em words de 32 bits (ex.: `5` significa 20 bytes).
- **Tipo de serviço (ToS - 8 bits):** Historicamente usado para prioridade/atraso.
- **Tamanho total (16 bits):** Tamanho total do datagrama em bytes (cabeçalho + payload), até ~64 KiB.
- **Identificação (16 bits):** Identifica um datagrama para fins de fragmentação. Todos os fragmentos do mesmo datagrama compartilham o mesmo identificador.
- ***Flags* (3 bits):** Controle de fragmentação (DF/MF):
	- **DF (*Don't Fragment*):** `1 = não deve ser fragmentado`, `0 = pode ser fragmentado`.
	- **MF (*More Fragments*):** `1 = Tem outrs fragmentos`, `0 = Não tem mais fragmentos`.
- ***Fragment Offset* (13 bits):** Posição do fragmento no datagrama original, em unidades de 8 bytes.
	- `FO = 0`: Este fragmento começa no byte 0.
	- `FO = 3`: Este fragmento começa no byte 24 (`3 * 8`).
- **TTL (8 bits):** Decrementado a cada roteador. Evita loop infinito e limita o caminho.
- **Protocolo (8 bits):** Indica o que vem depois do IP (ex.: ICMP `0x01`, TCP `0x06`, UDP `0x11`).
- ***Checksum* (16 bits):** Total de verificação apenas do cabeçalho. Como campos mudam no caminho, roteadores precisam recalcular.
- **IP origem/destino:** Endereços de origem e destino.
## Fragmentação

Cada enlace tem um limite de tamanho de quadro (MTU). Se um datagrama IPv4 for maior que o MTU de algum enlace no caminho, ele pode precisar ser fragmentado.

No IPv4, a fragmentação é não transparente. Os roteadores podem fragmentar, mas a remontagem acontece no destino (camada IP do host). Isso evita que gateways tenham que guardar estado para remontar, mas aumenta overhead (cada fragmento ganha cabeçalho IP).

Em geral, todo fragmento (exceto o último) precisa ter tamanho de dados múltiplo de 8

O IPv4 define um mínimo de encaminhamento sem fragmentar de **68 bytes**, mas é comum também considerar que hosts devem aceitar datagramas de pelo menos **576 bytes**.

*OBS: Fragmentação aumenta a chance de perda. Se um fragmento se perde, o datagrama inteiro não remonta. Na prática, é comum evitar fragmentação (ex.: ajustando MTU ou usando descoberta de MTU do caminho).* 
## Referências

- Baseado no PDF do La salle [[redes-aula-05.pdf|Redes - Aula 05]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].
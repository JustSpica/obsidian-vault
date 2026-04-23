# Classes de IPv4

No IPv4 original, endereços eram divididos em classes (A/B/C) com tamanho fixo de rede/host. 

Isso simplificava roteamento no início (menos combinações), mas desperdiçava muitos endereços e não escalou bem.

Hoje, classes são mais um assunto histórico. a Internet moderna usa [[CIDR e Mascara de Rede (IPv4)|CIDR]].

Um IP era visto como: **bits de rede** + **bits de host**:

- Endereço com bits de host todos `0`: **número da rede**.
- Endereço com bits de host todos `1`: **broadcast da rede**.
## Classes principais

- **Classe A:** `0RRRRRRR HHHHHHHH HHHHHHHH HHHHHHHH` (0.0.0.0 até 127.255.255.255)
	- 8 bits de rede (na prática 7 efetivos) + 24 bits de host.
- **Classe B:** `10RRRRRR RRRRRRRR HHHHHHHH HHHHHHHH` (128.0.0.0 até 191.255.255.255)
	- 16 bits de rede + 16 bits de host.
- **Classe C:** `110RRRRR RRRRRRRR RRRRRRRR HHHHHHHH` (192.0.0.0 até 223.255.255.255)
	- 24 bits de rede + 8 bits de host.
- **Classe D:** `1110xxx`. Reservado para [[Transmissão de dados|multicast]] e não usado na internet (224.0.0.0 até 239.255.255.255).
- **Classe E:** `1111xxx`. Reservado sem uso. (224.0.0.0 até 255.255.255.255).
	- `255.255.255.255` = [[Transmissão de dados|broadcast]] "global" (conceito do [[IPv4]])
## Por que classes “morreram”

Resumidamente classes pararam de ser usadas porque:

- Classe B acabou rapidamente.
- Classe A era grande demais.
- Classe C era pequena demais para muitas empresas.

Isso levou ao uso de [[CIDR e Mascara de Rede (IPv4)|CIDR]], que permite prefixo variável e alocações mais ajustadas.

## Referências

- Baseado no PDF do La salle [[redes-aula-05.pdf|Redes - Aula 05]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].
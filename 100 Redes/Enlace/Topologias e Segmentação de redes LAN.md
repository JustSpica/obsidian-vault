# Topologias e Segmentação de redes LAN

Topologia descreve como será a estrutura física e lógica da rede local, incluindo como os dispositivos são interconectados e como o meio de transmissão é dividido. Já segmentação é a técnica de reduzir colisões/ruídos em LANs.
## Topologia física vs Topologia lógica

- **Topologia física:** Define a forma como os dispositivos estão fisicamente conectados (cabos, hubs, salas/andares).
- **Topologia lógica:** Define como os dados trafegam na rede, independentemente da topologia física.
### Tipos de topologia física

- **Malha:** Cada host tem links dedicados com outros. Possui alta redundância, caro, usado em WAN.
- **Estrela:** Cada host liga em um "centralizador" (hub/switch). Possui um ponto central de falha, mas é mais comum atualmente.
- **Barramento:** Um único meio físico compartilhado por todos os dispositivos. Tem problema de escalabilidade e colisão em toda a rede.
- **Anel:** Máquinas conectadas em círculo. Token passing, latência previsível
- **Híbrida:** Combinações de topologias. Mais flexível

***OBS:** No livro de Tanenbaum sobre redes de computadores, LANs de difusão aparecem muito associadas a **barramento** e **anel**. Em barramento, em geral só um transmite por vez e precisa de um mecanismo de arbitragem. Em anel, também existe regra para arbitrar acessos.* 
## Domínio de broadcast vs Domínio de colisão

- **Domínio de broadcast:** É um grupo de dispositivos que recebem quadros [[Transmissão de dados|broadcast]] (destinados a `FF:FF:FF:FF:FF:FF`).
- **Domínio de colisão:** Grupo de dispositivos que competem pelo mesmo meio de transmissão. Quando dois ou mais dispositivos transmitem um quadro simultaneamente, ocorre uma colisão.
### CSMA/CD

Tanenbaum explica que, quando dois dispositivos transmitem simultaneamente, ocorre colisão. Com CSMA/CD, um dispositivo escuta o canal e, se ele estiver livre, pode transmitir. Durante a transmissão, ele monitora para detectar colisão e se detectar colisão ele interrompe a transmissão, espera um tempo aleatório e tenta enviar denovo.
## HUBs, Bridges e Switches

- **HUBs:** É um equipamento antigo já deprecado. Todas as suas portas formam um mesmo domínio de broadcast/colisão.
- **Bridges:** Tem a mesma função de um HUB, com a diferença que:
	- Precisa manter uma tabela ***MAC address*** de todos os dispositivos conectados.
	- Monta essa tabela de forma estática (configuração manual) ou dinâmica (aprendizado).
	- Trabalha em modo promíscuo (recebe todos os quadros).
	- Repassa quadros somente se: MAC destino = broadcast ou MAC destino estiver no outro lado da bridge.
- **Switches:** Inicialmente é um Bridge, com mais portas onde cada porta é um domínio de colisão. (Sim, CSMA/CD se torna inutil com switches).

Tanenbaum comenta que protocolos de camadas superiores usam difusão (ex: descobrir endereço MAC por IP), e que ao interconectar muitas LANs, o volume de broadcast cresce.

***OBS:** Ambos os 3 dispositivos operam na [[Modelos OSI e TCP IP|camada de enlace]].*
***OBS2:** Segmentar com bridge/switch ajuda muito contra colisão, mas não resolve sozinho excesso de broadcast.*
### Cascateamento

Nada mais é do que a conexão de múltiplos hubs/bridges/switches em série. 

Problema: se não for configurado corretamente, máquinas de redes diferentes podem ficar no mesmo domínio de broadcast.

**Exemplo de cascateamento:** ![[exemplo_cascateamento_hubs.png]]
## Referências

- Baseado no PDF do La salle [[redes-aula-02.pdf|Redes - Aula 02]] e [[redes-aula-03.pdf|Redes - Aula 03]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].
# Ethernet (IEEE 802.x)

O padrão Ethernet (IEEE 802.x) é uma família de padrões que define as camadas **física** e ***enlace*** da pilha [[Modelos OSI e TCP IP|TCP/IP]], para redes locais.

Alguns protocólos mais conhecidos da família IEEE 802.x:

- **802.1:** Padrão de gerenciamento entre switches, bridges, VLANs e etc.
- **802.3:** Padrão Ethernet com fio 
- **802.11:** Padrão Wi-fi
- **802.15:** Padrão Bluetooth

Algumas formas de conexão do padrão 802.3:

- **10Base2:** Cabo coaxial, sem necessidade de hubs.
- **10BaseT:** Cabo par trançado. 10Mb/s
- **100BaseTX:** Fast Ethernet. 100Mb/s
- **1000BaseT:** Gigabit em cobre. 1000Mb/s

**Regra prática:** O ***"Base"*** indica banda-base e os sufixos (T, TX, SR, LR...) sugerem o meio/alcance (cobre, fibra...), dependendo da familia. 
## IEEE 802.3 e Ethernet II

Existem dois jeitos de identificar o protocolo carregado no quadro:

- **Ethernet II (DIX):** No header do quadro ethernet, o campo de 2 bytes é um ***EtherType*** (ex.: IPV4 - 0800, ARP - 0806, IPX - 8037, IPV6 - 86DD)
- **IEEE 802.3 (Com 802.2 LLC/SNAP):** No header do quadro ethernet, o campo de 2 bytes vira ***length***. A identificação do protocolo vai em um header extra (LLC/SNAP) dentro dos dados

**Exemplo de quadro Ethernet:** ![[exemplo_quadro_ethernet.png]]
Se o tamanho do campo de 16 bits for <= 1500 (05DC) ele expressa ***length***, sendo IEEE 802.3, e se for > 1500 ele expressa ***EtherType***, sendo Ethernet II.

Ethernet II é mais comum em LAN corporativa/Internet, mas o termo "802.3" continua sendo usado para falar do "Padrão Ethernet" como um todo.

***OBS:** Preâmbulo (sequência de bits para sincronizarr o receptor) e SFD (byte que marca o inicio do quadro lógico ethernet) fazem parte da camada física e não da camada de enlace.*

***OBS:** O tamanho minimo do payload em um quadro é 46 bytes e o máximo de dados é 1500 bytes. Se o payload for < 46 bytes, o campo será completado com padding.*

Na [[Modelos OSI e TCP IP|camada de enlace]], a placa de rede só passa para as camadas superiores se:

1. Receber um pacote [[Transmissão de dados|broadcast]].
2. Se o MAC destino for igual ao MAC da placa de rede.
3. Se o pacote for [[Transmissão de dados|multicast]] e a placa de rede estiver participando desse grupo.
4. Se a placa estiver em modo promíscuo (A placa aceita todos os pacotes)

## Referências

- Baseado no PDF do La salle [[redes-aula-02.pdf|Redes - Aula 02]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].
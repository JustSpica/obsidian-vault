# Modelos de camadas

Cada camada possui uma função especifica, comunicando-se apenas com a superior e a inferior, possibilitando a troca de camada por outra de forma transparente (sem interferências entre as camadas).
## **Modelo OSI**

Dividido em 7 camandas:

1. **Física:** Transmissão de dados por sinais digitais (0v = 0, 5v = 1). Formas de transmissão: [[Transmissão de dados|simplex, half-duplex ou full-duplex]].
2. **Enlace:** Estabele a conexão ponto a ponto, realizando controle de fluxo e detecção de erros, através do ***MAC address*** e ***LAN***.
3. **Rede:** Traça o caminho dos pacotes da origem até o destino. Roteamento e endereçamento IP.
4. **Transporte:** Realiza o transporte confiável dos pacotes da origem até destino.
5. **Sessão:** Realiza a conexão entre os dispositivos, estabelecendo uma comunicação entre eles.
6. **Apresentação:** Padroniza os dados em um formato em comum, entendido pelo protocolo usado, para mostrar na camada de aplicação.
7. **Aplicação:** Um programa obtem os dados e o usuário pode interagir com ele.

## **Modelo TCP/IP**

O modelo TCP/IP bruto é divido em 4 camadas, mas para fins de estudo vou usar o modelo Tanenbaum que adiciona a camada **física** como uma camada própria do modelo.

1. **Física:** Conversão de bits em sinais elétricos. (No modelo tradicional, essa camada é aglutinada com a camada de enlace).
2. **Enlace:** Igual ao modelo OSI, com a diferença que usa [[Padrão Ethernet|Ethernet]].
3. **Rede:** Igual ao modelo OSI, com a diferença que usa IPV4/IPV6, ICMP, ARP...
4. **Transporte:** Igual ao modelo OSI, com a diferença que permite a multiplexação via portas e usa TCP ou UDP.
5. **Aplicação:** Junção das camadas **sessão, apresentação e aplicação** do modelo OSI. É o lugar onde é encapsulado outros protocolos como **DHCP**, **HTTP**, **DNS** e por ai vai.

### **Processo de Encapsulamento**

Para os dados trafegarem, cada camada adiciona seu próprio cabeçalho nos dados vindos de cima:
1. **Aplicação:** Gera os Dados. 
2. **Transporte:** Adiciona cabeçalho (portas origem/destino) e vira segmento (TCP) ou datagrama (UDP). 
3. **Rede:** Adiciona cabeçalho (IP origem/destino) e vira pacote.
4. **Enlace:** Adiciona cabeçalho (MAC origem/destino) e checagem de erro para gerar um quadro.
5. **Física:** Transmite como bits no fio/ar.

## **Referências**

- Baseado no PDF do La salle [[redes-aula-01.pdf|Redes - Aula 01]].
- O vídeo [Como sua Internet Funciona | Introdução a Redes Parte 3](https://youtu.be/gcv5hXyTcIo?t=103]) da série de redes do canal Fábio Akita, a partir do momento **01:43** explica o comparativo entre o modelo OSI e TCP/IP.
- Os artigos [Desmistificando Redes de Computadores: Diferenças entre Modelos OSI e TCP/IP.](https://www.estrategiaconcursos.com.br/blog/redes-computadores-modelos-osi-tcp-ip/) e [Principal diferença entre o modelo TCP/IP e OSI](https://www.fortinet.com/br/resources/cyberglossary/tcp-ip-model-vs-osi-model) explicam de forma resumida, e boa, sobre os dois modelos.
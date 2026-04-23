# Modelos OSI e TCP/IP

Modelos de referência organizam uma rede em camadas. A ideia central é modularidade, cada camada oferece serviços para a de cima e usa os serviços da de baixo, reduzindo acoplamento e facilitando evolução/troca de implementações.

*OBS: Modelo de referência é diferente de uma pilha de protocolos concreta. Ex.: o modelo OSI é uma referência, já a Internet usa a pilha TCP/IP (IP, TCP, UDP, etc.).*
## Modelo OSI (referência)

O OSI foi pensado como um modelo geral e mais formal para padronização. Ele define **7 camadas**:

1. **Física:** Transmissão de bits brutos pelo meio (sinais, sincronização, conectores, taxas).
2. **Enlace:** Entrega nó-a-nó; quadros, detecção de erros e controle de acesso ao meio (MAC) em redes de difusão.
3. **Rede:** Roteamento e endereçamento lógico para levar pacotes entre redes.
4. **Transporte:** Comunicação fim a fim entre processos; segmentação e confiabilidade/ordenação quando necessário.
5. **Sessão:** Controle de diálogo e gestão de sessão (ex.: sincronização/checkpoints).
6. **Apresentação:** Representação dos dados (sintaxe/semântica, codificações/formatos).
7. **Aplicação:** Protocolos usados diretamente por aplicações (ex.: Web, e-mail, nomes).

Tanenbaum destaca como grande contribuição do OSI a distinção explícita entre **serviço**, **interface** e **protocolo** (o que a camada fornece vs como se acessa vs como é implementado).

Na prática, os protocolos OSI raramente são usados, mas o modelo continua útil para comparação e raciocínio.
## Modelo TCP/IP (Internet)

No TCP/IP, os protocolos vieram primeiro e o modelo virou uma descrição da pilha da Internet. A forma clássica do modelo tem **4 camadas**:

1. **Enlace (host/rede):** Como um host se conecta e envia/recebe em uma rede específica (ex.: Ethernet, Wi-Fi).
2. **Rede:** Entrega de pacotes entre redes (IP) e roteamento.
3. **Transporte:** Comunicação fim a fim (TCP/UDP) e multiplexação por portas.
4. **Aplicação:** Protocolos de alto nível usados por programas (ex.: HTTP, DNS, SMTP).

Tanenbaum separa a camada de enlace do modelo TCP/IP em **Física + Enlace**, resultando em um modelo de **5 camadas**, mas estritamente não faz parte do modelo TCP/IP original.

No TCP/IP não existem camadas separadas de **Sessão** e **Apresentação**, essas funções aparecem quando necessário dentro da camada de **Aplicação**.
## Comparação

- **Camadas:** OSI (7) vs TCP/IP (4, ou 5 na versão didática).
- **Formalismo:** OSI separa bem serviço/interface/protocolo e TCP/IP historicamente é menos rigoroso nessa distinção.
- **Origem:** OSI foi definido antes dos protocolos e TCP/IP descreve protocolos já existentes.
- **Generalidade:** OSI é mais “universal” como modelo e TCP/IP descreve muito bem a pilha da Internet, mas é pior para descrever outras pilhas.
- **Conexões:** no TCP/IP, a camada Internet é sem conexão e na camada de transporte existem opções com e sem conexão (ex.: TCP vs UDP). O OSI contempla modos diferentes dependendo da camada.
## Encapsulamento

Ao descer a pilha, cada camada adiciona informação de controle (tipicamente um cabeçalho. Em enlace é comum haver **trailer/FCS**). No destino ocorre o **desencapsulamento**:

1. **Aplicação:** Gera os Dados.
2. **Transporte:** Adiciona cabeçalho (portas origem/destino) e vira segmento (TCP) ou datagrama (UDP).
3. **Rede:** Adiciona cabeçalho (IP origem/destino) e vira pacote.
4. **Enlace:** Adiciona cabeçalho (MAC origem/destino) e checagem de erro para gerar um quadro.
5. **Física:** Transmite como bits no fio/ar.

*OBS: Em geral, o cabeçalho de enlace é local por salto (muda a cada rede). Já IP e transporte são fim a fim (com alguns campos podendo ser atualizados no caminho, como TTL/hop limit).* 
## Referências

- Baseado no PDF [[redes-resumo.pdf|Redes - Resumo]] e [[redes-aula-01.pdf|Redes - Aula 01]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].
- O vídeo [Como sua Internet Funciona | Introdução a Redes Parte 3](https://youtu.be/gcv5hXyTcIo?t=103%5D) da série de redes do canal Fábio Akita, a partir do momento **01:43** explica o comparativo entre o modelo OSI e TCP/IP.
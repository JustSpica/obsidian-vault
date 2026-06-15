# TCP

O TCP (*Transmission Control Protocol*) é um protocolo da [[Modelos OSI e TCP IP|camada de transporte]] que oferece um **fluxo de bytes confiável, ordenado e orientado à conexão** sobre uma rede IP que, por si só, não garante entrega, ordem nem ausência de perdas.

No [[IPv4]], o TCP aparece no campo **Protocolo** como `0x06`. No [[IPv6]], ele aparece no campo **próximo cabeçalho**.

Tanenbaum resume a ideia central: o TCP existe para dar às aplicações a confiabilidade que o IP não fornece.

*OBS: O TCP não transforma a rede em confiável. Ele mascara perdas, desordem e duplicações usando estado, numeração, confirmações, janelas, timers e retransmissões.*

## Serviço do TCP

O TCP é usado quando a aplicação precisa de uma conversa mais controlada do que a oferecida pelo [[UDP]]. Ele fornece:

- **Conexão:** Antes de trocar dados, cliente e servidor estabelecem uma conexão.
- **Entrega confiável:** Dados perdidos podem ser retransmitidos.
- **Ordem:** A aplicação recebe os bytes na ordem correta.
- **Fluxo de bytes:** TCP não preserva fronteiras de mensagens.
- **[[Transmissão de dados#Direção de fluxo de dados|Full-Duplex]]:** Os dois lados podem enviar e receber ao mesmo tempo.
- **Ponto a ponto:** uma conexão TCP liga exatamente dois pontos finais.

Uma conexão TCP é identificada pelo par de soquetes das duas pontas, isto é, pela combinação: `IP origem + porta origem + IP destino + porta destino`

Isso permite que várias conexões cheguem à mesma porta de servidor, desde que a combinação completa de IPs e portas seja diferente.

*OBS: TCP não faz broadcast nem multicast. Esse tipo de comunicação é típico de UDP ou de mecanismos em outras camadas.*

## Fluxo de bytes, não mensagens

O TCP entrega uma sequência contínua de bytes. Isso significa que ele não promete entregar os dados nas mesmas divisões em que a aplicação escreveu:

Se por exemplo, a aplicação envia `4` blocos de `512 bytes`, o TCP pode entregar os mesmos `4` blocos de `512 bytes`, ou `2` blocos de `1024 bytes`, ou `1` único bloco de `2048 bytes`. 

Na prática, se a aplicação precisa separar mensagens, ela deve criar sua própria regra: tamanho fixo, delimitador, cabeçalho com tamanho, etc.

## Estabelecimento de conexão

O TCP usa o **three-way handshake** para abrir uma conexão:

1. Cliente envia `SYN`.
2. Servidor responde `SYN + ACK`.
3. Cliente responde `ACK`.

Durante esse processo, cada lado escolhe um **número de sequência inicial**. Esse número não precisa começar em `0`, ele serve como base para numerar o fluxo de bytes daquele sentido da conexão.

*OBS: O `SYN` consome espaço de sequência. Isso permite confirmar o próprio estabelecimento da conexão sem ambiguidade.*

## Sequência e ACK

O TCP numera bytes, não pacotes abstratos. Cada byte no fluxo tem uma posição lógica.

Dois campos são centrais:

- **Número de sequência:** Indica a posição dos bytes enviados naquele segmento.
- **Número ACK:** Indica o **próximo byte esperado** pelo receptor.

Essa confirmação é cumulativa. Se o receptor envia `ACK = 5000`, ele está dizendo: Recebi tudo até 4999, o próximo byte que espero é 5000.

Se um segmento se perde, o transmissor pode perceber pela falta de confirmação ou por sinais de ACKs repetidos, dependendo da implementação e dos mecanismos ativos.

## Janela deslizante

O TCP não precisa esperar a confirmação de cada segmento antes de enviar o próximo. Ele usa uma **janela deslizante** para permitir vários bytes em trânsito ao mesmo tempo.

A janela define quanto o transmissor pode enviar sem receber novas confirmações.

- **Janela pequena:** Consome pouca memória, mas pode travar o desempenho.
- **Janela grande:** Melhora vazão, mas exige mais buffers e pode amplificar retransmissões se houver perda.
- **Janela `0`:** Funciona como um pause. O receptor está dizendo que recebeu os dados anteriores, mas não tem espaço agora.

Tanenbaum destaca uma nuance importante: No TCP, **confirmação** e **permissão para enviar mais dados** são coisas relacionadas, mas não iguais. O receptor pode confirmar que recebeu até certo byte e, ao mesmo tempo, anunciar janela `0`.

## Retransmissão e timeout

Quando o TCP envia dados, ele acompanha confirmações e timers. Se uma confirmação não chega dentro do tempo esperado, o segmento pode ser retransmitido.

Esse timeout não pode ser fixo de qualquer jeito:

- Se for curto demais, gera retransmissões desnecessárias;
- Se for longo demais, demora para recuperar perdas reais;
- Se a rede muda, o tempo ideal também muda.

Por isso, implementações reais estimam dinamicamente o RTT (*round-trip time*) e ajustam timers de retransmissão.

*OBS: Em redes cabeadas modernas, muitas perdas são tratadas como sinal de congestionamento. Em redes sem fio, isso é mais delicado, porque perdas podem vir do meio físico e não necessariamente de congestionamento.*

## Cabeçalho TCP

O cabeçalho TCP mínimo tem **20 bytes**, podendo crescer com opções.

**Exemplo cabeçalho TCP:** ![[exemplo_cabecalho_tcp.png]]

- **Porta de origem (16 bits):** Identifica o processo de origem junto com o IP de origem.
- **Porta de destino (16 bits):** Identifica o processo de destino junto com o IP de destino.
- **Número de sequência (32 bits):** Posição dos bytes enviados.
- **Número ACK (32 bits):** Próximo byte esperado.
- **HLEN/Data Offset (4 bits):** Tamanho do cabeçalho TCP em *words* de `32 bits`.
- **Flags (6 bits):** Controlam o tipo de segmento ou comportamento esperado:
	- **URG:** Pacote possui dados urgentes.
	- **ACK:** Confirmação.
	- **PSH (Push):** Descarregamento de buffer.
	- **RST:** Resetar/Abortar sessão.
	- **SYN:** *Synchronize sequence number*.
	- **FIN:** Finalização de conexão.
- **Janela (16 bits):** Quantidade de bytes que o receptor aceita a partir do ACK anunciado.
- **Checksum (16 bits):** Detecta corrupção no segmento.
- **Ponteiro urgente (16 bits):** Usado com `URG`.
- **Opções:** Permitem recursos extras, como tamanho máximo de segmento e escala de janela.

*OBS: Ferramentas modernas podem mostrar mais flags do que as seis clássicas, porque parte dos bits antes tratados como reservados ganhou uso posterior.*

## Encerramento da conexão

Como a conexão TCP é [[Transmissão de dados|full-duplex]], cada sentido pode ser encerrado separadamente:

1. Um lado envia `FIN`, dizendo que não tem mais dados para enviar.
2. O outro confirma com `ACK`.
3. O outro lado também envia seu `FIN` quando terminar.
4. O primeiro confirma com `ACK`.

Na prática, alguns desses passos podem ser combinados, mas a ideia é que cada sentido da comunicação precisa ser fechado de forma controlada.

## Concorrência em servidores TCP

Na programação com sockets, o servidor TCP costuma seguir este fluxo:

1. `bind`: Associa o socket a uma porta local.
2. `listen`: Coloca a porta em modo passivo, aguardando conexões.
3. `accept`: Bloqueia até chegar uma conexão.
4. `accept` Devolve um **socket de conexão** para conversar com aquele cliente.

Isso separa duas coisas:

- **Socket Ouvinte:** Fica na porta do serviço, esperando novas conexões.
- **Socket de Conexão:** Representa uma conversa específica com um cliente.

A pilha TCP mantém o estado de cada conexão. Por isso, um servidor pode ter vários clientes conectados na mesma porta de serviço, cada um com seu próprio socket de conexão.

A estratégia mais abordada para lidar com concorrência, tende a ser o **gerenciamento de um pool de processos filhos ou threads**, onde o processo pai aceita conexões e repassa para filhos disponíveis. É mais rápido, mas mais complexo de implementar: ![[exemplo_concorrencia_tcp.png]]
 
Na prática, servidores reais costumam usar variações de processos, threads, pools ou modelos orientados a eventos.

## Referências

- Baseado no PDF do La salle [[redes-aula-13.pdf|Redes - Aula 13]].
- Baseado no livro [[computer-networks-tanenbaum.pdf|Redes de computadores de Tanenbaum]].

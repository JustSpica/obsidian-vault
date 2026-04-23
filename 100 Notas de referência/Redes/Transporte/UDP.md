# UDP

O UDP (*User Datagram Protocol*) é um protocolo da [[Modelos OSI e TCP IP|camada de transporte]] da pilha TCP/IP. Ele é **sem conexão** e oferece um serviço simples de envio de datagramas entre [[Portas e processos|processos, identificados por portas]].

No [[IPv4]], o UDP aparece no campo **Protocolo** como `0x11`. No [[IPv6]], ele pode aparecer no campo **próximo cabeçalho**.

Tanenbaum resume bem a ideia: o UDP é basicamente o IP com um cabeçalho pequeno e com o acréscimo de **multiplexação/demultiplexação por portas**.

*OBS: O UDP não estabelece sessão, não faz handshake e não mantém estado de conexão como o TCP.*
## Cabeçalho UDP

O cabeçalho UDP é bem pequeno: **8 bytes**.

- **Porta de origem (16 bits)**
- **Porta de destino (16 bits)**
- **Tamanho (16 bits):** tamanho total do segmento UDP (cabeçalho + dados).
- **Checksum (16 bits):** usado para detectar corrupção.

Como o cabeçalho é pequeno e não há mecanismos extras de controle, o overhead do UDP é baixo.

Tanenbaum destaca que o principal ganho do UDP sobre “usar IP bruto” é justamente a existência das portas. Sem elas, a camada de transporte não teria como entregar os dados ao processo correto.
## O que o UDP não garante

O UDP é um serviço **não confiável** e **best-effort**. Isso significa que ele:

- não garante entrega;
- não garante ordem de chegada;
- não garante ausência de duplicação;
- não garante controle de fluxo;
- não garante retransmissão;
- não garante sincronização entre emissor e receptor.

Se alguma dessas propriedades for importante, a responsabilidade sai do UDP e vai para a [[Modelos OSI e TCP IP|camada de aplicação]], implementando sua própria lógica, ou outro protocolo de transporte, como o **TCP**.

*OBS: Em materiais introdutórios costuma-se dizer que o checksum do UDP é “opcional”. Historicamente isso é verdade no IPv4. Na prática moderna, abrir mão dele raramente faz sentido.*
## Quando o UDP faz sentido

Apesar de não ser confiável, o UDP é muito útil quando a simplicidade e a latência baixa valem mais do que controle fino de entrega.
### Requisição/resposta curta

Um caso clássico é o modelo cliente/servidor com mensagens pequenas:

- cliente envia uma pergunta curta;
- servidor devolve uma resposta curta;
- se houver perda, o cliente faz *timeout* e tenta de novo.

O exemplo mais clássico é o **DNS**, em que uma consulta curta pode ser respondida com um único pacote UDP, sem precisar abrir e encerrar conexão.

Tanenbaum destaca justamente essa vantagem, com UDP, muitas vezes bastam **duas mensagens pela rede** (pedido e resposta), enquanto um protocolo orientado a conexão exigiria tráfego adicional de configuração.
### Multimídia e tempo real

Outro caso importante é multimídia em tempo real:

- **VoIP**
- Áudio ao vivo
- Vídeo ao vivo
- Fluxos RTP sobre UDP

Nesses cenários, um pacote atrasado muitas vezes vale quase o mesmo que um pacote perdido. Reenviar pode fazer o dado chegar tarde demais para ser útil.

Por isso, é comum preferir:

- aceitar pequenas perdas;
- interpolar/reconstruir no destino quando possível;
- evitar retransmissões demoradas.

Essa ideia também aparece no Tanenbaum ao discutir RTP sobre UDP, em aplicações de tempo real, normalmente é melhor estimar o que faltou do que pedir retransmissão.
## UDP em rede local

Em uma rede local, a chance de perda, duplicação ou desordenamento costuma ser menor do que em trajetos maiores com vários roteadores.

Em uma LAN com equipamentos saudáveis:

- É improvável haver desordenamento.
- Perdas tendem a ser menos comuns.
- O custo de usar um protocolo mais pesado pode não compensar.

Por isso, em alguns cenários locais, o UDP pode ser uma solução bem razoável.

*OBS: “menos provável” não significa “impossível”. Aplicações críticas continuam precisando tratar erro, perda e validação.*
## Confiabilidade sobre UDP

Se você quiser confiabilidade sobre UDP, ela precisa ser implementada na [[Modelos OSI e TCP IP|camada de aplicação]].

Os problemas clássicos a tratar são:

- Perda de pacotes;
- Duplicação de pacotes;
- Pacotes fora de ordem;
- Mistura de mensagens de clientes diferentes;
- Definição de *timeout* e retransmissão.
## Concorrência em servidores UDP

Outro detalhe importante é que o UDP também não entrega, por si só, uma estrutura pronta de concorrência como o TCP entrega com conexões separadas.

Para atender vários clientes, o servidor precisa identificar cada conversa pelo menos com o par **IP + Porta** de origem

Duas estratégias comuns seriam:

- **Um servidor central com tabela de clientes/estado**, despachando os pacotes corretamente.
- **Um processo filho por cliente**, possivelmente migrando a conversa para outra porta UDP.

O exemplo clássico é o **TFTP**, que usa UDP e trabalha com troca para portas específicas por sessão.
## Referências

- Baseado no PDF [[redes-aula-12.pdf|Redes - Aula 12]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].

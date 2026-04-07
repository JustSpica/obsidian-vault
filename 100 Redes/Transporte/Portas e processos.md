# Portas e processos

O papel principal da [[Modelos OSI e TCP IP|camada de transporte]] aqui é permitir que os dados cheguem ao **processo certo** dentro da máquina de destino.

- **Porta de origem:** identifica de onde a mensagem saiu e ajuda no caminho da resposta.
- **Porta de destino:** indica qual processo/serviço deve receber os dados.

Em geral:

- **0 a 1023:** portas bem conhecidas (*well-known*), gerenciadas pela IANA.
- **1024 a 49151:** portas registradas.
- **49152 em diante:** portas efêmeras/dinâmicas, comuns em clientes.

Exemplos comuns:

- **53:** DNS
- **67/68:** DHCP
- **80:** HTTP
- **443:** HTTPS

O sistema operacional mantém internamente a associação entre **porta** e **processo dono da porta**. Quando chega um segmento UDP, a carga útil é entregue ao processo associado à porta de destino.
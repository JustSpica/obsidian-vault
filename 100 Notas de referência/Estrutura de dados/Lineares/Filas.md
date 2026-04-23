# Fila

Fila é uma estrutura de dados linear que segue o princípio **FIFO (First-In, Last-Out)**, onde o primeiro elemento que é adicionado na estrutura é o primeiro elemento que é removido ou processado, como se fosse uma fila de pessoas esperando para comprar um ingresso.

**Exemplo de como uma fila FIFO funciona:** ![[exemplo_acao_fila.png]]

Assim como a [[Pilhas|pilha]], toda fila deve oferecer um conjunto básico de operações simples e eficientes, que idealmente serão executadas em tempo constante $O(1)$:

- **enqueue:** Adiciona um elemento no final da fila. Se a fila tiver cheia, irá causar um erro de ***overflow***.
- **dequeue**: Remove o elemento no início da fila. Se a fila estiver vazia, irá causar um erro de ***underflow***.
- **peek/front**: Retorna o primeiro elemento da fila, sem remove-lo.
- **rear/back:** Retorna o último elemento da fila, sem remove-lo.
- **size**: Retorna o tamanho da fila.
- **isEmpty**: Retorna um *boolean value* verificando se a fila está vazia ou não.
- **isFull**: Retorna um *boolean value* verificando se a fila está cheia.

Abaixo uma lista das possiveis aplicações de filas:

- **Multiprogramação:** Significa que vários programas estão em execução na memória principal. É essencial organizar esses múltiplos programas, que são organizados em filas.
- **Agendamento de Tarefas:** O computador tem a tarefa de executar um determinado número de tarefas agendadas para serem executadas uma após a outra. Essas tarefas são atribuídas ao processador uma a uma, organizadas em uma fila.
- **Buffer:** Funcionar como um buffer entre um dispositivo lento e um rápido. Por exemplo, teclado e CPU, e dois dispositivos em rede.
## Tipos de fila

Filas podem ser classificadas em 3 tipos:

- **Fila Simples:** Ela simplesmente segue a estrutura **FIFO**. Só pode inserir um elemento no final e remover o elemento da frente da fila.
- **Fila Dupla (Dequeue):** Em uma *dequeue*, as operações de adicionar e remover um elemento podem ser realizadas em ambas as extremidades. Além disso elas podem ter restrições como ***Input Restricted*** (só pode adicionar por um dos lados da fila, mas pode remover por ambos) e ***Output Restricted*** (só pode remover por um dos lados da fila, mas pode adicionar por ambos).
- **Fila Circular:** Em uma fila circular, os elementos da fila atuam como um anel circular. O funcionamento de uma fila circular é semelhante ao da fila simples, exceto pelo fato de que o último elemento é conectado ao primeiro.
### Fila de prioridade

É um tipo de fila que organiza os elementos com base em seus valores de prioridade. Cada elemento tem uma prioridade associada, onde no momento que ele é inserido na fila sua posição é definida com base em sua prioridade.

O método mais comum de se implementar uma fila de prioridade é usando uma [[Binary Heap]].

Filas de prioridade possuem dois tipos, sendo eles ***Ascending Order*** (onde elementos com valores menores tem maior prioridade) e ***Descending Order*** (onde elementos com valores maiores tem maior prioridade).

**Exemplo de uma fila do tipo *Descending Order:*** ![[exemplo_descending_order_queue.png]]
## Referências

- Os artigos [Introduction to Queue Data Structure](https://www.geeksforgeeks.org/dsa/introduction-to-queue-data-structure-and-algorithm-tutorials/) e [Applications, Advantages and Disadvantages of Queue](https://www.geeksforgeeks.org/dsa/applications-advantages-and-disadvantages-of-queue/) do geeksforgeeks tem uma boa explicação sobre o que são filas. Essa nota é quase que inteiramente baseada nesses artigos.
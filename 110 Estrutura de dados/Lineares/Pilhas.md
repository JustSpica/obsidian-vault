# Pilhas

Pilha é uma estrutura de dados linear que segue uma ordem específica na qual as operações são realizadas. 

Toda pilha se baseia em um princípio simples: **LIFO (Last-In, First-Out)**, isto é, o último elemento que entra na pilha é o primeiro a ser desempilhado. Os novos elementos são sempre inseridos no topo da pilha e a remoção de um elemento também só acontece a partir do topo dela.

**Exemplo de como a pilha LIFO funciona:** ![[exemplo_acao_pilha.png]]

Uma pilha pode ter um tamanho fixo ou dinâmico:

- **Tamanho fixo:** É geralmente implementada usando [[Arrays|arrays]]. Assim que a pilha atinge essa capacidade, nenhum elemento pode ser adicionado nela, causando ***overflow***. Se a pilha estiver vazia e houver a tentativa de remover um elemento dela, irá causar um erro de ***underflow***.
- **Tamanho dinâmico:** Se a pilha estiver cheia, seu tamanho se expande para permitir mais elementos, e a medida que elementos são desempilhados, o uso de memória alocada também diminui. Pode ser implementado usando [[Listas encadeadas|listas encadeadas]] ou [[Arrays|arrays]] dinâmicos.

Toda a pilha deve oferecer um conjunto básico de operações, e esse conjunto básico deve ser simples e eficiente, de modo que idealmente todas as operações abaixo devem ser executadas em tempo constante $O(1)$:

- **push:** Para inserir elementos na pilha.
- **pop:** Para remover o elemento superior na pilha.
- **top:** Retorna o elemento superior da pilha.
- **isEmpty:** Para validar com um *boolean value* se a pilha está vazia.
- **size:** Retorna o tamanho da pilha.

Abaixo uma lista das aplicações de pilhas:

- **Gerenciamento de funções (Call Stack):** Pilhas são usadas para "rastrear" os endereços de retorno das chamadas de funções. Por exemplo, quando o código chama uma `fn_B()` de dentro de uma `fn_A()`, o estado de `fn_A` é empilhado e só é desempilhado quando `fn_B` termina de executar.
- **Gerenciamento de memória:** Pilhas são usadas para alocar e gerenciar a memória em algumas linguagens de programação e sistemas operacionais.
- **Parsers e Compilers:** Pilhas são essenciais para verificar se a sintaxe de um código está correta e para converter expressões matemáticas.
	- **Conversão infixa para pós-fixa:** A notação que o ser humano usa é infixa (`3 + 4`). Computadores "preferem" a notação pós-fixa (`3 4 +`). O algoritmo Shunting-yard usa uma pilha para fazer essa conversão de forma eficiente.
## Referências

- O artigo [Introduction to Stack Data Structure](https://www.geeksforgeeks.org/dsa/introduction-to-stack-data-structure-and-algorithm-tutorials/) do geeksforgeeks tem todo o básico do conceito de pilhas. além de mostrar como é a implementação de pilhas com arrays, dequeues e listas encadeadas.
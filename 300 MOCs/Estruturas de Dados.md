---
node_size: 32
---
# Estruturas de Dados

Ponto de partida para entender o que é uma estrutura de dados, a diferença entre estruturas lineares e não lineares e como esse tema se relaciona com memória.

- [[Ponteiros]]: Endereços de memória, desreferenciação e base conceitual para estruturas dinâmicas como listas, árvores e grafos.
## Estruturas lineares contíguas

Aqui entram as estruturas em que os elementos ocupam posições contíguas ou previsíveis na memória, o que facilita o cálculo de endereços e o acesso por índice.

- [[Arrays]]: Vetores unidimensionais, acesso por índice e cálculo de endereço com ponteiros.
- [[100 Notas de referência/Estrutura de dados/Lineares/Matrizes|Matrizes]]: Arrays multidimensionais, organização _row-major_ em C e noção de matrizes esparsas.
## Estruturas lineares encadeadas

Assuntos ligados a estruturas formadas por nós conectados por ponteiros, em que a ordem lógica não depende da posição física na memória.

- [[Listas encadeadas]]: Conceito de nodes, head, tail, header e variações simples, duplas e circulares.
## Estruturas lineares com acesso restrito

Essas estruturas continuam sendo lineares, mas restringem a forma como inserção e remoção acontecem, modelando padrões frequentes de processamento.

- [[Pilhas]]: Estrutura LIFO, operações básicas, implementações e aplicações como call stack e parsing.
- [[Filas]]: Estrutura FIFO, operações básicas, aplicações práticas e tipos como fila circular, dequeue e fila de prioridade.

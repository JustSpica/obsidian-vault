# Listas encadeadas

Lista encadeada é uma coleção linear de elementos, chamados de *nodes*, onde sua ordem não é determinada pela localização na memória. Ao invés dos elementos estarem de forma sequencial na memória, como em [[Arrays|arrays]], cada elemento contém um [[Ponteiros|ponteiro]] que aponta para o próximo elemento da sequência.

A ordem dos elementos é ditada por essas conexões lógicas entre os *nodes*, e não pela sua proximidade física na memória.

Ao contrário dos arrays, que possuem um tamanho fixo determinado em tempo de compilação, as listas encadeadas podem crescer e diminuir em tamanho durante o tempo de execução, à medida que os elementos são adicionados ou removidos, evitando desperdício de memória.

Listas encadeadas basicamente são divididas da seguinte forma:

- **Head:** É o primeiro elemento de uma lista encadeada. Ele serve como o ponto de entrada principal para acessar e percorrer toda a lista.
- **Node:** É qualquer elemento dentro da lista encadeada, que possui o ponteiro para o seu sucessor (ou antecessor) e um dado atrelado.
- **Tail:** É o último elemento da lista encadeada.

Uma lista encadeada pode conter uma estrutura auxiliar chamada *header*, que armazena informações adicionais sobre toda a lista como o tamanho, o *head*, o *tail* e qualquer outra informação relevante que desejar ser implementada.

O benefício principal de uma lista encadeada é a facilidade e eficiência de inserir ou remover elementos. Como os *nodes* não precisam ser armazenados contiguamente na memória, operações como inserção e exclusão no início ou em uma posição conhecida podem ser realizadas com um número constante de operações $O(1)$, sem a necessidade de realocação ou reorganização da estrutura. 

Em contra partida, listas encadeadas não permitem acesso aleatório direto. Para acessar um elemento em uma posição específica, é necessário percorrer a lista desde o *head* (ou *tail* para listas duplamente encadeadas), resultando em uma complexidade de tempo linear $O(n)$.
## Listas simplesmente encadeadas

É a forma mais simples de uma lista encadeada. Cada *node* contém um campo `data` e um único [[Ponteiros|ponteiro]] `next` que aponta exclusivamente para o *node* subsequente na sequência. O ponteiro `next` do último *node* é `NULL`, marcando o fim da lista.

A travessia neste tipo de lista é estritamente unidirecional, o que significa que os elementos só podem ser acessados movendo-se para frente, do *head* para o *tail*.

**Exemplo de uma lista simplesmente encadeada:** ![[exemplo_lista_simplesmente_encadeada.png]]
## Listas duplamente encadeadas

É um aprimoramento das listas simplesmente encadeadas. Cada *node* contém três componentes: um campo `data`, um ponteiro `next` (para o *node* sucessor) e um ponteiro `prev` (para o *node* antecessor). Esse sistema de ponteiro duplo permite conexões em ambas as direções.

A principal vantagem das listas duplamente encadeadas é a capacidade de percorrer a lista tanto para frente, quanto para trás, permitindo diretamente a travessia bidirecional e simplifica certas operações, como a exclusão de um *node* específico sem a necessidade de seu anterior. 

Em uma lista duplamente encadeada, o *node* anterior pode ser acessado diretamente através do ponteiro `prev` do *node* a ser excluído, tornando a operação $O(1)$.

**Exemplo de uma lista duplamente encadeada:** ![[exemplo_lista_duplamente_encadeada.png]]
## Listas encadeadas circulares

É uma variação das listas anteriores, com a diferença que o último *node* aponta de volta para o primeiro *node*, formando um loop contínuo.

As listas encadeadas circulares, podem ser simplesmente encadeadas (com apenas um [[Ponteiros|ponteiro]] `next`), ou duplamente encadeadas(com os ponteiros `next` e `prev`).

As vantagens das listas circulares incluem a capacidade de travessia contínua sem a necessidade de verificar um terminador `NULL`, o que simplifica algoritmos para processos cíclicos. Os dados podem ser adicionados e removidos da lista a qualquer momento sem um início ou fim definidos, tornando-as ideais para dados em constante mudança.

**Exemplo de uma lista simplesmente encadeada circular:** ![[exemplo_lista_simplesmente_encadeada_circular.png]]

**Exemplo de uma lista duplamente encadeada circular:** ![[exemplo_lista_duplamente_encadeada_circular.png]]
## Referências

- Baseado no PDF do La Salle [[500 Materiais/data-structure/aula-02.pdf|Estrutura de dados - Aula 02]] e [[500 Materiais/logic-mathematics/aula-03.pdf|Estrutura de dados - Aula 03]]
- O artigo [Linked List Data Structure](https://www.geeksforgeeks.org/dsa/linked-list-data-structure/) do geeksforgeeks tem o básico sobre a definição de listas encadeadas, além de ter links para os tipos de listas encadeadas citados na nota.
- O vídeo [O que vem DEPOIS do Hello World | Consertando meu C](https://www.youtube.com/watch?v=YyWMN_0g3BQ&t=956s)a partir de **15:56** tem uma boa explicação e implementação básica em C sobre listas encadeadas.
# Árvores

Árvore é uma estrutura de dados não linear formada por **nós** ligados por **arestas**, organizada a partir de uma raiz e sem ciclos. Ela serve para representar relações hierárquicas, onde cada nó pode ter filhos e é alcançado por um único caminho a partir da raiz.

Em termos de grafos, uma árvore livre é um grafo não dirigido, conexo e acíclico. Em estrutura de dados, normalmente o foco está na árvore enraizada, porque a raiz define a direção lógica de acesso aos demais nós.

*OBS: A árvore não exige que os nós estejam contíguos na memória. Assim como em [[Listas encadeadas|listas encadeadas]], a ligação entre elementos costuma ser feita por [[Ponteiros|ponteiros]].*

## Componentes de uma árvore

Os nomes usados em árvores descrevem a posição de cada nó dentro da hierarquia.

- **Nó ou vértice:** Cada posição armazenada na árvore.
- **Aresta:** Ligação entre dois nós.
- **Raiz:** Nó inicial da árvore. É o único nó sem pai.
- **Pai:** Nó imediatamente anterior no caminho vindo da raiz.
- **Filho:** Nó diretamente ligado abaixo de outro nó.
- **Irmãos:** Nós que possuem o mesmo pai.
- **Folha ou nó externo:** Nó sem filhos.
- **Nó interno:** Nó que possui pelo menos um filho.
- **Ancestral:** Nó que aparece no caminho da raiz até outro nó.
- **Descendente:** Nó que aparece abaixo de outro nó na hierarquia.

Todo nó de uma árvore enraizada tem no máximo um pai. Se um nó precisa ter dois pais, a estrutura deixa de ser uma árvore nesse modelo.

## Árvores livres

Uma árvore livre pode ser definida de várias formas equivalentes. A ideia central é que a estrutura é conectada sem formar ciclos:

- **Conexa e acíclica:** Existe caminho entre os nós, mas nenhum ciclo.
- **Caminho simples único:** Entre dois vértices quaisquer existe exatamente um caminho simples.
- **Aresta crítica:** Se qualquer aresta for removida, o grafo fica desconexo.
- **Quantidade de arestas:** Para $|V|$ vértices, uma árvore possui $|E| = |V| - 1$ arestas.
- **Adicionar aresta cria ciclo:** Se qualquer nova aresta for adicionada, a árvore deixa de ser acíclica.

Se um grafo é acíclico, mas não é conexo, ele é uma **floresta**. Uma floresta é basicamente um conjunto de árvores separadas.

**Exemplo de árvores livres:** ![[exemplo_arvores_livres.png]]

*OBS: Em uma [[Listas encadeadas|lista encadeada]], cada elemento aponta para no máximo um próximo elemento. Em uma árvore, um nó pode apontar para vários filhos, mas a estrutura ainda não permite caminhos alternativos que criem ciclos.*

## Grau de saída

O **grau de saída** de um nó é a quantidade de filhos que ele possui. Esse valor aparece como `GS`.

- **Folha:** Possui `GS = 0`.
- **Nó interno:** Possui `GS > 0`.
- **Grau de saída da árvore:** É o maior `GS` entre todos os nós da árvore.

Por exemplo, se o nó `A` tem os filhos `B`, `C` e `D`, então `A` possui `GS = 3`. Se o maior grau de saída entre todos os nós da árvore é `4`, então a árvore possui `GS = 4`.

## Profundidade, nível e altura

A posição de um nó também pode ser medida pela distância até a raiz.

- **Nível:** Conjunto de nós com a mesma distância em relação à raiz.
- **Profundidade de um nó:** Número de arestas no caminho da raiz até esse nó.
- **Altura de um nó:** Número de arestas no maior caminho descendente desse nó até uma folha.
- **Altura da árvore:** Altura da raiz, isto é, a maior profundidade de qualquer nó.

A raiz fica no nível `0` e possui profundidade `0`. Os filhos da raiz ficam no nível `1`, os netos no nível `2`, e assim por diante.

*OBS: Se os níveis começam em `0`, uma árvore com níveis `0`, `1`, `2` e `3` tem altura `3`, mas possui `4` níveis.*

## Subárvores

Subárvore é a árvore formada ao escolher um nó como nova raiz e considerar todos os seus descendentes. Isso reforça a natureza recursiva de árvores.

Se um nó `C` tem o filho `G`, e `G` tem os filhos `H`, `I`, `J` e `K`, então `C` pode ser visto como a raiz de uma subárvore formada por esses nós. Até uma folha é uma subárvore: ela é uma árvore com raiz própria, sem filhos.

Por isso, algoritmos de árvore geralmente são recursivos. A operação aplicada em uma árvore inteira costuma ser a mesma operação aplicada em suas subárvores.

## Árvores enraizadas e ordenadas

A árvore enraizada destaca um nó como raiz. A partir disso, ficam bem definidos os papéis de pai, filho, ancestral e descendente.

Uma **árvore ordenada** é uma árvore enraizada em que a ordem dos filhos importa. Se um nó tem `k` filhos, existe um primeiro filho, um segundo filho, até um `k`-ésimo filho.

Duas árvores podem ter os mesmos nós e as mesmas relações de pai e filho, mas serem diferentes como árvores ordenadas se a ordem dos filhos for diferente.

## Árvores binárias e posicionais

Uma **árvore binária** é uma árvore definida recursivamente como uma raiz, uma subárvore da esquerda e uma subárvore da direita. Cada uma dessas subárvores pode ser vazia.

Isso significa que uma árvore binária não é apenas uma árvore ordenada com no máximo dois filhos por nó. Se um nó tem apenas um filho, importa se ele está à esquerda ou à direita.

- **Filho da esquerda:** Raiz da subárvore esquerda, quando ela existe.
- **Filho da direita:** Raiz da subárvore direita, quando ela existe.
- **Árvore vazia ou nula:** Árvore sem nós, normalmente usada como caso base.

Uma **árvore posicional** generaliza essa ideia. Os filhos recebem posições inteiras, e uma posição pode estar ausente. Uma árvore `k`-ária limita essas posições a no máximo `k` filhos por nó.

*OBS: Em árvores ordenadas, a ordem relativa dos filhos importa. Em árvores posicionais, a posição específica também importa, inclusive quando uma posição está faltando.*

## Árvores cheias e completas

Uma árvore cheia é aquela em que todos os nós internos possuem o grau de saída esperado para a árvore. No caso binário, isso significa que cada nó interno tem exatamente `2` filhos e que não existem nós internos com apenas `1` filho.

Uma árvore `k`-ária completa é uma árvore `k`-ária em que todas as folhas estão na mesma profundidade e todos os nós internos possuem grau `k`.

Para uma árvore `k`-ária completa de altura $h$, com $k > 1$, o número de folhas é:

$$
k^h
$$

O número de nós internos é:

$$
1 + k + k^2 + \cdots + k^{h-1} = \frac{k^h - 1}{k - 1}
$$

No caso binário, com $k = 2$, uma árvore completa de altura $h$ possui $2^h$ folhas e $2^h - 1$ nós internos.

## Representação em C

Uma forma simples de representar uma árvore com grau de saída máximo fixo é armazenar, em cada nó, o número de filhos usados e um [[Arrays|array]] de ponteiros para esses filhos.

```c
#define GSA 3

struct ARV {
    int gs;
    struct ARV *f[GSA];
};
```

Nesse exemplo, `GSA` define o grau de saída máximo da árvore. O campo `gs` guarda quantos filhos o nó possui de fato, enquanto `f` guarda os [[Ponteiros|ponteiros]] para esses filhos.

Essa representação funciona bem quando há um limite conhecido de filhos por nó. Se o número de filhos puder variar muito, pode ser mais flexível armazenar os filhos em uma [[Listas encadeadas|lista encadeada]] ou em um array dinâmico.

## Referências

- Baseado no PDF do La Salle [[500 Materiais/data-structure/aula-06-1.pdf|Estrutura de Dados - Aula 06]].
- Baseado no livro [[500 Materiais/data-structure/books/algoritmos-teoria-pratica.pdf|Algoritmos: Teoria e Prática]], páginas 942-948.

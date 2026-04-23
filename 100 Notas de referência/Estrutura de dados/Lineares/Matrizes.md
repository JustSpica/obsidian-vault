# Matrizes

Matrizes são vetores multidimensionais, tipicamente bidimensionais (linhas e colunas), que de forma grosseira pode ser definida como um [[Arrays|array]] dentro de um array.

Conceitualmente, são úteis para representar tabelas de valores, grades, matrizes matemáticas etc.

No caso de matrizes em C, a linguagem adota a organização por linhas (_row-major order_). Isso significa que a matriz é linearizada linha por linha na memória. Todos os elementos da linha 0 vêm primeiro, depois os da linha 1, e assim por diante.

O acesso a `mat[i][j]` funciona da seguinte forma: o compilador transforma em um cálculo linear para encontrar o elemento. A fórmula para o endereço de `mat[i][j]` é:

```C
Address(mat[i][j]) = Base_address(mat) + ((i * N) + j) * sizeof(type)
```

Por exemplo: suponha `int mat[1][2]` onde cada `int` ocupa 4 bytes e o endereço inicial hipotético é 1000:

- Endereço de `m[0][0]` = 1000 (início da linha 0)
- Endereço de `m[0][1]` = 1000 + ((0 * 3) + 1) * 4 = 1004
- Endereço de `m[0][2]` = 1000 + ((0 * 3) + 2) * 4 = 1008
- Endereço de `m[1][0]` = 1000 + ((1 * 3) + 0) * 4 = 1000 + 3 * 4 = 1012 (início da linha 1)
- Endereço de `m[1][1]` = 1000 + ((1 * 3) + 1) * 4 = 1016
- Endereço de `m[1][2]` = 1000 + ((1 * 3) + 2) * 4 = 1020

O cálculo de endereço explica por que, ao passar matrizes para funções, precisasse informar o número de colunas. O compilador precisa saber o valor de `n` para realizar o cálculo acima corretamente. Sem saber o número de colunas, não é possível calcular a posição de `mat[i][j]` apenas a partir de `i` e `j`.
## Matrizes Esparsas

Matriz esparsa é aquela em que a maioria das posições é vazia ou zero, e poucos elementos têm valores diferentes de zero.

Armazenar todos os zeros explicitamente em uma grande matriz pode ser extremamente ineficiente em termos de memória. 

Por exemplo, uma matriz de 200.000 linhas por 15.000 colunas (isso seriam 3 bilhões de elementos). Armazenar isso em `int` consumiria por volta de 12 GB de memória. Porém, se apenas 0,2% desses elementos tiverem valores não nulos, isso significa que só 6 milhões de posições realmente importam, cerca de 68 MB se armazenadas individualmente.

Para lidar com esse tipo de situação, usasse **representação de matriz esparsa**, onde se armazena somente os elementos presentes. Uma representação comum é usar uma lista de trios _(linha, coluna, valor)_ para cada elemento não-nulo.

Por exemplo, suponha a matriz 3x4 abaixo (os traços representam 0 ou nulo):

```C
[ 7   -   -   2  ]
[ -   5   -   -  ]
[ -   -   1   -  ]
```

Em que há valores: 7 em (0,0), 2 em (0,3), 5 em (1,1), 1 em (2,2). Pode ser representado como:

```C
// (3 linhas, 4 colunas, 4 valores não-zero)
[3 4 4]
[0 0 7]
[0 3 2]
[1 1 5]
[2 2 1]
```

A primeira "linha" da representação indica dimensões e quantidade de valores, e cada linha subsequente lista um valor existente na matriz original com sua posição.

Se a matriz original tivesse 12 posições (3x4) com apenas 4 preenchidas, economizei 8 zeros. 

Para matrizes extremamente grandes e esparsas, a economia é substancial.
## Referências

- Baseado no PDF do La Salle [[500 Materiais/data-structure/aula-01.pdf|Estrutura de dados - Aula 01]] e [[500 Materiais/data-structure/aula-02.pdf|Estrutura de dados - Aula 02]].
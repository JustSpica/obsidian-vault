# Matrizes

Matrizes funcionam como quadros organizados de números que tem aplicações em diversas áreas de conhecimento, desde o processamento e resolução de imagens até computação gráfica e machine learning.

Uma matriz é, em sua essência, um quadro retangular de números dispostos em *i* linhas e *j* colunas, representada como `i x j`: $$M = \begin{bmatrix} a_{11} & a_{12} & ... & a_{1n} \\ a_{21} & a_{22} & ... & a_{2n} \\ \vdots & \vdots & \vdots & \vdots \\ a_{n1} & a_{n2} & ... & a_{nn} \end{bmatrix}$$
Casos especiais de matrizes incluem a **matriz-linha**, que possui apenas uma linha (`1_j`), e a **matriz-coluna**, que possui apenas uma coluna (`i_1`).

Em matrizes quadradas (mesmo número de linhas e colunas), duas diagonais recebem nomes especiais:

- **Diagonal Principal:** Composta pelos elementos onde o índice da linha é igual ao da coluna (`a_11`, `a_22`, `a_33`, etc.).
- **Diagonal Secundária:** Atravessa a matriz no sentido oposto à principal.

Por exemplo, uma matrix $A_{5x5}$ que possui lei de formação $a_{ij}=5i-j^2$: $$M=\begin{bmatrix} a_{11}=5.1-1^2 & a_{12} & a_{13} & a_{14} & a_{15} \\ a_{21} & a_{22}=5.2-2^2 & a_{23} & a_{24} & a_{25} \\ a_{31} & a_{32} & a_{33}=5.3-3^2 & a_{24} & a_{25} \\ a_{41} & a_{42} & a_{43} & a_{44}=5.4-4^2 & a_{25} \\ a_{51} & a_{52} & a_{53} & a_{54} & a_{55}=5.5-5^2 \end{bmatrix}$$
onde o resultado da diagonal principal é $a_{11}=4 \;/ a_{22}=6 \;/ a_{33}=6 \;/ a_{44}=4 \;/ a_{55}=0$, a soma dos termos dessa diagonal será **20**.
## Igualdade de matrizes

Para que duas matrizes, A e B, sejam consideradas iguais, duas condições rigorosas devem ser atendidas:

- Elas devem possuir exatamente a **mesma ordem** (mesmo número de linhas e colunas).
- Todos os seus **elementos correspondentes** (aqueles na mesma posição `ij`) devem ser iguais.

Essa é a definição de igualdade de matrizes: $$[a_{ij}]=[b_{ij}] \Leftrightarrow a_{ij} = b_{ij} \; \forall \; i \in \{1,2,...,m\} \; e \; j \in \{1,2,...,n\}$$
Por exemplo, para que $\begin{bmatrix} m+n & x \\ n & y \end{bmatrix} = \begin{bmatrix} 0 & 3 \\ 2 & 1 \end{bmatrix}$ deve ter: $m+n=0 \;/ x=3 \;/ n=2 \;/ y=1$. Com essas equações, podesse facilmente deduzer que $m=-2$.
## Tipos especiais de matrizes

- **Matriz Quadrada:** É toda matriz cujo número de linhas é igual ao número de colunas (`n x n`): $$M=\begin{bmatrix} 0 & 1 \\ 2 & 3 \end{bmatrix}_{2x2}$$
- **Matriz Nula:** É uma matriz de qualquer ordem em que todos os seus elementos são iguais a zero: $$M=\begin{bmatrix} 0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix}_{3x3}$$
- **Matriz Transposta:** A matriz transposta é obtida trocando-se ordenadamente suas linhas por colunas. A primeira linha da matriz original se torna a primeira coluna da transposta, a segunda linha se torna a segunda coluna, e assim por diante: $$M=\begin{bmatrix} 2 & 3 & 5 \\ 7 & 11 & 13 \\ 17 & 19 & 23 \end{bmatrix} \Longrightarrow M^t=\begin{bmatrix} 2 & 7 & 17 \\ 3 & 11 & 19 \\ 5 & 13 & 23 \end{bmatrix}$$
- **Matriz Inversa ($A^{−1}$):** Este é um conceito aplicável apenas a matrizes quadradas. A inversa de uma matriz A, denotada como $A^{-1}$, é uma matriz tal que, quando multiplicada pela matriz original A, o resultado é a **Matriz Identidade (I)**. A Matriz Identidade é uma matriz quadrada especial onde os elementos da diagonal principal são 1 e todos os outros são 0. A relação é: $A⋅A^{−1}=A^{−1}⋅A=I.$ $$\begin{align} &A = \begin{bmatrix} 2 & 4 \\ 1 & 5 \end{bmatrix} \; A^{-1} = \begin{bmatrix} A & B \\ C & D \end{bmatrix} \; I = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} \\ \\ &\begin{cases} 2A+4C = 1 \\ A+5C = 0 \end{cases} \; \begin{cases} 2B+4D = 0 \\ B+5D = 1 \end{cases} \\ \\ &A^{-1} = \begin{bmatrix} \frac{5}{6} & -\frac{2}{3} \\ -\frac{1}{6} & \frac{1}{3} \end{bmatrix} \end{align}$$
## Operações com matrizes

As operações com matrizes seguem regras específicas e bem definidas.

- **Adição e Subtração:** A soma ou subtração de duas matrizes só é possível se elas tiverem a mesma ordem. A operação é realizada somando ou subtraindo os elementos que ocupam a mesma posição em cada matriz: $$\begin{align} A = \begin{bmatrix} 6 & -5 \\ -15 & -14 \end{bmatrix} \; B = \begin{bmatrix} 9 & 8 \\ 4 & 0 \end{bmatrix} &\Longrightarrow A + B = \begin{bmatrix} 6+9 & -5+8 \\ -15+4 & -14+0 \end{bmatrix} = \begin{bmatrix} 15 & 3 \\ -11 & -14 \end{bmatrix} \\ &\Longrightarrow A - B = \begin{bmatrix} 6-9 & -5-8 \\ -15-4 & -14-0 \end{bmatrix} = \begin{bmatrix} -3 & -13 \\ -19 & -14 \end{bmatrix} \end{align}$$
- **Multiplicação Escalar:** Multiplicação escalar é o nome dado para multiplicar cada elemento da matriz por um número real. O resultado é uma nova matriz de mesma ordem da original: $$A = \begin{bmatrix} -9 & 2 & 8 \\ 10 & 8 & -7 \end{bmatrix} \Longrightarrow 3A = \begin{bmatrix} -9.3 & 2.3 & 8.3 \\ 10.3 & 8.3 & -7.3 \end{bmatrix} = \begin{bmatrix} -27 & 6 & 24 \\ 30 & 24 & -21 \end{bmatrix}$$
### Multiplicação de matrizes

A multiplicação de matrizes é uma das operações mais importantes da Álgebra Linear, com regras e propriedades únicas.

Para que a multiplicação entre duas matrizes seja possível, é necessário seguir um conjunto estrito de regras:

- **Condição de Existência:** O número de colunas da primeira matriz deve ser exatamente igual ao número de linhas da segunda matriz.
- **Dimensão da Matriz Resultante:** Se a condição de existência for atendida, a operação resultará em uma nova matriz. A dimensão dessa matriz resultante terá o número de linhas da primeira matriz e o número de colunas da segunda matriz.

O processo envolve multiplicar os elementos de uma linha da primeira matriz pelos elementos correspondentes de uma coluna da segunda matriz e, em seguida, somar esses produtos: $$A = \begin{bmatrix} 1 & 2 \\ 0 & 1 \end{bmatrix} \; B = \begin{bmatrix} 4 & -1 \\ 5 & 0 \end{bmatrix} \Longrightarrow A.B = \begin{bmatrix} 1.4+2.5 & 1.(-1)+0 \\ 0+1.5 & 0 \end{bmatrix} = \begin{bmatrix} 14 & -1 \\ 5 & 0 \end{bmatrix}$$
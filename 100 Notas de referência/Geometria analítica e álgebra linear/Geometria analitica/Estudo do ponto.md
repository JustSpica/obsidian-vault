# Estudo do ponto

Um **ponto** é a localização mais básica da geometria analítica: um par ordenado $P(x,y)$ que marca uma posição exata no plano cartesiano. A partir de pontos é possível medir distâncias, encontrar centros e decidir se três pontos formam uma reta ou um triângulo.

O plano cartesiano conecta geometria e álgebra, cada posição vira um par de números, e cada cálculo com esses números tem um significado geométrico. É a base sobre a qual o [[Estudo da reta]] e as figuras planas são construídos.

## Plano cartesiano

O plano cartesiano é formado por dois eixos perpendiculares que se cruzam na **origem** $O(0,0)$: o eixo horizontal `x` (eixo das **abscissas**) e o eixo vertical `y` (eixo das **ordenadas**). Um ponto $P(x,y)$ é localizado andando $x$ na horizontal e $y$ na vertical.

Os eixos dividem o plano em quatro **quadrantes**, cada um com uma combinação de sinais:

- **1º quadrante:** $(+,+)$
- **2º quadrante:** $(-,+)$
- **3º quadrante:** $(-,-)$
- **4º quadrante:** $(+,-)$

*OBS: Um ponto sobre um eixo não pertence a nenhum quadrante. Se $y=0$ o ponto está no eixo `x`; se $x=0$ está no eixo `y`.*

## Bissetrizes dos quadrantes

As bissetrizes são as duas retas que cortam os quadrantes ao meio, passando pela origem. Cada uma tem uma condição simples sobre as coordenadas do ponto:

- **Bissetriz ímpar (`b13`):** corta o 1º e o 3º quadrantes. Um ponto pertence a ela quando suas coordenadas são **iguais** ($x=y$). Sua equação é $x-y=0$.
- **Bissetriz par (`b24`):** corta o 2º e o 4º quadrantes. Um ponto pertence a ela quando suas coordenadas são **opostas** ($x=-y$). Sua equação é $x+y=0$.

Por exemplo, $A(-2,-2)$ e $B(3,3)$ estão na `b13` (coordenadas iguais), enquanto $C(-4,4)$ e $D(1,-1)$ estão na `b24` (coordenadas opostas).

## Distância entre dois pontos

A distância entre $A(x_A,y_A)$ e $B(x_B,y_B)$ é o comprimento do segmento $\overline{AB}$. Ela sai direto do Teorema de Pitágoras: o segmento é a hipotenusa de um triângulo retângulo cujos catetos são as diferenças em `x` e em `y`.

$$d_{AB}=\sqrt{(x_B-x_A)^2+(y_B-y_A)^2}$$

Por exemplo, para $E(-2,5)$ e $F(4,-3)$:

$$d_{EF}=\sqrt{(4-(-2))^2+(-3-5)^2}=\sqrt{6^2+(-8)^2}=\sqrt{36+64}=\sqrt{100}=10$$

Quando os pontos estão alinhados com um eixo, o cálculo simplifica para um módulo, porque um dos catetos é zero:

- **Mesma abscissa** ($x_A=x_B$): o segmento é vertical (paralelo ao eixo `y`) e $d_{AB}=|y_A-y_B|$. Para $A(2,-1)$ e $B(2,3)$: $d_{AB}=|-1-3|=4$.
- **Mesma ordenada** ($y_A=y_B$): o segmento é horizontal (paralelo ao eixo `x`) e $d_{AB}=|x_A-x_B|$. Para $A(5,2)$ e $B(-5,2)$: $d_{AB}=|5-(-5)|=10$.

## Ponto médio

O **ponto médio** $M$ de um segmento $\overline{AB}$ é o ponto que fica exatamente no meio dele. Cada coordenada de $M$ é a média das coordenadas correspondentes dos extremos:

$$M=\left(\frac{x_A+x_B}{2},\frac{y_A+y_B}{2}\right)$$

Por exemplo, para $A(0,2)$ e $B(-2,5)$:

$$x_M=\frac{0+(-2)}{2}=-1 \qquad y_M=\frac{2+5}{2}=\frac{7}{2}$$

$$M=\left(-1,\frac{7}{2}\right)$$

## Mediana e baricentro

Num triângulo de vértices $A$, $B$ e $C$, a **mediana** é o segmento que liga um vértice ao ponto médio do lado oposto. Todo triângulo tem três medianas, uma por vértice.

Para calcular o comprimento de uma mediana, o processo é sempre o mesmo: achar o ponto médio do lado oposto e medir a distância do vértice até ele. Por exemplo, a mediana $\overline{AM}$ é a distância de $A$ até o ponto médio de $\overline{BC}$, a $\overline{BM}$ vai de $B$ até o ponto médio de $\overline{AC}$, e a $\overline{CM}$ de $C$ até o ponto médio de $\overline{AB}$:

O **baricentro** $G$ é o ponto de encontro das três medianas (o "centro de massa" do triângulo). Suas coordenadas são a média das coordenadas dos três vértices:

$$G=\left(\frac{x_A+x_B+x_C}{3},\frac{y_A+y_B+y_C}{3}\right)$$

## Condição de alinhamento de três pontos

Três pontos são **colineares** (alinhados) quando pertencem a uma mesma reta. O teste é feito com o **determinante** montado com as coordenadas dos pontos e uma coluna de `1`:

$$\begin{vmatrix} x_A & y_A & 1 \\ x_B & y_B & 1 \\ x_C & y_C & 1 \end{vmatrix}=0$$

A leitura do resultado é direta:

- **det $=0$** → os pontos são **colineares** (alinhados).
- **det $\neq 0$** → os pontos **não** são colineares, ou seja, formam um triângulo.

Por exemplo, para $A(1,2)$, $B(3,3)$ e $C(5,4)$, aplicando o método de Sarrus:

$$\begin{vmatrix} 1 & 2 & 1 \\ 3 & 3 & 1 \\ 5 & 4 & 1 \end{vmatrix}\begin{vmatrix} 1 & 2 \\ 3 & 3 \\ 5 & 4 \end{vmatrix}=(3+10+12)-(15+4+6)=25-25=0$$

Como o determinante é zero, os três pontos estão alinhados.

## Área de um triângulo

Quando o determinante anterior **não** dá zero, seu valor mede o quanto os pontos "abrem" um triângulo. A área é a metade do módulo desse mesmo determinante:

$$A_{\triangle ABC}=\frac{1}{2}\,|D| \qquad\text{onde}\qquad D=\begin{vmatrix} x_A & y_A & 1 \\ x_B & y_B & 1 \\ x_C & y_C & 1 \end{vmatrix}$$

*OBS: É o mesmo determinante da condição de alinhamento. Faz sentido, pois os pontos alinhados dão $D=0$, e um triângulo "achatado" sobre uma reta tem área zero.*

Por exemplo, para $A(4,0)$, $B(0,0)$ e $C(0,6)$:

$$D=\begin{vmatrix} 4 & 0 & 1 \\ 0 & 0 & 1 \\ 0 & 6 & 1 \end{vmatrix}=-24 \Longrightarrow A=\frac{1}{2}\,|-24|=\frac{1}{2}\cdot 24=12$$

Como a área é sempre o módulo, esse cálculo também serve para achar uma coordenada desconhecida. Se os pontos $A(0,0)$, $B(0,-8)$ e $C(x,0)$ formam um triângulo de área $20$, então $D=8x$ e:

$$\frac{1}{2}|8x|=20 \Longrightarrow |8x|=40 \Longrightarrow x=5 \;\text{ou}\; x=-5$$

## Referências

- Baseado no PDF do La salle [[GAAL-aula-08.pdf|GA-AL - Aula 08]].

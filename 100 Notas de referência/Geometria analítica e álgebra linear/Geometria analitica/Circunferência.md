# Circunferência

A **circunferência** é a figura plana formada por todos os pontos que estão à **mesma distância** de um ponto fixo chamado **centro**. Essa distância constante é o **raio**.

É a primeira curva estudada na geometria analítica plana. Enquanto a [[Estudo da reta|reta]] é descrita por uma equação do 1º grau, a circunferência é descrita por uma equação do 2º grau. Toda a sua definição se apoia na [[Estudo do ponto#Distância entre dois pontos|distância entre dois pontos]], a condição "estar a uma distância fixa do centro" é o que gera a equação.

## Elementos da circunferência

Os elementos básicos descrevem as medidas e os segmentos notáveis da figura:

- **Centro:** O ponto fixo $O(a,b)$ do qual todos os pontos da curva são equidistantes.
- **Raio ($r$):** O segmento que liga o centro a qualquer ponto da circunferência.
- **Diâmetro ($d$):** O segmento que une dois pontos da circunferência passando pelo centro. É o dobro do raio: $d=2r$
- **Corda:** Qualquer segmento que une dois pontos da circunferência sem obrigatoriamente passar pelo centro (o diâmetro é a maior corda possível).
- **Arco:** cada uma das partes da curva delimitadas por dois de seus pontos.

## Comprimento e área

O **comprimento** (ou perímetro) da circunferência é o produto de $\pi$ pelo dobro do raio:

$$C=2\pi r$$

A **área** da região delimitada pela circunferência é o produto de $\pi$ pelo quadrado do raio:

$$A=\pi r^2$$

A constante $\pi$ é justamente a razão entre o comprimento de qualquer circunferência e o seu diâmetro ($\pi = C/d \approx 3{,}14159$), é por isso que ela aparece nas duas fórmulas.

*OBS: Rigorosamente, quem tem área é o círculo (a região interna), não a circunferência (a curva). "Área da circunferência" é um uso informal comum para se referir à área do círculo que ela delimita.*

## Equação reduzida

A **equação reduzida** descreve a circunferência a partir do seu centro $O(a,b)$ e do raio $r$. Ela vem diretamente da definição: um ponto $P(x,y)$ pertence à circunferência quando sua distância até o centro é igual a $r$.

Partindo da distância entre $P$ e $O$ e elevando os dois lados ao quadrado para eliminar a raiz:

$$\sqrt{(x-a)^2+(y-b)^2}=r \Longrightarrow (x-a)^2+(y-b)^2=r^2$$

Essa é a forma mais prática de ler ou montar uma circunferência, porque o centro e o raio ficam visíveis. Por exemplo, $(x-3)^2+(y+1)^2=25$ tem centro $O(3,-1)$ e raio $r=5$.

*OBS: Ter cuidado com os sinais. Como a fórmula usa $(x-a)$, um $(y+1)$ significa $b=-1$, e não $b=1$.*

## Equação geral

A **equação geral** é obtida desenvolvendo os quadrados da equação reduzida (com produtos notáveis) e passando tudo para o primeiro membro:

$$(x-a)^2+(y-b)^2=r^2$$
$$x^2-2ax+a^2+y^2-2by+b^2=r^2$$
$$x^2+y^2-2ax-2by+a^2+b^2-r^2=0$$

Para achar a equação geral de uma circunferência, o roteiro é:

1. identificar o centro $(a,b)$ e o raio $r$ 
2. Substituir esses valores na fórmula e simplificar. 

Por exemplo, para uma circunferência de centro $O(-1,1)$ e raio $r=2$:

$$x^2+y^2-2\cdot(-1)\cdot x-2\cdot 1\cdot y+(-1)^2+1^2-2^2=0$$
$$x^2+y^2+2x-2y+1+1-4=0 \Longrightarrow x^2+y^2+2x-2y-2=0$$

### Encontrando o centro e o raio pela equação geral

O caminho inverso, dada a equação geral, achar centro e raio, usa o **método da comparação**. Comparam-se os coeficientes da equação dada com os da fórmula geral. Por exemplo, para $x^2+y^2+8x-2y+1=0$:

$$-2a=8 \Rightarrow a=-4 \qquad -2b=-2 \Rightarrow b=1$$

Com $a$ e $b$ conhecidos, o termo independente fornece o raio:

$$a^2+b^2-r^2=1 \Longrightarrow (-4)^2+1^2-r^2=1 \Longrightarrow 16+1-r^2=1 \Longrightarrow r=\sqrt{16}=4$$

Logo, a circunferência tem centro $O(-4,1)$ e raio $r=4$.

## Círculo vs circunferência

São coisas diferentes, e a distinção é o número de dimensões:

- **Circunferência:** É só a **curva** (a borda), formada pelos pontos equidistantes do centro. Tem uma dimensão.
- **Círculo:** é a **região** preenchida, ou seja, a circunferência mais todo o seu interior. Tem duas dimensões.

Em outras palavras, a circunferência é o contorno e o círculo é a área fechada por esse contorno.

## Posições relativas entre ponto e circunferência

Um ponto $P(x_P,y_P)$ pode ocupar três posições em relação a uma circunferência de centro $O(a,b)$ e raio $r$. O critério é comparar a distância de $P$ ao centro com o raio, o que equivale a substituir $P$ no lado esquerdo da equação reduzida e comparar com $r^2$:

- **Interno:** $d_{PO}<r$, ou seja, $(x_P-a)^2+(y_P-b)^2<r^2$.
- **Pertencente:** $d_{PO}=r$, ou seja, $(x_P-a)^2+(y_P-b)^2=r^2$.
- **Externo:** $d_{PO}>r$, ou seja, $(x_P-a)^2+(y_P-b)^2>r^2$.

Por exemplo, para a circunferência $(x-1)^2+(y-2)^2=25$ (centro $O(1,2)$, $r=5$) e o ponto $P(4,6)$:

$$(4-1)^2+(6-2)^2=9+16=25=r^2 \Longrightarrow P \text{ pertence à circunferência}$$

## Posições relativas entre reta e circunferência

Uma reta e uma circunferência no mesmo plano podem compartilhar dois, um ou nenhum ponto. O critério é comparar a [[Estudo da reta#Distância entre ponto e reta|distância do centro à reta]] $d(C,l)$ com o raio $r$:

- **Secante:** $d(C,l)<r$. A reta corta a circunferência em **2 pontos**.
- **Tangente:** $d(C,l)=r$. A reta toca a circunferência em **1 único ponto**, chamado de ponto de tangência.
- **Exterior:** $d(C,l)>r$. A reta **não** intersecta a circunferência (nenhum ponto em comum).

*OBS: Na reta tangente, o raio traçado até o ponto de tangência é sempre perpendicular à reta, é justamente por isso que a distância do centro à reta é igual ao raio.*

## Referências

- Baseado no PDF do La salle [[GAAL-aula-09.pdf|GA-AL - Aula 09]].
- Sugestões de vídeos complementares para tópicos específicos: [equação reduzida](https://www.youtube.com/watch?v=p93CirSoL8A), [equação geral](https://www.youtube.com/watch?v=tu81HCPl4mU), [círculo vs circunferência](https://www.youtube.com/watch?v=TboRqNNQb4A), [posições ponto e circunferência](https://www.youtube.com/watch?v=8187RbQWFas) e [posições reta e circunferência](https://www.youtube.com/watch?v=5GNJmo1bMlY).

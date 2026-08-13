# Estudo da reta

Uma **reta** no plano cartesiano é o conjunto de todos os pontos $(x,y)$ que satisfazem uma equação do 1º grau em `x` e `y`. Ela representa, algebricamente, a ideia geométrica de "alinhamento": dois pontos quaisquer já determinam uma única reta.

Estudar a reta é traduzir entre as suas várias formas de escrita (geral, fundamental, reduzida) e extrair delas informações geométricas: inclinação, paralelismo, perpendicularidade, ângulos e distâncias. Tudo isso parte do [[Estudo do ponto]].

## Equação geral da reta

A forma mais padrão de escrever uma reta é a **equação geral**:

$$ax+by+c=0$$

onde $a$, $b$ e $c$ são constantes (com $a$ e $b$ não simultaneamente nulos). Uma maneira de obtê-la a partir de dois pontos conhecidos $A$ e $B$ é impor que um ponto genérico $(x,y)$ esteja alinhado com eles, usando o determinante da [[Estudo do ponto#Condição de alinhamento de três pontos|condição de alinhamento]]:

$$\begin{vmatrix} x & y & 1 \\ x_A & y_A & 1 \\ x_B & y_B & 1 \end{vmatrix}=0$$

Por exemplo, para a reta $r$ que passa por $(-1,4)$ e $(0,6)$, o determinante resulta em $-2x+y-6=0$. Como é comum deixar o coeficiente de `x` positivo, multiplica-se tudo por $-1$:

$$r:\;2x-y+6=0$$

### Casos particulares

Quando um dos coeficientes zera, a reta assume uma posição especial:

- **$a=0$** (e $c\neq 0$): sobra $by+c=0 \Rightarrow y=-\frac{c}{b}$, uma reta **horizontal** (paralela ao eixo `x`).
- **$b=0$** (e $c\neq 0$): sobra $ax+c=0 \Rightarrow x=-\frac{c}{a}$, uma reta **vertical** (paralela ao eixo `y`).
- **$c=0$**: sobra $ax+by=0$, uma reta que **passa pela origem**.

*OBS: dois casos de reta pela origem têm nome próprio — $x-y=0$ é a bissetriz dos quadrantes ímpares (`b13`) e $x+y=0$ é a bissetriz dos quadrantes pares (`b24`).*

## Coeficiente angular e inclinação

A **inclinação** de uma reta é o ângulo $\alpha$ que ela forma com o eixo `x` (medido no sentido anti-horário). O **coeficiente angular** $m$ é a tangente desse ângulo:

$$m=\tan\alpha$$

Na prática, $m$ mede o quanto a reta "sobe" para cada passo na horizontal, e pode ser calculado por dois pontos:

$$m=\frac{\Delta y}{\Delta x}=\frac{y_B-y_A}{x_B-x_A}\quad (x_B\neq x_A)$$

O sinal de $m$ indica o comportamento da reta: $\alpha=0°$ dá $m=0$ (reta horizontal); $\alpha$ agudo dá $m>0$ (reta crescente); $\alpha$ obtuso dá $m<0$ (reta decrescente); e $\alpha=90°$ não tem tangente definida (reta vertical, sem coeficiente angular).

Por exemplo, para $A(-6,5)$ e $B(3,4)$:

$$m=\frac{5-4}{-6-3}=\frac{1}{-9}=-\frac{1}{9}$$

Alguns ângulos notáveis aparecem o tempo todo: $\tan 30°=\frac{\sqrt{3}}{3}$, $\tan 45°=1$ e $\tan 60°=\sqrt{3}$.

## Equação fundamental da reta

Quando se conhece um ponto $P(x_0,y_0)$ da reta e o coeficiente angular $m$, a forma mais rápida de escrevê-la é a **equação fundamental**:

$$y-y_0=m(x-x_0)$$

Ela vem direto da definição de $m=\frac{y-y_0}{x-x_0}$, multiplicada cruzado. Por exemplo, para $m=-2$ passando por $(4,-3)$:

$$y-(-3)=-2(x-4) \Longrightarrow y+3=-2x+8 \Longrightarrow y=-2x+5$$

Se a reta for dada pela inclinação em vez do $m$, basta calcular $m=\tan\alpha$ antes. Para o ponto $P(-4,5)$ com inclinação de $30°$, tem-se $m=\frac{\sqrt{3}}{3}$ e a equação fica $y-5=\frac{\sqrt{3}}{3}(x+4)$.

## Posições relativas entre retas

Duas retas no plano podem se relacionar de quatro formas, e o coeficiente angular costuma ser o critério mais rápido para distingui-las. Considerando as retas na forma reduzida $y=mx+n$ (onde $n$ é a **ordenada na origem**, o ponto onde a reta cruza o eixo `y`):

- **Paralelas:** mesma direção, sem ponto em comum. Têm $m_1=m_2$ e $n_1\neq n_2$. A distância entre elas é constante.
- **Concorrentes:** cruzam-se num único ponto. Têm $m_r\neq m_s$.
- **Perpendiculares:** caso particular de concorrentes, cruzam-se a $90°$. Têm $m_r\cdot m_s=-1$, ou seja, $m_1=-\frac{1}{m_2}$.
- **Coincidentes:** são a mesma reta (todos os pontos em comum). Têm $m_1=m_2$ e $n_1=n_2$.

Por exemplo, $r:6x+4y-3=0$ e $s:9x+6y-1=0$. Isolando `y` em cada uma, ambas dão $m=-\frac{3}{2}$, mas com ordenadas na origem diferentes ($\frac{3}{4}$ e $\frac{1}{6}$) — logo são **paralelas**.

## Mediatriz de um segmento

A **mediatriz** de um segmento $\overline{AB}$ é a reta perpendicular a ele que passa pelo seu ponto médio. Todo ponto da mediatriz é equidistante de $A$ e $B$.

Para encontrá-la, usam-se duas informações: o coeficiente angular (perpendicular ao de $\overline{AB}$, logo $m_r=-\frac{1}{m_{AB}}$) e o ponto médio $M$ de $\overline{AB}$. Por exemplo, para $A(2,4)$ e $B(6,2)$:

$$m_{AB}=\frac{2-4}{6-2}=-\frac{1}{2} \Longrightarrow m_r=2 \qquad M=\left(\frac{6+2}{2},\frac{4+2}{2}\right)=(4,3)$$

Aplicando a equação fundamental com $m_r=2$ e $M(4,3)$:

$$y-3=2(x-4) \Longrightarrow r:\;2x-y-5=0$$

## Ângulo entre duas retas

Quando duas retas concorrentes $r$ e $s$ (oblíquas e não perpendiculares) se cruzam, o ângulo agudo $\alpha$ entre elas se calcula a partir dos coeficientes angulares:

$$\tan\alpha=\left|\frac{m_s-m_r}{1+m_s\cdot m_r}\right|$$

Por exemplo, para $r:y=3x+4$ ($m_r=3$) e $s:y=-2x+8$ ($m_s=-2$):

$$\tan\alpha=\left|\frac{-2-3}{1+(-2)\cdot 3}\right|=\left|\frac{-5}{-5}\right|=1 \Longrightarrow \alpha=45°$$

*OBS: se uma das retas for vertical (sem coeficiente angular) e a outra oblíqua com coeficiente $m_r$, a fórmula vira $\tan\alpha=\left|\frac{1}{m_r}\right|$.*

## Distância entre ponto e reta

A distância de um ponto $P(x_0,y_0)$ a uma reta $r:ax+by+c=0$ é a medida do segmento perpendicular de $P$ até $r$ (o menor caminho possível). A fórmula usa diretamente os coeficientes da equação geral:

$$d_{P,r}=\frac{|a x_0+b y_0+c|}{\sqrt{a^2+b^2}}$$

Por exemplo, a distância de $A(-2,3)$ à reta $t:4x+3y-2=0$:

$$d_{A,t}=\frac{|4\cdot(-2)+3\cdot 3+(-2)|}{\sqrt{4^2+3^2}}=\frac{|-8+9-2|}{\sqrt{25}}=\frac{|-1|}{5}=\frac{1}{5}$$

*OBS: se a reta for dada por dois pontos, primeiro encontre sua equação geral (pelo coeficiente angular ou pelo determinante) e só depois aplique a fórmula.*

## Referências

- Baseado no PDF do La salle [[GAAL-aula-08.pdf|GA-AL - Aula 08]].

# Vetores

Vetores são objetos matemáticos que possuem **módulo**, **direção** e **sentido**. Eles servem para representar deslocamentos, posições relativas e grandezas com orientação.

Em computação, a ideia aparece em muitos lugares: posição `(x,y,z)`, cor `(R,G,B)`, embeddings, atributos de um item, características de um usuário, etc.

Vetores nos liberta de pensar apenas em escalares. Eles são a linguagem para descrever pontos e movimentos em qualquer espaço. A mesma operação de soma que funciona para mover um personagem num jogo 2D pode ser generalizada para analisar um cliente com 500 características diferentes em um e-commerce.

*OBS: Um vetor não é apenas “uma seta desenhada”. A seta é uma representação visual. O vetor é a informação matemática de deslocamento, direção e intensidade.*

## Comparando vetores

Existem algumas situações especiais com vetores:

- **Vetores iguais:** Quando eles possuem tudo igual (módulo, direção e sentido): $\vec{A}=\vec{B}$
- **Vetores opostos:** Quando possuem módulo e direção iguais, mas sentidos opostos: $\vec{A}=-\vec{B}$
- **Multiplicação por escalar**: Quando um vetor é multiplicado por um número real. Multiplicar por um número negativo é o mesmo que inverter o sentido do vetor.

## Demarcando vetores

Em um plano (2D), um vetor pode ser escrito por suas componentes como $\vec{v}=(v_x,v_y)$ e no espaço (3D) como $\vec{v}=(v_x,v_y,v_z)$.

Quando o vetor não nasce na origem, é necessário usar o ponto inicial e o ponto final do vetor para encontrar o seu módulo, direção e sentido. Se $A=(x_A,y_A)$ e $B=(x_B,y_B)$, então o vetor de `A` até `B` é:

$$\vec{AB}=(x_B-x_A,y_B-y_A)$$

### Módulo de um vetor

O módulo de um vetor, é o comprimento dele. Em $\mathbb{R}^2$, a fórmula para encontrar o módulo do vetor é: 

$$|\vec{v}|=\sqrt{v_x^2+v_y^2}$$

E em $\mathbb{R}^3$ é adicionado apenas o eixo `z` na equação:

$$|\vec{v}|=\sqrt{v_x^2+v_y^2+v_z^2}$$

## Soma de vetores

Normalmente, a operação mais realizada com vetores é a soma entre eles. Existem alguns métodos para fazer a soma de vetores:

### Método das projeções

Quando um vetor tem módulo e ângulo, podemos decompor ele em componentes. Essas componentes permitem somar vetores usando álgebra simples.

O método das projeções, é o método mais bruto que se usa para calcular vetores. É a álgebra dos vetores, se baseando na decomposição de cada vetor em suas componentes nos eixos.

Por exemplo, dado os vetores $\vec{A}$ e $\vec{B}$ no plano cartesiano: ![[exemplo_vetores_metodo_projecoes.png]]

Eu preciso descobrir a projeção dos meus vetores `A` e `B` em relação aos ângulos `X` e `Y`, sendo denominado suas componentes $Ax$ e $Ay$ para $\vec{A}$, e $Bx$ e $By$ para $\vec{B}$, usando o seguinte cálculo: 

$$\begin{align} Ax &= |\vec{A}|\cos{θ_1} \\ Ay &= |\vec{A}|\sin{θ_1} \\ \\ Bx &= |\vec{B}|\cos{θ} \\ By &= |\vec{B}|\sin{θ} \end{align}$$

*OBS: Quando a projeção está associada ao cateto adjacente ao ângulo, usasse cos θ (cosseno) e quando está associada ao cateto oposto, usasse sin θ (seno)*

Com isso se tem as componentes do meu vetor resultante, e com essas componentes, eu tenho a descrição completa do vetor (módulo, direção e sentido):

$$\begin{align} Rx &= Ax + Bx \\ Ry &= Ay + By\end{align}$$

Para descobrir o módulo do meu vetor resultante, eu simplesmente aplico Pitágoras: $$|R|=\sqrt{Rx^2 + Ry^2}$$

### Método poligonal

É uma versão geométrica do método das projeções. Útil quando tenho muitos vetores espalhados em um plano. 

É necessário conectar o final de um vetor com o início de outro vetor, independente da ordem. E no final conectar o início do primeiro vetor ao final do último vetor, tendo assim a minha resultante: ![[exemplo_vetores_metodo_poligonal.png]]
Nesse caso eu descubro que $\vec{R}=\vec{A}+\vec{B}+\vec{C}$ em soma vetorial.

### Método do paralelogramo

É o método equivalente ao método poligonal mas apenas para quando tenho 2 vetores: ![[exemplo_vetores_metodo_paralelogramo.png]]

Igual ao método poligonal, aqui eu descubro que $\vec{R}=\vec{A}+\vec{B}$ em soma vetorial, e para eu calcular o módulo da minha resultante, eu uso a lei dos cossenos: $$R^2=A^2 + B^2 + 2.A.B.\cos{θ}$$

## Relações entre vetores

Além de somar vetores, é comum precisar saber como dois vetores se posicionam um em relação ao outro: se apontam na mesma direção, se formam um ângulo reto, ou qual a "sombra" de um sobre o outro. Essas três relações se apoiam em conceitos já vistos (multiplicação por escalar e produto escalar).

### Vetores paralelos

Dois vetores são **paralelos** (ou colineares) quando têm a mesma direção, independente do sentido ou do módulo. Isso acontece quando um é **múltiplo escalar** do outro, ou seja, quando existe um número real $k$ tal que $\vec{v}=k\cdot\vec{w}$.

Na prática, isso equivale a dizer que as componentes dos dois vetores são proporcionais. Em $\mathbb{R}^3$, dados $\vec{v}=(x_1,y_1,z_1)$ e $\vec{w}=(x_2,y_2,z_2)$:

$$\frac{x_1}{x_2}=\frac{y_1}{y_2}=\frac{z_1}{z_2}$$

Se todas as razões derem o mesmo valor, esse valor é o próprio $k$ e os vetores são paralelos. Por exemplo, para $\vec{u}=(2,3,4)$ e $\vec{v}=(4,6,8)$:

$$\frac{2}{4}=\frac{3}{6}=\frac{4}{8}=\frac{1}{2}\Longrightarrow \text{paralelos}$$

Já para $\vec{u}=(1,7,-1)$ e $\vec{w}=(2,14,3)$, eu testo as razões:

$$\frac{1}{2}=\frac{7}{14}=0{,}5 \quad\text{mas}\quad \frac{-1}{3}\approx-0{,}33$$

Como a terceira razão é diferente das outras, os vetores **não** são paralelos.

*OBS: essa condição também serve para encontrar uma componente desconhecida. Se eu sei que $\vec{v}=(3,6,9)$ e $\vec{w}=(k,4,6)$ são paralelos, basta resolver $\frac{3}{k}=\frac{6}{4}=\frac{9}{6}$, que dá $k=2$.*

### Vetores perpendiculares

Dois vetores são **perpendiculares** (ou ortogonais) quando formam um ângulo de 90° entre si. O critério é direto: o **produto escalar entre eles precisa ser zero**.

$$\vec{v}\cdot\vec{w}=0 \Longrightarrow \vec{v}\perp\vec{w}$$

Isso vem da própria fórmula do ângulo entre vetores ($\cos\theta=\frac{\vec{v}\cdot\vec{w}}{|\vec{v}|\,|\vec{w}|}$): quando $\theta=90°$, $\cos\theta=0$, e o numerador precisa zerar.

Por exemplo, para $\vec{v}=(1,2,3)$ e $\vec{w}=(-2,1,0)$:

$$\vec{v}\cdot\vec{w}=(1)(-2)+(2)(1)+(3)(0)=-2+2+0=0\Longrightarrow \text{perpendiculares}$$

*OBS: assim como no paralelismo, o critério serve para descobrir uma componente. Para $\vec{u}=(k,1,-2)$ e $\vec{v}=(2,3,1)$ serem perpendiculares, faço $\vec{u}\cdot\vec{v}=2k+3-2=2k+1=0$, logo $k=-\frac{1}{2}$.*

### Projeção ortogonal

A **projeção ortogonal** de um vetor sobre outro pode ser comparada à sombra que esse vetor projeta sobre a direção do outro quando o sol está a pino: a sombra tem o tamanho da parte do vetor que "anda na mesma direção" do segundo, sem profundidade nenhuma.

A projeção de $\vec{v}$ sobre $\vec{w}$ é um vetor com a mesma direção de $\vec{w}$, dado por:

$$\text{proj}_{\vec{w}}\,\vec{v}=\frac{\vec{v}\cdot\vec{w}}{|\vec{w}|^2}\,\vec{w}$$

O escalar $\frac{\vec{v}\cdot\vec{w}}{|\vec{w}|^2}$ diz quantas vezes o vetor $\vec{w}$ cabe na sombra, e multiplicá-lo por $\vec{w}$ devolve o resultado já na direção certa.

Por exemplo, para projetar $\vec{v}=(1,2,3)$ sobre $\vec{w}=(4,-1,2)$, eu calculo primeiro o produto escalar e o módulo ao quadrado:

$$\vec{v}\cdot\vec{w}=(1)(4)+(2)(-1)+(3)(2)=4-2+6=8$$

$$|\vec{w}|^2=4^2+(-1)^2+2^2=16+1+4=21$$

Aplicando na fórmula:

$$\text{proj}_{\vec{w}}\,\vec{v}=\frac{8}{21}(4,-1,2)=\left(\frac{32}{21},-\frac{8}{21},\frac{16}{21}\right)$$

*OBS: se $\vec{v}$ e $\vec{w}$ forem perpendiculares, $\vec{v}\cdot\vec{w}=0$ e a projeção dá o vetor nulo. Faz sentido, porque um vetor perpendicular não tem nenhuma sombra na direção do outro.*

## Referências

- Baseado no PDF do La salle [[GAAL-aula-04.pdf|GA-AL - Aula 04]], [[GAAL-aula-05.pdf|GA-AL - Aula 05]], [[GAAL-aula-06.pdf|GA-AL - Aula 06]] e [[GAAL-aula-07.pdf|GA-AL - Aula 07]].
- O vídeo [MEGA AULA COMPLETA de VETORES!!!](https://www.youtube.com/watch?v=eAAKzZcbITI) tem uma boa explicação sobre vetores e soma de vetores gerais.
- O vídeo [SOMA de VETORES MÉTODO DAS PROJEÇÕES EXERCÍCIOS](https://www.youtube.com/watch?v=iR4lAzl6_qM) é um excelente vídeo de resolvendo exercicios para vetores.
- O vídeo [Decomposição de Vetores - Física do Zero](https://www.youtube.com/watch?v=AX78Ce6gSLU) também explica de forma clara e mais curta sobre a decomposição de vetores para física.
- O vídeo [# Como funciona a SOMA de VETORES? | Aula de FÍSICA](https://www.youtube.com/watch?v=W6T7qf60ky4) é outra boa explicação sobre os métodos poligonal e paralelogramo.

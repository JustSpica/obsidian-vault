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

## Formulas para lembrar

### Em R2 (x, y)

- **Distancia entre dois pontos:** Dados $A(x_a, y_a)$ e $B(x_b, y_b)$: 
$$d_{AB}=\sqrt{(x_b-x_a)^2 + (y_b-y_a)^2}$$
- **Ponto medio:** Dados $A(x_1, y_1)$ e $B(x_2, y_2)$, o ponto medio $M(x_m, y_m)$ e: 
$$M=\left(\frac{x_1+x_2}{2},\frac{y_1+y_2}{2}\right)$$
- **Baricentro (triangulo):** Para $A(x_a,y_a)$, $B(x_b,y_b)$ e $C(x_c,y_c)$: 
$$G=\left(\frac{x_A+x_B+x_C}{3},\frac{y_A+y_B+y_C}{3}\right)$$
- **Reta:** Coeficiente angular (por 2 pontos), dados $A(x_1,y_1)$ e $B(x_2,y_2)$ com $x_2\neq x_1$: 
$$m=\frac{y_2-y_1}{x_2-x_1}$$
- **Forma ponto-inclinacao:** Dado um ponto $P(x_0,y_0)$ na reta: 
$$(y-y_0)=m(x-x_0)$$
*OBS: se $x_2=x_1$, a reta e vertical e fica $x=x_1$ (nao existe coeficiente angular finito).* 

### Em R3 (x, y, z)

- **Ponto medio:** Dados $A(x_1, y_1, z_1)$ e $B(x_2, y_2, z_2)$, o ponto medio $M(x_m, y_m, z_m)$ é: 
$$M=\left(\frac{x_1+x_2}{2},\frac{y_1+y_2}{2},\frac{z_1+z_2}{2}\right)$$
- **Baricentro (triangulo).** Para $A(x_a,y_a,z_a)$, $B(x_b,y_b,z_b)$ e $C(x_c,y_c,z_c)$: 
$$G=\left(\frac{x_A+x_B+x_C}{3},\frac{y_A+y_B+y_C}{3},\frac{z_A+z_B+z_C}{3}\right)$$
- **Modulo de um vetor.** Se $\vec{v}=(v_x,v_y,v_z)$: 
$$\lvert\vec{v}\rvert=\sqrt{v_x^2+v_y^2+v_z^2}$$
- **Angulo entre dois vetores (produto escalar):** 
$$\cos{\theta}=\frac{\vec{v}\cdot\vec{w}}{\lvert\vec{v}\rvert\,\lvert\vec{w}\rvert}$$

## Referências

- Baseado no PDF do La salle [[GAAL-aula-04.pdf|GA-AL - Aula 04]], [[GAAL-aula-05.pdf|GA-AL - Aula 05]] e [[GAAL-aula-06.pdf|GA-AL - Aula 06]].
- O vídeo [MEGA AULA COMPLETA de VETORES!!!](https://www.youtube.com/watch?v=eAAKzZcbITI) tem uma boa explicação sobre vetores e soma de vetores gerais.
- O vídeo [SOMA de VETORES MÉTODO DAS PROJEÇÕES EXERCÍCIOS](https://www.youtube.com/watch?v=iR4lAzl6_qM) é um excelente vídeo de resolvendo exercicios para vetores.
- O vídeo [Decomposição de Vetores - Física do Zero](https://www.youtube.com/watch?v=AX78Ce6gSLU) também explica de forma clara e mais curta sobre a decomposição de vetores para física.
- O vídeo [# Como funciona a SOMA de VETORES? | Aula de FÍSICA](https://www.youtube.com/watch?v=W6T7qf60ky4) é outra boa explicação sobre os métodos poligonal e paralelogramo.

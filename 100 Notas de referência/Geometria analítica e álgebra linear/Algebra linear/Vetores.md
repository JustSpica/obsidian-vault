# Vetores

Vetores é um ente matemático (algo desenvolvido pela matemática) que possui módulo (intensidade) direção e sentido. 

Em computação, é a forma mais básica de representar dados que tem múltiplas características, como posições (x, y, z) de um objeto e cores (R, G, B) de um pixel.

Vetores nos liberta de pensar apenas em escalares. Eles são a linguagem para descrever pontos e movimentos em qualquer espaço. A mesma operação de soma que funciona para mover um personagem num jogo 2D pode ser generalizada para analisar um cliente com 500 características diferentes em um e-commerce.
## Comparando vetores

Existem algumas situações especiais com vetores:

- **Vetores iguais:** Quando eles possuirem tudo igual (módulo, direção e sentido): $\vec{A}=\vec{B}$![[exemplo_vetores_iguais.png]]
- **Vetores opostos:** Quando possuem módulo e direção iguais, mas sentidos opostos: $\vec{A}=-\vec{B}$![[exemplo_vetores_opostos.png]]
- **Multiplicação por escalar**: Quando um vetor é multiplicado por um número real. Multiplicar por um número negativo é o mesmo que inverter o sentido do vetor: ![[exemplo_vetores_escalar.png]]
## Soma de vetores

Existem alguns métodos para fazer a soma de vetores:
### Método das projeções

É o método mais bruto que se usa para calcular vetores. É a álgebra dos vetores, se baseando na decomposição de cada vetor em suas componentes nos eixos, servindo para todos os casos em que vetores são projetados nos eixos em R2 (x, y) ou R3 (x, y, z) e em *N* quantidades.

Por exemplo, dado os vetores $\vec{A}$ e $\vec{B}$ no plano cartesiano: ![[exemplo_vetores_metodo_projecoes.png]]
Eu preciso descobrir a projeção dos meus vetores (`A e B`) em relação aos angulos X e Y, sendo denominado suas componentes $Ax$ e $Ay$ para $\vec{A}$, e $Bx$ e $By$ para $\vec{B}$, usando o seguinte cálculo: $$\begin{align} Ax &= A.\cos{θ_1} \\ Ay &= A.\sin{θ_1} \\ \\ Bx &= B.\cos{θ} \\ By &= B.\sin{θ} \end{align}$$
*OBS: Quando a projeção está associada ao cateto adjacente ao ângulo, usasse cos θ (cosseno) e quando está associada ao cateto oposto, usasse sin θ (seno)*

Agora eu consigo obter as componentes do meu vetor resultate, e com essas componentes, eu tenho a descrição completa do vetor (módulo, direção e sentido): 
$$\begin{align} Rx &= Ax + Bx \\ Ry &= Ay + By\end{align}$$
Para descobrir o módulo do meu vetor resultante, eu simplesmente aplico Pitágoras: $$|R|=\sqrt{Rx^2 + Ry^2}$$
### Método poligonal

É uma versão geométrica do método das projeções. Útil quando tenho muitos vetores espalhados em um plano. 

Basicamente é necessário conectar o final de um vetor com o início de outro vetor, independente da ordem. E no final conectar o início do primeiro vetor ao final do último vetor, tendo assim a minha resultante: ![[exemplo_vetores_metodo_poligonal.png]]
Nesse caso eu descubro que $\vec{R}=\vec{A}+\vec{B}+\vec{C}$ em soma vetorial.
### Método do paralelogramo

É o método equivalente ao método poligonal mas apenas para quando tenho 2 vetores: ![[exemplo_vetores_metodo_paralelogramo.png]]
Igual ao método poligonal, aqui eu descubro que $\vec{R}=\vec{A}+\vec{B}$ em soma vetorial, e para eu calcular o módulo da minha resultante, eu uso a lei dos cossenos: $$R^2=A^2 + B^2 + 2.A.B.\cos{θ}$$
## Formulas para lembrar

### Em R2 (x, y)

- **Distancia entre dois pontos:** Dados $A(x_a, y_a)$ e $B(x_b, y_b)$: $$d_{AB}=\sqrt{(x_b-x_a)^2 + (y_b-y_a)^2}$$
- **Ponto medio:** Dados $A(x_1, y_1)$ e $B(x_2, y_2)$, o ponto medio $M(x_m, y_m)$ e: $$\begin{align} x_m&=\frac{x_1 + x_2}{2} \\ y_m&=\frac{y_1 + y_2}{2} \end{align}$$
- **Baricentro (triangulo):** Para $A(x_a,y_a)$, $B(x_b,y_b)$ e $C(x_c,y_c)$: $$\begin{align} x_g&=\frac{x_a + x_b + x_c}{3} \\ y_g&=\frac{y_a + y_b + y_c}{3} \end{align}$$
- **Reta:** Coeficiente angular (por 2 pontos), dados $A(x_1,y_1)$ e $B(x_2,y_2)$ com $x_2\neq x_1$: $$m=\frac{y_2-y_1}{x_2-x_1}$$
- **Forma ponto-inclinacao:** Dado um ponto $P(x_0,y_0)$ na reta: $$(y-y_0)=m(x-x_0)$$*OBS: se $x_2=x_1$, a reta e vertical e fica $x=x_1$ (nao existe coeficiente angular finito).* 
### Em R3 (x, y, z)

- **Ponto medio:** Dados $A(x_1, y_1, z_1)$ e $B(x_2, y_2, z_2)$, o ponto medio $M(x_m, y_m, z_m)$ é: $$\begin{align} x_m&=\frac{x_1 + x_2}{2} \\ y_m&=\frac{y_1 + y_2}{2} \\ z_m&=\frac{z_1 + z_2}{2} \end{align}$$
- **Baricentro (triangulo).** Para $A(x_a,y_a,z_a)$, $B(x_b,y_b,z_b)$ e $C(x_c,y_c,z_c)$: $$\begin{align} x_g&=\frac{x_a + x_b + x_c}{3} \\ y_g&=\frac{y_a + y_b + y_c}{3} \\ z_g&=\frac{z_a + z_b + z_c}{3} \end{align}$$
- **Modulo de um vetor.** Se $\vec{v}=(v_x,v_y,v_z)$: $$\lvert\vec{v}\rvert=\sqrt{v_x^2+v_y^2+v_z^2}$$
- **Angulo entre dois vetores (produto escalar):** $$\cos{\theta}=\frac{\vec{v}\cdot\vec{w}}{\lvert\vec{v}\rvert\,\lvert\vec{w}\rvert}$$
## Referências

- O vídeo [MEGA AULA COMPLETA de VETORES!!!](https://www.youtube.com/watch?v=eAAKzZcbITI) tem uma boa explicação sobre vetores e soma de vetores gerais.
- O vídeo [SOMA de VETORES MÉTODO DAS PROJEÇÕES EXERCÍCIOS](https://www.youtube.com/watch?v=iR4lAzl6_qM) é um excelente vídeo de resolvendo exercicios para vetores.
- O vídeo [Decomposição de Vetores - Física do Zero](https://www.youtube.com/watch?v=AX78Ce6gSLU) também explica de forma clara e mais curta sobre a decomposição de vetores para física.
- O vídeo [# Como funciona a SOMA de VETORES? | Aula de FÍSICA](https://www.youtube.com/watch?v=W6T7qf60ky4) é outra boa explicação sobre os métodos poligonal e paralelogramo.

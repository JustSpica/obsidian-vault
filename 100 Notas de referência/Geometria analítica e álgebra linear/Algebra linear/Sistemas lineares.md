# Sistemas lineares

Sistemas lineares são uma ferramenta para modelar e resolver problemas que envolvem múltiplas varáveis interdependentes.

Um sistema linear, especificamente um sistema linear 2x2, ocorre quando se possui um conjunto de duas equações do primeiro grau, cada uma contendo as mesmas duas variáveis. O objetivo é encontrar um par de valores que satisfaça ambas as equações simultaneamente. 

Graficamente, cada equação linear de duas variáveis representa uma reta no plano cartesiano. A solução do sistema, portanto, corresponde ao ponto de intersecção entre essas duas retas.

A natureza da solução de um sistema linear permite classificá-lo de três maneiras distintas:

- **Sistema Possível e Determinado (Solução Única):** É o caso em que existe exatamente um par de valores (`x,y`) que resolve o sistema. Graficamente, isso acontece quando as retas representadas pelas equações são concorrentes. Esse ponto de intersecção é a solução única do sistema.
- **Sistema Possível e Indeterminado (Infinitas Soluções):** O sistema possui um número infinito de soluções. Isso acontece quando as duas equações são equivalentes. Graficamente, ambas as equações representam retas coincidentes. Portanto, qualquer ponto sobre essa linha é uma solução válida para o sistema.
- **Sistema Impossível (Nenhuma Solução):** Um sistema é classificado como impossível quando não existe nenhum par de valores que satisfaça ambas as equações ao mesmo tempo. Graficamente, isso corresponde a duas retas que são paralelas e distintas. Como elas nunca se cruzam, não há um ponto em comum e, consequentemente, não há solução para o sistema.

Para encontrar a solução de um sistema, se utiliza métodos algébricos. Por exemplo, dado o seguinte sistema linear: $$\begin{cases}x+y=3\\x+2y=4\end{cases}$$
- **Método da Substituição:** Consiste em um processo de três etapas:
	1. **Isolar uma variável:** Escolhe-se uma das equações e isola-se uma das variáveis: $$x+y=3 \Longrightarrow x=3-y$$
    2. **Substituir:** A expressão encontrada é substituída na outra equação. Isso resulta em uma nova equação com apenas uma variável: $$x+2y=4 \Longrightarrow 3-y+2y=4 \Longrightarrow y=1$$
    3. **Encontrar a outra variável:** Agora o valor encontrado é substituído de volta na expressão isolada, para determinar o valor da segunda variável. O resultado é o par ordenado que compõe a solução:$$\begin{align} x&=3-1 \Longrightarrow x=2 \\ \\ S&=\{(2,1)\} \end{align}$$
- **Método da Adição:** O objetivo é manipular as equações para que, ao somá-las, uma das variáveis seja eliminada. Para isso, é necessário multiplicar uma ou ambas as equações por um número que torne os coeficientes de uma das variáveis opostos. Ao somar as equações, obtém-se uma equação simplificada com uma única variável: $$\begin{cases} -1(x+y=3) \\ x+2y=4 \end{cases} \Longrightarrow \begin{cases} \cancel{-x}-y=-3 \\ \cancel{x}+2y=4 \end{cases} \Longrightarrow y=4-3 \Longrightarrow y=1$$Após encontrar seu valor, o processo é finalizado substituindo esse valor em uma das equações originais para achar a variável restante: $$\begin{align} x+1&=3 \Longrightarrow x=3-1 \Longrightarrow x=2 \\ \\ S&=\{(2,1)\} \end{align}$$
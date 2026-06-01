# Regressão Linear

Regressão linear é um modelo de [[Classificação e Regressão|regressão]] que aproxima a relação entre atributos e alvo por uma **função linear parametrizada**. Ela serve para prever valores contínuos quando a tendência dos dados pode ser representada por uma reta, plano ou hiperplano.

Na forma simples, com um único atributo, o modelo pode ser escrito como:

$$s=\theta_0+\theta_1x$$

## Modelo Linear

Um modelo linear descreve a saída como combinação linear dos atributos. Na aula, o exemplo relaciona satisfação com a vida e PIB per capita:

$$s=\theta_0+\theta_1 \times PIB\_per\_capita$$

Nesse caso:

- **$s$:** Satisfação com a vida.
- **$\theta_0$:** Intercepto da reta.
- **$\theta_1$:** Inclinação da reta.
- **$PIB\_per\_capita$:** Atributo usado para fazer a predição.

## Parâmetros

Os parâmetros definem qual reta será usada. Com valores diferentes de $\theta_0$ e $\theta_1$, o modelo produz retas diferentes.

O treinamento consiste em escolher os parâmetros que produzem a melhor performance nos dados de treino.

*OBS: Na regressão linear, o algoritmo não escolhe “qualquer curva”. Ele escolhe uma função dentro do espaço de funções lineares definido pela representação.*

## Função De Custo

Para escolher os parâmetros, é necessário medir quão mal o modelo desempenhou. Essa medida é a **função de custo**.

A função de custo compara predições e valores reais. O objetivo do treinamento supervisionado é minimizar essa diferença.

Em termos conceituais:

$$\text{melhor modelo}=\arg\min J(\theta)$$

Onde $J(\theta)$ representa o custo associado aos parâmetros do modelo.

## Treinamento Como Otimização

A regressão linear pode ser entendida dentro do paradigma de otimização. O modelo possui parâmetros, a função de custo mede erro, e o treinamento procura os parâmetros que minimizam esse custo.

Esse processo conecta regressão linear a [[Gradiente Descendente]], que é um método para navegar pela paisagem de custo e encontrar parâmetros melhores.

## Predição

Depois de treinado, o modelo pode ser usado para estimar valores em novos casos. Na aula, o modelo ajustado aparece como:

$$s=3,75+6,78 \times 10^{-5} \times PIB\_per\_capita$$

Se eu tiver o PIB per capita de um país, posso substituir esse valor na fórmula e estimar a satisfação com a vida segundo o modelo.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-09.pdf|Inteligência Artificial - Aula 09]].

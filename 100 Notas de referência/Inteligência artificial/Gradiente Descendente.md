# Gradiente Descendente

Gradiente descendente é um método de otimização que ajusta parâmetros movendo-os na direção de **maior redução da função de custo**. Ele serve para treinar modelos quando o objetivo é minimizar um erro medido por uma função $J(\theta)$.

Em [[Aprendizado de Máquina]], o gradiente descendente aparece quando o treinamento é formulado como um problema de otimização.

## Paisagem Do Custo

A função de custo pode ser imaginada como uma paisagem. Cada ponto da paisagem representa uma configuração de parâmetros, e a altura representa o custo.

No exemplo com dois parâmetros, a paisagem depende de $\theta_0$ e $\theta_1$:

$$J(\theta_0,\theta_1)$$

Treinar o modelo significa encontrar uma região baixa nessa paisagem.

## Inicialização

O processo começa escolhendo valores iniciais para os parâmetros. Esses valores determinam o ponto inicial na paisagem do custo.

A partir desse ponto, o algoritmo calcula como a função de custo varia em relação aos parâmetros.

## Atualização Dos Parâmetros

O gradiente indica a direção de maior crescimento da função. Para reduzir o custo, o algoritmo se move na direção oposta ao gradiente.

De forma conceitual:

$$\theta \leftarrow \theta - \alpha \nabla J(\theta)$$

Onde:

- **$\theta$:** Parâmetros do modelo.
- **$\alpha$:** Taxa de aprendizado.
- **$\nabla J(\theta)$:** Gradiente da função de custo.

## Taxa De Aprendizado

A taxa de aprendizado controla o tamanho do passo em cada atualização.

- **Taxa muito baixa:** Converge devagar.
- **Taxa muito alta:** Pode oscilar, divergir ou pular regiões boas.

Na prática, é comum começar com valores baixos e aumentar com cuidado, sempre verificando se a função de custo reduz a cada iteração.

*OBS: Se o custo aumenta repetidamente durante o treino, a implementação ou a taxa de aprendizado provavelmente estão problemáticas.*

## Mínimo Global E Mínimos Locais

O **mínimo global** é o ponto com menor custo em toda a paisagem. Um **mínimo local** é um ponto baixo em relação à vizinhança, mas não necessariamente o melhor ponto possível.

Em paisagens simples, o gradiente descendente pode encontrar o mínimo global. Em paisagens complexas, pode parar em mínimos locais ou regiões planas.

## Relação Com Modelos

O gradiente descendente não é um modelo por si só. Ele é um procedimento de treino. Pode ser usado para ajustar modelos como [[Regressão Linear]], [[Regressão Logística]] e redes neurais.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-09.pdf|Inteligência Artificial - Aula 09]].

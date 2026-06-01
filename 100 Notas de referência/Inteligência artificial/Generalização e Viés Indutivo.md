# Generalização e Viés Indutivo

Generalização é a capacidade de um modelo de [[Aprendizado de Máquina]] fazer **boas predições em dados novos**. Viés indutivo é o conjunto de suposições que permite ao algoritmo sair dos exemplos observados e escolher uma hipótese para casos ainda não vistos.

Sem viés indutivo, o algoritmo não teria critério para preferir uma hipótese em vez de outra. Com viés demais ou viés inadequado, ele pode aprender uma representação ruim do problema.

## Generalização

O objetivo de um modelo não é apenas acertar os dados de treino. O objetivo é capturar regularidades que continuem funcionando fora dos exemplos usados no aprendizado.

Isso significa que o desempenho relevante é medido em dados não vistos durante o treino. Esses dados simulam a situação real em que o modelo precisa tomar decisões sobre novos casos.

*OBS: Um modelo pode ter erro baixo no treino e ainda ser ruim. Nesse caso, ele aprendeu detalhes específicos da amostra, não o padrão geral do problema.*

## Viés Indutivo

Viés indutivo é o conjunto de suposições implícitas ou explícitas feitas por um algoritmo para induzir hipóteses. Ele restringe quais funções podem ser aprendidas ou quais funções são preferidas.

Exemplos:

- **k-NN:** Supõe que instâncias próximas são semelhantes.
- **Árvores de decisão:** Preferem regras organizadas em testes sucessivos sobre atributos.
- **Regressão linear:** Supõe que a relação pode ser bem aproximada por uma função linear.

Esse viés é necessário porque existem infinitas hipóteses compatíveis com um conjunto finito de dados.

## Espaço De Hipóteses E Espaço De Modelos

O **espaço de hipóteses** é o conjunto de funções que poderiam explicar o problema. O **espaço de modelos** é o conjunto de funções que um algoritmo específico consegue representar.

Nem sempre o modelo ideal está dentro do espaço de modelos escolhido. Mesmo quando está, o processo de busca pode não encontrá-lo.

Por isso, escolher um algoritmo também significa escolher um tipo de restrição sobre o problema.

## Viés De Representação

Viés de representação define quais hipóteses o algoritmo consegue expressar. Uma regressão linear, por exemplo, representa funções lineares. Uma árvore de decisão representa regras em estrutura de árvore.

Quando a representação é simples demais, o algoritmo pode não conseguir expressar o padrão real. Quando é flexível demais, pode memorizar ruído.

## Viés De Busca

Viés de busca define como o algoritmo procura dentro do espaço de modelos. Mesmo que existam muitos modelos possíveis, o algoritmo precisa de um procedimento para escolher um.

Algoritmos gulosos, como a indução top-down de [[Árvores de Decisão]], fazem escolhas locais. Isso torna o aprendizado eficiente, mas não garante encontrar o melhor modelo global.

## Underfitting E Overfitting

Dois erros típicos afetam a generalização:

- **Underfitting:** O modelo é simples demais e não aprende nem os padrões principais.
- **Overfitting:** O modelo é complexo demais e aprende ruídos ou detalhes específicos do treino.

O equilíbrio entre esses extremos é uma parte central da avaliação de modelos.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-03.pdf|Inteligência Artificial - Aula 03]].

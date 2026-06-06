# Generalização, Viés, Underfitting e Overfitting

## Generalização

O objetivo dos modelos em [[Aprendizado de máquina|aprendizado de máquina]] não é apenas acertar os exemplos já vistos. O objetivo é produzir boas predições em dados novos. Generalização é a capacidade de um modelo fazer essas boas predições.

Isso significa que o desempenho relevante é medido em dados não vistos durante o treino. Esses dados simulam a situação real em que o modelo precisa tomar decisões sobre novos casos.

*OBS: Um modelo pode ter erro baixo no treino e ainda ser ruim. Nesse caso, ele aprendeu detalhes específicos da amostra, não o padrão geral do problema.*

## Viés Indutivo

Viés indutivo é o conjunto de suposições implícitas ou explícitas feitas por um algoritmo para induzir hipóteses. Ele restringe quais funções podem ser aprendidas ou quais funções são preferidas.

Sem viés indutivo, o algoritmo não teria critério para preferir uma hipótese em vez de outra. Com viés demais ou viés inadequado, ele pode aprender uma representação ruim do problema.

## Viés de Representação

Viés de representação define quais hipóteses o algoritmo consegue expressar. Uma [[Regressão Linear|regressão linear]], por exemplo, representa funções lineares.

Quando a representação é simples demais, o algoritmo pode não conseguir expressar o padrão real. Quando é flexível demais, pode memorizar ruído.

## Viés de Busca

Viés de busca define como o algoritmo procura dentro do espaço de modelos. Mesmo que existam muitos modelos possíveis, o algoritmo precisa de um procedimento para escolher um.

Algoritmos gulosos, como a indução top-down de [[Árvores de decisão|árvores de desição]], fazem escolhas locais. Isso torna o aprendizado eficiente, mas não garante encontrar o melhor modelo global.

## Underfitting e Overfitting

Dois erros típicos afetam o processo de generalização:

- **Underfitting:** O modelo é simples demais e não aprende nem os padrões principais.
- **Overfitting:** O modelo é complexo demais e aprende ruídos ou detalhes específicos do treino.

O equilíbrio entre esses extremos é uma parte central da avaliação de modelos.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-03.pdf|Inteligência Artificial - Aula 03]].

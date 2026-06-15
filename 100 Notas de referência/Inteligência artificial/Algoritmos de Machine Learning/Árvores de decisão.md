# Árvores de Decisão

Árvores de decisão são modelos preditivos que representam uma sequência de **testes encadeados sobre atributos** até chegar a uma decisão final. Elas servem para [[Classificação e Regressão|classificação e regressão]], produzindo regras interpretáveis no formato `IF-ELSE`.

Em uma árvore, cada caminho da raiz até uma folha define uma regra de decisão.

## Estrutura

Uma árvore de decisão possui três componentes principais:

- **Nó interno:** Representa um teste sobre algum atributo.
- **Ramo:** Representa um possível resultado do teste.
- **Folha:** Representa uma predição final.

Em classificação, a folha costuma indicar uma classe. Em regressão, pode indicar um valor numérico ou média dos exemplos que chegaram àquela folha.

## Regras de decisão

Árvores de decisão podem ser lidas como regras `IF-ELSE`. Por exemplo:

```text
IF X1 > 10 AND X2 < 5 THEN Y = Sim
```

Essa legibilidade é uma das principais vantagens do método. Diferente de modelos mais opacos, a árvore mostra quais testes levaram à predição.

## Partições recursivas

Árvores de decisão dividem o espaço de entrada em regiões. Cada teste cria uma partição, e cada novo nó refina uma região anterior.

A ideia é buscar regiões com menor impureza possível. Em [[Classificação e Regressão|classificação]], uma região pura contém instâncias de uma única classe. Em [[Classificação e Regressão|regressão]], uma região pura contém valores alvo próximos.

*OBS: Árvores de decisão tendem a gerar fronteiras paralelas aos eixos dos atributos. Isso pode exigir muitas divisões para representar fronteiras diagonais ou curvas.*

## Indução de árvores

A indução é o processo de construir a árvore a partir dos dados. O procedimento mais comum é utilizando o algoritmo de Hunt (top-down), que começa na raiz e divide o conjunto recursivamente.

O algoritmo de Hunt segue esta lógica:

1. Se todas as [[Dados|instâncias]] que chegam ao nó pertencem à mesma classe, o nó vira folha.
2. Se o conjunto não é homogêneo, escolhe-se o melhor atributo para dividir as instâncias.
3. O processo é aplicado recursivamente aos subconjuntos criados.

Esse processo usa a ideia de **dividir para conquistar**. Cada divisão transforma o problema original em subproblemas menores.

## Critérios de parada

A árvore não deve crescer sem limite. Critérios de parada comuns são:

- **Homogeneidade da classe:** Todas as instâncias do nó pertencem à mesma classe.
- **Homogeneidade das instâncias:** Os [[Dados|atributos]] das instâncias são iguais.
- **Critério de divisão satisfatório:** A melhoria obtida pela divisão é pequena ou suficiente.
- **Profundidade máxima:** A árvore atingiu um limite definido.

Sem critérios de parada adequados, a árvore pode se ajustar demais aos dados de treino.

## Impureza

Medidas de impureza ajudam a escolher qual atributo deve ser testado em cada nó.

Algumas métricas que podem ser usadas são:

- **Ganho de informação:** Usado no ID3, baseado em entropia.
- **Razão de ganho:** Usada no C4.5.
- **Índice Gini:** Muito usado em árvores modernas.

O algoritmo normalmente escolhe a divisão que reduz mais a impureza local. Isso torna a indução gulosa.

## Prós e contras

Vantagens:

- **Interpretabilidade:** A decisão pode ser rastreada pelo caminho da árvore.
- **Regras explícitas:** Caminhos podem ser convertidos em regras.
- **Flexibilidade:** Pode lidar com diferentes tipos de relação entre atributos.

Limitações:

- **Tamanho:** Árvores podem crescer demais.
- **[[Generalização, Viés, Underfitting e Overfitting|Overfitting]]:** Podem memorizar detalhes do treino.
- **Instabilidade:** Pequenas mudanças nos dados podem alterar muito a árvore.
- **Fronteiras por eixo:** As divisões são baseadas em testes sobre atributos individuais.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-05.pdf|Inteligência Artificial - Aula 05]].

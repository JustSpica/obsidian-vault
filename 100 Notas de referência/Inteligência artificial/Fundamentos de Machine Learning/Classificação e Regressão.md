# Classificação e Regressão

Classificação e regressão são as duas tarefas principais de [[Aprendizado supervisionado|aprendizado supervisionado]]. A classificação prevê uma **classe discreta**, enquanto a regressão prevê um **valor contínuo**.

A diferença entre as duas tarefas está no tipo de atributo alvo. Isso muda a forma de treinar, avaliar e interpretar o modelo.

## Classificação

Classificação é a tarefa de designar uma [[Dados|instância]] a uma classe com base em seus atributos. O algoritmo induz um **classificador**.

**Exemplos:**

- Prever se um e-mail é spam ou não.
- Diagnosticar se um tumor é benigno ou maligno.
- Classificar uma imagem como gato, cachorro ou carro.

Tipos comuns de classificação:

- **Classificação binária:** Duas classes possíveis.
- **Classificação multiclasse:** Três ou mais classes possíveis.
- **Classificação multirrótulo:** Mais de uma classe pode ser atribuída à mesma instância.

### Fronteira De Decisão

Um classificador costuma dividir o espaço de atributos em regiões associadas a classes. Essa separação é chamada de **fronteira de decisão**.

Em problemas simples, a fronteira pode ser uma reta. Em espaços com mais atributos, pode ser um hiperplano ou uma superfície mais complexa.

A ideia é separar as classes da melhor forma possível, preservando boa [[Generalização, Viés, Underfitting e Overfitting|generalização]] para casos novos.

## Regressão

Regressão é a tarefa de atribuir um valor contínuo de saída para uma instância, com base em seus atributos preditivos. O algoritmo induz um **regressor**.

**Exemplos:**

- Estimar o preço de uma casa.
- Prever a temperatura de amanhã.
- Estimar satisfação com a vida a partir do PIB per capita.

Na regressão, o erro normalmente mede distância entre o valor previsto e o valor real.

## Comparação

- **Saída da classificação:** Classe ou probabilidade de classe.
- **Saída da regressão:** Número contínuo.
- **Modelo de classificação:** Classificador.
- **Modelo de regressão:** Regressor.
- **Erro típico na classificação:** Classe incorreta ou probabilidade mal calibrada.
- **Erro típico na regressão:** Distância entre valor previsto e valor real.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-03.pdf|Inteligência Artificial - Aula 03]].
- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-10.pdf|Inteligência Artificial - Aula 10]].

# Aprendizado Supervisionado

Aprendizado supervisionado é um regime de [[Aprendizado de Máquina]] em que o modelo aprende a partir de exemplos formados por **atributos preditivos** e **atributo alvo**. Ele serve para prever saídas conhecidas durante o treino em novos casos ainda não vistos.

Um conjunto supervisionado é formado por pares:

$$(x,y)$$

Nesse par, $x$ representa o vetor de atributos da instância, e $y$ representa a saída esperada.

## Atributos Preditivos E Alvo

Os atributos preditivos descrevem a instância. O atributo alvo é o fenômeno que se deseja prever.

Por exemplo, em um problema de diagnóstico:

- **Atributos preditivos:** Resultados de exames, idade, sintomas e medidas clínicas.
- **Atributo alvo:** Diagnóstico final.

A tarefa do modelo é aprender uma função $f$ que aproxime a relação entre $x$ e $y$:

$$f(x) \approx y$$

## Treinamento

Durante o treinamento, o algoritmo recebe instâncias com as respostas esperadas. Com isso, ajusta sua hipótese para reduzir erros de predição.

O treino pode significar coisas diferentes dependendo do algoritmo:

- **k-NN:** Memorizar os exemplos de treino.
- **Árvores de decisão:** Criar testes e ramificações que separam melhor as classes.
- **Regressão linear:** Ajustar parâmetros para reduzir uma função de custo.

## Teste

O teste aplica o modelo induzido em dados que não foram usados no treino. Isso permite estimar [[Generalização e Viés Indutivo|generalização]].

Separar treino e teste evita medir o modelo apenas pela capacidade de repetir exemplos conhecidos.

*OBS: O conjunto de teste não deve orientar ajustes do modelo. Se ele for usado para escolher parâmetros muitas vezes, deixa de representar dados realmente novos.*

## Tarefas Supervisionadas

As duas tarefas supervisionadas centrais são [[Classificação e Regressão|classificação e regressão]].

- **Classificação:** O alvo é uma classe discreta.
- **Regressão:** O alvo é um valor contínuo.

Essa diferença muda a saída do modelo, as métricas de avaliação e a forma de interpretar erros.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-02.pdf|Inteligência Artificial - Aula 02]].
- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-03.pdf|Inteligência Artificial - Aula 03]].

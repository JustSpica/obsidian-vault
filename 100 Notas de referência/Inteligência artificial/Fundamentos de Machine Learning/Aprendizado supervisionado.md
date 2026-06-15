# Aprendizado Supervisionado

Aprendizado supervisionado é um regime de [[Aprendizado de máquina|aprendizado de máquina]] em que o modelo aprende a partir de exemplos formados por [[Dados|atributos e atributo alvo]]. Ele serve para prever saídas conhecidas durante o treino em novos casos ainda não vistos.

Uma instância supervisionada pode ser representada como um par composto pelos vetores $(x,y)$. Nesse par, o vetor $x$ contém todos os atributos preditivos, e o vetor $y$ contém a saída esperada.

Por isso, o processo de aprendizado pode ser visto como a busca por uma função:

$$f(x) \approx y$$

## Treinamento

Durante o treinamento, o algoritmo recebe instâncias com as respostas esperadas. Com isso, ajusta sua hipótese para reduzir erros de predição. O treino pode significar coisas diferentes dependendo do algoritmo.

## Teste

O teste aplica o modelo induzido em dados que não foram usados no treino. Isso permite estimar [[Generalização, Viés, Underfitting e Overfitting|generalização]].

Separar treino e teste evita medir o modelo apenas pela capacidade de repetir exemplos conhecidos.

*OBS: O conjunto de teste não deve orientar ajustes do modelo. Se ele for usado para escolher parâmetros muitas vezes, deixa de representar dados realmente novos.*

## Tarefas supervisionadas

As duas tarefas supervisionadas centrais são [[Classificação e Regressão|classificação e regressão]].

- **Classificação:** O alvo é uma classe discreta.
- **Regressão:** O alvo é um valor contínuo.

Essa diferença muda a saída do modelo, as métricas de avaliação e a forma de interpretar erros.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-02.pdf|Inteligência Artificial - Aula 02]].
- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-03.pdf|Inteligência Artificial - Aula 03]].

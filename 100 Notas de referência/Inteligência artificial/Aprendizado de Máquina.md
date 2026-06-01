# Aprendizado de Máquina

Aprendizado de Máquina é uma abordagem de [[Inteligência Artificial]] em que um sistema melhora seu desempenho em uma tarefa a partir de **experiência representada por dados**. Ele serve para induzir padrões quando as regras do problema não são fáceis de escrever manualmente.

Na definição clássica de Mitchell, um programa aprende a partir de uma experiência $E$, em relação a uma tarefa $T$ e uma medida de desempenho $P$, se seu desempenho em $T$, medido por $P$, melhora com $E$.

## Tarefa, Experiência E Desempenho

A definição de Mitchell separa aprendizado em três partes:

- **Tarefa ($T$):** O que o sistema precisa fazer.
- **Experiência ($E$):** O contato com exemplos, dados ou interações anteriores.
- **Desempenho ($P$):** A medida usada para avaliar se o sistema melhorou.

Por exemplo, em um programa que aprende a jogar xadrez:

- **Tarefa:** Jogar xadrez.
- **Experiência:** Praticar contra diversos adversários.
- **Desempenho:** Taxa de vitórias.

Isso permite tratar aprendizado como melhoria mensurável, não como uma ideia vaga de inteligência.

## Indução De Hipóteses

O aprendizado de máquina trabalha por **indução de hipóteses**. A partir de exemplos observados, o algoritmo tenta encontrar uma regra geral que explique ou aproxime os padrões presentes nos dados.

Uma **hipótese** é uma função aproximadora $f$. Um **modelo** é uma configuração específica de um algoritmo que representa essa hipótese.

Por exemplo, se os dados mostram os pares $(1,3)$, $(2,6)$, $(3,9)$, $(4,12)$ e $(5,15)$, uma hipótese possível é:

$$f(x)=3x$$

Com essa hipótese, a inferência para $x=6$ seria:

$$f(6)=18$$

*OBS: O modelo não “descobre a verdade” do domínio. Ele encontra uma função que parece compatível com a experiência disponível e com o viés do algoritmo.*

## Modelo E Algoritmo

Algoritmo e modelo não são a mesma coisa. O algoritmo é o procedimento usado para aprender. O modelo é o resultado ajustado a partir dos dados.

Em termos práticos:

- **Algoritmo:** O método de aprendizado, como k-NN, árvore de decisão ou regressão logística.
- **Dados de treino:** A experiência usada para ajustar ou construir a hipótese.
- **Modelo:** A hipótese obtida depois do aprendizado.
- **Inferência:** O uso do modelo para prever novos casos.

## Generalização

O objetivo do aprendizado de máquina não é apenas acertar os exemplos já vistos. O objetivo é produzir boas predições em dados novos. Essa capacidade é chamada de [[Generalização e Viés Indutivo|generalização]].

Sem generalização, o modelo apenas memoriza a experiência passada. Com generalização, ele captura regularidades úteis para casos ainda não observados.

## Tipos De Aprendizado

A disciplina apresenta três regimes principais:

- **[[Aprendizado Supervisionado]]:** O conjunto de dados possui atributos preditivos e atributo alvo.
- **Aprendizado não supervisionado:** O algoritmo busca estrutura nos dados sem um alvo explícito.
- **Aprendizado por reforço:** O sistema aprende a agir a partir de recompensas ou punições recebidas no ambiente.

Essa taxonomia diferencia as tarefas contempladas e o tipo de feedback fornecido ao sistema.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-01.pdf|Inteligência Artificial - Aula 01]].
- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-03.pdf|Inteligência Artificial - Aula 03]].

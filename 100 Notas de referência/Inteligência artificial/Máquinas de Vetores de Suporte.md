# Máquinas de Vetores de Suporte

Máquinas de Vetores de Suporte (*Support Vector Machines*) são modelos de classificação que buscam uma **fronteira de decisão com margem máxima** entre classes. Elas servem para separar dados usando hiperplanos, margens suaves e kernels quando a separação linear direta não é suficiente.

O nome vem dos **vetores de suporte**, que são os pontos mais próximos da fronteira e determinam a margem do classificador.

## Fronteira De Decisão

Em um problema simples com uma única dimensão, a fronteira pode ser um limiar. Em duas dimensões, pode ser uma reta. Em três dimensões, um plano. Em dimensões maiores, um hiperplano.

A ideia da SVM não é apenas separar as classes. É separar mantendo o maior espaço possível entre a fronteira e os exemplos mais próximos de cada classe.

## Margem Máxima

A margem é a distância entre a fronteira de decisão e os pontos mais próximos das classes. A SVM escolhe a fronteira que maximiza essa margem.

Isso cria uma separação mais robusta para novas instâncias. Em vez de escolher qualquer limiar que separa os dados de treino, a SVM escolhe um limiar com o maior espaço possível ao redor da decisão.

## Vetores De Suporte

Os vetores de suporte são os exemplos que ficam mais próximos da fronteira. Eles são os pontos que realmente definem a margem.

Pontos muito distantes da fronteira influenciam menos a posição final do classificador. Isso torna o conceito de margem central para entender SVM.

## Margem Suave

Quando existem outliers ou classes que não são perfeitamente separáveis, uma margem rígida pode produzir uma fronteira ruim. A solução é permitir alguns erros de classificação.

Essa ideia é chamada de **margem suave**. Ela troca separação perfeita por maior capacidade de generalização.

O hiperparâmetro `C` controla esse rigor:

- **`C` alto:** Tenta acomodar melhor os dados de treino, aumentando risco de overfitting.
- **`C` baixo:** Tolera mais erros, podendo regularizar melhor.

## Kernels

Quando os dados não são linearmente separáveis no espaço original, uma transformação pode projetá-los para uma dimensão superior onde a separação por hiperplano se torna possível.

Funções kernel fazem essa projeção de forma implícita. Elas calculam relações em um espaço transformado sem precisar construir manualmente todas as novas dimensões.

Por exemplo, um problema de dosagem pode não ser separável usando apenas `dosagem`, mas pode ficar separável ao considerar uma relação como `dosagem²`.

*OBS: Kernel não é “mágica”. Ele é uma forma matemática de mudar a noção de similaridade e separação usada pelo classificador.*

## Normalização E Custo Computacional

SVM é sensível à escala dos atributos. Se um atributo possui valores muito maiores que outro, a fronteira pode depender demais dele.

Por isso, normalizar ou padronizar os dados é uma etapa importante antes do treino.

Outra limitação prática é o custo computacional. O tempo de treinamento de SVMs cresce de forma quadrática em relação ao tamanho do conjunto de dados, o que pode ser problemático em bases grandes.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-11.pdf|Inteligência Artificial - Aula 11]].

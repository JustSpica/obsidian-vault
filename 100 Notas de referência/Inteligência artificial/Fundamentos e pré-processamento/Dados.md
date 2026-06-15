# Dados

Dados em [[Aprendizado de máquina|aprendizado de máquina]] são a **experiência observável** usada por algoritmos para induzir padrões. Eles representam exemplos do problema e servem como base para treinamento, teste e avaliação de modelos.

Em aprendizado de máquina, dados não são apenas valores armazenados. Eles precisam estar organizados de forma que façam sentido para o algoritmo.

## Dados estruturados e não estruturados

Uma primeira classificação importante separa os dados pela estrutura:

- **Dados estruturados:** Geralmente tabulares, com campos pré-definidos e organização em linhas e colunas.
- **Dados não estruturados:** Não seguem uma tabela simples, como imagens, áudio, texto livre e vídeos.

Dados estruturados podem ser interpretados como uma matriz com $M$ linhas e $N$ colunas. Cada linha representa uma observação, e cada coluna representa uma característica medida.

*OBS: Dados não estruturados também podem virar vetores numéricos. A diferença é que essa representação não vem pronta em uma tabela simples.*

## Instâncias

Instâncias são as unidades observacionais que compõem um conjunto de dados (*datasets*). Cada instância é um exemplo do fenômeno que se deseja estudar.

Por exemplo, em uma tabela de flores, cada flor é uma instância. Em uma base de pacientes, cada paciente é uma instância. Em uma base de transações, cada compra é uma instância.

## Atributos

Atributos são as características mensuráveis das instâncias. Eles descrevem cada exemplo por meio de valores observados.

**Exemplos de atributos:**

- **Paciente:** Idade, pressão arterial, colesterol, resultado de exame.
- **Flor:** Comprimento da sépala, largura da sépala, comprimento da pétala.
- **Transação:** Valor, horário, país, tipo de cartão.

Quando cada instância é descrita por seus atributos, ela pode ser representada por um **vetor de atributos**.

$$x=(x_1,x_2,\dots,x_n)$$

## Atributo Alvo

O atributo alvo ou variável de desfecho, é o fenômeno de interesse que se deseja prever. Em [[Aprendizado supervisionado|aprendizado supervisionado]], ele é a saída esperada e costuma ser representado por $y$.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-02.pdf|Inteligência Artificial - Aula 02]].

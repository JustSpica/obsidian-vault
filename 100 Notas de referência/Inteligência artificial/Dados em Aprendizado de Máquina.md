# Dados em Aprendizado de Máquina

Dados em [[Aprendizado de Máquina]] são a **experiência observável** usada por algoritmos para induzir padrões. Eles representam exemplos do problema e servem como base para treinamento, teste e avaliação de modelos.

Em aprendizado de máquina, dados não são apenas valores armazenados. Eles precisam estar organizados de forma que atributos, instâncias e possíveis alvos façam sentido para o algoritmo.

## Dados Estruturados E Não Estruturados

Uma primeira classificação importante separa os dados pela estrutura:

- **Dados estruturados:** Geralmente tabulares, com campos pré-definidos e organização em linhas e colunas.
- **Dados não estruturados:** Não seguem uma tabela simples, como imagens, áudio, texto livre e vídeos.

Dados estruturados podem ser interpretados como uma matriz com $M$ linhas e $N$ colunas. Cada linha representa uma observação, e cada coluna representa uma característica medida.

*OBS: Dados não estruturados também podem virar vetores numéricos. A diferença é que essa representação não vem pronta em uma tabela simples.*

## Instâncias

Instâncias são as unidades observacionais que compõem um conjunto de dados. Cada instância é um exemplo do fenômeno que se deseja estudar.

Em uma tabela de flores, cada flor é uma instância. Em uma base de pacientes, cada paciente é uma instância. Em uma base de transações, cada compra é uma instância.

## Atributos

Atributos são as características mensuráveis das instâncias. Eles descrevem cada exemplo por meio de valores observados.

Exemplos de atributos:

- **Paciente:** Idade, pressão arterial, colesterol, resultado de exame.
- **Flor:** Comprimento da sépala, largura da sépala, comprimento da pétala.
- **Transação:** Valor, horário, país, tipo de cartão.

Quando cada instância é descrita por seus atributos, ela pode ser representada por um **vetor de atributos**.

$$x=(x_1,x_2,\dots,x_n)$$

## Atributo Alvo

O atributo alvo é o fenômeno de interesse que se deseja prever. Em [[Aprendizado Supervisionado]], ele costuma ser representado por $y$.

Uma instância supervisionada pode ser representada como um par:

$$(x,y)$$

Nesse par, $x$ contém os atributos preditivos, e $y$ contém a saída esperada.

Por isso, o processo de aprendizado pode ser visto como a busca por uma função:

$$f(x) \approx y$$

## Representação Numérica

Algoritmos de aprendizado de máquina trabalham com representações numéricas. Mesmo quando os dados originais são textuais, categóricos ou visuais, é necessário transformá-los em valores que o algoritmo consiga manipular.

Essa transformação faz parte de [[Pré-processamento de Dados]]. Ela inclui lidar com valores ausentes, codificar categorias, normalizar escalas e tratar valores anômalos.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-02.pdf|Inteligência Artificial - Aula 02]].

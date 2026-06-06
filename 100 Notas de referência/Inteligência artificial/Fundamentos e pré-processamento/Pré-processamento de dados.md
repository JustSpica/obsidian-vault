# Pré-processamento de Dados

Pré-processamento de dados é o conjunto de transformações aplicadas antes do treinamento de um modelo para tornar os dados **consistentes**, **comparáveis** e **utilizáveis** por algoritmos de [[Aprendizado de máquina|aprendizado de máquina]]. Ele serve para reduzir problemas causados por escala, ausência de valores, categorias textuais e anomalias.

Muitos algoritmos dependem diretamente da forma como os atributos aparecem. Por isso, a qualidade da representação pode ser tão importante quanto a escolha do algoritmo.

## Distribuição dos atributos

A distribuição de um atributo descreve como seus valores aparecem no conjunto de dados. Alguns algoritmos são sensíveis ao intervalo e à forma dessa distribuição.

Quando dois atributos têm escalas muito diferentes, um deles pode dominar o cálculo do modelo. Por exemplo, um atributo como salário pode variar em dezenas de milhares, enquanto idade varia em dezenas.

Isso afeta principalmente algoritmos baseados em distância, como [[k-NN]], e algoritmos baseados em otimização, como [[Regressão Linear|regressão linear]] e [[Regressão Logística|regressão logística]].

## Valores ausentes

Valores ausentes aparecem quando uma instância não possui valor para um ou mais atributos. Isso pode acontecer por erro de coleta, falha de integração, campo opcional ou impossibilidade de medição.

As estratégias mais comuns são:

- **Remover a instância:** Útil quando há poucos casos afetados e a perda não distorce o conjunto.
- **Remover o atributo:** Útil quando o atributo possui ausência demais para ser confiável.
- **Imputar valor:** Substituir o valor ausente por média, mediana, moda ou outro valor estimado.

*OBS: Imputar pela média pode ser simples, mas também pode esconder padrões importantes. A escolha depende do domínio e do motivo da ausência.*

## Atributos textuais e categóricos

Algoritmos de aprendizado de máquina trabalham com representações numéricas. Mesmo quando os dados originais são textuais, categóricos ou visuais, é necessário transformá-los em valores que o algoritmo consiga manipular. Por isso, categorias textuais e afins precisam ser codificadas.

Antes da codificação, é necessário distinguir dois tipos de categoria:

- **Nominal:** Não possui ordem natural. Exemplos: cor, cidade, tipo de produto.
- **Ordinal:** Possui ordem natural. Exemplos: pequeno, médio, grande; baixo, médio, alto.

Categorias nominais não devem receber números que sugiram hierarquia artificial. Categorias ordinais podem preservar ordem, desde que a escala faça sentido para o problema.

## Escala dos atributos

Escalas muito diferentes entre atributos podem enviesar modelos. Duas transformações comuns são:

- **Normalização:** Ajusta valores para um intervalo, geralmente entre `0` e `1`.
- **Padronização:** Centraliza os valores pela média e ajusta pela variância ou desvio padrão.

A normalização é útil quando se quer preservar um intervalo fixo. A padronização é útil quando o algoritmo se beneficia de atributos centrados e comparáveis.

## Outliers

Outliers são valores muito pequenos ou muito grandes em comparação com o restante das medições. Eles podem representar casos raros reais ou erros de coleta.

Possíveis causas:

- **Falha de sensor:** Um equipamento registra valor fisicamente improvável.
- **Erro de digitação:** Um valor é inserido com casas ou zeros errados.
- **Unidade divergente:** Parte dos dados está em metros e outra parte em centímetros.

O tratamento pode envolver remoção, correção, transformação de escala ou manutenção do valor quando ele representa um caso real importante.

*OBS: Nem todo outlier é erro. Em detecção de fraude, por exemplo, a anomalia pode ser justamente o fenômeno de interesse.*

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-02.pdf|Inteligência Artificial - Aula 02]].

# Regressão Logística

Regressão logística é um algoritmo de [[Classificação e Regressão|classificação]] que estima a **probabilidade de uma instância pertencer a uma classe**. Apesar do nome, ela não é usada como regressão comum quando o alvo é uma classe discreta.

O caso mais comum é classificação binária, como prever se um e-mail é spam ou se um aluno foi reprovado.

## Por Que Não Usar Regressão Linear

Em classificação binária, a saída desejada costuma ser `0` ou `1`. Uma reta pode produzir valores menores que `0` ou maiores que `1`, o que não faz sentido como probabilidade.

Por isso, a regressão logística usa uma função que transforma qualquer valor real em um valor entre `0` e `1`.

## Probabilidade E Chances

Probabilidade varia entre `0` e `1`. Chances variam de `0` a `+∞`.

Para conectar um modelo linear a probabilidades, trabalha-se com o log das chances. O log das chances varia de `-∞` a `+∞`, o que combina melhor com uma combinação linear dos atributos.

Depois, a função sigmoide converte o resultado de volta para uma probabilidade.

## Função Sigmoide

A função sigmoide é definida por:

$$\sigma(x)=\frac{1}{1+\exp(-x)}$$

Ela recebe qualquer valor real e devolve um valor no intervalo `[0,1]`.

Na regressão logística, a predição pode ser vista como:

$$\hat{y}=\sigma(\theta^Tx)$$

Onde $\theta^Tx$ é a combinação linear dos atributos com os parâmetros do modelo.

## Limiar E Fronteira De Decisão

A saída da regressão logística é uma probabilidade estimada. Para transformar essa probabilidade em classe, define-se um limiar.

Com limiar de `50%`:

- Se $\hat{y} \geq 0,5$, prediz classe `1`.
- Se $\hat{y} < 0,5$, prediz classe `0`.

Esse limiar cria uma **fronteira de decisão** no espaço de atributos.

*OBS: O limiar de `50%` é comum, mas não é obrigatório. Problemas com custos diferentes para falso positivo e falso negativo podem exigir outro limiar.*

## Função De Custo

A regressão logística precisa punir o modelo de forma compatível com probabilidades. A aula apresenta uma penalização logarítmica:

$$custo(\hat{f}(x), f(x))=\begin{cases}-\log(\hat{f}(x)), & \text{se } f(x)=1 \\ -\log(1-\hat{f}(x)), & \text{se } f(x)=0\end{cases}$$

Essa função pune fortemente previsões confiantes e erradas. Se a classe real é `1`, prever probabilidade próxima de `0` gera custo alto. Se a classe real é `0`, prever probabilidade próxima de `1` também gera custo alto.

## Relação Com Otimização

Assim como na [[Regressão Linear]], os parâmetros da regressão logística são ajustados minimizando uma função de custo. O treino pode usar [[Gradiente Descendente]] ou outros otimizadores.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-10.pdf|Inteligência Artificial - Aula 10]].

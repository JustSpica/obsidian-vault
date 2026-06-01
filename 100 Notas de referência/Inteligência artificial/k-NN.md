# k-NN

k-NN (*k-Nearest Neighbors*) é um algoritmo de [[Aprendizado Supervisionado]] baseado em instâncias que prediz novos casos comparando-os com os **k vizinhos mais próximos** no conjunto de treino. Ele serve para classificação e regressão quando a proximidade entre instâncias carrega informação sobre o alvo.

O k-NN segue a intuição de que exemplos parecidos tendem a ter saídas parecidas.

## Aprendizado Baseado Em Instâncias

No aprendizado baseado em instâncias, o modelo não é uma função explícita ajustada durante o treino. O treinamento é basicamente armazenar as instâncias conhecidas.

Por isso, o k-NN é chamado de algoritmo de aprendizado **lazy**. Ele adia o trabalho principal para o momento da predição.

*OBS: “Lazy” não significa que o algoritmo é ruim. Significa que ele não constrói uma representação compacta antes das consultas.*

## Funcionamento

Para predizer uma nova instância, o k-NN segue estes passos:

1. Calcula a distância entre a nova instância e as instâncias de treino.
2. Seleciona os `k` vizinhos mais próximos.
3. Combina os alvos desses vizinhos para produzir a predição.

Em classificação, a classe pode ser escolhida por votação. Em regressão, o valor pode ser estimado por média dos vizinhos.

## Viés Indutivo

O viés indutivo do k-NN é simples:

- Instâncias próximas tendem a pertencer à mesma classe.
- Instâncias próximas tendem a ter valores alvo semelhantes.
- A princípio, todos os atributos têm a mesma importância.

Esse último ponto torna o algoritmo sensível à escala. Se um atributo tem valores muito maiores que outro, ele pode dominar a distância.

## Medidas De Distância

O k-NN depende de uma medida de proximidade. Algumas opções citadas nas aulas são:

- **Distância euclidiana:** Mede distância em linha reta, associada à norma L2.
- **Distância de Manhattan:** Soma diferenças absolutas, associada à norma L1.
- **Similaridade do cosseno:** Mede alinhamento entre vetores.
- **Simple-matching:** Compara correspondências entre atributos categóricos.
- **Coeficiente de Jaccard:** Mede sobreposição entre conjuntos.

A escolha da distância depende do tipo de dado e da representação usada.

## Escolha De k

O valor de `k` controla o nível de suavização da predição.

- **k pequeno:** O modelo fica mais sensível a ruídos e outliers.
- **k grande:** O modelo fica mais estável, mas pode apagar padrões locais.

O conjunto de teste ou validação é importante para escolher `k` de forma mais cuidadosa.

## Pré-processamento

O k-NN exige atenção especial a [[Pré-processamento de Dados]]. Como ele compara instâncias por distância, atributos em escalas diferentes podem distorcer a vizinhança.

Normalizar ou padronizar atributos quantitativos costuma ser necessário antes de aplicar o algoritmo.

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-04.pdf|Inteligência Artificial - Aula 04]].
- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-05.pdf|Inteligência Artificial - Aula 05]].

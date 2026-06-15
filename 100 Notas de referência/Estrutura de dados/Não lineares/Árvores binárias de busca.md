# Árvores binárias de busca

Uma árvore binária de busca (*Binary Search Tree*, BST) é uma [[Árvores|árvore]] binária cujas chaves são organizadas segundo a **propriedade de árvore de busca binária**: para qualquer nó $x$, toda chave na subárvore esquerda de $x$ é no máximo $x.chave$, e toda chave na subárvore direita de $x$ é no mínimo $x.chave$. Ela serve para representar conjuntos dinâmicos, suportando operações de busca, inserção, eliminação, mínimo, máximo, sucessor e predecessor.

As operações básicas em uma BST demoram tempo proporcional à altura $h$ da árvore. No caso de uma árvore balanceada com $n$ nós, $h = O(\lg n)$ e as operações custam $O(\lg n)$. Porém, se a árvore degenera em uma cadeia linear, $h = n - 1$ e as mesmas operações custam $O(n)$.

*OBS: Uma árvore de busca binária pode ser usada como um dicionário e também como uma [[Filas|fila de prioridades]], já que suporta as operações de conjuntos dinâmicos necessárias para ambas as abstrações.*

## Árvores binárias

Antes da propriedade de busca, é preciso entender a árvore binária em si. Uma árvore binária é uma [[Árvores|árvore]] cujo [[Árvores#Grau de saída|grau de saída]] é no máximo `2`. Cada nó pode ter `0`, `1` ou `2` filhos, chamados de **filho à esquerda** e **filho à direita**.

Na representação por estrutura ligada, cada nó é um objeto que contém uma **chave**, dados satélites e três [[Ponteiros|ponteiros]]: *esquerda* (filho à esquerda), *direita* (filho à direita) e $p$ (pai). Se o filho ou o pai não existe, o ponteiro contém `NIL`. O nó raiz é o único nó cujo $p$ é `NIL`.

### Classificações de árvores binárias

- **Estritamente binária:** Todos os nós internos possuem exatamente dois filhos. Nenhum nó interno tem apenas um filho.
- **Completa (cheia):** Todos os nós internos possuem dois filhos **e** todas as folhas estão no último nível. Uma árvore completa é estritamente binária, mas nem toda árvore estritamente binária é completa.
- **Quase completa:** Todas as folhas estão no último ou no penúltimo nível. Se um nó tem um descendente direito no último nível, todos os seus descendentes esquerdos folhas também devem estar no último nível. Uma árvore quase completa não precisa ser estritamente binária.

**Exemplo de classificações de árvores binárias:** ![[exemplo_arvores_bst_classificacao.png]]

*OBS: A terminologia varia entre autores. Aaron Tenenbaum define "completa" como sinônimo de "cheia" (todos os níveis totalmente preenchidos). Outros autores usam "completa" para o que Tenenbaum chama de "quase completa".*

## Propriedade de árvore de busca binária

A propriedade que distingue uma árvore de busca de uma árvore binária genérica é a seguinte:

Seja $x$ um nó na árvore. Se $y$ é um nó na subárvore esquerda de $x$, então $y.chave \leq x.chave$. Se $y$ é um nó na subárvore direita de $x$, então $y.chave \geq x.chave$.

Essa propriedade vale recursivamente para **todos** os nós, não apenas para a raiz. Por exemplo, considere uma árvore com raiz `6`, subárvore esquerda contendo `{2, 5, 5}` e subárvore direita contendo `{7, 8}`. As chaves à esquerda não são maiores que `6`, e as chaves à direita não são menores que `6`. Dentro da subárvore esquerda, o nó `5` tem `2` à esquerda e `5` à direita, satisfazendo a propriedade localmente também.

Árvores de busca binária diferentes podem representar o mesmo conjunto de chaves. O conjunto $\{2, 3, 5, 5, 6, 7, 8\}$ pode ser armazenado em uma árvore de altura `2` (balanceada) ou em uma de altura `4` (mais degenerada). O tempo de execução das operações depende da altura, não apenas da quantidade de chaves.

## Percursos

Percorrer uma árvore binária significa visitar todos os seus nós exatamente uma vez. Visitar significa realizar alguma operação sobre o nó, como consultar ou imprimir seu valor. Existem três percursos clássicos, todos recursivos, que diferem apenas no momento em que o nó atual é visitado em relação à descida nas subárvores. Os três percursos descem primeiro pela esquerda e depois pela direita.

Para exemplificar, considere o exemplo abaixo de uma árvore com raiz `A`, filho esquerdo `B` (com filhos `D` e `E`) e filho direito `C`: 
![[exemplo_arvores_bst_percurso.png|center]]

### Percurso em pré-ordem (pre-order)

Visita o nó **antes** de descer para as subárvores:

1. Visita o nó.
2. Percorre a subárvore esquerda recursivamente.
3. Percorre a subárvore direita recursivamente.

```
PRE-ORDER-WALK(x)
  if x ≠ NIL
      visita(x)
      PRE-ORDER-WALK(x.esquerda)
      PRE-ORDER-WALK(x.direita)
```

Para o exemplo acima, o percurso em pré-ordem visita na sequência: `A`, `B`, `D`, `E`, `C`.

### Percurso em ordem (*inorder*)

Visita o nó **entre** a descida para a esquerda e a descida para a direita:

1. Percorre a subárvore esquerda recursivamente.
2. Visita o nó.
3. Percorre a subárvore direita recursivamente.

```
INORDER-TREE-WALK(x)
  if x ≠ NIL
      INORDER-TREE-WALK(x.esquerda)
      visita(x)
      INORDER-TREE-WALK(x.direita)
```

Em uma árvore binária de busca, o percurso em ordem imprime as chaves em **sequência ordenada crescente**. Isso decorre diretamente da propriedade de BST, onde toda chave à esquerda é menor ou igual, o nó atual vem no meio, e toda chave à direita é maior ou igual. Para a mesma árvore do exemplo, a sequência seria: `D`, `B`, `E`, `A`, `C`.

### Percurso em pós-ordem (post-order)

Visita o nó **depois** de descer para ambas as subárvores:

1. Percorre a subárvore esquerda recursivamente.
2. Percorre a subárvore direita recursivamente.
3. Visita o nó.

```
POST-ORDER-WALK(x)
  if x ≠ NIL
      POST-ORDER-WALK(x.esquerda)
      POST-ORDER-WALK(x.direita)
      visita(x)
```

Para a mesma árvore: `D`, `E`, `B`, `C`, `A`.

### Complexidade dos percursos

Percorrer uma árvore de $n$ nós demora $O(n)$. O procedimento chama a si mesmo recursivamente duas vezes para cada nó (uma vez para o filho à esquerda e uma vez para o filho à direita), e cada chamada em nó `NIL` demora tempo constante.

Se $T(n)$ é o tempo para percorrer uma subárvore de $n$ nós, com $T(0) = c$ para subárvore vazia, e o nó $x$ tem subárvore esquerda com $k$ nós, o tempo é limitado por:

$$T(n) \leq T(k) + T(n - k - 1) + d$$

Pelo método da substituição, prova-se que $T(n) \leq (c + d)n + c$, logo $T(n) = O(n)$. Como todo nó é visitado ao menos uma vez, $T(n) = \Omega(n)$. Portanto $T(n) = O(n)$.

## Consultas

Além da busca por chave, árvores de busca binária suportam consultas de mínimo, máximo, sucessor e predecessor. Todas são executadas no tempo $O(h)$, onde $h$ é a altura da árvore, pois cada uma percorre um único caminho simples na árvore (descendente ou ascendente).

### Busca

A busca começa na raiz e traça um caminho descendente simples. Para cada nó $x$, compara-se a chave procurada $k$ com $x.chave$:

- Se $k = x.chave$, a busca encontrou o nó.
- Se $k < x.chave$, a propriedade de BST garante que $k$ não está na subárvore direita, então a busca continua na subárvore esquerda.
- Se $k > x.chave$, a busca continua na subárvore direita.
- Se $x$ é `NIL`, a chave não está na árvore.

Versão recursiva:

```
TREE-SEARCH(x, k)
  if x == NIL ou k == x.chave
      return x
  if k < x.chave
      return TREE-SEARCH(x.esquerda, k)
  else return TREE-SEARCH(x.direita, k)
```

Versão iterativa, geralmente mais eficiente por evitar o custo das chamadas recursivas:

```
ITERATIVE-TREE-SEARCH(x, k)
  while x ≠ NIL e k ≠ x.chave
      if k < x.chave
          x = x.esquerda
      else x = x.direita
  return x
```

Por exemplo, para procurar a chave `13` em uma árvore cuja raiz é `15`, eu desço para a esquerda (13 < 15) chegando em `6`, depois para a direita (13 > 6) chegando em `7`, depois para a direita (13 > 7) chegando em `13`. O caminho percorrido é `15 → 6 → 7 → 13`: 
![[exemplo_arvores_bst_busca.png|center]]

### Mínimo e máximo

O elemento com a **menor chave** é encontrado seguindo ponteiros de filho à esquerda desde um nó qualquer até chegar em `NIL`:

```
TREE-MINIMUM(x)
  while x.esquerda ≠ NIL
      x = x.esquerda
  return x
```

A correção decorre da propriedade de BST: se $x$ não tem subárvore esquerda, toda chave na subárvore direita é no mínimo $x.chave$, então $x$ contém a menor chave da subárvore. Se $x$ tem subárvore esquerda, a menor chave está necessariamente lá, pois todas as chaves na subárvore esquerda não são maiores que $x.chave$.

O procedimento para o **máximo** é simétrico, seguindo ponteiros à direita:

```
TREE-MAXIMUM(x)
  while x.direita ≠ NIL
      x = x.direita
  return x
```

Ambos percorrem um caminho descendente simples e custam $O(h)$.

### Sucessor e predecessor

O **sucessor** de um nó $x$ é o nó com a menor chave maior que $x.chave$, o próximo na sequência ordenada definida pelo percurso em ordem. O **predecessor** é o simétrico: o nó com a maior chave menor que $x.chave$.

A busca pelo sucessor tem dois casos:

1. **Se $x$ tem subárvore direita:** O sucessor é o mínimo dessa subárvore, obtido por `TREE-MINIMUM(x.direita)`. Por exemplo, o sucessor do nó com chave `15` numa árvore onde `15` tem como subárvore direita `{17, 18, 20}` é `17`.
2. **Se $x$ não tem subárvore direita:** O sucessor é o ancestral mais baixo de $x$ cujo filho à esquerda também é ancestral de $x$ (ou é o próprio $x$). Para encontrá-lo, sobe-se na árvore enquanto o nó atual for filho à direita de seu pai. Por exemplo, se o nó `13` não tem subárvore direita, eu subo para `7` (13 é filho à direita de 7), depois subo para `6` (7 é filho à direita de 6), e `6` é filho à esquerda de `15` — logo o sucessor de `13` é `15`.

```
TREE-SUCCESSOR(x)
  if x.direita ≠ NIL
      return TREE-MINIMUM(x.direita)
  y = x.p
  while y ≠ NIL e x == y.direita
      x = y
      y = y.p
  return y
```

O predecessor é simétrico: se $x$ tem subárvore esquerda, é `TREE-MAXIMUM(x.esquerda)`. Caso contrário, sobe-se até encontrar um nó que seja filho à direita de seu pai.

Ambos custam $O(h)$, pois seguem um caminho simples na árvore (descendente ou ascendente).

*OBS: O sucessor e o predecessor são determinados pela estrutura da árvore, sem a necessidade de comparar chaves. Isso é uma consequência direta da propriedade de árvore de busca binária.*

## Inserção

A inserção de um novo nó $z$ segue o mesmo princípio da busca: desce pela árvore comparando $z.chave$ com a chave de cada nó encontrado, indo para a esquerda se menor, para a direita caso contrário, até encontrar uma posição `NIL` onde $z$ deve ser colocado.

O procedimento mantém um **ponteiro acompanhante** $y$ que segue um passo atrás de $x$. Quando $x$ se torna `NIL`, $y$ aponta para o futuro pai de $z$:

```
TREE-INSERT(T, z)
  y = NIL
  x = T.raiz
  while x ≠ NIL
      y = x
      if z.chave < x.chave
          x = x.esquerda
      else x = x.direita
  z.p = y
  if y == NIL
      T.raiz = z
  else if z.chave < y.chave
      y.esquerda = z
  else y.direita = z
```

O ponteiro acompanhante é necessário porque, quando $x$ atinge `NIL`, a busca já ultrapassou o nó cujo ponteiro precisa ser atualizado. Se $y$ é `NIL`, a árvore estava vazia e $z$ se torna a raiz.

Por exemplo, para inserir a chave `13` em uma árvore com raiz `12`, eu desço pela direita (13 > 12) até `18`, pela esquerda (13 < 18) até `15`, e pela esquerda novamente (13 < 15) até `NIL`. O ponteiro acompanhante $y$ aponta para `15`, e `13` é inserido como filho à esquerda de `15`.

O tempo de execução é $O(h)$, pois o laço percorre um caminho descendente simples.

*OBS: A inserção sempre cria uma nova folha. Ela nunca reorganiza nós internos existentes. Por isso, a ordem de inserção das chaves determina completamente a forma da árvore.*

## Eliminação

A eliminação de um nó $z$ é a operação mais complexa em uma árvore de busca binária. Existem três casos:

1. **$z$ não tem filhos (folha):** Remove-se $z$ simplesmente, substituindo-o por `NIL` no ponteiro de seu pai.
2. **$z$ tem exatamente um filho:** Eleva-se o único filho de $z$ para ocupar a posição de $z$, atualizando o ponteiro do pai de $z$.
3. **$z$ tem dois filhos:** Encontra-se o **sucessor** de $z$, chamado $y$, que está na subárvore direita de $z$ e não tem filho à esquerda (se tivesse, não seria o mínimo dessa subárvore). Recorta-se $y$ de sua posição atual e coloca-se $y$ no lugar de $z$.

O terceiro caso se subdivide dependendo da posição de $y$:

- **$y$ é filho direto à direita de $z$:** Substitui-se $z$ por $y$ diretamente. A subárvore esquerda de $z$ torna-se a subárvore esquerda de $y$, e o filho à direita de $y$ permanece inalterado.
- **$y$ está mais abaixo na subárvore direita:** Primeiro substitui-se $y$ por seu próprio filho à direita (que pode ser `NIL`). Depois substitui-se $z$ por $y$, e ajustam-se os ponteiros para que $y$ herde ambas as subárvores de $z$.

### Subrotina Transplant

Para movimentar subárvores durante a eliminação, usa-se a subrotina `TRANSPLANT`. Ela substitui a subárvore enraizada em $u$ pela subárvore enraizada em $v$, atualizando o ponteiro do pai de $u$:

```
TRANSPLANT(T, u, v)
  if u.p == NIL
      T.raiz = v
  elseif u == u.p.esquerda
      u.p.esquerda = v
  else u.p.direita = v
  if v ≠ NIL
      v.p = u.p
```

`TRANSPLANT` não atualiza $v.esquerda$ nem $v.direita$, isso é responsabilidade do procedimento que a invoca.

### Procedimento Tree-Delete

```
TREE-DELETE(T, z)
  if z.esquerda == NIL
      TRANSPLANT(T, z, z.direita)
  elseif z.direita == NIL
      TRANSPLANT(T, z, z.esquerda)
  else y = TREE-MINIMUM(z.direita)
      if y.p ≠ z
          TRANSPLANT(T, y, y.direita)
          y.direita = z.direita
          y.direita.p = y
      TRANSPLANT(T, z, y)
      y.esquerda = z.esquerda
      y.esquerda.p = y
```

As duas primeiras condições tratam os casos em que $z$ tem no máximo um filho. O bloco `else` trata o caso com dois filhos: encontra o sucessor $y$ (mínimo da subárvore direita), que necessariamente não tem filho à esquerda, e reorganiza a árvore. Se $y$ não é filho direto de $z$, primeiro $y$ é recortado de sua posição (substituído por seu filho à direita) e recebe a subárvore direita de $z$. Em seguida, $y$ substitui $z$ e herda a subárvore esquerda de $z$.

Cada linha de `TREE-DELETE` demora tempo constante, exceto a chamada a `TREE-MINIMUM`, que percorre no máximo $h$ nós. O tempo total é $O(h)$.

## Altura esperada

A altura de uma árvore de busca binária depende da ordem de inserção das chaves. Se os $n$ itens são inseridos em ordem estritamente crescente, a árvore degenera em uma cadeia com altura $n - 1$. Se as chaves são inseridas em ordem aleatória, a situação é mais favorável.

Uma **árvore de busca binária construída aleatoriamente** em $n$ chaves distintas é aquela que surge da inserção das chaves em uma árvore inicialmente vazia, onde cada uma das $n!$ permutações de entrada é igualmente provável.

A altura esperada dessa árvore é $O(\lg n)$. A prova define a **altura exponencial** $Y_n = 2^{X_n}$, onde $X_n$ é a altura de uma árvore construída aleatoriamente com $n$ chaves. Usando variáveis aleatórias indicadoras $Z_{n,i} = \text{I}\{R_n = i\}$ (onde $R_n$ é a classificação da chave escolhida como raiz), e explorando a independência entre as subárvores esquerda e direita, obtém-se a recorrência:

$$E[Y_n] \leq \frac{4}{n} \sum_{i=0}^{n-1} E[Y_i]$$

Pelo método da substituição com a identidade $\sum_{i=0}^{n-1}\binom{i+3}{3} = \binom{n+3}{4}$, prova-se que:

$$E[Y_n] \leq \frac{1}{4}\binom{n+3}{3}$$

Como $f(x) = 2^x$ é convexa, pela desigualdade de Jensen:

$$2^{E[X_n]} \leq E[2^{X_n}] = E[Y_n] \leq \frac{1}{4}\binom{n+3}{3} = \frac{(n+3)(n+2)(n+1)}{24}$$

Tomando logaritmos de ambos os lados, conclui-se que $E[X_n] = O(\lg n)$. Isso significa que, em média, todas as operações básicas em uma árvore construída aleatoriamente custam $O(\lg n)$.

*OBS: Na prática, nem sempre as inserções são aleatórias, e eliminações também alteram a forma da árvore. Por isso existem variações de árvores de busca binária com garantia de balanceamento no pior caso, como as árvores rubro-negras (altura $O(\lg n)$ garantida) e as árvores B (otimizadas para armazenamento em disco).*

## Tabela de complexidades

| **Operação**                | **Tempo** |
| --------------------------- | --------- |
| Percurso (pre/in/pós-ordem) | $O(n)$    |
| Busca                       | $O(h)$    |
| Mínimo / Máximo             | $O(h)$    |
| Sucessor / Predecessor      | $O(h)$    |
| Inserção                    | $O(h)$    |
| Eliminação                  | $O(h)$    |

Onde $h$ é a altura da árvore. No melhor caso (árvore balanceada), $h = O(\lg n)$. No pior caso (cadeia linear), $h = O(n)$. Em uma árvore construída aleatoriamente, $h = O(\lg n)$ em média.

## Referências

- Baseado no PDF do La Salle [[500 Materiais/data-structure/aula-07.pdf|Estrutura de Dados - Aula 07]].
- Baseado no livro [[500 Materiais/data-structure/books/algoritmos-teoria-pratica.pdf|Algoritmos: Teoria e Prática]].
- O vídeo [Árvores: O Começo de TUDO | Estruturas de Dados e Algoritmos](https://youtu.be/9GdesxWtOgs?t=1101) a partir do minuto **18:21** explica de forma introdutória o conceito de árvores e exemplifica o processo de uma BST.

# Árvores Red-Black

Uma árvore red-black (*red-black tree*, ou árvore vermelho-preto) é uma [[Árvores binárias de busca|árvore de busca binária]] com **um bit extra de cor por nó**, vermelho ou preto, onde as cores são restringidas de modo a garantir que a árvore permaneça **aproximadamente balanceada**. Ela serve para garantir que as operações básicas (busca, inserção, eliminação, mínimo, máximo, sucessor e predecessor) custem $O(\lg n)$ no **pior caso**, e não apenas em média.

Por ser uma árvore de busca binária, ela herda toda a terminologia geral de [[Árvores|árvores]]. O problema que ela resolve aparece nas [[Árvores binárias de busca|BSTs]] comuns: as operações custam $O(h)$, e $h$ pode degenerar para $n - 1$ quando as chaves são inseridas em ordem, tornando a árvore tão lenta quanto uma [[Listas encadeadas|lista ligada]]. 

A red-black é um dos vários esquemas de árvore balanceada que impedem essa degeneração, restringindo as cores ao longo de qualquer caminho da raiz até uma folha. Como nenhum caminho pode ser mais que duas vezes mais longo que qualquer outro, a árvore nunca degenera.

*OBS: A red-black continua sendo uma árvore de busca binária. Todas as propriedades e operações de uma [[Árvores binárias de busca|BST]] (a propriedade de ordenação, percursos, consultas) continuam valendo. A cor é apenas informação auxiliar usada para manter o balanceamento.*

## Propriedades red-black

Cada nó contém, além de *chave*, *esquerda*, *direita* e $p$ (pai), o atributo *cor*. Quando um filho ou o pai não existe, o ponteiro correspondente é tratado como apontando para uma folha `NIL`. Uma árvore de busca binária é uma árvore red-black que satisfaz as cinco **propriedades red-black**:

1. Todo nó é vermelho ou preto.
2. A raiz é preta.
3. Toda folha (`NIL`) é preta.
4. Se um nó é vermelho, então os seus dois filhos são pretos.
5. Para cada nó, todos os caminhos simples desse nó até folhas descendentes contêm o **mesmo número de nós pretos**.

A propriedade 4 é o que impede dois nós vermelhos consecutivos em um caminho. A propriedade 5 é o que força os caminhos a terem comprimentos comparáveis. Juntas, elas garantem o balanceamento aproximado.

*OBS: A propriedade 4 implica que, em qualquer caminho da raiz a uma folha, pelo menos metade dos nós (sem contar a raiz) é preta. Por isso o caminho mais longo tem no máximo o dobro do comprimento do mais curto.*

### A sentinela T.nil

Para tratar as condições de fronteira com elegância, em vez de usar `NIL` como ponteiro nulo, usa-se uma **única sentinela** `T.nil` que representa todas as folhas `NIL` e o pai da raiz. `T.nil` é um objeto preto, com os mesmos atributos de um nó comum, cujos demais campos (*p*, *esquerda*, *direita*, *chave*) podem assumir valores arbitrários conforme a conveniência de cada procedimento.

A vantagem é poder tratar o filho `NIL` de um nó $x$ como um nó comum cujo pai é $x$. Adicionar uma sentinela distinta para cada `NIL` desperdiçaria espaço, então uma única `T.nil` representa todas elas.

*OBS: Ao desenhar uma árvore red-black, é comum omitir as folhas `NIL` e o pai da raiz, mostrando apenas os nós internos que de fato carregam chaves.*

### Altura preta

A **altura preta** de um nó $x$, denotada $bh(x)$, é o número de nós pretos em qualquer caminho simples descendente de $x$ (sem contar $x$) até uma folha. Pela propriedade 5, essa noção é bem definida, já que todos os caminhos descendentes têm a mesma contagem de pretos. A altura preta da árvore é a altura preta de sua raiz.

**Exemplo de árvore Red-Black:** ![[exemplo_arvores_red_black.png]]

## Lema da altura

A garantia de desempenho da red-black vem do seguinte lema: *Uma árvore red-black com $n$ nós internos tem altura no máximo $2\lg(n + 1)$*.

Primeiro, mostra-se por indução na altura de $x$ que a subárvore enraizada em qualquer nó $x$ contém pelo menos $2^{bh(x)} - 1$ nós internos. Na base, se $x$ tem altura `0`, então $x$ é uma folha `T.nil` e sua subárvore contém $2^0 - 1 = 0$ nós internos. No passo indutivo, um nó interno $x$ com dois filhos tem cada filho com altura preta $bh(x)$ ou $bh(x) - 1$ (dependendo da cor do filho). Aplicando a hipótese de indução, cada filho tem pelo menos $2^{bh(x) - 1} - 1$ nós internos, logo:

$$(2^{bh(x) - 1} - 1) + (2^{bh(x) - 1} - 1) + 1 = 2^{bh(x)} - 1$$

Segundo, seja $h$ a altura da árvore. Pela propriedade 4, ao menos metade dos nós em qualquer caminho da raiz a uma folha (excluindo a raiz) é preta, então a altura preta da raiz é no mínimo $h/2$. Daí:

$$n \geq 2^{h/2} - 1$$

Passando o `1` para o lado esquerdo e tomando logaritmos:

$$\lg(n + 1) \geq h/2 \Longrightarrow h \leq 2\lg(n + 1)$$

Como consequência imediata, as operações de consulta (`SEARCH`, `MINIMUM`, `MAXIMUM`, `SUCCESSOR`, `PREDECESSOR`), que custam $O(h)$ em uma [[Árvores binárias de busca|BST]] , custam $O(\lg n)$ em uma red-black, pois são executadas diretamente sem modificar a árvore.

*OBS: As consultas funcionam sem alteração, mas `TREE-INSERT` e `TREE-DELETE` da [[Árvores binárias de busca|BST]] não podem ser usados diretamente: embora rodem em $O(\lg n)$, eles não garantem que a árvore resultante continue sendo red-black. Por isso a inserção e a eliminação precisam de versões especializadas.*

## Rotações

A inserção e a eliminação modificam a árvore e podem violar as propriedades red-black. Para restaurá-las, muda-se a cor de alguns nós e altera-se a estrutura de ponteiros por meio de **rotações**. 

Uma rotação é uma operação **local** que preserva a propriedade de árvore de busca binária.

Existem dois tipos: rotação para a esquerda e rotação para a direita, simétricas entre si. Em uma rotação para a esquerda em um nó $x$ (supondo que seu filho à direita $y$ não seja `T.nil`), $x$ "pivota" ao redor da ligação com $y$, $y$ se torna a nova raiz da subárvore, $x$ se torna o filho à esquerda de $y$, e o antigo filho à esquerda de $y$ se torna o filho à direita de $x$.

```
LEFT-ROTATE(T, x)
  y = x.direita              // define y
  x.direita = y.esquerda     // subárvore esq. de y vira subárvore dir. de x
  if y.esquerda ≠ T.nil
      y.esquerda.p = x
  y.p = x.p                  // liga o pai de x a y
  if x.p == T.nil
      T.raiz = y
  elseif x == x.p.esquerda
      x.p.esquerda = y
  else x.p.direita = y
  y.esquerda = x             // coloca x à esquerda de y
  x.p = y
```

O código de `RIGHT-ROTATE` é simétrico. Ambas as rotações custam $O(1)$, pois apenas um número constante de ponteiros é alterado, todos os demais atributos permanecem iguais.

A rotação preserva a ordenação porque mantém a relação de precedência entre as chaves. Por isso um percurso em ordem produz a mesma sequência antes e depois da rotação.

**Exemplo do processo de rotação e recoloração:** ![[exemplo_arvores_red_black_rotacao.png]]
## Inserção

A inserção em uma red-black de $n$ nós custa $O(\lg n)$. Usa-se uma versão modificada do `TREE-INSERT` da [[Árvores binárias de busca|BST]] para inserir o nó $z$ como se fosse uma árvore de busca comum, e depois um procedimento auxiliar `RB-INSERT-FIXUP` recolore e rotaciona para restaurar as propriedades.

```
RB-INSERT(T, z)
  y = T.nil
  x = T.raiz
  while x ≠ T.nil
      y = x
      if z.chave < x.chave
          x = x.esquerda
      else x = x.direita
  z.p = y
  if y == T.nil
      T.raiz = z
  elseif z.chave < y.chave
      y.esquerda = z
  else y.direita = z
  z.esquerda = T.nil
  z.direita = T.nil
  z.cor = VERMELHO
  RB-INSERT-FIXUP(T, z)
```

Há quatro diferenças em relação ao `TREE-INSERT` da BST: 

1. As instâncias de `NIL` viram `T.nil`. 
2. Os filhos de $z$ são definidos como `T.nil`.
3. $z$ é colorido de **vermelho**.
4. Chama-se `RB-INSERT-FIXUP` ao final.

O novo nó $z$ é colorido de vermelho justamente para não violar a propriedade 5 (a contagem de pretos não muda). Mas colorir $z$ de vermelho pode violar a propriedade 2 (se $z$ for a raiz) ou a propriedade 4 (se o pai de $z$ também for vermelho).

### RB-Insert-Fixup

```
RB-INSERT-FIXUP(T, z)
  while z.p.cor == VERMELHO
      if z.p == z.p.p.esquerda
          y = z.p.p.direita              // y é o "tio" de z
          if y.cor == VERMELHO
              z.p.cor = PRETO            // caso 1
              y.cor = PRETO              // caso 1
              z.p.p.cor = VERMELHO       // caso 1
              z = z.p.p                  // caso 1
          else if z == z.p.direita
                  z = z.p                // caso 2
                  LEFT-ROTATE(T, z)      // caso 2
              z.p.cor = PRETO            // caso 3
              z.p.p.cor = VERMELHO       // caso 3
              RIGHT-ROTATE(T, z.p.p)     // caso 3
      else (igual, com "direita" e "esquerda" trocadas)
  T.raiz.cor = PRETO
```

A única propriedade que pode ser violada ao entrar no laço é a 4: $z$ é vermelho e seu pai $z.p$ também é. O laço sobe pela árvore até que $z.p$ seja preto. O comportamento depende da cor do **tio** $y$ de $z$ (o irmão de $z.p$). Os três casos são descritos para a situação em que $z.p$ é filho à esquerda do avô $z.p.p$, os outros três são simétricos.

- **Caso 1 - o tio $y$ é vermelho:** Recolore-se $z.p$ e $y$ de preto e o avô $z.p.p$ de vermelho. Isso corrige a violação localmente e empurra o problema dois níveis para cima, fazendo $z = z.p.p$ e repetindo o laço. A altura preta é preservada.
- **Caso 2 - o tio $y$ é preto e $z$ é filho à direita:** Faz-se $z = z.p$ e uma rotação para a esquerda, transformando a situação no caso 3.
- **Caso 3 - o tio $y$ é preto e $z$ é filho à esquerda:** Recolore-se $z.p$ de preto e $z.p.p$ de vermelho, e faz-se uma rotação para a direita em $z.p.p$. Isso encerra o laço, pois não há mais dois nós vermelhos em sequência.

A última linha colore a raiz de preto, restaurando a propriedade 2 caso ela tenha sido violada.

### Análise da inserção

As linhas de `RB-INSERT` antes do *fixup* custam $O(\lg n)$, pois percorrem um caminho da raiz. Em `RB-INSERT-FIXUP`, o laço só se repete quando o caso 1 ocorre, e nesse caso $z$ sobe dois níveis. Como a árvore tem altura $O(\lg n)$, o laço executa $O(\lg n)$ vezes. Os casos 2 e 3 encerram o laço imediatamente. Portanto, `RB-INSERT` custa $O(\lg n)$ e executa **no máximo duas rotações**, já que os casos 2 e 3 terminam o laço.

## Eliminação

A eliminação é mais complexa que a inserção, mas também custa $O(\lg n)$. Ela se baseia no `TREE-DELETE` da [[Árvores binárias de busca|BST]], com a subrotina `TRANSPLANT` customizada para red-black e um procedimento auxiliar `RB-DELETE-FIXUP` ao final.

### RB-Transplant

```
RB-TRANSPLANT(T, u, v)
  if u.p == T.nil
      T.raiz = v
  elseif u == u.p.esquerda
      u.p.esquerda = v
  else u.p.direita = v
  v.p = u.p
```

Há duas diferenças em relação ao `TRANSPLANT` da BST: 

1. A linha 1 referencia `T.nil` em vez de `NIL`.
2. A atribuição `v.p = u.p` ocorre **incondicionalmente** (pode-se atribuir a $v.p$ mesmo que $v$ seja a sentinela). 

Essa capacidade de atribuir a $v.p$ quando $v = T.nil$ é explorada na eliminação.

### RB-Delete

```
RB-DELETE(T, z)
  y = z
  y-cor-original = y.cor
  if z.esquerda == T.nil
      x = z.direita
      RB-TRANSPLANT(T, z, z.direita)
  elseif z.direita == T.nil
      x = z.esquerda
      RB-TRANSPLANT(T, z, z.esquerda)
  else y = TREE-MINIMUM(z.direita)
      y-cor-original = y.cor
      x = y.direita
      if y.p == z
          x.p = y
      else RB-TRANSPLANT(T, y, y.direita)
          y.direita = z.direita
          y.direita.p = y
      RB-TRANSPLANT(T, z, y)
      y.esquerda = z.esquerda
      y.esquerda.p = y
      y.cor = z.cor
  if y-cor-original == PRETO
      RB-DELETE-FIXUP(T, x)
```

O procedimento mantém o nó $y$ como o nó que é fisicamente removido ou movido na árvore, e o nó $x$ como o que ocupa a posição original de $y$. 

Quando $z$ tem menos de dois filhos, $y$ é o próprio $z$. Quando $z$ tem dois filhos, $y$ é o sucessor de $z$ (o mínimo da subárvore direita), que assume a posição de $z$ e herda sua cor.

A variável `y-cor-original` guarda a cor de $y$ antes de qualquer mudança. Isso importa porque, se a cor removida da árvore for **preta**, a propriedade 5 pode ser violada (algum caminho perde um nó preto) e dois nós vermelhos podem se tornar adjacentes (propriedade 4). Se a cor removida for vermelha, nenhuma propriedade é violada e nenhum reparo é necessário.

Quando um nó preto $y$ é removido ou movido, sua cor é transferida para o nó $x$ que o substitui, tornando $x$ **duplamente preto** (ou *vermelho e preto*). Esse preto extra é o que viola a propriedade 1 e precisa ser empurrado para cima na árvore até ser absorvido.

### RB-Delete-Fixup

```
RB-DELETE-FIXUP(T, x)
  while x ≠ T.raiz e x.cor == PRETO
      if x == x.p.esquerda
          w = x.p.direita               // w é o irmão de x
          if w.cor == VERMELHO
              w.cor = PRETO              // caso 1
              x.p.cor = VERMELHO         // caso 1
              LEFT-ROTATE(T, x.p)        // caso 1
              w = x.p.direita            // caso 1
          if w.esquerda.cor == PRETO e w.direita.cor == PRETO
              w.cor = VERMELHO           // caso 2
              x = x.p                    // caso 2
          else if w.direita.cor == PRETO
                  w.esquerda.cor = PRETO // caso 3
                  w.cor = VERMELHO       // caso 3
                  RIGHT-ROTATE(T, w)     // caso 3
                  w = x.p.direita        // caso 3
              w.cor = x.p.cor            // caso 4
              x.p.cor = PRETO            // caso 4
              w.direita.cor = PRETO      // caso 4
              LEFT-ROTATE(T, x.p)        // caso 4
              x = T.raiz                 // caso 4
      else (igual, com "direita" e "esquerda" trocadas)
  x.cor = PRETO
```

O objetivo do laço é mover o preto extra para cima na árvore. Ele continua até que $x$ aponte para um nó vermelho-e-preto (que é simplesmente colorido de preto na linha final), ou até $x$ chegar à raiz (onde o preto extra é apenas descartado). O comportamento depende da cor do **irmão** $w$ de $x$. Os quatro casos são descritos para $x$ sendo filho à esquerda, os simétricos valem para filho à direita.

- **Caso 1 - o irmão $w$ é vermelho:** Trocam-se as cores de $w$ e $x.p$, e faz-se uma rotação para a esquerda em $x.p$. O novo irmão de $x$ passa a ser preto, convertendo o caso 1 em um dos casos 2, 3 ou 4.
- **Caso 2 - $w$ é preto e ambos os filhos de $w$ são pretos:** Remove-se um preto de $w$ (colorindo-o de vermelho) e empurra-se o preto extra para $x.p$, fazendo $x = x.p$ e repetindo o laço. É o único caso que faz o laço se repetir.
- **Caso 3 - $w$ é preto, filho à esquerda de $w$ é vermelho e filho à direita é preto:** Trocam-se as cores de $w$ e de seu filho à esquerda, e faz-se uma rotação para a direita em $w$. O novo irmão de $x$ passa a ter um filho à direita vermelho, transformando o caso 3 no caso 4.
- **Caso 4 - $w$ é preto e o filho à direita de $w$ é vermelho:** Algumas mudanças de cor e uma rotação para a esquerda em $x.p$ removem o preto extra, tornando $x$ unicamente preto. Define-se $x = T.raiz$ para encerrar o laço.

### Análise da eliminação

A parte de `RB-DELETE` sem o *fixup* custa $O(\lg n)$. Em `RB-DELETE-FIXUP`, os casos 1, 3 e 4 encerram após um número constante de mudanças de cor e no máximo três rotações. O caso 2 é o único que repete o laço, e move $x$ para cima $O(\lg n)$ vezes sem rotacionar. Portanto, `RB-DELETE-FIXUP` custa $O(\lg n)$ e executa **no máximo três rotações**, e o tempo total de `RB-DELETE` é $O(\lg n)$.

## Tabela de complexidades

| **Operação** | **Tempo (pior caso)** | **Rotações** |
|---|---|---|
| Busca / Mínimo / Máximo | $O(\lg n)$ | — |
| Sucessor / Predecessor | $O(\lg n)$ | — |
| Rotação | $O(1)$ | 1 |
| Inserção | $O(\lg n)$ | $\leq 2$ |
| Eliminação | $O(\lg n)$ | $\leq 3$ |

A diferença fundamental para a [[Árvores binárias de busca|BST]] comum é que esses limites valem no **pior caso**, e não apenas em média. O preço pago é o bit de cor por nó e a lógica adicional de recoloração e rotação nas operações que modificam a árvore.

*OBS: Existem outros esquemas de árvore balanceada com a mesma garantia $O(\lg n)$, como as árvores AVL e as árvores B (estas otimizadas para armazenamento em disco). A red-black costuma ser preferida na prática por fazer menos rotações na eliminação que a AVL, o que a torna eficiente em estruturas com muitas modificações.*

## Referências

- Baseado no livro [[500 Materiais/data-structure/books/algoritmos-teoria-pratica.pdf|Algoritmos: Teoria e Prática]].
- O vídeo [Árvores: O Começo de TUDO | Estruturas de Dados e Algoritmos](https://youtu.be/9GdesxWtOgs?t=2147) a partir do minuto **35:47** explica de forma clara e resumida o que é uma árvore red-black, o processo de inserção, rotação e recoloração dos nós na árvore.

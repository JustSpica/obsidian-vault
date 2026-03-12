# Arrays

Array é um vetor unidimensional que armazena uma sequência de elementos do mesmo tipo, de forma sequencial na memória.

Pelo array ter os elementos alocados de forma sequencial e contígua na memória, isso nos permite usar um cálculo de [[Ponteiros|ponteiros]] para encontrar qualquer elemento desse array, dado que eu saiba o endereço do elemento inicial. 

Dado um array declarado, o nome do array representa o endereço do primeiro elemento (índice 0). O elemento de índice `n` fica a um deslocamento de `i * (tamanho em bytes do tipo do array)` bytes a partir do início:

```C
Address(values[i]) = Base_address(values) + i * sizeof(type) // "i" é o meu índice
```

Por exemplo, supondo que declaro o array `int values[5];` onde cada `int` ocupa 4 bytes, e que `values` inicia no endereço hipotético 1000:

- Endereço de `values[0]` = 1000 (posição inicial)
- Endereço de `values[1]` = 1000 + 1 * 4 = 1004
- Endereço de `values[2]` = 1000 + 2 * 4 = 1008
- Endereço de `values[3]` = 1000 + 3 * 4 = 1012
- Endereço de `values[4]` = 1000 + 4 * 4 = 1016
## **Referências**

- No vídeo [Hello World Como Você Nunca Viu! | Entendendo C](https://www.youtube.com/watch?v=Gp2m8ZuXoPg&t=1338s) a partir do minuto **22:18** tem uma boa explicação sobre o que são arrays e outros assuntos como endereços e referências, ponteiros e recursão.
- No vídeo [O que vem DEPOIS do Hello World | Consertando meu C](https://www.youtube.com/watch?v=YyWMN_0g3BQ&ab_channel=FabioAkita) do início do vídeo até os **15:56** possuem algumas erratas em relação ao vídeo anterior e complementos como segmento de memória virtual e comparação com o array do Javascript.
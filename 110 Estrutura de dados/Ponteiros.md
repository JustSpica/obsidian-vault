# Ponteiros

Ponteiro nada mais é do que uma variável que armazena o endereço de memória de outra variável, em vez de armazenar um valor direto.

Em sua essência, um ponteiro permite a manipulação indireta de dados. Em vez de operar diretamente sobre um valor, opera-se sobre sua localização na memória, sendo crucial para a implementação de diversas estrutura de dados como [[Listas encadeadas]], [[Árvores]] e [[Grafos]], onde os elementos não estão necessariamente armazenaddos em blocos contíguos na memória.

O tamanho de um ponteiro em C depende da arquitetura da máquina, não do tipo de dado para o qual ele aponta:

- Em **32 bits** , todos os ponteiros normalmente ocupam **4 bytes** .
- Em **64 bits** , todos os ponteiros normalmente ocupam **8 bytes** .

Linguangens como C, C++, Pascal e Go oferecem um suporte direto e explícito a ponteiros, significa que eu posso:

- Declarar variáveis do tipo ponteiro.
- Obter o endereço de memória de uma variável usando operadores específicos (como o `&` em C/C++).
- Acessar o valor armazenado no endereço apontado (através da "desreferenciação", com o operador `*` em C/C++).
- Realizar operações aritméticas com os endereços de memória.

Já outras linguagens de programação modernas, embora internamente façam uso de conceitos análogos aos ponteiros para gerenciar a memória, não os expõem diretamente ao programador, como é o caso de Java, Javascript, Python e até C++ que a tendência moderna é desencorajar o uso de *raw pointers* em favor de *smart pointers* (como `std::unique_ptr` e `std::shared_ptr`)

**Exemplo de declaração de um ponteiro em C:**

```C
int main() {
    int var = 10;
    
    // Variável ponteiro que armazena o endereço de "var".
    int* ptr = &var; 
     
    // Acessando diretamente o ponteiro.
    printf("%d", ptr); // Output: 0x7fffa0757dd4
    
    // Desreferencia de ponteiro para acessar o valor.
    printf("%d", *ptr) // Output: 10
    
    return 0;
}
```
## **Referências**

- O artigo [Ponteiros C](https://www.geeksforgeeks.org/c/c-pointers/) do geeksforgeeks possui bons exemplos e definição sobre ponteiros.
- O vídeo [Hello World Como Você Nunca Viu! | Entendendo C](https://www.youtube.com/watch?v=Gp2m8ZuXoPg&t=2577s) a partir de **42:57** até **48:55** tem uma excelente explicação básica do que são ponteiros e um exemplo prático em C. 
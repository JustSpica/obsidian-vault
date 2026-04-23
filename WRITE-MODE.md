# WRITE-MODE

## Propósito

Este arquivo descreve o padrão de escrita observado nas notas já produzidas, mas formulado de modo **agnóstico ao assunto**.

A ideia não é definir um tema, e sim registrar **como a escrita funciona**: estrutura, tom, ritmo, densidade, uso de links, observações e referências.

## Resumo do estilo

O estilo é **técnico, didático, modular e orientado a revisão**.

Ele privilegia:

- definição clara logo no início;
- blocos curtos e bem segmentados;
- progressão do geral para o específico;
- ligação constante entre conceitos;
- preocupação com exceções, limites e interpretações erradas;
- fechamento com fontes quando fizer sentido.

Não é escrita de artigo longo, nem texto acadêmico pesado. É escrita de **nota de estudo para consulta rápida**, mas com precisão suficiente para sustentar entendimento real.

## Intenção da escrita

Cada nota tende a cumprir uma função muito específica:

- explicar o que algo é;
- situar esse algo dentro de um contexto maior;
- mostrar como ele funciona;
- apontar por que ele importa;
- registrar onde costuma haver confusão.

Ou seja, a nota não tenta apenas nomear um conceito. Ela tenta torná-lo utilizável mentalmente.

## Estrutura recorrente

O padrão mais comum é:

1. Título direto com o nome do tema.
2. Abertura curta definindo o assunto.
3. Seções quebradas por aspecto, função, tipo, funcionamento ou implicação.
4. Uso de listas para organizar elementos que precisam ser lembrados.
5. Inserções de `*OBS:*` para nuance, exceção ou correção de simplificação.
6. Fechamento com referências, se a nota estiver apoiada em material externo.

Esse formato favorece leitura rápida sem virar lista seca de tópicos.

## Como a nota costuma começar

A abertura normalmente tenta entregar três coisas de uma vez:

- definição;
- contexto;
- função.

Em termos práticos, a primeira frase costuma responder:

- `o que é isso?`
- `onde isso se encaixa?`
- `para que isso serve?`

Esse início evita introduções longas demais e reduz ambiguidade logo no começo.

## Ordem típica de explicação

O desenvolvimento costuma seguir esta lógica:

1. Conceito central.
2. Partes ou categorias internas.
3. Funcionamento.
4. Efeito prático.
5. Limites, pegadinhas ou exceções.

Nem toda nota precisa ter todas essas camadas, mas essa é a progressão dominante.

## Tom de voz

O tom é:

- direto;
- explicativo;
- tecnicamente preciso;
- informal com controle.

O texto evita dois extremos:

- formalismo excessivo;
- simplificação solta demais.

O resultado é uma voz que tenta ser séria sem ficar dura, e acessível sem ficar rasa.

## Ritmo das frases

As frases tendem a ser:

- relativamente curtas;
- orientadas por causa e efeito;
- quebradas em blocos lógicos;
- seguidas de listas quando há enumeração natural.

Quando uma ideia fica abstrata demais, a escrita puxa para consequência concreta com construções como:

- `Na prática, ...`
- `Isso significa que ...`
- `Por isso, ...`
- `Em geral, ...`
- `Se ... então ...`

Essas fórmulas aparecem como mecanismo de clareza, não como vício vazio.

## Estratégia didática

O padrão didático dominante é explicar por camadas.

### Definir primeiro

Primeiro a nota estabelece o núcleo do conceito. Isso evita que o leitor percorra vários parágrafos sem saber exatamente o objeto da explicação.

### Decompor depois

Depois da definição, o assunto é quebrado em partes menores, como tipos, campos, etapas, propriedades, regras, cenários ou classificações.

### Mostrar consequência

A explicação geralmente não para em `o que é`. Ela avança para `o que isso muda`.

Essa transição é uma marca forte do estilo. O conceito quase sempre é acompanhado por impacto, comportamento esperado, limitação ou efeito observável.

### Corrigir simplificações

As observações `*OBS:*` entram justamente quando a explicação principal, por ser didática, pode induzir uma leitura incompleta.

Elas servem para:

- acrescentar nuance;
- registrar exceção;
- corrigir uma simplificação comum;
- separar modelo didático de caso real.

### Relacionar com outras notas

As notas são escritas como partes de uma rede de conceitos. Por isso, o texto frequentemente remete a outros pontos do vault em vez de reexplicar tudo dentro da mesma página.

## Uso de links internos

Os links `[[...]]` fazem parte da escrita, não apenas da organização do vault.

Eles ajudam a:

- conectar conceitos sem repetir blocos inteiros;
- manter notas curtas sem perder profundidade;
- transformar uma nota em ponto de entrada para um assunto maior;
- preservar continuidade entre materiais.

O uso de alias é especialmente importante porque permite encaixar o link em linguagem natural.

Exemplo abstrato:

```md
[[conceito-base|nome natural dentro da frase]]
```

## Uso de listas

Listas aparecem quando melhoram retenção e escaneabilidade.

São usadas principalmente para:

- propriedades;
- etapas;
- categorias;
- diferenças;
- consequências;
- regras práticas.

O texto tende a usar:

- lista numerada quando existe ordem, sequência ou hierarquia;
- lista com `-` quando a ordem não importa.

## Uso de exemplos

O estilo favorece exemplos quando eles reduzem abstração.

O padrão mais comum é:

1. introduzir a ideia;
2. preparar o exemplo com uma frase curta;
3. mostrar imagem, tabela, cenário ou caso;
4. voltar à explicação.

O exemplo não entra sozinho. Ele é sempre amarrado à ideia que precisa ser iluminada.

## Uso de imagens e tabelas

Imagens e tabelas aparecem como apoio, não como substituto da explicação.

Antes delas, costuma haver uma frase do tipo:

- `Exemplo:`
- `Estrutura geral:`
- `Comparação:`
- `Caso prático:`

Isso prepara a leitura e evita que o elemento visual fique solto.

## Formatação recorrente

O padrão de formatação é simples e estável:

- `#` para o título da nota;
- `##` e `###` para organizar subtemas;
- `**negrito**` para conceitos centrais;
- `*itálico*` para observações, termos estrangeiros ou ênfase leve;
- `` `código` `` para valores literais, nomes, sintaxe, identificadores ou exemplos formais.

Não há dependência de enfeite visual. A legibilidade vem mais da estrutura do que da ornamentação.

## Tratamento do vocabulário técnico

O vocabulário segue uma lógica híbrida:

- português como base;
- termos técnicos mantidos no idioma mais natural para a área, quando isso melhora precisão;
- explicação contextual quando o termo sozinho não basta.

O foco não é traduzir tudo. O foco é manter o texto claro sem perder aderência ao uso real do tema.

## Densidade da nota

As notas tendem a ser densas, mas não compactadas demais.

Isso significa:

- pouca enrolação;
- pouco contexto ornamental;
- bastante informação por seção;
- segmentação suficiente para consulta rápida.

O conteúdo normalmente vai além de definição superficial, mas para antes de virar documentação exaustiva.

## Relação com fontes

Quando a nota nasce de material-base, as fontes costumam aparecer de dois jeitos:

- no corpo do texto, quando uma formulação ou ideia é atribuída;
- no fim, em `## Referências`.

Isso cria dois efeitos:

- deixa explícito de onde veio a formulação;
- mantém a nota útil mesmo fora do contexto imediato da aula, livro ou material original.

## O que o estilo tenta evitar

O padrão observado evita:

- introduções longas sem definição;
- texto corrido demais;
- enumeração sem explicação;
- excesso de jargão sem amarração;
- simplificação que apaga nuance importante;
- exemplo jogado sem preparação;
- conclusão sem fonte quando a nota depende de estudo externo.

## Template agnóstico

Um esqueleto fiel a esse modo de escrita seria:

```md
# Nome do tema

Definição curta do conceito, já situando onde ele se encaixa e por que ele importa.

*OBS: Se existir uma confusão comum logo no começo, ela pode ser corrigida aqui.*

## Parte principal

Explicação objetiva do primeiro bloco do assunto.

- propriedade, tipo ou regra;
- propriedade, tipo ou regra;
- propriedade, tipo ou regra.

## Funcionamento

Descrição de como o conceito opera ou se manifesta.

## Efeito prático

Consequência, uso, limitação ou impacto observável.

## Exemplo

Frase curta preparando o caso, tabela ou imagem.

## Limites ou pegadinhas

*OBS: Nuance, exceção ou simplificação que precisa ser corrigida.*

## Referências

- Fonte 1.
- Fonte 2.
```

## Checklist implícito de escrita

Antes de considerar uma nota pronta, este estilo tende a checar implicitamente:

- o conceito foi definido cedo?
- ficou claro onde ele se encaixa?
- a explicação saiu da definição e chegou na consequência?
- há boa segmentação visual?
- os links internos ajudam sem poluir?
- existe alguma simplificação que precisa de `*OBS:*`?
- as fontes foram registradas quando necessário?

## Síntese

Este modo de escrita pode ser resumido assim:

**definir cedo, organizar em blocos curtos, explicar por consequência, conectar com outras notas, registrar nuance com `OBS` e escrever para revisão rápida sem perder precisão.**

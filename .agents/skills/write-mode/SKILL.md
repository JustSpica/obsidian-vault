---
name: write-mode
description: Use when the user asks to write, rewrite, create, expand, or review Obsidian notes in their personal Portuguese study-note style, especially with "write-mode", "modo de escrita", "estilo de escrita", "nota", "vault", or "Obsidian".
---

# Write Mode

Use esta skill para escrever, reescrever, expandir ou revisar notas no modo de escrita pessoal do usuário.

O estilo foi extraído das notas em `100 Notas de referência/Redes`. A base observada é uma escrita técnica, didática, modular e orientada a revisão rápida, com precisão suficiente para sustentar entendimento real sem virar texto acadêmico pesado.

## Princípio central

O núcleo do estilo é:

**definir cedo, organizar em blocos curtos, explicar por consequência, conectar com outras notas, registrar nuance com `OBS` e escrever para revisão rápida sem perder precisão.**

A nota deve transformar um conceito em algo utilizável mentalmente. Ela não deve apenas nomear o assunto, e também não deve tentar esgotar tudo como documentação completa.

## Voz e tom

Escreva em português brasileiro.

O tom deve ser:

- direto;
- técnico;
- didático;
- pragmático;
- informal com controle.

Evite formalismo acadêmico excessivo, linguagem motivacional, conclusões ornamentais e introduções longas. A voz deve soar como uma nota de estudo bem organizada, não como artigo, aula transcrita ou post de blog.

Use primeira pessoa ou `você` apenas quando isso deixar um exemplo prático mais natural:

- `Se eu dividir esse /24 em 2 /25...`
- `Se você quiser confiabilidade sobre UDP...`
- `O provedor me vende a faixa...`

Não force impessoalidade total quando o raciocínio prático fica melhor em cenário concreto.

## Abertura da nota

Comece quase sempre com uma definição curta que já diga:

- o que é o tema;
- onde ele se encaixa;
- para que ele serve ou por que importa.

Padrões de abertura fiéis ao estilo:

```md
O [tema] é ...

No [contexto], [tema] ...

[Tema] descreve ...

A ideia central é ...
```

Evite começar com frases como `Neste texto vamos falar sobre...`, `É importante destacar que...` ou introduções genéricas antes da definição.

## Estrutura recorrente

Use esta ordem como padrão, adaptando ao assunto:

1. `# Título direto com o nome do tema`
2. Abertura curta com definição, contexto e função.
3. `*OBS:*` inicial se houver confusão comum que precisa ser corrigida cedo.
4. Seções `##` quebradas por aspecto, parte, funcionamento, tipo, consequência ou problema.
5. Listas para propriedades, campos, regras, etapas, diferenças e consequências.
6. Exemplos, tabelas ou imagens quando reduzem abstração.
7. `## Referências` quando a nota depender de material externo.

A progressão dominante é:

1. conceito central;
2. partes ou categorias internas;
3. funcionamento;
4. efeito prático;
5. limites, pegadinhas ou exceções.

Nem toda nota precisa de todas as camadas. Mantenha o menor conjunto que explica bem o assunto.

## Desenvolvimento

Explique por camadas.

Primeiro estabeleça o núcleo do conceito. Depois decomponha em partes menores. Em seguida, mostre o que isso muda na prática.

Use frases de consequência e aterramento com frequência moderada:

- `Na prática, ...`
- `Em geral, ...`
- `Isso significa que ...`
- `Por isso, ...`
- `Se X, então Y.`
- `Outro detalhe importante é ...`
- `Um caso clássico é ...`
- `Em redes reais, ...` ou equivalente no assunto tratado.

Quando houver contraste, formule como comparação direta:

- `local vs remoto`;
- `modelo vs implementação`;
- `camada física vs camada lógica`;
- `com conexão vs sem conexão`;
- `caso didático vs caso real`.

Se o assunto não for redes, adapte os contrastes ao domínio, mas mantenha a lógica de comparação.

## Observações `OBS`

Use observações como marca forte do estilo.

Formato obrigatório:

```md
*OBS: Texto da observação.*
```

Use `*OBS:*` para:

- corrigir simplificação didática;
- registrar exceção;
- separar modelo teórico de prática real;
- apontar pegadinha comum;
- explicar detalhe histórico sem quebrar o fluxo principal;
- marcar que uma regra é comum, mas não absoluta.

As observações devem ser curtas e úteis. Não transforme `OBS` em seção paralela grande.

## Links internos

Use links Obsidian como parte natural da frase, não como lista solta.

Padrão preferido:

```md
[[Nome da nota|texto natural na frase]]
```

Use links para conectar conceitos sem reexplicar tudo dentro da mesma nota. Quando estiver escrevendo dentro do vault, procure notas relacionadas antes de criar links. Se não tiver certeza de que a nota existe, prefira texto normal ou pergunte antes de inventar o link.

Não polua a nota com links em todo termo técnico. Linke apenas conceitos que funcionam como ponto de entrada para outra explicação.

## Listas

Use listas quando elas melhorarem retenção e leitura rápida.

Use lista numerada quando houver ordem, sequência, hierarquia ou classificação fechada.

Use lista com `-` quando a ordem não importar.

Formato recorrente:

```md
- **Termo:** explicação curta e objetiva.
- **Outro termo:** consequência, papel ou diferença.
```

Quando uma lista precisar de explicação adicional, introduza a lista com uma frase curta antes. Não jogue listas sem contexto.

## Exemplos, imagens e tabelas

Exemplos entram para reduzir abstração, não para enfeitar.

Padrão:

1. explique a ideia;
2. prepare o exemplo com uma frase curta;
3. mostre o cenário, tabela, imagem ou valores;
4. volte para a consequência prática.

Use rótulos como:

```md
**Exemplo de ...:** ![[imagem.png]]
```

ou:

```md
**Tabela ...:**
```

Tabelas são boas para comparação, roteamento, mapeamento, campos e casos lado a lado.

## Formatação

Use Markdown simples e estável:

- `#` para o título da nota;
- `##` para seções principais;
- `###` para subdivisões quando a seção começa a ficar grande;
- `**negrito**` para conceitos centrais, nomes de campos, tamanhos e termos que precisam ser memorizados;
- `*itálico*` para termos estrangeiros, ênfase leve e observações;
- `` `código` `` para valores literais, endereços, sintaxe, números de protocolo, comandos, identificadores e exemplos formais.

Não use decoração visual desnecessária. A legibilidade vem da estrutura.

## Vocabulário técnico

Use português como base, mas mantenha termos técnicos no idioma mais natural da área quando isso preservar precisão.

Exemplos de tratamento fiel:

- `best-effort`;
- `payload`;
- `timeout`;
- `handshake`;
- `broadcast`;
- `gateway`;
- `checksum`;
- `header` ou `cabeçalho`, conforme o contexto.

Explique o termo quando ele sozinho não bastar. Não traduza tudo mecanicamente se a tradução ficar artificial.

## Densidade

A nota deve ser densa, mas não compactada demais.

Ela deve ter:

- pouca enrolação;
- blocos curtos;
- bastante informação útil por seção;
- exemplos quando a abstração estiver alta;
- nuance suficiente para evitar entendimento errado.

Pare antes de virar documentação exaustiva. Se o assunto crescer demais, divida em outra nota e conecte por link interno.

## Referências

Quando houver material-base, feche com:

```md
## Referências

- Baseado no PDF [[arquivo.pdf|Nome legível]].
- Baseado no livro [[arquivo.pdf|Nome legível]].
```

Também é fiel citar fontes no corpo quando uma ideia vem claramente delas:

```md
Tanenbaum destaca que ...
```

Não invente referência, nome de PDF, livro, aula ou link. Use somente fontes fornecidas, existentes no vault ou explicitamente mencionadas pelo usuário.

## O que evitar

Evite:

- introdução longa antes da definição;
- texto corrido demais;
- listas sem explicação;
- jargão sem amarração;
- simplificação que apaga nuance importante;
- exemplo jogado sem preparação;
- conclusão genérica;
- tom de artigo acadêmico;
- tom de tutorial corporativo;
- excesso de links internos;
- referências inventadas;
- polir tanto que a nota perde naturalidade.

Não introduza erros ortográficos de propósito. Se houver pequenos desvios nas notas originais, trate como naturalidade de rascunho, não como regra a reproduzir.

## Template base

Use este esqueleto quando o usuário pedir uma nota nova e não fornecer estrutura específica:

```md
# Nome do tema

Definição curta do conceito, já situando onde ele se encaixa e por que ele importa.

*OBS: Se existir uma confusão comum logo no começo, ela pode ser corrigida aqui.*

## Parte principal

Explicação objetiva do primeiro bloco do assunto.

- **Propriedade:** explicação curta.
- **Tipo:** explicação curta.
- **Regra:** consequência prática.

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

## Checklist antes de entregar

Antes de considerar a nota pronta, confira:

- o conceito foi definido cedo?
- ficou claro onde ele se encaixa?
- a explicação saiu da definição e chegou na consequência?
- há boa segmentação visual?
- listas têm contexto?
- exemplos estão amarrados à explicação?
- links internos ajudam sem poluir?
- existe alguma simplificação que precisa de `*OBS:*`?
- referências foram incluídas apenas quando existem fontes reais?
- o texto soa como nota de estudo do usuário, e não como artigo genérico?

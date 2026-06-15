---
name: writing-style
description: Replicate the user's personal note-taking style for the Obsidian vault (Computer Science college notes in Brazilian Portuguese). Use whenever drafting, expanding, or rewriting notes inside the vault so the output matches the user's voice, structure, and formatting conventions.
---

# Writing style

These rules describe how the user writes reference notes in this Obsidian vault. Notes are study material for college Computer Science topics (networking, linear algebra, etc.), written in **Brazilian Portuguese**. The reader is the user himself, weeks or months later. The goal is durable comprehension: enough depth to study the topic later without reopening the source for the main idea, while still avoiding filler. Every choice in the style serves clarity, recall, and connecting concepts.

When writing or editing notes inside `100 Notas de referência/`, follow these rules faithfully. The output must be indistinguishable from notes the user wrote himself.

## Global rules

- **Language:** Brazilian Portuguese. Technical English terms (protocol names, classical terms, original acronyms) stay in italic on first relevant mention: `*Transmission Control Protocol*`, `*best-effort*`, `*round-trip time*`.
- **Tone:** explanatory and confident, neither academic nor casual. The user is teaching his future self — direct, no filler, no hedging like "talvez seja interessante notar que...".
- **Person:** mostly impersonal third person. Slip into first person ("eu posso", "eu preciso", "se eu dividir") **only** when walking through a concrete worked example or a calculation. Never in conceptual exposition.
- **No padding:** no introductions like "Neste documento vamos ver...", no closing summaries like "Em resumo, vimos que...". Each section earns its place by adding information.
- **No emojis. Ever.**
- **Concise sentences, complete explanations:** prefer medium-short sentences and direct paragraphs, but do not remove mechanisms, examples, formulas, caveats, comparisons, or source details that are needed for understanding. Cut filler, not substance.

## Depth and coverage

Concision means avoiding filler, not making the note short. A note can and should be long when the reference material is dense.

When source material is provided, extract the important study content before writing. The note should let the future reader reconstruct the main idea, mechanism, and practical consequences of the topic without reopening the source.

For each important concept from the source, decide whether it needs one of these treatments:

- **Definition:** What it is.
- **Purpose:** Why it exists or what problem it solves.
- **Mechanism:** How it works internally, procedurally, or mathematically.
- **Example:** A concrete case, calculation, rule, diagram, or mini-scenario.
- **Contrast:** How it differs from a nearby concept.
- **Limitation:** Where it fails, becomes imprecise, or needs care.
- **Connection:** How it links to other notes in the vault.

Do not collapse a dense mechanism into one sentence just to keep the note short. If a source explains a process in steps, reproduce the process in steps. If a source gives formulas, criteria, algorithms, examples, edge cases, comparisons, or assumptions, preserve them unless they are clearly redundant.

For math-heavy notes, preserve formulas and at least one worked example when the source provides enough material. A formula without interpretation is usually too shallow; an interpretation without the formula is usually too vague.

A shallow note is worse than a long note with no filler. The target is not minimum length; the target is enough depth for studying.

## Document structure

Every note follows this skeleton:

```
# <Title>

<Opening definition: 1-5 sentences>

<Optional context paragraph: where this concept lives, what it serves for, why it matters>

*OBS: <optional first caveat if there's an obvious confusion to head off>*

## <First topical section>
...
## <More sections>
...
## Referências

- <reference list>
```

### Title (H1)

- Always one `# Title` at the top, matching the note's core concept.
- Use the concept's canonical name as the title — what someone would search for. Acronyms are titles when the acronym is what's commonly used (`TCP`, `UDP`, `ICMP`, `IPv4`, `VLANs e Protocolo IEEE 802.1q`).
- No subtitle, no metadata block, no frontmatter.

### Opening paragraph

The first paragraph **defines** the concept. Pattern:

> `<Concept> é/são <short definition>. Ele(s) serve(m) para <purpose> / aparece(m) em <context>.`

Examples from existing notes:

- "Vetores são objetos matemáticos que possuem **módulo**, **direção** e **sentido**. Eles servem para representar deslocamentos, posições relativas e grandezas com orientação."
- "O TCP (*Transmission Control Protocol*) é um protocolo da [[Modelos OSI e TCP IP|camada de transporte]] que oferece um **fluxo de bytes confiável, ordenado e orientado à conexão** sobre uma rede IP que, por si só, não garante entrega, ordem nem ausência de perdas."

Rules for the opening:

- Define before explaining. No history, no motivation before the definition lands.
- First mention of an acronym: full name in italic in parentheses — `TCP (*Transmission Control Protocol*)`.
- Bold the **core differentiating properties** in the definition (`**módulo**, **direção** e **sentido**`, `**fluxo de bytes confiável, ordenado e orientado à conexão**`).
- Link the parent concept with a wiki-link when relevant (`[[Modelos OSI e TCP IP|camada de transporte]]`).

### Context paragraph(s)

After the definition, add 1-3 focused paragraphs that situate the concept when useful. Keep them direct, but do not make context superficial just to keep the note short. Common patterns:

- **Where it lives in the stack:** "No [[IPv4]], o TCP aparece no campo **Protocolo** como `0x06`."
- **Where the idea shows up in CS practice:** "Em computação, a ideia aparece em muitos lugares: posição `(x,y,z)`, cor `(R,G,B)`, embeddings, atributos de um item, características de um usuário, etc."
- **Tanenbaum quote/summary** (for networking notes): "Tanenbaum resume a ideia central: o TCP existe para dar às aplicações a confiabilidade que o IP não fornece."
- **A reframing that breaks a common misconception** as an italic `*OBS: ...*`.

### H2 sections

Use `##` for the main topical divisions of the note. Section titles are short noun phrases naming what the section covers — `Cabeçalho TCP`, `Fragmentação`, `Sub-redes`, `Operações com matrizes`, `Soma de vetores`.

Inside each H2:

1. Start with a sentence introducing what this section addresses.
2. Then explain the necessary mechanism, process, properties, assumptions, formulas, criteria, or edge cases from the source.
3. Add a concrete example, calculation, mini-scenario, or comparison when the concept would otherwise stay abstract.
4. End with relevant `*OBS:*` notes if a subtlety needs flagging.

### H3 sections

Use `###` for sub-topics inside an H2 — typically:

- Specific **methods** of a general technique (`### Método das projeções`, `### Método poligonal`).
- **Specific cases** of a general concept (`### Em R2 (x, y)`, `### Em R3 (x, y, z)`).
- **Sub-protocols** or sub-mechanisms (`### CSMA/CD`, `### Trunk vs Access (tagged vs untagged)`).

Avoid H4 and deeper. If you'd reach for `####`, restructure.

### References section

Every note ends with `## Referências` listing sources as a bulleted list. Patterns:

```markdown
## Referências

- Baseado no PDF do La salle [[redes-aula-05.pdf|Redes - Aula 05]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].
- O vídeo [Título do vídeo](URL) tem uma boa explicação sobre <tópico>.
```

- PDF source: `Baseado no PDF do La salle [[arquivo.pdf|Alias legível]]`.
- Book source: `Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]]`.
- Video source: `O vídeo [<title>](<url>) <one-sentence description of what it covers>`.
- Sources are stated as facts ("Baseado no..."), not as a TODO ("Ver também:").

## Formatting conventions

### Bold (`**...**`)

Use bold for:

- **Key terms** on the line where they're first introduced or formally named: `**três camadas**`, `**three-way handshake**`, `**Diagonal Principal**`.
- **Labels** in definition-style bullet lists: `- **Conjunto unitário:** Contém exatamente um elemento`.
- **Distinguishing properties** in the opening definition (see above).
- **Field names** when listing header fields: `**Porta de origem (16 bits):** ...`.

Do not bold whole sentences. Do not bold for visual emphasis alone — bold is reserved for terminology.

### Italic (`*...*`)

Use italic for:

- **English/technical terms** that don't have a clean Portuguese equivalent: `*best-effort*`, `*Transmission Control Protocol*`, `*round-trip time*`, `*longest prefix match*`, `*EtherType*`, `*timeout*`.
- **OBS notes** — always entirely in italic (see OBS section below).
- **Emphasis on a single conceptual word** inside a definition: e.g., when "fim a fim" or "ponto a ponto" carries the weight of the sentence.

Italic is *not* used for general emphasis. If the sentence needs emphasis to be understood, rewrite the sentence.

### Inline code (`` `...` ``)

Use inline code for:

- IP addresses, MAC addresses, ports, prefixes: `192.168.10.50/24`, `FF:FF:FF:FF:FF:FF`, `:443`.
- Hex values, byte values, opcodes: `0x06`, `0x8100`, `0800`.
- Code identifiers, syscall names, flag names: `bind`, `listen`, `accept`, `SYN`, `ACK`, `FIN`, `eth0`, `eth0.10`.
- Network/CIDR notation: `/24`, `10.0.0.0/8`.
- Literal values from formulas or bit patterns: `0RRRRRRR HHHHHHHH`, `i = j`, `2^(bits_host) - 2`.
- Short technical strings the reader will see in a tool or config.

Inline code is **not** used for ordinary technical terms that have prose forms — write "broadcast" not `broadcast`.

### Code blocks

Used sparingly. Reserved for things that genuinely benefit from monospaced multi-line layout (worked snippets like the reference-list pattern above, or skeleton structures). Do **not** wrap math, IP examples, or short multi-value listings in code blocks — those go in LaTeX, inline code, or prose.

### LaTeX math

- Inline: `$...$` for variables and tiny expressions inside prose: `$\vec{v}=(v_x,v_y)$`, `$a_{ij}$`.
- Display: `$$...$$` for any formula that deserves its own line — definitions, derivations, worked steps. Math notes lean heavily on display math.
- Matrices use `\begin{bmatrix}...\end{bmatrix}`.
- Use `\begin{cases}...\end{cases}` for systems of equations.
- Use `\begin{align}...\end{align}` when chaining multiple equalities or steps.
- Use `\Longrightarrow` (`⟹`) inside math to chain transformations across an example.
- Use `\cancel{...}` to show cancellation in a step.
- For worked examples, embed multiple `$$...$$` blocks in sequence, with short prose lines between them explaining the step.

### Wiki-links (`[[...]]`)

Wiki-links carry a lot of weight in this vault — they're how concepts connect. Use them liberally but not gratuitously.

- **Always link** the first mention of another concept that has its own note: `[[Sistemas lineares|sistemas lineares]]`, `[[Modelos OSI e TCP IP|camada de rede]]`, `[[IPv4]]`.
- Use the `[[Note|alias]]` form when the natural reading word differs from the note's title, especially when linking to a noun phrase: `[[Topologias e Segmentação de redes LAN|domínio de broadcast]]`, `[[Padrão Ethernet|Ethernet]]`.
- Link the same concept once per section, not every occurrence. The second mention in the same section is plain text.
- PDF and book references in `## Referências` always use wiki-link form: `[[redes-aula-05.pdf|Redes - Aula 05]]`.

### Image embeds

`![[image_name.png]]` — Obsidian embed syntax. Patterns:

- **Inline labeled example:** `**Exemplo de cabeçalho TCP:** ![[exemplo_cabecalho_tcp.png]]` — bold caption, colon, then embed on the same line or directly below.
- **Caption-then-embed:** for figures that illustrate a worked example mentioned in the prose. The prose that precedes the image refers to "essa figura" / "o exemplo a seguir" / "como na figura abaixo".
- Image files live in `998 Imagens/` and are referenced by filename. Use the `998 Imagens/` prefix when needed to disambiguate.

### Lists

**Bulleted lists** (`- `) — use for:

- Taxonomies / classifications (`- **Classe A:** ...`).
- Properties or characteristics (`- não garante entrega; - não garante ordem;`).
- Header field breakdowns (`- **Porta de origem (16 bits):** ...`).
- Loose enumerations where order is irrelevant.

**Numbered lists** (`1. `) — use for:

- Sequential procedures (handshake steps, packet processing steps, calculation methods).
- Layer enumerations where the number matters (`1. **Física:** ...`).

**Definition-list style** (very common):

```
- **Term:** Description goes here, usually one sentence.
- **Other term:** Description.
```

The bold term is followed by `:` and a space, then a normal-sentence description. End with a period.

### Tables

Used when comparison is genuinely tabular (multiple rows × multiple columns of structured data):

- Routing tables.
- NAT translation tables.
- Comparison of properties across many entities.

Header row uses bold inside cells: `| **Rede** | **Destino** | **Observação** |`.

Don't tabulate something that fits as a prose comparison or a bulleted list.

## The OBS pattern

`*OBS: ...*` (entirely in italic, starting with `OBS:`) is a load-bearing pattern. It marks asides that are too important to omit but would disrupt the main flow.

Use OBS for:

- **Common misconceptions:** `*OBS: Um vetor não é apenas "uma seta desenhada". A seta é uma representação visual.*`
- **Boundary clarifications:** `*OBS: O `SYN` consome espaço de sequência.*`
- **Practical caveats vs theory:** `*OBS: Em redes reais, é comum evitar expor MAC diretamente...*`
- **Edge cases the reader will trip on:** `*OBS: Em geral, o primeiro e o último endereço da sub-rede não são atribuídos a hosts.*`
- **Modern-practice notes** that contradict the textbook: `*OBS: Em materiais introdutórios costuma-se dizer que o checksum do UDP é "opcional". Historicamente isso é verdade no IPv4. Na prática moderna, abrir mão dele raramente faz sentido.*`

Rules:

- Always starts with `*OBS:` and ends with `*`.
- One paragraph long. If it needs more, it's not an OBS — promote it to a normal paragraph or sub-section.
- Placed **after** the paragraph it qualifies, never before.
- A note can have several OBS asides; that's fine. They tend to cluster around dense conceptual sections.

## Voice patterns

### Tanenbaum as authority

Networking notes treat Tanenbaum as a recurring authority. Common phrasings:

- "Tanenbaum resume a ideia central: ..."
- "Tanenbaum destaca que ..."
- "Tanenbaum comenta que ..."
- "Tanenbaum diz que ..."
- "Tanenbaum define que ..."
- "Tanenbaum lista ... como ..."
- "De acordo com Tanenbaum, ..."

Use these to attribute **the key insight** of a section — not every fact, just the framing or the conceptual punchline. One Tanenbaum quote per section is plenty.

### Practical framing

Several openers signal "let's connect this to the real world":

- "Na prática, ..." — for real-world considerations and what actually happens vs the theoretical ideal.
- "Em geral, ..." — for the default/common case, often paired with an exception in an OBS.
- "Em redes reais, ..." — for what production deployments actually do.
- "Em redes cabeadas modernas, ..." / "Em redes sem fio, ..." — for environment-specific behavior.

### Examples

Examples are introduced and never just dropped. Common patterns:

- "Por exemplo, dado o sistema: $$...$$"
- "**Exemplo de cabeçalho TCP:** ![[...]]"
- "Por exemplo, para: $$...$$ Então: $$...$$ Com essas equações, é possível deduzir que ..."

When walking through a numeric or worked example, the user **does** use "eu" / "minha":

- "Eu preciso descobrir a projeção dos meus vetores ..."
- "Se eu dividir esse `/24` em 2 `/25`, terei duas redes: ..."
- "Na minha infra local eu tenho a seguinte situação: ..."

This is fine — and even desirable — inside examples. It mirrors the user thinking through the problem.

### Comparison and contrast

When two related concepts need disambiguation:

- A `## Comparação` section near the end of the note.
- Or a section titled `<A> vs <B>` (`Topologia física vs Topologia lógica`, `Trunk vs Access`).
- Inside, prefer bulleted contrasts: `- **Aspect:** A side vs B side`.

### Connecting ideas

Discourse markers that show up constantly:

- "Por isso, ..." — for consequences.
- "Isso significa que ..." — for explaining implications.
- "Isso permite que ..." — for capabilities unlocked by a feature.
- "Na prática, ..." — already covered.
- "A ideia é ..." — for restating the intent behind a mechanism.
- "Em outras palavras, ..." — only when actually rephrasing, never as filler.

## Section types worth knowing

These recur across notes — when a note covers one of these topics, lean on the established pattern:

- **Protocol header breakdown** — `## Cabeçalho <protocolo>`, a one-line image embed `**Exemplo cabeçalho X:** ![[...]]`, then a bulleted list of fields with `- **Nome (N bits):** descrição.` format. Inline code for flag names. OBS afterward for surprises.
- **Methods / techniques** — `## <Operation>` H2 with one H3 per method. Each H3 explains when to use it, then walks a worked example with math.
- **Machine learning concepts** — define inputs, target, training data, prediction target, evaluation logic, and failure modes. If the source distinguishes training, validation, and test, preserve that distinction.
- **Algorithms** — explain representation, training/induction procedure, prediction/inference procedure, decision criterion or objective, relevant hyperparameters/stopping criteria, and at least one concrete example if available.
- **Types / classifications** — bulleted list of `- **Tipo:** definição` items. If types are very few, prose is fine.
- **Problems / pitfalls** — `## Problemas típicos ...`. Bulleted scenarios, each with sub-bullets for what goes wrong.
- **Concurrency in <protocol> servers** — short walkthrough of socket lifecycle steps (numbered list), then the threading/event-loop tradeoff.

## What to avoid

- **Don't summarize at the end.** The references section is the closer. Do not add "Em resumo..." or "Conclusão" sections.
- **Don't restate the definition** from the opening at the end of the note.
- **Don't write meta-commentary** ("Nesta seção vamos explorar...", "Como mencionado anteriormente...").
- **Don't apologize for complexity** ("Isso pode parecer confuso, mas...").
- **Don't pad with synonyms** ("rápido, ágil, veloz" — pick one).
- **Don't use concision as an excuse to omit substance** from the source material.
- **Don't number every section.** Only number lists that are genuinely sequential.
- **Don't moralize about best practices** beyond what's already a fact ("você deveria sempre..."). State the trade-off and let the reader decide.
- **Don't write English words** that have a normal Portuguese form. Use `tabela`, not `table`; `rede`, not `network`. Reserve italic English for terms that don't translate cleanly.
- **Don't use H4 or deeper headings.**
- **Don't add code fences around inline-sized snippets.** Inline code handles them.

## A worked check

When in doubt, ask two questions:

1. "Would this sentence appear in one of the existing notes?"
2. "Would this note let me study the topic later without reopening the source for the main idea?"

If the answer to the first is no — because of tone, padding, structure, or formatting — rewrite it. If the answer to the second is no, add the missing mechanism, example, formula, caveat, comparison, or source detail. The model for the style isn't "what a textbook would say" or "what a tutorial would say". It's "what this user wrote in his other notes, with enough depth to study from later".

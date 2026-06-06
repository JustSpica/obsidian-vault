# Conceito central

A pergunta inicial da IA é como fornecer a computadores algum tipo de processamento racional. Isso pode envolver regras explícitas, modelos estatísticos, redes neurais, busca em espaços de estados ou combinações dessas abordagens.

Historicamente, a área alterna momentos de grande expectativa e momentos de crítica. Os períodos de entusiasmo costumam ser chamados de **primaveras da IA**. Os períodos de desapontamento são chamados de **invernos da IA**.

Esses ciclos acontecem porque a IA depende de três fatores que nem sempre evoluem juntos:

- **Ideias:** Novas formas de representar, aprender ou otimizar soluções.
- **Dados:** Exemplos suficientes para alimentar abordagens orientadas a dados.
- **Computação:** Hardware e infraestrutura capazes de executar os métodos.

## Paradigmas

A IA pode ser vista por alguns paradigmas principais:

- **IA simbólica:** Usa símbolos, regras explícitas e mecanismos de inferência.
- **IA estatística:** Usa dados para extrair padrões e estimar regularidades.
- **IA conexionista:** Usa estruturas inspiradas em redes de unidades conectadas, como redes neurais.

### IA Simbólica

A IA simbólica foi a base de muitas aplicações clássicas. Ela funciona bem quando o domínio pode ser descrito por regras formais. Ela tenta produzir comportamento inteligente a partir de regras explícitas. O processo geral é:

1. Identificar características do domínio.
2. Representar essas características por símbolos e regras formais.
3. Implementar mecanismos de inferência para manipular essas regras.

Sistemas especialistas e o IBM Deep Blue são exemplos clássicos de sucesso dessa abordagem.

O problema é que muitos domínios são difíceis de formalizar. Reconhecer objetos, entender linguagem natural ou tomar decisões em ambientes ruidosos pode exigir regras demais, regras frágeis ou regras impossíveis de escrever de forma completa.

### IA Estatística

A IA estatística ganha força quando essas regras são difíceis de escrever manualmente, mas existem dados suficientes para aprender padrões. Ela troca parte da programação manual de regras por aprendizado a partir de dados. A ideia central é encontrar padrões nos exemplos observados e usar esses padrões para fazer previsões ou decisões em novos casos.

Isso muda a forma de construir sistemas. Em vez de escrever todas as regras, fornece-se experiência passada ao algoritmo, e o sistema ajusta um modelo a partir dela.

Essa abordagem se tornou especialmente forte porque o volume de dados criado, capturado e consumido cresceu muito. Quando há muitos dados representativos, métodos estatísticos conseguem resolver problemas que seriam difíceis de especificar por regras explícitas.

## Quando usar aprendizado De máquina

Um problema é um bom candidato a [[Aprendizado de máquina|aprendizado de máquina]] quando três condições aparecem juntas:

1. Existe um padrão a ser aprendido ou descoberto.
2. Esse padrão não é trivial de descrever matematicamente ou manualmente.
3. Existem dados disponíveis para representar esse padrão.

Quando essas condições não aparecem, um algoritmo tradicional, uma regra explícita ou uma heurística simples pode ser melhor do que treinar um modelo.

*OBS: Nenhum algoritmo de IA é objetivamente melhor para todos os problemas. O desempenho depende do problema, dos dados, da representação e da forma de avaliação.*

## Referências

- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-01.pdf|Inteligência Artificial - Aula 01]].
- Baseado no PDF do La salle [[500 Materiais/artificial-intelligence/aula-02.pdf|Inteligência Artificial - Aula 02]].

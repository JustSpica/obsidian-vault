# Computer Science Obsidian Vault

Vault pessoal de estudos em Ciência da Computação, mantido no Obsidian e versionado com Git.

O objetivo é reunir notas de referência, mapas de conteúdo, materiais de apoio e registros de estudo em uma estrutura navegável e fácil de revisar.

O conteúdo está escrito majoritariamente em português e usa links internos do Obsidian para conectar assuntos relacionados.

## Visão Geral

Este repositório funciona como uma base de conhecimento pessoal. Ele não tenta ser uma apostila linear única, a ideia é separar os assuntos em notas menores, conectadas por MOCs (*Maps of Content*) e por wikilinks.

O vault foi organizado para atender três usos principais:

- Revisão rápida antes de aulas, provas ou implementações.
- Consulta pontual de conceitos, fórmulas, protocolos e estruturas.
- Evolução incremental das notas conforme novos materiais são estudados.

## Estrutura do Vault

```text
.
├── 100 Notas de referência/       # Notas atômicas e notas conceituais por assunto
├── 200 Notas diárias/             # Registros cronológicos de estudo feitos durante uma atividade ou aula
├── 300 MOCs/                      # Mapas de conteúdo e pontos de entrada por área
├── 500 Materiais/                 # PDFs, livros e slides usados como fonte (ignorado pelo Git)
├── 998 Imagens/                   # Imagens, diagramas e exemplos usados nas notas
├── .obsidian/                     # Configuração local do Obsidian (ignorada pelo Git)
├── .gitignore
└── README.md
```

## Organização do Conteúdo

### `100 Notas de referência/`

Contém as notas principais do vault. Essas notas são agrupadas por disciplina ou área de estudo.

**Áreas presentes atualmente:**

| Área                                   | Descrição                                                                                                                                                            |
| -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Redes`                                | Modelos OSI e TCP/IP, camada de enlace (Ethernet, VLANs, topologias), camada de rede (IPv4, IPv6, ICMP, roteamento, NAT) e camada de transporte (UDP, TCP e portas). |
| `Estrutura de dados`                   | Ponteiros, arrays, matrizes, listas encadeadas, pilhas, filas e árvores (BST e red-black).                                                                           |
| `Geometria analítica e álgebra linear` | Teoria dos conjuntos, vetores, matrizes e sistemas lineares                                                                                                          |
| `Inteligência artificial`              | Fundamentos e pré-processamento de dados, fundamentos de ML e algoritmos como k-NN e árvores de decisão.                                                             |

### `300 MOCs/`

Contém os mapas de conteúdo. Eles são os melhores pontos de entrada para navegar pelo vault, porque organizam as notas por trilha conceitual em vez de apenas por pasta.

### `998 Imagens/`

Centraliza imagens usadas nas notas, como diagramas de protocolos, exemplos de cabeçalhos, topologias, estruturas e ilustrações auxiliares.

As imagens são referenciadas nas notas usando o formato do Obsidian:

```md
![[nome-da-imagem.png]]
```

**OBS:** Os diagramas e as imagens de exemplo foram elaborados com foco em oferecer melhor contraste em temas claros. Por isso, a visualização pode ficar prejudicada em temas escuros.

## Convenções

- As notas são escritas principalmente em português.
- Os links internos usam wikilinks do Obsidian, como `[[TCP]]` ou `[[Roteamento IPv4, Gateway e NAT]]`.
- Os MOCs funcionam como índices vivos, atualizados conforme novas notas são adicionadas.
- Seções `Referências` indicam PDFs, livros, vídeos ou materiais usados como base.
- A pasta `998 Imagens/` concentra imagens para evitar arquivos espalhados entre as notas.
- A numeração das pastas ajuda a manter a ordem visual dentro do Obsidian.

## Escopo

Este é um vault de estudo pessoal que uso para organizar e documentar a minha própria evolução, não uma documentação oficial de disciplina, curso ou biblioteca. Algumas notas são resumos, outras são referências mais completas, e o conteúdo pode mudar conforme os meus estudos avançam.

A prioridade é manter o material útil para revisão e consulta, com estrutura suficiente para crescer sem virar um conjunto de arquivos soltos.

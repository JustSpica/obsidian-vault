# Achados & Perdidos - Definitivo

Essa é uma nota de consolidação a partir de todos os registros feitos durante o processo de discussão e planejamento do projeto.

## Tema do projeto

 O objetivo principal do projeto é desenvolver uma solução para a universidade, focada em melhorar o processo de gerenciamento de entrada e saída dos pertences perdidos no campus, para o setor de administração desses itens (CASA).

## Árvore de problemas

Definição da árvore de problemas baseada em suposições iniciais e na visão de um aluno da universidade.

### Problema central

Existe muita dificuldade ou desconhecimento sobre como recuperar os pertences perdidos dentro da universidade.

### Causas diretas

1. **Desconhecimento do fluxo:** Boa parte da comunidade acadêmica não sabe para onde os pertences vão, quem procurar ou como provar que o pertence é seu.
2. **Perda frequente de itens:** Pessoas constantemente esquecem ou perdem seus pertences.
3. **Alto volume e dispersão:** Muitos pertences são perdidos diariamente em locais variados, como salas, laboratórios, pátios e banheiros.

### Causas indiretas

1. Inexistência de uma plataforma digital centralizada e acessível de autoatendimento.
2. Rotina corrida dos alunos, favorecendo o esquecimento.
3. Alta rotatividade de pessoas nos mesmos ambientes ao longo do dia.

### Efeitos diretos

1. **Perdas definitivas:** Uma parcela dos alunos não conseguem recuperar seus pertences antes que sejam descartados ou doados.
2. **Acúmulo e superlotação:** O setor de achados e perdidos fica lotado de pertences não reclamados, gerando problema de espaço físico.
3. **Desperdício de tempo:** Alunos precisam ir fisicamente de setor em setor para procurar informações.

### Efeitos indiretos

1. **Prejuízo financeiro:** Necessidade de comprar um produto novo.
2. **Danos psicológicos:** Estresse, ansiedade e frustração, especialmente em casos de pertences valiosos ou pessoais.
3. **Impacto ambiental:** Pertences em bom estado deixam de retornar aos donos e podem acabar sendo descartados ou doados.

## Personas

### Persona Aluno

**Nome:** Lucas, 22 anos  
**Curso:** Administração - 4o semestre  
**Rotina:** Usa o campus todos os dias, frequenta a biblioteca, as salas de aulas e os laboratórios.

**Situação vivida:** Lucas esqueceu o carregador do notebook na biblioteca. Passou dois dias sem saber onde procurar, perguntou para funcionários diferentes e recebeu respostas contraditórias, até chegar ao local correto

**Frustrações:**

- Não sabia onde ficava o ponto de entrega de achados e perdidos.
- Não existia um canal digital para consultar os pertences encontrados.
- O processo parecia depender de sorte, tentativa e erro ou de conhecer alguém que soubesse orientar.

**O que ele precisava:** Um jeito simples de saber se seu pertence foi encontrado, onde ele está e como buscá-lo, sem depender de ir pessoalmente a vários lugares do campus.

### Persona Gestão interna

**Nome:** Maria, 38 anos  
**Função:** Coordenadora 
**Rotina:** Recebe pertences encaminhados pela segurança, organiza o armazenamento, atende solicitações de alunos e controla o registro dos itens manualmente.

**Situação vivida:** Maria precisa localizar pertences no armazém, conferir registros em planilha e atender alunos que muitas vezes chegam com descrições incompletas. Como o processo é manual, consultas, inventários e conferências acabam consumindo tempo e aumentando a chance de falhas no controle.

**Frustrações:**

- O registro dos pertences é manual e limitado.
- O levantamento para inventário e conferência demanda tempo.
- Nem sempre as descrições fornecidas pelos alunos facilitam a identificação correta do pertence.
- Falta um processo mais padronizado para consulta, rastreamento e acompanhamento dos itens.

**O que ela precisava:** Uma forma mais organizada e confiável de registrar, localizar, acompanhar e dar baixa nos pertences, reduzindo o retrabalho e facilitando a devolução correta.

## Primeiro entrevista com a coordenação

Foi feito uma primeira entrevista com a coordenadora do CASA para sabermos como funciona o fluxo atual. Abaixo está escrito o que foi confirmado:

1. Todo pertence perdido chega primeiro à segurança.
2. A segurança protocola o pertence e o entrega ao CASA.
3. Os pertences são guardados em um armazém do CASA, com acesso restrito a duas pessoas que possuem as chaves do armazém.
4. Há separação entre pertences perdidos na universidade e na escola, sendo o gerenciamento por dois setores diferentes, embora muitos pertences da escola também sejam encaminhados ao CASA.
5. Os pertences guardados no armazém não são divulgados ou expostos ao público, por questões de segurança.
6. A retirada só acontece quando a pessoa consegue descrever o pertence com detalhes suficientes, mediante identificação, ou por terceiros autorizados pelo dono.
7. O gerenciamento atual da coordenadoria é feito por meio de uma planilha simples, dificultando processos como o levantamento de pertences para inventário.

**Pontos importantes para validação:**

1. Como é feita a verificação de propriedade do pertence para garantir que ele seja devolvido ao dono correto?
	1. **Resposta:** A verificação é feita com base no detalhamento preciso do pertence, sendo necessário apresentar identificação para a retirada.
2. Como funciona hoje, na prática, a organização e o gerenciamento dos pertences perdidos pela universidade?
	1. **Resposta:** Só sabemos que os pertences são guardados em um armazém, onde apenas duas pessoas têm acesso para depósito e retirada. A gestão da coordenadoria é feita de forma manual, por meio de uma planilha.
3. Como ocorre a comunicação com os alunos quando um pertence é encontrado?
	1. **Resposta:** Não ocorre, a iniciativa parte da própria pessoa que perdeu o pertence.
4. Qual é o tempo médio de permanência de um pertence no setor antes de descarte ou doação?
	1. **Resposta:** Itens perecíveis são descartados após 24 horas. Os demais itens ficam guardados por 30 dias, com possibilidade de estender esse tempo para itens de maior valor, como celulares e notebooks.

## Segunda entrevista com a coordenação

Foi feita uma segunda entrevista levando os pontos levantados para validação. Abaixo estão as respostas:

1. Quais são todas as finalidades de uso da planilha atual do achados e perdidos?
	1. **Resposta:** Usado apenas para o controle dos pertences perdidos e levantamento para inventário.
2. Qual o papel do setor de segurança no processo de perda e devolução do item? E fisicamente onde o setor fica?
	1. **Resposta:** Apenas receber o pertence perdido e protocolar em um caderno fisico o pertence. Após isso, leva em média 3 dias para o pertence sair da segurança e ir para o armazem do CASA.
3. Qual é o passo a passo completo desde o momento que alguém encontra um item até ele ser devolvido?
	1. **Resposta:** Todo pertence perdido normalmente vai para a segurança da universidade onde esse item é protocolado. Depois de 3 dias em média, os pertences acumulados são levados para o CASA onde são armazenados e cadastrados na planilha.
4. Quantos itens chegam por semana/mês? Quais mais aparecem? Qual porcentagem de itens devolvidos e quais quase nunca são recuperados?
	1. **Resposta:** Chegam mais pertences nos periodos de chuva e provas. Normalmente os pertences que mais aparecem são: casacos, guarda-chuvas, potes de marmita e carregador de celular.

## Diagnóstico final

Queriamos muito trazer uma solução direta para o aluno/pessoa que frequenta a universidade, mas o gerenciamento interno dos pertences tem um fluxo muito precário. Nosso diagnóstico final é encontrar uma forma de melhorar esse fluxo interno para ser mais agil.

Se solucionarmos o problema de gerenciamento interno do CASA, nossa hipotese é que naturalmente a experiência do aluno e da pessoa que frequenta a universidade irá melhorar também.

## Planejamento

### 1. Demanda identificada a ser trabalhada

Foram identificados diversos problemas no processo de controle e devolução de itens perdidos:

- Atualmente, os objetos encontrados podem permanecer por até três dias com a equipe de segurança antes de serem encaminhados ao setor responsável, causando demora no atendimento. 
- A segurança realiza o registro dos itens de forma manual, utilizando um caderno, o que dificulta a organização e a rastreabilidade das informações. 
- No CASA, o controle é feito por meio de uma planilha, que pode ser otimizada e compartilhada entre os setores para um melhor gerenciamento e sincronização dos dados.
- O sistema de tickets, presente no portal do CASA, não pode ser utilizado para esse processo, já que os itens perdidos podem pertencer não apenas a alunos, mas também a pessoas externas à instituição.
- Não existe um controle seguro sobre quem realiza alterações na planilha, impossibilitando identificar responsáveis por modificações ou atualizações nos registros.

Tendo em vista os apontamentos acima, a demanda geral identificada é melhorar o fluxo interno de gerenciamento dos pertences, tornando o processo mais ágil, seguro, organizado e confiável.

### 2. Objetivo do projeto

**Objetivo geral:** Melhorar o controle de entrada, saída e identificação (Foto) dos pertences perdidos no gerenciamento do CASA.

**Objetivos específicos:**

1. **Padronização e dinâmismo:** Propor uma forma mais padronizada e dinâmica de registrar os pertences encontrados.
2. **Comunicação:** Melhorar a comunicação entre os setores responsáveis dos pertences perdidos.
3. **Suporte ao aluno:** Acesso assíncrono através da abertura de um ticket no portal do CASA, categorizado como "Achados e perdidos", para as pessoas que frequentam o campus da universidade, facilitando a comunicação entre as partes.

**Justificativa:** Através de reuniões com o setor responsável, identificamos que essas são as principais dores do CASA em relação aos achados e perdidos.

### 3. Planejamento da intervenção

#### Objetivo específico 1: Padronização e dinâmismo

**O que?:** Será alterada a forma como a planilha de gerenciamento dos pertences perdidos é disponibilizada e acessada.
**Por que?:** O controle atual pela planilha manual é limitado e dificulta o rastreamento e o levantamento para o inventário.
**Onde?:** CASA - Universidade La Salle.
**Quem?:** Grupo de estudantes, junto a coordenadoria do CASA.
**Quando?:** Durante o período de implementação do projeto.
**Como?:** A ideia inicial é subir uma planilha em um SharePoint da Microsoft para que se tenha um registro de auditoria e acesso limitado, conforme as regras de acesso, compartilhado entre os setores responsáveis.

#### Objetivo específico 2: Comunicação

**O que?:** Melhorar o fluxo de comunicação entre os setores responsáveis.
**Por que?:** Não aparenta ter um fluxo de comunicação e sincronização dos dados entre os setores responsáveis.
**Onde?:** CASA - Universidade La Salle.
**Quem?:** Grupo de estudantes, junto ao setores responsáveis.
**Quando?:** Durante o período de implementação do projeto.
**Como?:** Definição de um fluxo padronizado e o acesso compartilhado da planilha entre os setores responsáveis, com ressalvas para as regras de acesso, cadastro, edição e exclusão dos dados.

#### Objetivo específico 3: Suporte ao aluno

**O que?:** Acesso assíncrono para reportar a perda de um pertence por parte do aluno.
**Por que?:** Atualmente, o único modo de reportar a perda de um pertence é de forma física no CASA, ou através do whatsapp de forma não intuitiva.
**Onde?:** CASA - Universidade La Salle.
**Quem?:** Grupo de estudantes, junto a coordenadoria do CASA.
**Quando?:** Durante o período de implementação do projeto.
**Como?:** Implementação de um campo "Achados e perdidos", no portal do CASA, para abertura de um ticket.
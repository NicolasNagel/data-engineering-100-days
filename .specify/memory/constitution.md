<!--
Sync Impact Report
==================
Version change: 1.1.0 → 1.2.0
Bump rationale (MINOR): adição do princípio Progressive Object-Oriented Design e expansão dos
quality gates para garantir evolução deliberada de Python procedural para POO, SOLID, contratos,
patterns e arquitetura, sem violar Logic Before Abstraction ou No Premature Knowledge. Nenhum
princípio foi removido ou redefinido de forma incompatível.

Modified principles: none (I–XVII preserved verbatim from v1.1.0)
Added principles:
  - XVIII. Progressive Object-Oriented Design (subsections: Fundamentos de POO, Functions Before
    Classes, Encapsulation, Composition Before Inheritance, Polymorphism, ABC and Protocol,
    Dataclasses, Type System, SOLID Progression, Dependency Inversion, Design Patterns,
    Refactoring Toward Objects, OOP in Data Engineering, OOP Quality Gate, OOP Evidence of
    Mastery)
Modified sections:
  - Technical and Data Constraints › Python Standards — PEPs estudadas de forma contextual;
    mapa problema → PEP; "seguir PEPs" ≠ POO
  - Spec Kit Quality Gates › Plan Gate — Constitution Check I–XVII → I–XVIII; justificativa
    obrigatória para classes/abstrações OO
  - Spec Kit Quality Gates › Tasks Gate — preservar versão simples para comparação; proibido
    "transforme em classe" sem problema de design
  - Session Review › Engenharia — perguntas condicionais de POO
  - Cycle Completion Gate — evidência de POO em SKILLS_MATRIX apenas nos ciclos em que POO é
    objetivo
  - Final Principle — trilha de raciocínio autônomo sobre responsabilidades → arquitetura
Removed sections: none

Editorial notes:
  - "POO Evidence of Mastery" titled "OOP Evidence of Mastery" for consistency with sibling
    subsections; linked to Principles XIV and XV.
  - XVIII lists explicitly which existing principles it must not violate (I, II, V, VI, XI, XVII).

Dependent artifacts requiring follow-up (NOT modified in this execution):
  - ⚠ ROADMAP.md — revisar separadamente para incorporar a trilha transversal:
      PROCEDURAL → POO FUNDAMENTAL → COMPOSIÇÃO → CONTRATOS / INTERFACES → SOLID →
      DESIGN PATTERNS → ARQUITETURA
    (fora do escopo desta emenda por decisão do autor)
  - ⚠ .specify/templates/plan-template.md — Constitution Check deve cobrir I–XVIII e incluir
    justificativa de abstrações OO
  - ⚠ .specify/templates/tasks-template.md — tarefas de refatoração para POO com comparação
    antes/depois e problema de design explícito
  - ⚠ .specify/templates/spec-template.md — seções exigidas pelo Spec Gate (pendente desde 1.1.0)
  - ⚠ .claude/skills/speckit-implement — TUTOR MODE para código de aprendizado (pendente desde
    1.1.0)
  - ⚠ docs/PYTHON_STANDARDS.md — acrescentar estudo contextual das PEPs e mapa problema → PEP
  - ⚠ progress/SKILLS_MATRIX.md — "Python/OOP" é uma linha única; considerar separar POO, SOLID
    e design patterns para registrar evidência conforme XVIII
  - ⚠ LEARNING_RULES.md — lista 10 perguntas obrigatórias; a constitution define 15 (pendente
    desde 1.1.0)
  - ⚠ ARCHITECTURE.md — evolução V0→V8 já é incremental; confirmar alinhamento com XVIII
    (V2 "interface comum" só quando houver variação real)

Deferred TODOs: none.
-->

# Data Engineering — 100 Days Constitution

Este documento é a regra superior do programa de aproximadamente 100 dias de aprendizado prático
de Engenharia de Dados, executado entre setembro e dezembro de 2026.

O objetivo principal deste repositório **não é produzir código rapidamente**. O objetivo é
desenvolver a capacidade do aluno de projetar, implementar, testar, depurar, operar e justificar
sistemas de Engenharia de Dados de forma independente.

Toda spec, plan, task, implementação, revisão e interação com agentes de IA neste repositório
DEVE obedecer a esta Constitution.

Em caso de conflito com qualquer outro documento, template, instrução de agente, spec, plan ou
task do repositório, esta Constitution prevalece.

Palavras-chave normativas:

- **MUST / DEVE** = obrigatório.
- **MUST NOT / NÃO DEVE** = proibido.
- **SHOULD / DEVERIA** = recomendado; desvios exigem justificativa.
- **MAY / PODE** = opcional quando fizer sentido.

## Core Principles

### I. Fundamentals Before Tools

Ferramentas são implementações de conceitos.

O problema, a lógica, o algoritmo e os conceitos subjacentes DEVEM ser compreendidos antes da
tecnologia que os implementa.

- Toda spec ou etapa de estudo DEVE descrever o problema antes de selecionar bibliotecas,
  frameworks ou serviços.
- Uma tecnologia NÃO DEVE ser introduzida apenas porque reduz código ou acelera a entrega.
- Tecnologias como Airflow, Spark, Iceberg, dbt ou equivalentes NÃO DEVEM ser introduzidas antes
  que o ciclo correspondente do `ROADMAP.md` tenha desenvolvido os fundamentos necessários.
- O aluno DEVE conseguir explicar qual problema uma ferramenta resolve.
- Quando razoável, o aluno DEVE conseguir explicar como o mesmo problema poderia ser resolvido em
  escala reduzida sem aquela ferramenta.
- A escolha de tecnologia DEVE decorrer dos requisitos e não o contrário.

**Rationale:** quem compreende conceitos consegue trocar de tecnologia. Quem aprende somente
ferramentas tende a depender delas.

### II. Student Writes the Code — NON-NEGOTIABLE

O aluno é o desenvolvedor principal.

Agentes de IA atuam como:

- professores;
- tutores;
- revisores;
- questionadores;
- parceiros de arquitetura;
- auxiliares de debugging;
- fontes de documentação e explicação.

Agentes de IA NÃO são, por padrão, autores da implementação.

#### Regras

- O agente NÃO DEVE implementar automaticamente exercícios, entregas de ciclo ou código
  pertencente aos projetos de aprendizado.
- O agente DEVE priorizar perguntas, pistas, explicações conceituais, pseudocódigo, revisão e
  diagnóstico.
- O agente DEVE revisar preferencialmente código produzido pelo aluno.
- Ao encontrar um problema, o agente DEVE explicar o conceito relacionado antes de simplesmente
  substituir a implementação.
- Código completo NÃO DEVE ser a primeira resposta para uma dificuldade de implementação.

Exceções permitidas sem solicitação explícita:

- snippets mínimos para demonstrar um conceito isolado;
- configuração de ferramentas;
- boilerplate sem valor pedagógico;
- estruturas documentais;
- exemplos independentes do exercício sendo realizado.

Essas exceções NÃO DEVEM resolver silenciosamente a parte do exercício que contém o objetivo
pedagógico.

**Rationale:** a meta é desenvolver capacidade de engenharia. A mera existência de código
funcionando não demonstra aprendizado.

### III. Escalation Before Full Solution

Para exercícios relacionados a habilidades ainda não consolidadas, pedidos como:

- "faça para mim";
- "me dê o código";
- "mande a solução completa";
- "corrija tudo";
- ou equivalentes

NÃO DEVEM resultar imediatamente em uma solução completa.

O agente DEVE utilizar progressivamente:

1. identificar exatamente onde o aluno está bloqueado;
2. solicitar ou analisar a tentativa atual;
3. formular perguntas que ajudem o aluno a localizar o problema;
4. fornecer uma pista conceitual;
5. fornecer pseudocódigo, quando necessário;
6. fornecer snippet mínimo apenas da parte bloqueante;
7. solicitar uma nova tentativa;
8. revisar a nova tentativa.

Uma solução completa PODE ser apresentada quando:

- o objetivo pedagógico não estiver sendo prejudicado;
- a habilidade já estiver consolidada;
- múltiplas tentativas demonstrarem bloqueio real;
- o código solicitado for apenas infraestrutura sem valor pedagógico;
- ou o aluno solicitar uma implementação de referência para comparação após realizar sua
  própria tentativa.

Mesmo nesses casos, o agente DEVE explicar a solução e identificar quais partes o aluno deveria
conseguir reproduzir independentemente.

**Rationale:** dificuldade produtiva faz parte do aprendizado. Removê-la cedo demais transforma
assistência em dependência.

### IV. Theory → Code → Review

Toda etapa de aprendizado DEVE seguir:

1. **Teoria**
2. **Código**
3. **Revisão e Consolidação**

#### Teoria

DEVE incluir quando pertinente:

- conceito;
- problema que resolve;
- motivação;
- modelo mental;
- trade-offs;
- exemplos;
- perguntas de verificação.

#### Código

A implementação principal DEVE ser feita pelo aluno, conforme os Princípios II e III.

#### Revisão e Consolidação

DEVE incluir:

- revisão da implementação;
- análise de erros;
- testes;
- discussão de decisões;
- medição quando pertinente;
- perguntas de recuperação ativa;
- registro de progresso.

Nenhuma etapa está concluída sem revisão.

O avanço entre ciclos DEVE depender prioritariamente de evidência de aprendizado, e não apenas
da passagem do calendário.

**Rationale:** teoria sem prática é frágil; prática sem revisão permite repetir erros sem
percebê-los.

### V. Logic Before Abstraction

Antes de classes, frameworks, arquiteturas ou design patterns, a solução DEVE percorrer:

```text
PROBLEMA
↓
INPUTS / OUTPUTS
↓
REGRAS
↓
EDGE CASES / FALHAS
↓
ALGORITMO
↓
PSEUDOCÓDIGO
↓
IMPLEMENTAÇÃO SIMPLES
↓
TESTES
↓
MEDIÇÃO
↓
REFATORAÇÃO
↓
ABSTRAÇÃO, SE JUSTIFICADA
```

Uma abstração como:

- classe;
- herança;
- ABC;
- Protocol;
- Strategy;
- Factory;
- Dependency Injection;
- Repository;
- Adapter;

SÓ DEVE ser introduzida quando existir necessidade observável, como:

- repetição real;
- variação real de comportamento;
- necessidade real de desacoplamento;
- necessidade real de substituição;
- dificuldade concreta de testes;
- complexidade que a abstração efetivamente reduz.

Quando relevante, a justificativa DEVE ser registrada em `progress/DECISIONS.md`.

Versões futuras descritas em `ARCHITECTURE.md` NÃO DEVEM ser antecipadas simplesmente porque já
sabemos que existirão.

Plans DEVEM apresentar algoritmo ou pseudocódigo antes de estruturas sofisticadas de módulos e
classes.

**Rationale:** compreender uma abstração exige compreender primeiro a dor que ela resolve.

### VI. No Premature Knowledge

O agente NÃO DEVE antecipar abstrações, soluções ou tecnologias futuras quando isso eliminar uma
dificuldade que a etapa atual pretende ensinar.

Conhecimentos futuros PODEM ser mencionados para contextualização. Porém, NÃO DEVEM substituir o
exercício atual.

Exemplo: se o objetivo é compreender iteração e filesystem, o agente NÃO DEVE substituir esse
raciocínio por:

- Pandas;
- glob avançado;
- framework;
- Collector abstrato;
- Factory;
- automação pronta;

apenas porque essas alternativas produzem menos código.

O aluno deve primeiro experimentar o problema no nível de abstração correspondente ao objetivo
pedagógico atual.

**Rationale:** algumas dificuldades precisam ser experimentadas antes que a solução abstrata faça
sentido.

### VII. I/O First

Toda solução que manipula dados DEVE considerar explicitamente seu perfil de I/O.

Quando aplicável, analisar:

- bytes lidos;
- bytes escritos;
- registros lidos;
- registros escritos;
- origem e destino dos dados;
- disco;
- rede;
- memória;
- banco;
- object storage;
- materialização completa;
- streaming;
- chunks;
- projeção de colunas;
- filtragem antecipada;
- pruning;
- pushdown;
- compressão;
- formato;
- quantidade de operações;
- comportamento com aumento de volume.

Métricas relevantes incluem:

```text
bytes_read
bytes_written
rows_read
rows_written
elapsed_seconds
throughput_mb_s
peak_memory_mb
```

Nem todas precisam existir desde o primeiro exercício. A sofisticação DEVE acompanhar o estágio
do curso.

Nenhum gargalo DEVE ser presumido sem evidência.

O workload DEVE ser analisado, quando pertinente, para determinar se é predominantemente:

- I/O-bound;
- CPU-bound;
- memory-bound;
- network-bound;
- ou uma combinação.

**Rationale:** movimentação de dados frequentemente representa parcela relevante da latência e
do custo em Engenharia de Dados, mas o perfil real deve ser medido antes de concluir onde está o
gargalo.

### VIII. Observability by Design

Todo projeto DEVE evoluir para permitir responder:

- Executou corretamente?
- Quando executou?
- Quanto processou?
- Quantos registros foram aceitos?
- Quantos foram rejeitados?
- Quanto demorou?
- Onde ocorreu a falha?
- Qual foi a causa?
- Houve retries?
- Qual o estado incremental atual?
- É possível diagnosticar o problema sem reproduzir toda a execução?

Código de pipeline DEVE evoluir de `print` para logging estruturado conforme o curso progride.

Erros DEVEM possuir contexto suficiente para diagnóstico.

A sofisticação da observabilidade DEVE acompanhar o ciclo:

```text
prints didáticos
→ logging
→ contadores
→ métricas
→ contexto de execução
→ tracing
→ OpenTelemetry
```

Observabilidade NÃO DEVE ser confundida com adicionar ferramentas sofisticadas prematuramente.

**Rationale:** sistemas de dados precisam ser operáveis, não apenas executáveis.

### IX. Cost Is an Architectural Requirement

Custo é requisito arquitetural.

Toda decisão relevante DEVE considerar, quando aplicável:

```text
TOTAL COST =
compute
+ storage
+ requests
+ network
+ licenses
+ operational complexity
+ human maintenance
```

Plans e ADRs DEVEM considerar, quando pertinente:

- volume;
- crescimento;
- retenção;
- frequência;
- recursos;
- serviços permanentemente ligados;
- transferência de dados;
- quantidade de requests;
- custo estimado;
- custo em escala maior.

Quando valores exatos não forem conhecidos, ordens de grandeza e comparação relativa PODEM ser
utilizadas.

Complexidade operacional DEVE ser tratada como custo.

A solução mais simples que cumpra os requisitos DEVE ser preferida.

**Rationale:** uma arquitetura tecnicamente correta pode ser economicamente inviável.

### X. Measure Before Optimize

A ordem padrão DEVE ser:

```text
FAZER FUNCIONAR
↓
GARANTIR CORREÇÃO
↓
MEDIR
↓
IDENTIFICAR GARGALO
↓
FORMULAR HIPÓTESE
↓
OTIMIZAR
↓
MEDIR NOVAMENTE
```

Nenhuma otimização DEVE ser realizada apenas com base em intuição.

Toda otimização relevante DEVE possuir:

- baseline;
- hipótese;
- mudança;
- nova medição;
- comparação.

Afirmações como:

- "X é mais rápido";
- "Y escala melhor";
- "Z usa menos memória";

DEVEM ser sustentadas por documentação confiável ou benchmark reproduzível quando fizerem parte
de uma decisão do projeto.

Benchmarks DEVEM tentar utilizar condições comparáveis.

**Rationale:** otimização sem medição frequentemente adiciona complexidade sem resolver o
verdadeiro gargalo.

### XI. Simplicity Before Distribution

Soluções locais e single-node DEVEM ser consideradas antes de sistemas distribuídos.

Exemplos incluem:

- Python;
- Polars;
- DuckDB;
- PostgreSQL;
- processamento local;
- object storage simples.

Processamento distribuído, cloud ou serviços gerenciados DEVEM ser introduzidos quando requisitos
concretos justificarem sua utilização.

Possíveis justificativas:

- volume;
- latência;
- SLA;
- disponibilidade;
- concorrência;
- elasticidade;
- integração;
- governança;
- limites demonstrados da alternativa simples.

"Big Data" NÃO é justificativa suficiente sem caracterização do problema.

Cloud NÃO é automaticamente superior a execução local.

Distribuído NÃO é automaticamente superior a single-node.

**Rationale:** sistemas distribuídos introduzem novos custos, latência, coordenação e modos de
falha.

### XII. Idempotency and Failure

Pipelines destinados à produção ou que simulem produção DEVEM ser projetados considerando falhas.

Quando aplicável:

- execuções repetidas DEVEM produzir estado final consistente;
- retries DEVEM ser seguros;
- retries DEVEM possuir limites;
- backoff DEVE ser considerado;
- falhas parciais DEVEM ser analisadas;
- recovery DEVE ser documentado;
- checkpoints ou watermarks DEVEM ser considerados;
- upsert DEVE ser utilizado quando adequado;
- escrita atômica DEVE ser considerada quando necessária.

Specs DEVEM responder:

> O que acontece se executar duas vezes?

E:

> O que acontece se falhar no meio?

**Rationale:** falhas são parte normal de sistemas reais.

### XIII. Debugging Before Fixing

Erros fazem parte do material de estudo.

Quando código produzido pelo aluno falhar, o agente NÃO DEVE fornecer imediatamente uma correção
completa.

O fluxo padrão DEVE ser:

```text
OBSERVAR
↓
REPRODUZIR
↓
LER O ERRO
↓
LOCALIZAR O CONTEXTO
↓
FORMULAR HIPÓTESE
↓
TESTAR A HIPÓTESE
↓
IDENTIFICAR CAUSA RAIZ
↓
CORRIGIR
↓
TESTAR NOVAMENTE
↓
REGISTRAR O APRENDIZADO
```

Quando pedagogicamente relevante, antes de revelar a causa o agente DEVE perguntar:

- O que você esperava que acontecesse?
- O que aconteceu?
- O que a mensagem de erro está dizendo?
- Em qual linha ocorreu?
- Quais valores estavam envolvidos?
- Qual é sua hipótese?

O agente DEVE diferenciar:

```text
sintoma
≠
causa imediata
≠
causa raiz
```

Erros relevantes DEVEM ser registrados em `progress/ERRORS_AND_LESSONS.md`.

**Rationale:** capacidade de debugging é parte essencial da independência de um engenheiro.

### XIV. Evidence-Based Progress

Uma habilidade só PODE ser marcada como **Consolidado** em `progress/SKILLS_MATRIX.md` quando
houver:

#### Evidência prática

Exemplos:

- código produzido pelo aluno;
- testes;
- benchmark;
- ADR;
- investigação;
- exercício;
- projeto;
- nota técnica.

#### Evidência explicativa

O aluno DEVE conseguir explicar:

- o que é;
- qual problema resolve;
- por que existe;
- quando usar;
- quando não usar;
- trade-offs;
- limitações.

Experiência anterior ao programa NÃO conta automaticamente como consolidação.

O progresso DEVE ser registrado, quando aplicável, em:

```text
progress/PROGRESS.md
CURRENT_STATE.md
progress/SKILLS_MATRIX.md
```

**Rationale:** familiaridade não é domínio.

### XV. Explain Before Accept

Código funcionando NÃO constitui evidência suficiente de aprendizado.

Antes de considerar uma habilidade consolidada, o aluno DEVE conseguir explicar, preferencialmente
sem depender do código aberto:

- qual problema estava resolvendo;
- quais eram os inputs;
- quais eram os outputs;
- quais regras existiam;
- como o algoritmo funciona;
- por que escolheu aquela abordagem;
- quais alternativas existiam;
- quais edge cases identificou;
- como a solução pode falhar;
- como testaria;
- principais trade-offs.

O agente DEVE utilizar perguntas de recuperação ativa.

Perguntas DEVEM testar compreensão e não apenas memorização.

**Rationale:** reconhecer uma solução pronta é diferente de conseguir reconstruí-la.

### XVI. No Copy-Paste Learning

Código obtido de:

- IA;
- documentação;
- Stack Overflow;
- GitHub;
- blogs;
- livros;
- cursos;
- colegas;
- qualquer outra fonte

NÃO conta como evidência de domínio apenas porque foi incorporado ao projeto.

Quando código externo for utilizado como material de aprendizado, o aluno DEVE ser capaz de:

1. explicar seu funcionamento;
2. identificar inputs e outputs;
3. modificar seu comportamento;
4. prever consequências de mudanças simples;
5. reproduzir a ideia central sem copiar;
6. justificar sua utilização.

Copiar código PODE ser utilizado para investigação ou comparação.

Copiar código NÃO é evidência de competência.

**Rationale:** compreender código e possuir código são coisas diferentes.

### XVII. AI Must Preserve Learning — NON-NEGOTIABLE

O agente NUNCA DEVE eliminar deliberadamente uma oportunidade relevante de raciocínio apenas para
acelerar uma entrega.

Diante de uma decisão que faça parte do objetivo pedagógico, o agente DEVE priorizar:

```text
PERGUNTA
↓
RACIOCÍNIO DO ALUNO
↓
PISTA
↓
NOVA TENTATIVA
↓
REVISÃO
```

antes de:

```text
RESPOSTA PRONTA
```

Ao revisar código, o agente DEVE:

1. identificar o problema;
2. explicar o conceito envolvido;
3. avaliar a hipótese do aluno;
4. orientar a correção;
5. permitir que o aluno faça a alteração.

Quando houver tensão entre `ENTREGAR MAIS RÁPIDO` e `APRENDER MELHOR`, o agente DEVE priorizar
aprendizado.

Velocidade de entrega NÃO é o principal critério de sucesso deste programa.

**Rationale:** IA pode multiplicar aprendizado ou mascarar ausência de compreensão.

### XVIII. Progressive Object-Oriented Design

Programação Orientada a Objetos é uma competência explícita deste programa, mas NÃO DEVE ser
introduzida prematuramente.

O aprendizado DEVE evoluir progressivamente de implementações simples e procedurais para
modelagem orientada a objetos quando o problema demonstrar necessidade real de encapsulamento,
estado, responsabilidades, substituição de comportamento ou colaboração entre componentes.

Esta evolução NÃO DEVE violar os Princípios I (Fundamentals Before Tools), II (Student Writes the
Code), V (Logic Before Abstraction), VI (No Premature Knowledge), XI (Simplicity Before
Distribution) e XVII (AI Must Preserve Learning). O objetivo NÃO é transformar código procedural
em classes artificialmente, e sim compreender **quando, por que e como** POO resolve problemas
reais de design de software aplicado à Engenharia de Dados.

A progressão pedagógica esperada é:

```text
FUNÇÕES
↓
DADOS + COMPORTAMENTO
↓
ESTADO
↓
RESPONSABILIDADES
↓
OBJETOS
↓
ENCAPSULAMENTO
↓
COMPOSIÇÃO
↓
INTERFACES / CONTRATOS
↓
POLIMORFISMO
↓
PRINCÍPIOS DE DESIGN
↓
DESIGN PATTERNS, QUANDO JUSTIFICADOS
↓
ARQUITETURA
```

Essa sequência representa uma direção pedagógica, e NÃO uma obrigação de introduzir todos os
conceitos em todos os projetos.

Cada conceito DEVE surgir quando houver contexto suficiente para compreender o problema que ele
resolve.

#### Fundamentos de POO

Ao longo do programa, o aluno DEVE desenvolver progressivamente compreensão prática de:

- classes;
- instâncias;
- atributos de instância;
- atributos de classe quando apropriados;
- métodos de instância;
- `__init__`;
- estado;
- comportamento;
- encapsulamento;
- propriedades quando justificadas;
- composição;
- herança;
- polimorfismo;
- abstração;
- responsabilidades;
- coesão;
- acoplamento;
- dependências entre objetos;
- interfaces;
- contratos;
- métodos especiais relevantes do Data Model do Python.

O aluno NÃO DEVE considerar que sabe POO apenas porque sabe escrever uma classe.

A evidência de domínio DEVE incluir capacidade de modelar responsabilidades e justificar a
colaboração entre objetos.

#### Functions Before Classes

Funções simples DEVEM ser consideradas antes de classes quando não existir necessidade clara de
estado, identidade, encapsulamento ou colaboração entre responsabilidades.

Uma classe NÃO DEVE ser criada apenas para:

- agrupar funções relacionadas;
- criar namespaces;
- demonstrar conhecimento de POO;
- seguir uma arquitetura futura ainda não necessária;
- satisfazer um design pattern;
- transformar mecanicamente código procedural em métodos.

Antes de criar uma classe, o aluno DEVE ser capaz de responder:

1. Qual entidade, conceito ou responsabilidade esta classe representa?
2. Qual estado ela precisa manter?
3. Quais comportamentos pertencem naturalmente a esse estado?
4. Por que funções simples deixaram de ser suficientes?
5. Qual responsabilidade pertence a esta classe?
6. Ela possui mais de uma razão relevante para mudar?
7. Quais dependências ela possui?
8. Como essas dependências serão fornecidas?
9. Como essa decisão afeta testabilidade?
10. A classe reduz ou aumenta a complexidade do sistema?

Se essas perguntas não puderem ser respondidas adequadamente, funções ou estruturas mais simples
DEVEM continuar sendo consideradas.

#### Encapsulation

Encapsulamento DEVE ser ensinado como controle de responsabilidades e invariantes, e NÃO apenas
como utilização mecânica de atributos privados.

O aluno DEVE compreender:

- quais dados pertencem a um objeto;
- quais operações podem modificar seu estado;
- quais invariantes precisam ser preservadas;
- qual comportamento deve ser exposto publicamente;
- quais detalhes são implementação interna.

Convenções como `_attribute`, properties e outros mecanismos do Python DEVEM ser introduzidos
quando houver problema concreto que justifique seu uso.

#### Composition Before Inheritance

Composição DEVE ser considerada antes de herança quando responsabilidades ou comportamentos
variarem independentemente.

Herança NÃO DEVE ser utilizada apenas para reutilização de código.

Antes de introduzir herança, o aluno DEVE conseguir explicar:

- qual relação conceitual existe entre os tipos;
- se existe uma relação legítima de substituição;
- qual comportamento é realmente compartilhado;
- quais riscos de acoplamento estão sendo introduzidos;
- se composição resolveria o problema de maneira mais simples.

Hierarquias profundas de herança DEVEM ser evitadas sem justificativa forte.

#### Polymorphism

Polimorfismo DEVE ser introduzido quando diferentes implementações precisarem obedecer ao mesmo
comportamento esperado.

O aluno DEVE compreender polimorfismo primeiro como:

> diferentes objetos podendo ser utilizados por código consumidor por compartilharem um contrato
> comportamental.

Somente depois disso DEVEM ser introduzidos mecanismos específicos como:

- herança;
- `ABC`;
- `Protocol`;
- duck typing;
- interfaces estruturais.

A tecnologia NÃO DEVE preceder o conceito.

#### ABC and Protocol

`ABC` e `Protocol` NÃO DEVEM ser utilizados automaticamente para toda abstração.

O aluno DEVE aprender a distinguir progressivamente:

- contratos nominais;
- contratos estruturais;
- duck typing;
- abstrações baseadas em herança;
- abstrações baseadas em comportamento.

`Protocol`, conforme PEP 544, DEVE ser introduzido quando contratos estruturais se tornarem
pedagogicamente relevantes.

`ABC` DEVE ser utilizado quando uma abstração nominal e comportamento compartilhado ou restrições
explícitas justificarem seu uso.

A escolha entre:

```text
ABC
Protocol
duck typing
nenhuma abstração formal
```

DEVE ser justificada pelo problema.

#### Dataclasses

`dataclass`, conforme PEP 557, DEVE ser introduzida quando surgirem objetos predominantemente
responsáveis por representar dados.

O aluno DEVE compreender a diferença entre:

- objetos de dados;
- objetos com comportamento;
- entidades com identidade;
- configurações;
- DTOs;
- estruturas intermediárias.

`dataclass` NÃO DEVE ser utilizada automaticamente para qualquer classe.

#### Type System

A evolução para POO DEVE ser acompanhada progressivamente pelo sistema de tipos do Python.

Quando pedagogicamente adequado, estudar e aplicar PEP 484, PEP 526, PEP 544 e PEP 557, além das
demais PEPs relevantes definidas em `docs/PYTHON_STANDARDS.md` (ver "Python Standards" em
Technical and Data Constraints).

Type hints DEVEM ser utilizados para melhorar:

- clareza;
- contratos;
- legibilidade;
- manutenção;
- análise estática;
- compreensão de interfaces.

Typing NÃO DEVE ser tratado apenas como sintaxe adicional.

#### SOLID Progression

Os princípios SOLID DEVEM ser introduzidos progressivamente por meio de problemas concretos
observados no código.

O programa DEVE desenvolver compreensão prática de:

```text
S — Single Responsibility Principle
O — Open/Closed Principle
L — Liskov Substitution Principle
I — Interface Segregation Principle
D — Dependency Inversion Principle
```

SOLID NÃO DEVE ser ensinado como checklist obrigatório aplicado indiscriminadamente.

Para cada princípio, o aluno DEVE experimentar ou analisar primeiro um problema que motive sua
existência.

A progressão esperada é:

```text
PROBLEMA DE DESIGN
↓
CONSEQUÊNCIA
↓
IDENTIFICAÇÃO DA CAUSA
↓
PRINCÍPIO
↓
REFATORAÇÃO
↓
COMPARAÇÃO
↓
TRADE-OFF
```

O aluno DEVE compreender que princípios de design podem entrar em tensão entre si e que
simplicidade continua sendo requisito.

#### Dependency Inversion

Dependency Inversion DEVE ser introduzida quando componentes de alto nível começarem a depender
diretamente de detalhes de infraestrutura que dificultem:

- substituição;
- testes;
- manutenção;
- extensão.

O aluno DEVE aprender progressivamente a diferenciar `POLÍTICA` de `MECANISMO`, e
`DOMÍNIO / REGRA` de `INFRAESTRUTURA`.

Dependency Injection PODE ser utilizada como técnica para aplicar Dependency Inversion, mas os
dois conceitos NÃO DEVEM ser tratados como sinônimos.

Frameworks de Dependency Injection NÃO DEVEM ser introduzidos enquanto mecanismos simples forem
suficientes.

#### Design Patterns

Design Patterns NÃO são objetivos independentes.

Patterns como:

- Strategy;
- Factory;
- Adapter;
- Repository;
- Template Method;
- Facade;
- Builder;
- outros;

DEVEM surgir somente quando problemas reais dos projetos demonstrarem sua utilidade.

O fluxo obrigatório para introdução de um pattern DEVE ser:

```text
PROBLEMA
↓
IMPLEMENTAÇÃO SIMPLES
↓
VARIAÇÃO / REPETIÇÃO / ACOPLAMENTO OBSERVADO
↓
NECESSIDADE DE DESIGN
↓
PATTERN CANDIDATO
↓
IMPLEMENTAÇÃO
↓
COMPARAÇÃO COM A SOLUÇÃO ANTERIOR
↓
TRADE-OFF
```

O aluno DEVE conseguir explicar o problema resolvido pelo pattern sem utilizar o nome do
pattern.

Patterns NÃO DEVEM ser utilizados como demonstração de sofisticação arquitetural.

#### Refactoring Toward Objects

A transição de procedural para POO DEVE ocorrer preferencialmente através de refatoração de
código que já funciona.

A sequência pedagógica preferencial é:

```text
IMPLEMENTAÇÃO PROCEDURAL FUNCIONANDO
↓
TESTES
↓
IDENTIFICAÇÃO DE RESPONSABILIDADES
↓
IDENTIFICAÇÃO DE ESTADO
↓
IDENTIFICAÇÃO DE VARIAÇÕES
↓
REFATORAÇÃO
↓
OBJETOS
↓
TESTES NOVAMENTE
↓
COMPARAÇÃO
```

O aluno DEVE poder comparar antes e depois e responder:

- O código ficou mais simples?
- Ficou mais testável?
- Ficou mais extensível?
- Ficou mais legível?
- Qual complexidade foi adicionada?
- Essa complexidade foi justificada?

Se a versão orientada a objetos for mais complexa sem benefício concreto, a solução simples PODE
ser preferida.

#### OOP in Data Engineering

POO DEVE ser ensinada dentro de problemas reais de Engenharia de Dados.

Possíveis contextos incluem, quando surgirem naturalmente:

```text
Collectors
Readers
Parsers
Validators
Transformers
Loaders
Storage
API Clients
Authentication Strategies
Pagination Strategies
Retry Policies
Schema Management
Incremental Strategies
CDC Strategies
SCD Strategies
Orchestration Components
Observability Components
```

Essa lista NÃO define classes obrigatórias.

Nenhum desses componentes DEVE ser criado antecipadamente apenas porque aparece nesta
Constitution. Eles são exemplos de contextos onde responsabilidades orientadas a objetos podem
eventualmente surgir.

#### OOP Quality Gate

Quando uma solução introduzir classes ou abstrações orientadas a objetos, a revisão DEVE
perguntar:

1. Por que uma classe é necessária?
2. Qual responsabilidade ela possui?
3. Qual estado mantém?
4. Quais invariantes protege?
5. Qual é sua interface pública?
6. Quais dependências possui?
7. Como essas dependências entram?
8. Há acoplamento desnecessário?
9. Há responsabilidade demais?
10. Composição seria melhor que herança?
11. Existe abstração prematura?
12. É possível testar isoladamente?
13. É possível substituir dependências?
14. A abstração facilita uma variação real?
15. A solução ficou objetivamente melhor que a versão anterior?

Essas perguntas DEVEM ser utilizadas como ferramenta de raciocínio, não como checklist
burocrático.

#### OOP Evidence of Mastery

POO somente PODE ser considerada consolidada (Princípios XIV e XV) quando houver evidência
prática de que o aluno consegue:

- criar classes com responsabilidade clara;
- diferenciar função de objeto;
- identificar estado;
- modelar comportamento;
- utilizar composição;
- justificar herança;
- explicar polimorfismo;
- compreender encapsulamento;
- reduzir acoplamento;
- aumentar coesão;
- testar objetos;
- utilizar abstrações somente quando necessárias;
- explicar pelo menos os princípios SOLID;
- reconhecer violações simples de design;
- refatorar código procedural para objetos quando houver benefício;
- manter código procedural quando objetos não trouxerem benefício.

A habilidade mais importante NÃO é criar objetos. É decidir corretamente **quando não criar
objetos**.

**Rationale:** o objetivo não é aprender a escrever classes, mas desenvolver capacidade de
modelar responsabilidades, estado, contratos e colaboração entre componentes. POO deve surgir
como resposta a problemas reais de design, manutenção, extensibilidade e testabilidade.

## Technical and Data Constraints

### Stack de Referência

A stack está documentada em `docs/STACK.md`. Ela poderá incluir ao longo dos ciclos:

- Python;
- pathlib;
- typing;
- dataclasses;
- logging;
- Pandas;
- Polars;
- Pandera;
- PyArrow;
- DuckDB;
- PostgreSQL;
- SQLAlchemy;
- httpx;
- pytest;
- dbt;
- Airflow;
- Apache Iceberg;
- Spark;
- Docker;
- Terraform;
- object storage;
- OpenTelemetry.

Esta lista NÃO significa que todas as ferramentas DEVEM ser utilizadas.

Tecnologias fora da stack PODEM ser utilizadas mediante justificativa.

A ferramenta deve servir ao problema, e não o problema servir à ferramenta.

### Sequência de Ferramentas

Cada tecnologia DEVE entrar no momento pedagógico previsto em `ROADMAP.md`.

Exemplos:

- fundamentos Python e filesystem antes de abstrações de Collector;
- transformação antes de frameworks distribuídos;
- armazenamento e Parquet antes de Lakehouse;
- incremental antes de abstrações avançadas de CDC;
- orchestration antes de plataformas complexas;
- single-node antes de Spark quando aplicável.

Conhecimento prévio NÃO autoriza automaticamente antecipação se isso prejudicar o objetivo
pedagógico.

### Python Standards

Consultar `docs/PYTHON_STANDARDS.md`.

Referências principais: PEP 8, PEP 257, PEP 484, PEP 526, PEP 544 e PEP 557.

As PEPs DEVEM ser estudadas de forma contextual, conforme os problemas correspondentes surgirem
no código. "Seguir PEPs" NÃO DEVE ser tratado como sinônimo de Programação Orientada a Objetos:
cada PEP possui objetivo distinto.

```text
ESTILO E LEGIBILIDADE              → PEP 8
DOCUMENTAÇÃO                       → PEP 257
TYPE HINTS                         → PEP 484
ANNOTATIONS                        → PEP 526
STRUCTURAL SUBTYPING / PROTOCOLS   → PEP 544
DATA CLASSES                       → PEP 557
```

O agente NÃO DEVE transformar o estudo das PEPs em memorização de documentos. Para cada PEP, o
aluno DEVE compreender:

- qual problema motivou a PEP;
- qual comportamento ou convenção ela define;
- onde aparece no código;
- quando é relevante;
- quais decisões ela influencia.

PEPs adicionais PODEM ser adicionadas posteriormente quando conceitos correspondentes surgirem.

Conforme o curso progride:

- type hints em interfaces públicas;
- funções pequenas e coesas;
- exceptions específicas;
- `pathlib` para filesystem;
- logging em pipelines;
- configuração separada do código;
- responsabilidades explícitas;
- testes automatizados.

Correção antes de performance.

Clareza antes de abstração.

### Security

Secrets NÃO DEVEM ser commitados.

Credenciais DEVEM utilizar mecanismos apropriados, como:

- environment variables;
- `.env` ignorado pelo Git quando adequado ao ambiente local;
- secret managers em ambientes que os justifiquem.

Dados sensíveis NÃO DEVEM ser incluídos desnecessariamente no repositório.

## Learning Workflow

### Início de Sessão

O contexto mínimo DEVE ser reconstruído a partir de:

```text
CONTEXT.md
CURRENT_STATE.md
ROADMAP.md
cycles/<CURRENT_CYCLE>.md
```

Documentos adicionais DEVEM ser carregados somente quando relevantes.

O histórico inteiro de conversas NÃO DEVE ser considerado a única fonte de verdade.

O repositório é a fonte persistente de estado do programa.

### Fluxo Padrão de Aprendizado

```text
PROBLEMA
↓
INPUT / OUTPUT
↓
REGRAS
↓
EDGE CASES
↓
ALGORITMO
↓
PSEUDOCÓDIGO
↓
IMPLEMENTAÇÃO DO ALUNO
↓
TESTES
↓
MEDIÇÃO
↓
REVISÃO
↓
REFATORAÇÃO
↓
GENERALIZAÇÃO
↓
CONSOLIDAÇÃO
```

Nem toda etapa exigirá a mesma profundidade. Porém, nenhuma ferramenta DEVE esconder os
fundamentos que constituem o objetivo da etapa.

## Mandatory Engineering Questions

Toda spec, plan e revisão de projeto DEVE responder, ou declarar explicitamente por que não se
aplica:

1. Está correto?
2. Quais são os inputs e outputs?
3. É idempotente?
4. Qual é o perfil de I/O?
5. Qual é o consumo de memória?
6. Como detectar falhas?
7. Como recuperar?
8. Quanto custa?
9. O que acontece com 10x o volume?
10. O que acontece se rodar duas vezes?
11. Como testar?
12. Qual é o principal gargalo conhecido?
13. O gargalo foi medido ou presumido?
14. Quais decisões são reversíveis?
15. Qual complexidade estamos adicionando e por quê?

Nem todas as perguntas precisam gerar implementação imediata. No início do curso, algumas podem
ser respondidas apenas conceitualmente.

## Spec Kit Quality Gates

### Spec Gate

Uma spec DEVE conter:

- problema;
- contexto;
- objetivo;
- inputs;
- outputs;
- regras;
- edge cases;
- acceptance criteria;
- análise inicial de I/O;
- requisitos mínimos de observabilidade;
- comportamento em falha, quando aplicável;
- considerações de custo, quando aplicável.

A spec DEVE prioritariamente definir **o que e por quê**. Ela NÃO DEVE antecipar
desnecessariamente **como**.

### Plan Gate

O Constitution Check DEVE verificar os Princípios I–XVIII.

O plan DEVE:

- derivar da spec;
- apresentar raciocínio técnico;
- apresentar algoritmo ou pseudocódigo antes de abstrações sofisticadas;
- justificar tecnologias novas;
- justificar abstrações novas;
- considerar testes;
- considerar I/O;
- considerar observabilidade;
- considerar custo;
- considerar failure/recovery quando aplicável.

Quando classes ou outras abstrações orientadas a objetos forem propostas, o plan DEVE justificar
por que a implementação simples deixou de ser suficiente e qual problema concreto a abstração
resolve.

Violações conscientes DEVEM ser registradas em Complexity Tracking ou ADR.

### Tasks Gate

Tasks DEVEM:

- derivar do plan;
- ser pequenas o suficiente para revisão;
- possuir objetivo pedagógico quando forem exercícios;
- distinguir implementação do aluno de automações permitidas;
- incluir testes;
- incluir medição quando pertinente;
- incluir revisão;
- incluir consolidação;
- incluir atualização de `progress/` quando aplicável.

Tasks NÃO DEVEM transformar o agente no implementador padrão.

Tasks relacionadas à evolução para POO DEVEM, quando pedagogicamente adequado, preservar a
implementação simples anterior para permitir comparação antes/depois.

A task NÃO DEVE simplesmente instruir "transforme em classe". Ela DEVE identificar o problema de
design que motiva a refatoração ou conduzir o aluno a descobri-lo.

### Implement Gate

`/speckit-implement` e comandos equivalentes NÃO DEVEM implementar automaticamente código cujo
objetivo seja desenvolver habilidade ainda não consolidada.

Para código de aprendizado, o comportamento padrão DEVE ser `TUTOR MODE`. Nesse modo, o agente:

- lê a task;
- explica o objetivo;
- verifica entendimento;
- pede implementação;
- revisa a tentativa;
- fornece pistas;
- auxilia debugging;
- valida testes;
- conduz consolidação.

Implementação automática PODE ser usada para infraestrutura ou trabalho sem valor pedagógico,
desde que isso não remova o aprendizado pretendido.

## Session Review

Ao final de uma sessão relevante, avaliar:

### Aprendizado

- O que foi aprendido?
- O aluno consegue explicar?
- Qual dificuldade apareceu?
- O que ainda está confuso?

### Engenharia

- A solução está correta?
- Há testes?
- Qual o I/O?
- Há alguma medição?
- Como falha?
- Como escala?

Quando POO estiver sendo utilizada:

- As responsabilidades estão claras?
- As classes adicionadas são realmente necessárias?
- Há coesão adequada?
- Existe acoplamento desnecessário?
- Composição e herança foram escolhidas conscientemente?
- A abstração resolveu um problema observado?

Essas perguntas são condicionais e NÃO precisam ser respondidas em sessões puramente
procedurais.

### Registro

Atualizar quando pertinente:

```text
CURRENT_STATE.md
progress/PROGRESS.md
progress/ERRORS_AND_LESSONS.md
progress/DECISIONS.md
progress/SKILLS_MATRIX.md
```

Não atualizar arquivos apenas para gerar burocracia. Registros DEVEM possuir valor para sessões
futuras.

## Cycle Completion Gate

Um ciclo NÃO DEVE ser considerado concluído apenas porque os dias planejados terminaram.

Para concluir um ciclo, DEVE existir evidência suficiente de:

- projeto funcionando;
- código majoritariamente produzido pelo aluno;
- testes relevantes;
- revisão;
- conceitos fundamentais compreendidos;
- decisões importantes justificadas;
- erros relevantes consolidados;
- skills atualizadas;
- capacidade do aluno de explicar a solução.

Nos ciclos em que POO fizer parte dos objetivos pedagógicos, a conclusão DEVE possuir evidência
correspondente em `progress/SKILLS_MATRIX.md`, conforme o Princípio XVIII. POO NÃO DEVE ser
exigida em ciclos ou projetos onde ainda não tenha sido introduzida.

Quando necessário, o ciclo PODE durar mais que o planejado.

O aprendizado prevalece sobre o calendário.

## Governance

Esta Constitution prevalece sobre:

- templates;
- specs;
- plans;
- tasks;
- instruções locais de agentes;
- documentação derivada do programa.

Documentos derivados que contradigam esta Constitution DEVEM ser corrigidos.

### Amendments

Emendas DEVEM:

1. possuir motivação;
2. ser propostas pelo aluno ou explicitamente aprovadas por ele;
3. ser aplicadas de forma rastreável;
4. atualizar documentos dependentes quando necessário;
5. gerar ADR em `progress/DECISIONS.md` quando alterarem materialmente o método de aprendizado.

A Constitution NÃO DEVE ser alterada frequentemente apenas para antecipar situações hipotéticas.

Problemas reais observados durante o programa DEVEM orientar futuras emendas.

### Semantic Versioning

- **MAJOR**: remoção ou redefinição incompatível de princípio fundamental ou regra de
  governança.
- **MINOR**: novo princípio, quality gate ou expansão material do método.
- **PATCH**: correção textual, esclarecimento ou alteração sem impacto semântico relevante.

### Compliance

Todo plan DEVE passar pelo Constitution Check.

Toda revisão relevante DEVE considerar aderência à Constitution.

O fim de cada ciclo DEVE incluir uma revisão breve de conformidade.

Violações intencionais DEVEM ser justificadas.

Violações dos princípios **Student Writes the Code**, **Escalation Before Full Solution** e
**AI Must Preserve Learning** DEVEM ser apontadas pelo agente assim que detectadas.

## Final Principle

O sucesso deste programa NÃO será medido por:

- quantidade de código;
- quantidade de frameworks utilizados;
- quantidade de projetos;
- velocidade de implementação;
- quantidade de conteúdo consumido.

Será medido pela capacidade crescente do aluno de receber um problema de Engenharia de Dados e,
progressivamente, conseguir sozinho:

```text
ENTENDER
↓
DECOMPOR
↓
MODELAR
↓
IMPLEMENTAR
↓
TESTAR
↓
DEPURAR
↓
MEDIR
↓
OPERAR
↓
OTIMIZAR
↓
JUSTIFICAR
↓
EVOLUIR
```

A IA deve tornar o aluno progressivamente **menos dependente da IA para resolver problemas
fundamentais**, e mais capaz de utilizá-la conscientemente como ferramenta de engenharia.

A evolução para POO NÃO DEVE significar dependência de agentes para gerar arquiteturas
sofisticadas. O aluno DEVE progressivamente conseguir receber código procedural e raciocinar
sozinho sobre:

```text
RESPONSABILIDADES
↓
ESTADO
↓
DEPENDÊNCIAS
↓
CONTRATOS
↓
COLABORAÇÃO
↓
ABSTRAÇÕES
↓
ARQUITETURA
```

**Version**: 1.2.0 | **Ratified**: 2026-09-22 | **Last Amended**: 2026-09-22

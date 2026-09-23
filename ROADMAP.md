# Roadmap — 100 Days

## Objetivo

Este roadmap organiza aproximadamente 100 dias de aprendizado prático de Engenharia de Dados.

O objetivo não é apenas aprender ferramentas.

Ao final do programa, o aluno deve possuir capacidade crescente de receber um problema de dados e:

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

O aprendizado será desenvolvido através de projetos progressivos.

Cada ciclo combina duas trilhas inseparáveis:

1. **Engenharia de Dados**
2. **Engenharia de Software com Python**

Ferramentas são introduzidas conforme os problemas que resolvem aparecem.

A Constitution do projeto prevalece sobre este Roadmap.

---

# Trilha Transversal de Python e Engenharia de Software

Python e Programação Orientada a Objetos NÃO constituem um módulo isolado.

Essas competências evoluem durante todo o programa.

A progressão esperada é:

```text
LÓGICA
↓
FUNÇÕES
↓
ESTRUTURAS DE DADOS
↓
ITERADORES / GENERATORS
↓
EXCEPTIONS
↓
MÓDULOS
↓
TESTES
↓
ESTADO
↓
RESPONSABILIDADES
↓
CLASSES
↓
ENCAPSULAMENTO
↓
DATACLASSES
↓
COMPOSIÇÃO
↓
COESÃO / ACOPLAMENTO
↓
INTERFACES / CONTRATOS
↓
POLIMORFISMO
↓
ABC / PROTOCOL / DUCK TYPING
↓
SOLID
↓
DEPENDENCY INVERSION
↓
DESIGN PATTERNS
↓
ARQUITETURA
↓
SISTEMAS DE PRODUÇÃO
```

Essa sequência representa uma direção pedagógica.

Conceitos NÃO DEVEM ser introduzidos apenas porque aparecem neste Roadmap.

A necessidade deve surgir primeiro no problema.

---

# Trilha Transversal de PEPs

As PEPs serão estudadas no contexto em que se tornarem relevantes.

Referências iniciais:

```text
ESTILO E LEGIBILIDADE
→ PEP 8

DOCUMENTAÇÃO
→ PEP 257

TYPE HINTS
→ PEP 484

VARIABLE ANNOTATIONS
→ PEP 526

STRUCTURAL SUBTYPING / PROTOCOL
→ PEP 544

DATACLASSES
→ PEP 557
```

PEPs adicionais poderão ser incorporadas conforme novos conceitos Python surgirem.

O objetivo não é memorizar PEPs.

Para cada uma, o aluno deve compreender:

* qual problema ela aborda;
* por que existe;
* como aparece no código;
* quando é relevante;
* quais decisões influencia.

---

# Ciclo 1 — Fundamentos, Lógica, Python e I/O

## Objetivo

Aprender a transformar um problema de dados em lógica executável antes de introduzir abstrações sofisticadas.

O foco é desenvolver fundamentos de programação e compreender como programas interagem com dados e filesystem.

## Engenharia de Dados

Estudar:

* input e output;
* arquivos e diretórios;
* filesystem;
* metadata;
* leitura e escrita;
* formatos simples;
* custo de I/O;
* materialização;
* processamento incremental de elementos;
* memória;
* throughput;
* medição básica.

## Python

Estudar progressivamente:

* variáveis;
* tipos fundamentais;
* condicionais;
* loops;
* collections;
* funções;
* argumentos;
* retornos;
* escopo;
* módulos;
* imports;
* exceptions;
* `pathlib`;
* iteráveis;
* iteradores;
* generators;
* type hints básicos;
* docstrings;
* testes básicos.

PEPs introduzidas quando pertinentes:

* PEP 8;
* PEP 257;
* introdução à PEP 484.

## POO

POO NÃO é o ponto de partida deste ciclo.

O projeto deve começar com funções simples.

Classes somente poderão aparecer posteriormente caso o código demonstre necessidade concreta de:

* estado;
* responsabilidade;
* encapsulamento;
* colaboração entre componentes.

ABC, Protocol, Factory, Strategy ou outras abstrações avançadas NÃO constituem objetivos do ciclo.

## Performance

Introduzir:

* `time.perf_counter`;
* quantidade de arquivos processados;
* bytes observados;
* tempo total;
* throughput simples;
* diferença entre metadata e leitura de conteúdo;
* materialização versus iteração.

Nenhuma otimização deve ocorrer antes da medição.

## Entrega

**Universal File Collector**

O projeto deve evoluir incrementalmente.

Possível trajetória conceitual:

```text
PROBLEMA
↓
ALGORITMO
↓
FUNÇÃO
↓
TESTES
↓
MEDIÇÃO
↓
NOVOS REQUISITOS
↓
REFATORAÇÃO
```

A arquitetura final NÃO deve ser definida antecipadamente.

---

# Ciclo 2 — Transformação, Qualidade e Contratos

## Objetivo

Aprender a transformar dados de maneira previsível e estabelecer contratos explícitos sobre sua estrutura e qualidade.

## Engenharia de Dados

Estudar:

* transformação;
* normalização;
* limpeza;
* schema;
* data types;
* nullability;
* constraints;
* validação;
* data contracts;
* dados inválidos;
* quarantine;
* schema drift;
* schema evolution;
* qualidade de dados;
* testes de dados.

Ferramentas poderão incluir:

* Pandas;
* Polars;
* Pandera;
* pytest.

As ferramentas devem ser comparadas conforme necessidade e características do problema.

## Python / POO

Introduzir progressivamente:

* classes;
* instâncias;
* `__init__`;
* estado;
* comportamento;
* responsabilidades;
* encapsulamento;
* propriedades quando justificadas;
* dataclasses;
* type hints mais explícitos;
* exceptions customizadas quando justificadas.

PEPs relevantes:

* PEP 484;
* PEP 526;
* PEP 557.

O aluno deve aprender a responder:

> Quando uma função é suficiente?

e:

> Quando dados e comportamento começam a formar uma responsabilidade que justifica um objeto?

## Design

Introduzir:

* responsabilidade;
* coesão;
* acoplamento;
* separação de responsabilidades.

SOLID ainda NÃO deve ser aplicado como framework completo.

Problemas concretos podem preparar sua introdução futura.

## Entrega

**Data Quality Pipeline**

A entrega deve possuir:

```text
INPUT
↓
TRANSFORMAÇÃO
↓
VALIDAÇÃO
↓
DADOS VÁLIDOS / INVÁLIDOS
↓
QUARANTINE
↓
OUTPUT
```

---

# Ciclo 3 — Storage, Parquet e Data Lake

## Objetivo

Compreender armazenamento analítico e como formato, layout e particionamento influenciam I/O, performance e custo.

## Engenharia de Dados

Estudar:

* Data Lake;
* object storage;
* CSV versus Parquet;
* Apache Arrow;
* columnar storage;
* Parquet;
* compression;
* encoding;
* row groups;
* statistics;
* projection;
* predicate pushdown;
* pruning;
* partitioning;
* small files;
* file sizing;
* DuckDB.

## Python / POO

Evoluir para colaboração entre componentes.

Introduzir quando justificado:

* composição;
* dependências entre objetos;
* interfaces públicas;
* separação entre transformação e armazenamento;
* coesão;
* redução de acoplamento;
* test doubles simples.

Pergunta central:

> Como componentes diferentes colaboram sem conhecer detalhes internos uns dos outros?

Composição deve ser considerada antes de herança.

## I/O e Performance

Medir:

* bytes lidos;
* bytes escritos;
* elapsed time;
* throughput;
* memória;
* quantidade de arquivos;
* efeito de projection;
* efeito de filtering;
* efeito de partition pruning;
* efeito de compression.

## Custo

Relacionar:

```text
FORMATO
+
COMPRESSÃO
+
PARTICIONAMENTO
+
QUANTIDADE DE ARQUIVOS
+
SCAN
=
PERFORMANCE + CUSTO
```

## Entrega

**Mini Data Lake**

A solução deve permitir observar experimentalmente como decisões físicas alteram leitura, armazenamento e custo.

---

# Ciclo 4 — Bancos, Data Warehouse, Incremental, CDC e SCD2

## Objetivo

Compreender persistência estruturada, modelagem analítica e processamento incremental.

## Engenharia de Dados

Estudar:

* OLTP versus OLAP;
* PostgreSQL;
* transações;
* ACID;
* constraints;
* primary keys;
* indexes;
* query plans;
* dimensional modeling;
* fatos;
* dimensões;
* surrogate keys;
* incremental loading;
* watermark;
* idempotência;
* upsert;
* CDC;
* SCD;
* SCD Type 1;
* SCD Type 2.

Distinguir explicitamente:

```text
CHANGE DETECTION
≠
CDC LOG-BASED
≠
TARGET HISTORY
```

## Python / POO

Introduzir progressivamente:

* contratos entre componentes;
* polimorfismo;
* duck typing;
* abstrações justificadas;
* `ABC`;
* `Protocol`;
* PEP 544.

A escolha entre:

```text
duck typing
Protocol
ABC
nenhuma abstração
```

deve decorrer do problema.

## SOLID

Introduzir SOLID através de problemas reais encontrados nos projetos:

* Single Responsibility;
* Open/Closed;
* Liskov Substitution;
* Interface Segregation;
* Dependency Inversion.

Cada princípio deve seguir:

```text
PROBLEMA
↓
CONSEQUÊNCIA
↓
PRINCÍPIO
↓
REFATORAÇÃO
↓
COMPARAÇÃO
```

## Entrega

**Mini Data Warehouse**

A entrega deve possuir ingestão incremental e histórico quando necessário, além de permitir explicar as diferenças entre incremental loading, CDC e SCD2.

---

# Ciclo 5 — APIs, Conectores e Orquestração

## Objetivo

Construir coletores HTTP robustos e perceber naturalmente problemas de variação de comportamento que justificam patterns.

## Engenharia de Dados

Estudar:

* HTTP;
* REST;
* requests/responses;
* status codes;
* headers;
* authentication;
* pagination;
* retries;
* exponential backoff;
* rate limiting;
* timeouts;
* sessions;
* connection reuse;
* incremental APIs;
* observabilidade;
* orchestration;
* DAGs;
* scheduling;
* retries de tarefas;
* Airflow.

## Python / Arquitetura

Problemas de conectores diferentes poderão justificar:

* Strategy;
* Adapter;
* Factory;
* Dependency Injection.

Patterns NÃO são requisitos automáticos.

Primeiro deve existir:

```text
IMPLEMENTAÇÃO
↓
VARIAÇÃO
↓
DUPLICAÇÃO / ACOPLAMENTO
↓
PROBLEMA
↓
PATTERN CANDIDATO
```

## Dependency Inversion

Diferenciar:

```text
POLÍTICA
vs
MECANISMO
```

e:

```text
REGRA
vs
INFRAESTRUTURA
```

Dependency Injection deve ser entendida como técnica, e não confundida com Dependency Inversion.

## Entrega

**Connector SDK + OMIE**

O projeto deve demonstrar que diferentes APIs podem compartilhar infraestrutura sem forçar abstrações artificiais.

---

# Ciclo 6 — Lakehouse e Escala

## Objetivo

Compreender por que tecnologias de Lakehouse existem e quando single-node deixa de ser suficiente.

## Engenharia de Dados

Estudar:

* limitações de Data Lakes tradicionais;
* Lakehouse;
* table formats;
* Apache Iceberg;
* metadata;
* snapshots;
* manifests;
* catalog;
* schema evolution;
* partition evolution;
* compaction;
* time travel;
* concurrency;
* Polars;
* Spark;
* processamento distribuído.

## Escala

Comparar:

```text
PYTHON
↓
POLARS / DUCKDB
↓
SPARK
```

Não assumir que Spark é necessário.

Medir ou caracterizar quando possível:

* volume;
* memória;
* CPU;
* I/O;
* paralelismo;
* shuffle;
* custo;
* complexidade operacional.

## Python / Arquitetura

Evoluir para:

* arquitetura modular;
* substituição de engines;
* boundaries;
* ports/adapters quando justificados;
* componentes desacoplados;
* contratos estáveis.

Pergunta central:

> Conseguimos trocar um detalhe de infraestrutura sem reescrever a regra principal?

## Entrega

**Mini Lakehouse**

A entrega deve demonstrar os problemas que table formats resolvem e comparar soluções simples e distribuídas quando possível.

---

# Ciclo 7 — Produção, Observabilidade, Cloud e Custo

## Objetivo

Integrar os conhecimentos anteriores em um sistema próximo de condições reais de produção.

## Engenharia de Dados

Estudar:

* logging estruturado;
* metrics;
* traces;
* OpenTelemetry;
* retries;
* recovery;
* disaster scenarios;
* segurança;
* secrets;
* IAM;
* containers;
* Docker;
* infraestrutura;
* Terraform;
* cloud;
* object storage;
* compute;
* networking;
* FinOps.

## Engenharia de Software

Revisar e consolidar:

* responsabilidades;
* encapsulamento;
* composição;
* interfaces;
* polimorfismo;
* SOLID;
* Dependency Inversion;
* patterns;
* testabilidade;
* arquitetura;
* observabilidade;
* configuração;
* failure handling.

Nenhum pattern deve existir apenas porque foi estudado.

Toda abstração relevante deve conseguir responder:

> Qual problema concreto ela resolve?

## Cost Engineering

O projeto deve possuir modelo explícito de custo:

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

Avaliar pelo menos:

* cenário atual;
* 10x volume;
* frequência;
* retenção;
* transferência;
* serviços always-on;
* alternativas arquiteturais.

## Entrega

**Projeto Final End-to-End**

O problema deve exigir decisões reais sobre:

* múltiplas fontes;
* ingestão;
* incremental;
* qualidade;
* storage;
* Data Lake;
* Data Warehouse;
* Lakehouse quando justificado;
* transformação;
* orchestration;
* observabilidade;
* segurança;
* recovery;
* custo.

O aluno deve justificar as escolhas arquiteturais.

---

# Projetos e Marcos

Aproximadamente a cada 15 dias deverá existir uma entrega demonstrável.

```text
CICLO 1
Universal File Collector

CICLO 2
Data Quality Pipeline

CICLO 3
Mini Data Lake

CICLO 4
Mini Data Warehouse

CICLO 5
Connector SDK + OMIE

CICLO 6
Mini Lakehouse

CICLO 7
Final End-to-End Data Platform
```

O projeto não existe apenas para demonstrar ferramentas.

Ele deve produzir evidência de aprendizado.

---

# Regra de Passagem

Não avançar apenas pelo calendário.

Uma entrega deve:

* funcionar;
* possuir testes relevantes;
* passar por revisão;
* passar por consolidação;
* possuir evidência prática;
* possuir evidência explicativa;
* atualizar as skills correspondentes quando aplicável.

O aluno deve conseguir explicar:

* o problema;
* inputs e outputs;
* algoritmo;
* decisões;
* falhas;
* testes;
* I/O;
* principais trade-offs.

---

# Regra de Evolução Arquitetural

A arquitetura NÃO deve ser conhecida antecipadamente pelo aluno apenas porque versões futuras estão documentadas.

A evolução preferencial é:

```text
IMPLEMENTAR
↓
OBSERVAR
↓
ENCONTRAR LIMITAÇÃO
↓
ENTENDER O PROBLEMA
↓
ESTUDAR O CONCEITO
↓
REFATORAR
↓
COMPARAR
↓
CONSOLIDAR
```

Uma abstração só deve permanecer se trouxer benefício justificável.

---

# Regra de Escala

Para todo projeto relevante, perguntar:

```text
FUNCIONA COM O VOLUME ATUAL?
↓
ONDE ESTÁ O GARGALO?
↓
FOI MEDIDO?
↓
O QUE ACONTECE COM 10x?
↓
QUAL É A SOLUÇÃO MAIS SIMPLES?
↓
QUANDO PRECISAMOS DISTRIBUIR?
```

Não utilizar sistemas distribuídos apenas porque fazem parte da stack moderna.

---

# Regra de Custo

Toda evolução arquitetural relevante deve considerar custo.

Quando possível, comparar:

```text
SOLUÇÃO A
vs
SOLUÇÃO B
```

considerando:

* compute;
* storage;
* network;
* requests;
* manutenção;
* complexidade operacional;
* custo humano.

Performance sem custo é uma análise incompleta.

Custo sem requisitos é uma otimização prematura.

---

# Resultado Esperado

Ao final dos 100 dias, o aluno deve ter evoluído de:

```text
"Como faço isso em Python?"
```

para:

```text
"Qual é o problema?

Quais são os requisitos?

Quais são os inputs e outputs?

Qual é o algoritmo mais simples?

Qual é o perfil de I/O?

Como isso falha?

Como testo?

Como observo?

Quanto custa?

Como escala?

Qual abstração realmente preciso?

Como justifico essa decisão?"
```

O objetivo final não é depender de uma stack específica.

O objetivo é desenvolver capacidade de engenharia suficiente para aprender, avaliar e utilizar stacks diferentes conscientemente.

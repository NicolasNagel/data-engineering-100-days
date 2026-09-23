# Skills Matrix

## Objetivo

Este documento registra a evolução prática das competências desenvolvidas durante o programa Data Engineering — 100 Days.

A Skills Matrix NÃO representa apenas tecnologias conhecidas.

Ela deve responder:

> O que o aluno consegue fazer e explicar com evidência?

O estado de uma competência deve ser baseado em evidência observável produzida durante o programa.

Experiência anterior pode ser registrada como contexto, mas NÃO constitui automaticamente evidência de consolidação.

---

# Estados

Toda competência utiliza exatamente um dos seguintes estados:

```text
Não iniciado
↓
Exposto
↓
Praticado
↓
Consolidado
```

## Não iniciado

O conceito ainda não foi estudado formalmente no programa.

Pode existir conhecimento prévio, mas ainda não há evidência produzida dentro do programa.

## Exposto

O conceito foi apresentado e existe compreensão inicial.

O aluno consegue reconhecer:

* o conceito;
* seu propósito;
* exemplos básicos.

Ainda existe dependência significativa de documentação, exemplos ou orientação.

## Praticado

O aluno já utilizou a competência em exercícios ou projetos.

Existe evidência prática.

O aluno consegue implementar ou aplicar o conceito com alguma independência, mas ainda pode apresentar dificuldades em:

* edge cases;
* debugging;
* trade-offs;
* generalização;
* arquitetura;
* explicação profunda.

## Consolidado

Existe evidência prática e explicativa suficiente.

O aluno consegue:

* explicar o conceito;
* explicar qual problema resolve;
* aplicar sem depender de solução pronta;
* justificar decisões;
* identificar alternativas;
* discutir trade-offs;
* testar;
* depurar;
* reconhecer quando NÃO utilizar;
* aplicar em contexto diferente daquele em que aprendeu.

`Consolidado` exige evidência produzida durante o programa.

---

# Tipos de Evidência

Evidências podem incluir:

* implementação do aluno;
* exercício;
* projeto;
* teste automatizado;
* debugging documentado;
* benchmark;
* ADR;
* explicação técnica;
* perguntas de recuperação ativa;
* comparação entre soluções;
* refatoração;
* experimento;
* documentação produzida pelo aluno.

Código copiado ou produzido integralmente por IA NÃO constitui evidência suficiente.

---

# 1. Fundamentos de Programação

| Competência                    | Estado       | Evidência                                       |
| ------------------------------ | ------------ | ----------------------------------------------- |
| Decomposição de problemas      | Exposto      | Experiência prévia; validar durante o programa  |
| Input → Processamento → Output | Exposto      | Experiência prévia; validar durante o Ciclo 1   |
| Condicionais                   | Exposto      | Experiência prévia; validar durante o Ciclo 1   |
| Loops                          | Exposto      | Experiência prévia; validar durante o Ciclo 1   |
| Collections                    | Exposto      | Experiência prévia; validar durante o Ciclo 1   |
| Funções                        | Exposto      | Pipelines anteriores; validar durante o Ciclo 1 |
| Escopo                         | Não iniciado | —                                               |
| Exceptions                     | Exposto      | Experiência prévia; validar durante o Ciclo 1   |
| Módulos e imports              | Exposto      | Projetos anteriores; validar durante o Ciclo 1  |
| Iterables                      | Não iniciado | —                                               |
| Iterators                      | Não iniciado | —                                               |
| Generators                     | Não iniciado | —                                               |
| Debugging sistemático          | Não iniciado | —                                               |
| Pseudocódigo / algoritmo       | Não iniciado | —                                               |

---

# 2. Python Standards

| Competência                         | Estado       | Evidência                                |
| ----------------------------------- | ------------ | ---------------------------------------- |
| PEP 8                               | Exposto      | Uso anterior; validar durante o programa |
| PEP 257 / Docstrings                | Exposto      | Uso anterior; validar durante o programa |
| PEP 484 / Type Hints                | Exposto      | Projetos anteriores                      |
| PEP 526 / Variable Annotations      | Não iniciado | —                                        |
| pathlib                             | Exposto      | Uso anterior; aprofundar no Ciclo 1      |
| Exceptions específicas              | Exposto      | Uso anterior; validar no programa        |
| Public interfaces                   | Não iniciado | —                                        |
| Configuração separada               | Exposto      | Projetos anteriores                      |
| Secrets management                  | Exposto      | Projetos anteriores                      |
| Refactoring orientado por evidência | Não iniciado | —                                        |

---

# 3. Programação Orientada a Objetos

POO é acompanhada separadamente de Python fundamental.

| Competência                      | Estado       | Evidência                                              |
| -------------------------------- | ------------ | ------------------------------------------------------ |
| Classes e instâncias             | Exposto      | Pipelines anteriores; validar no programa              |
| Estado e comportamento           | Exposto      | Experiência anterior; validar no programa              |
| `__init__`                       | Exposto      | Projetos anteriores                                    |
| Responsabilidades                | Não iniciado | —                                                      |
| Encapsulamento                   | Não iniciado | —                                                      |
| Properties                       | Não iniciado | —                                                      |
| Dataclasses / PEP 557            | Não iniciado | —                                                      |
| Composição                       | Não iniciado | —                                                      |
| Herança                          | Exposto      | Conhecimento anterior; ainda sem evidência no programa |
| Polimorfismo                     | Não iniciado | —                                                      |
| Coesão                           | Não iniciado | —                                                      |
| Acoplamento                      | Não iniciado | —                                                      |
| Modelagem orientada a objetos    | Não iniciado | —                                                      |
| Refatoração procedural → objetos | Não iniciado | —                                                      |
| Decidir função vs classe         | Não iniciado | —                                                      |
| Composition over inheritance     | Não iniciado | —                                                      |

---

# 4. Contratos e Abstrações Python

| Competência                                 | Estado       | Evidência                                 |
| ------------------------------------------- | ------------ | ----------------------------------------- |
| Duck Typing                                 | Não iniciado | —                                         |
| ABC                                         | Exposto      | Experiência anterior; validar no programa |
| Protocol / PEP 544                          | Não iniciado | —                                         |
| Structural Subtyping                        | Não iniciado | —                                         |
| Contratos entre componentes                 | Não iniciado | —                                         |
| Dependency Inversion                        | Não iniciado | —                                         |
| Dependency Injection                        | Exposto      | Contato anterior; validar no programa     |
| Test doubles / substituição de dependências | Não iniciado | —                                         |

---

# 5. SOLID e Design

| Competência                            | Estado       | Evidência                                           |
| -------------------------------------- | ------------ | --------------------------------------------------- |
| Single Responsibility Principle        | Exposto      | Conhecimento prévio; validar através de refatoração |
| Open/Closed Principle                  | Não iniciado | —                                                   |
| Liskov Substitution Principle          | Não iniciado | —                                                   |
| Interface Segregation Principle        | Não iniciado | —                                                   |
| Dependency Inversion Principle         | Não iniciado | —                                                   |
| Reconhecer abstração prematura         | Não iniciado | —                                                   |
| Justificar abstrações                  | Não iniciado | —                                                   |
| Design orientado por responsabilidades | Não iniciado | —                                                   |

---

# 6. Design Patterns

Patterns só evoluem de estado quando surgirem de problemas reais.

| Competência                        | Estado       | Evidência                                        |
| ---------------------------------- | ------------ | ------------------------------------------------ |
| Strategy                           | Exposto      | Contato anterior em projetos de coletores        |
| Adapter                            | Não iniciado | —                                                |
| Factory                            | Exposto      | Contato anterior; validar no programa            |
| Repository                         | Exposto      | Contato anterior em FastAPI; validar no programa |
| Template Method                    | Não iniciado | —                                                |
| Facade                             | Não iniciado | —                                                |
| Builder                            | Não iniciado | —                                                |
| Seleção de pattern por problema    | Não iniciado | —                                                |
| Reconhecer quando NÃO usar pattern | Não iniciado | —                                                |

---

# 7. I/O e Performance

| Competência                     | Estado       | Evidência            |
| ------------------------------- | ------------ | -------------------- |
| Filesystem I/O                  | Não iniciado | —                    |
| Metadata vs leitura de conteúdo | Não iniciado | —                    |
| Materialização                  | Não iniciado | —                    |
| Streaming                       | Não iniciado | —                    |
| Chunking                        | Exposto      | Experiência anterior |
| Memory awareness                | Não iniciado | —                    |
| Bytes read / written            | Não iniciado | —                    |
| Throughput                      | Não iniciado | —                    |
| Benchmarking                    | Não iniciado | —                    |
| Profiling                       | Não iniciado | —                    |
| Identificar I/O-bound           | Não iniciado | —                    |
| Identificar CPU-bound           | Não iniciado | —                    |
| Identificar memory-bound        | Não iniciado | —                    |
| Identificar network-bound       | Não iniciado | —                    |

---

# 8. Transformação e Qualidade

| Competência               | Estado       | Evidência                      |
| ------------------------- | ------------ | ------------------------------ |
| Pandas                    | Praticado    | Projetos anteriores            |
| Polars                    | Não iniciado | —                              |
| Data transformation       | Praticado    | Projetos anteriores            |
| Schema validation         | Praticado    | Pandera em projetos anteriores |
| Pandera                   | Praticado    | Projetos anteriores            |
| Data contracts            | Exposto      | Projetos anteriores            |
| Nullability / constraints | Exposto      | Projetos anteriores            |
| Quarantine                | Não iniciado | —                              |
| Schema Drift              | Exposto      | SchemaManager anterior         |
| Schema Evolution          | Exposto      | SchemaManager anterior         |
| Data Quality Testing      | Exposto      | Experiência anterior           |

---

# 9. Storage e Data Lake

| Competência         | Estado       | Evidência                        |
| ------------------- | ------------ | -------------------------------- |
| CSV                 | Praticado    | Pipelines anteriores             |
| JSON                | Praticado    | APIs anteriores                  |
| Excel               | Praticado    | Pipelines anteriores             |
| Apache Arrow        | Exposto      | Conversão CSV → Parquet anterior |
| PyArrow             | Exposto      | Projeto Azure/Data Lake          |
| Parquet             | Exposto      | Projeto Azure/Data Lake          |
| Columnar Storage    | Exposto      | Conhecimento anterior            |
| Compression         | Não iniciado | —                                |
| Row Groups          | Não iniciado | —                                |
| Statistics          | Não iniciado | —                                |
| Projection          | Não iniciado | —                                |
| Predicate Pushdown  | Não iniciado | —                                |
| Partition Pruning   | Não iniciado | —                                |
| Partitioning        | Exposto      | Projetos anteriores              |
| Small Files Problem | Não iniciado | —                                |
| DuckDB              | Não iniciado | —                                |
| Data Lake Design    | Exposto      | Projeto Azure/Data Lake          |

---

# 10. Bancos de Dados e Data Warehouse

| Competência           | Estado    | Evidência                         |
| --------------------- | --------- | --------------------------------- |
| SQL                   | Praticado | Experiência profissional anterior |
| PostgreSQL            | Praticado | Projetos anteriores               |
| SQL Server            | Praticado | Experiência profissional          |
| SQLAlchemy            | Exposto   | Projetos anteriores               |
| Transactions          | Exposto   | Experiência anterior              |
| ACID                  | Exposto   | Conhecimento anterior             |
| Constraints           | Praticado | Projetos anteriores               |
| Indexes               | Exposto   | Experiência anterior              |
| Query Plans           | Exposto   | Experiência anterior              |
| OLTP vs OLAP          | Exposto   | Conhecimento anterior             |
| Dimensional Modeling  | Exposto   | Experiência anterior              |
| Fact Tables           | Exposto   | Experiência anterior              |
| Dimension Tables      | Exposto   | Experiência anterior              |
| Surrogate Keys        | Exposto   | Experiência anterior              |
| Data Warehouse Design | Exposto   | Experiência anterior              |

---

# 11. Incremental, CDC e SCD

| Competência          | Estado       | Evidência                                                  |
| -------------------- | ------------ | ---------------------------------------------------------- |
| Incremental Loading  | Praticado    | Pipelines anteriores                                       |
| Watermark            | Exposto      | Projetos anteriores                                        |
| Upsert               | Praticado    | PostgreSQL / pipelines anteriores                          |
| Idempotência         | Exposto      | Experiência anterior; validar formalmente                  |
| Change Detection     | Exposto      | Filtros por updated_at anteriores                          |
| CDC conceitual       | Exposto      | Estudo anterior                                            |
| Log-based CDC        | Não iniciado | —                                                          |
| SCD Type 1           | Exposto      | Conhecimento anterior                                      |
| SCD Type 2           | Exposto      | Estudos anteriores; ainda sem evidência prática suficiente |
| Recovery incremental | Não iniciado | —                                                          |
| Checkpoints          | Não iniciado | —                                                          |

---

# 12. HTTP e APIs

| Competência            | Estado    | Evidência                 |
| ---------------------- | --------- | ------------------------- |
| HTTP Fundamentals      | Praticado | HubSpot / OMIE            |
| REST APIs              | Praticado | HubSpot / OMIE            |
| Authentication         | Praticado | APIs anteriores           |
| Pagination             | Praticado | HubSpot / OMIE            |
| Sessions               | Exposto   | Projetos anteriores       |
| Retry                  | Praticado | OMIE                      |
| Exponential Backoff    | Exposto   | Retry policies anteriores |
| Rate Limiting          | Exposto   | APIs anteriores           |
| Timeouts               | Exposto   | APIs anteriores           |
| Connection Reuse       | Exposto   | Estudos anteriores        |
| Incremental APIs       | Praticado | Pipelines anteriores      |
| API Error Handling     | Praticado | HubSpot / OMIE            |
| Connector Architecture | Exposto   | HTTPCollector anterior    |

---

# 13. Orquestração

| Competência            | Estado       | Evidência           |
| ---------------------- | ------------ | ------------------- |
| Orchestration Concepts | Exposto      | Estudos anteriores  |
| DAG                    | Exposto      | Airflow             |
| Scheduling             | Exposto      | Airflow             |
| Task Dependencies      | Exposto      | Airflow             |
| Task Retry             | Exposto      | Airflow             |
| Airflow                | Exposto      | Experiência inicial |
| Cosmos                 | Exposto      | Estudos anteriores  |
| dbt orchestration      | Não iniciado | —                   |
| Failure Recovery       | Não iniciado | —                   |
| Backfill               | Não iniciado | —                   |

---

# 14. Lakehouse e Escala

| Competência                        | Estado       | Evidência          |
| ---------------------------------- | ------------ | ------------------ |
| Lakehouse                          | Exposto      | Estudos anteriores |
| Apache Iceberg                     | Não iniciado | —                  |
| Table Formats                      | Não iniciado | —                  |
| Snapshots                          | Não iniciado | —                  |
| Manifests                          | Não iniciado | —                  |
| Catalog                            | Não iniciado | —                  |
| Schema Evolution em Table Formats  | Não iniciado | —                  |
| Partition Evolution                | Não iniciado | —                  |
| Compaction                         | Não iniciado | —                  |
| Time Travel                        | Não iniciado | —                  |
| Polars                             | Não iniciado | —                  |
| Spark                              | Não iniciado | —                  |
| Distributed Processing             | Não iniciado | —                  |
| Shuffle                            | Não iniciado | —                  |
| Seleção single-node vs distributed | Não iniciado | —                  |

---

# 15. Observabilidade

| Competência           | Estado       | Evidência                            |
| --------------------- | ------------ | ------------------------------------ |
| Logging               | Exposto      | Uso anterior; aprofundar no programa |
| Structured Logging    | Não iniciado | —                                    |
| Metrics               | Não iniciado | —                                    |
| Traces                | Não iniciado | —                                    |
| OpenTelemetry         | Não iniciado | —                                    |
| Run Context           | Não iniciado | —                                    |
| Error Context         | Exposto      | Projetos anteriores                  |
| Pipeline Counters     | Não iniciado | —                                    |
| Operational Debugging | Não iniciado | —                                    |
| SLI/SLO conceitos     | Não iniciado | —                                    |

---

# 16. Testing

| Competência             | Estado       | Evidência            |
| ----------------------- | ------------ | -------------------- |
| Testes de comportamento | Exposto      | Experiência anterior |
| pytest                  | Exposto      | Experiência anterior |
| Unit Tests              | Exposto      | Experiência anterior |
| Integration Tests       | Não iniciado | —                    |
| Edge Cases              | Exposto      | Experiência anterior |
| Exception Testing       | Não iniciado | —                    |
| Test Doubles            | Não iniciado | —                    |
| Fixtures                | Exposto      | Experiência anterior |
| Idempotency Testing     | Não iniciado | —                    |
| Failure Testing         | Não iniciado | —                    |
| Performance Testing     | Não iniciado | —                    |

---

# 17. Cloud e Infraestrutura

| Competência            | Estado       | Evidência           |
| ---------------------- | ------------ | ------------------- |
| Cloud Fundamentals     | Exposto      | Estudos anteriores  |
| Object Storage         | Exposto      | Azure Blob          |
| IAM                    | Exposto      | Estudos anteriores  |
| Compute                | Exposto      | Estudos anteriores  |
| Networking             | Não iniciado | —                   |
| Docker                 | Praticado    | Projetos anteriores |
| Terraform              | Não iniciado | —                   |
| Secrets Management     | Exposto      | Projetos anteriores |
| Infrastructure as Code | Não iniciado | —                   |

---

# 18. Cost Engineering

| Competência                   | Estado       | Evidência |
| ----------------------------- | ------------ | --------- |
| Compute Cost                  | Não iniciado | —         |
| Storage Cost                  | Não iniciado | —         |
| Network Cost                  | Não iniciado | —         |
| Request Cost                  | Não iniciado | —         |
| Operational Complexity        | Não iniciado | —         |
| Human Maintenance Cost        | Não iniciado | —         |
| Cost Estimation               | Não iniciado | —         |
| FinOps                        | Não iniciado | —         |
| Cost vs Performance Trade-off | Não iniciado | —         |

---

# 19. Arquitetura de Dados

| Competência                   | Estado       | Evidência                      |
| ----------------------------- | ------------ | ------------------------------ |
| Separation of Concerns        | Exposto      | Projetos anteriores            |
| Component Boundaries          | Não iniciado | —                              |
| Modular Architecture          | Exposto      | FastAPI / pipelines anteriores |
| Ports and Adapters            | Não iniciado | —                              |
| Architecture Decision Records | Não iniciado | —                              |
| Failure-oriented Design       | Não iniciado | —                              |
| Scalability Reasoning         | Exposto      | Estudos anteriores             |
| 10x Volume Analysis           | Não iniciado | —                              |
| Trade-off Analysis            | Não iniciado | —                              |
| Architecture Justification    | Não iniciado | —                              |

---

# Regras de Atualização

A Skills Matrix deve ser atualizada quando existir nova evidência relevante.

NÃO atualizar automaticamente uma competência apenas porque ela apareceu em uma aula.

A progressão esperada é:

```text
Não iniciado
↓
Exposto
↓
Praticado
↓
Consolidado
```

Uma competência PODE permanecer em `Praticado` por vários ciclos.

Isso é normal.

`Consolidado` deve ser raro e possuir evidência forte.

---

# Regra para Experiência Anterior

Experiência anterior deve ser preservada como contexto.

Por exemplo:

```text
Estado: Exposto
Evidência: utilizado anteriormente em pipeline HubSpot
```

Isso indica que o conceito não é completamente novo.

Porém, para avançar para `Consolidado` dentro deste programa, deve existir nova evidência que satisfaça os critérios da Constitution.

---

# Regra de Evidência

Sempre que possível, a evidência deve apontar para algo concreto.

Exemplos futuros:

```text
projects/01_file_collector/
tests/test_csv_discovery.py
benchmarks/filesystem_iteration.md
progress/ERRORS_AND_LESSONS.md#iterator-exhaustion
progress/DECISIONS.md#adr-003
```

Evitar evidências vagas como:

```text
"estudei"
"vi em aula"
"sei isso"
"já usei"
```

quando houver evidência melhor disponível.

---

# Regra de Consolidação

Antes de alterar uma competência para `Consolidado`, verificar:

### Prática

O aluno consegue aplicar?

### Explicação

O aluno consegue explicar?

### Transferência

O aluno consegue aplicar em contexto diferente?

### Debugging

O aluno consegue investigar quando não funciona?

### Trade-offs

O aluno consegue discutir alternativas?

### Limites

O aluno sabe quando NÃO utilizar?

Se essas condições não forem suficientemente demonstradas, manter como `Praticado`.

---

# Estado Inicial

Esta matriz representa o baseline inicial do programa.

Ela NÃO representa uma avaliação definitiva das competências profissionais do aluno.

Os estados iniciais registram:

* conhecimento prévio conhecido;
* exposição anterior;
* projetos anteriores;
* áreas que precisam ser formalmente validadas durante os 100 dias.

A partir do início do programa, novas mudanças de estado devem ser orientadas por evidência.

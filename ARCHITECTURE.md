# Arquitetura Evolutiva

## Objetivo

Este documento descreve uma possível evolução arquitetural dos projetos ao longo do programa.

Ele NÃO define uma arquitetura que deve ser implementada antecipadamente.

A arquitetura deve emergir de problemas observados durante o desenvolvimento.

A `.specify/memory/constitution.md` prevalece sobre este documento.

---

## Alvo Conceitual

Ao longo do programa, um sistema de dados poderá evoluir conceitualmente para algo semelhante a:

```text id="yfq4tx"
Source
  ↓
Collector
  ↓
CollectionResult
  ↓
Normalizer
  ↓
Validator
  ↓
Transformer
  ↓
Change Detection
  ↓
Storage
  ↓
Loader
  ↓
Destination
```

Aspectos transversais podem incluir:

```text id="jwyj8s"
Configuration
Logging
Metrics
Tracing
Retries
Contracts
Testing
Lineage
Security
Cost
```

Esse desenho representa um **mapa conceitual**, não uma arquitetura obrigatória.

Nem todo projeto precisará de todos esses componentes.

---

# Regra Fundamental

Não antecipar versões futuras apenas porque sabemos que elas podem existir.

A evolução deve seguir:

```text id="5ofvdu"
IMPLEMENTAR
↓
OBSERVAR
↓
IDENTIFICAR LIMITAÇÃO
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

Uma versão futura só deve ser introduzida quando existir necessidade pedagógica ou problema concreto que a justifique.

---

# Evolução Possível

## V0 — Funções Simples

Começar com funções responsáveis por operações concretas.

Exemplos conceituais:

```text id="i7q5s8"
discover_files()
read_csv()
read_json()
```

Objetivos:

* lógica;
* inputs e outputs;
* filesystem;
* I/O;
* exceptions;
* testes;
* medição.

Nenhuma arquitetura orientada a objetos é necessária nesta etapa.

---

## V1 — Responsabilidades e Variações

Adicionar novas fontes ou comportamentos através da solução mais simples possível.

Exemplo:

```text id="47yn36"
CSV
JSON
Excel
```

Observar:

* responsabilidades;
* repetição;
* diferenças;
* estado;
* comportamento;
* dependências.

A existência de vários formatos NÃO obriga a criação imediata de uma hierarquia de classes.

Primeiro implementar e observar.

---

## V2 — Objetos e Contratos, se Justificados

Quando funções começarem a apresentar necessidade real de:

* estado;
* encapsulamento;
* responsabilidades persistentes;
* colaboração entre componentes;

considerar objetos.

Quando múltiplas implementações precisarem ser utilizadas através do mesmo contrato, considerar uma interface comum.

A sequência deve ser:

```text id="e3aq0n"
VARIAÇÃO REAL
↓
PROBLEMA DE SUBSTITUIÇÃO OU ACOPLAMENTO
↓
NECESSIDADE DE CONTRATO
↓
ESCOLHA DO MECANISMO
```

O mecanismo pode ser:

```text id="1lql1i"
duck typing
Protocol
ABC
ou nenhuma abstração formal
```

A escolha deve ser justificada pelo problema.

---

## V3 — Resultados Estruturados

Quando retornos simples deixarem de representar adequadamente o resultado de uma coleta, considerar um resultado estruturado.

Conceitualmente:

```text id="unacds"
CollectionResult

data
metadata
source
records
bytes
elapsed
status
```

`CollectionResult` só deve existir se houver informação que justifique essa estrutura.

Pode ser representado por:

* estrutura simples;
* dataclass;
* classe;

dependendo das necessidades observadas.

---

## V4 — Validação e Transformação

Quando regras de validação e transformação crescerem, avaliar separação de responsabilidades.

Possíveis conceitos:

```text id="dsv25b"
Normalizer
Validator
Transformer
```

Esses nomes representam responsabilidades.

Não implicam obrigatoriamente uma classe para cada conceito.

Separar componentes quando isso melhorar:

* coesão;
* testes;
* clareza;
* substituição;
* manutenção.

---

## V5 — Storage e Loading

Quando persistência se tornar relevante, distinguir progressivamente:

```text id="pt73sz"
dados
↓
formato
↓
storage
↓
carregamento
↓
destino
```

Possíveis responsabilidades:

```text id="vs7fsc"
Storage
Loader
Destination
```

Evitar acoplar regras de transformação diretamente a detalhes de infraestrutura quando isso dificultar testes ou evolução.

---

## V6 — Processamento Incremental e Histórico

Quando o projeto exigir processamento incremental, introduzir conceitos conforme o problema:

```text id="tnj6w4"
Watermark
Incremental Loading
Change Detection
Upsert
CDC
SCD1
SCD2
```

Esses conceitos NÃO são equivalentes.

A arquitetura deve distinguir especialmente:

```text id="2lncy4"
CHANGE DETECTION
≠
CDC LOG-BASED
≠
TARGET HISTORY
```

Idempotência e recovery tornam-se requisitos centrais.

---

## V7 — HTTP Collectors e Composição

Quando fontes HTTP apresentarem variações reais, decompor responsabilidades quando necessário.

Possíveis componentes:

```text id="2wpnyr"
HTTP Client
Authentication
Pagination
Retry
Rate Limiting
Response Parsing
Error Handling
```

Preferir composição quando comportamentos independentes precisarem variar.

Patterns como:

```text id="o2hd8e"
Strategy
Adapter
Factory
```

só devem aparecer após existir um problema concreto que justifique sua utilização.

Não criar uma arquitetura de framework antes de possuir variações reais para suportar.

---

## V8 — Pipeline e Orquestração

Quando múltiplas etapas precisarem ser coordenadas, considerar uma camada de pipeline ou orquestração.

Conceitualmente:

```text id="53x8ck"
EXTRACT
↓
VALIDATE
↓
TRANSFORM
↓
DETECT CHANGES
↓
STORE / LOAD
↓
OBSERVE
```

Orquestração deve coordenar responsabilidades existentes.

Ela não deve conter toda a lógica do pipeline.

Ferramentas como Airflow devem ser introduzidas quando existir necessidade de:

* scheduling;
* dependencies;
* retries;
* backfills;
* observabilidade operacional;
* coordenação de múltiplas tarefas.

---

# Evolução de Software

Paralelamente à arquitetura de dados, a evolução de Python deve seguir aproximadamente:

```text id="zrsf3j"
FUNÇÕES
↓
RESPONSABILIDADES
↓
ESTADO
↓
OBJETOS
↓
ENCAPSULAMENTO
↓
COMPOSIÇÃO
↓
CONTRATOS
↓
POLIMORFISMO
↓
SOLID
↓
PATTERNS, QUANDO JUSTIFICADOS
↓
ARQUITETURA
```

As duas evoluções devem se encontrar naturalmente.

Por exemplo:

```text id="z3ekqp"
mais fontes
        ↓
mais variações
        ↓
responsabilidades diferentes
        ↓
necessidade de substituição
        ↓
contrato
        ↓
possível polimorfismo
```

e não:

```text id="17v58h"
"quero estudar Protocol"
        ↓
criar Protocol artificialmente
```

---

# Regra de Comparação

Quando uma abstração importante for introduzida pedagogicamente, preservar a capacidade de comparar:

```text id="6dd85e"
ANTES
vs
DEPOIS
```

Perguntar:

* qual problema existia antes?
* o que mudou?
* qual complexidade foi adicionada?
* qual complexidade foi removida?
* ficou mais testável?
* ficou menos acoplado?
* ficou mais fácil de modificar?
* a abstração realmente valeu a pena?

A versão mais abstrata NÃO é automaticamente a melhor.

---

# Regra de Reversibilidade

Arquitetura evolutiva também significa aceitar que uma abstração pode ser removida.

Se uma refatoração produzir:

```text id="3z2x13"
mais código
+
mais conceitos
+
mais indireção
```

sem benefício proporcional, considerar retornar à solução simples.

---

# Regra Final

O objetivo não é chegar obrigatoriamente à V8.

O objetivo é compreender **por que cada evolução poderia ser necessária**.

Um projeto pode corretamente permanecer em:

```text id="y0kkn6"
V2
```

se seus requisitos não justificarem V3–V8.

O sucesso não é:

> "implementei toda a arquitetura."

O sucesso é conseguir responder:

> "qual problema arquitetural estou resolvendo, por que esta estrutura é necessária e qual é a solução mais simples que atende aos requisitos atuais?"

# Python Standards

## Objetivo

Este documento define os padrões de Python utilizados durante o programa Data Engineering — 100 Days.

O objetivo não é aplicar todas as regras desde o primeiro dia.

Os padrões DEVEM ser introduzidos progressivamente conforme os conceitos correspondentes forem estudados e os problemas surgirem nos projetos.

A prioridade é:

```text
CORREÇÃO
↓
CLAREZA
↓
TESTABILIDADE
↓
MANUTENIBILIDADE
↓
PERFORMANCE MEDIDA
↓
ABSTRAÇÃO JUSTIFICADA
```

Este documento está subordinado à `constitution.md`.

---

# 1. Princípios Gerais

Código Python produzido durante o programa DEVE evoluir para ser:

* correto;
* legível;
* explícito;
* testável;
* observável;
* tipado quando relevante;
* modular;
* previsível;
* simples de modificar;
* adequado ao volume de dados esperado.

O código NÃO DEVE buscar sofisticação arquitetural como objetivo.

Preferir:

```text
SIMPLES E CORRETO
```

antes de:

```text
ABSTRATO E SOFISTICADO
```

---

# 2. PEPs Prioritárias

As PEPs prioritárias do programa são:

| PEP     | Tema                 | Objetivo no programa                            |
| ------- | -------------------- | ----------------------------------------------- |
| PEP 8   | Style Guide          | Legibilidade e consistência                     |
| PEP 257 | Docstrings           | Documentação de interfaces                      |
| PEP 484 | Type Hints           | Contratos através de tipos                      |
| PEP 526 | Variable Annotations | Tipagem de variáveis e atributos                |
| PEP 544 | Protocols            | Structural subtyping e contratos                |
| PEP 557 | Data Classes         | Modelagem de objetos predominantemente de dados |

Outras PEPs PODEM ser adicionadas quando conceitos correspondentes surgirem.

PEPs NÃO DEVEM ser estudadas apenas por memorização.

Para cada PEP introduzida, compreender:

1. qual problema aborda;
2. por que existe;
3. como aparece no código;
4. quando utilizar;
5. quando não é relevante;
6. quais decisões influencia.

---

# 3. Progressão

Os padrões Python devem acompanhar a evolução do programa.

```text
LÓGICA
↓
FUNÇÕES
↓
MÓDULOS
↓
EXCEPTIONS
↓
ITERADORES / GENERATORS
↓
TYPE HINTS
↓
TESTES
↓
CLASSES
↓
ENCAPSULAMENTO
↓
DATACLASSES
↓
COMPOSIÇÃO
↓
INTERFACES
↓
PROTOCOL / ABC
↓
SOLID
↓
PATTERNS
↓
ARQUITETURA
```

Conceitos posteriores NÃO DEVEM ser utilizados para esconder fundamentos que ainda estão sendo estudados.

---

# 4. PEP 8 — Estilo e Legibilidade

PEP 8 deve orientar progressivamente o estilo do código.

Aplicar especialmente:

* nomes claros;
* indentação consistente;
* organização de imports;
* espaços adequados;
* tamanho e organização razoável de funções;
* convenções de nomenclatura.

Convenções principais:

```text
variáveis           snake_case
funções             snake_case
métodos             snake_case
classes             PascalCase
constantes          UPPER_CASE
módulos             snake_case
```

Nomes DEVEM expressar intenção.

Evitar nomes genéricos quando houver alternativa clara:

```python
x
data
obj
temp
thing
```

Isso NÃO significa que nomes curtos sejam sempre incorretos.

Variáveis locais com contexto evidente podem possuir nomes simples.

Legibilidade deve ser avaliada pelo contexto.

---

# 5. Funções

Funções devem possuir responsabilidade compreensível.

Uma função DEVE permitir responder:

> O que esta função faz?

sem exigir uma explicação longa contendo várias responsabilidades independentes.

Preferir funções:

* coesas;
* previsíveis;
* com inputs claros;
* com outputs claros;
* com efeitos colaterais explícitos.

Evitar misturar desnecessariamente:

```text
LER
+
TRANSFORMAR
+
VALIDAR
+
SALVAR
+
LOGAR DECISÕES DE NEGÓCIO
```

em uma única função.

Entretanto, funções NÃO DEVEM ser fragmentadas artificialmente apenas para reduzir quantidade de linhas.

Quantidade de linhas não determina responsabilidade.

---

# 6. Inputs e Outputs

Interfaces públicas devem possuir inputs e outputs compreensíveis.

Preferir contratos explícitos.

Exemplo conceitual:

```text
INPUT
Path

PROCESSAMENTO
descobrir arquivos CSV

OUTPUT
coleção de Path
```

Antes de implementar uma função, identificar:

* input;
* output;
* efeitos colaterais;
* possíveis erros.

Funções puras devem ser consideradas quando fizerem sentido, pois normalmente facilitam testes.

Nem toda função precisa ser pura.

Operações de Engenharia de Dados frequentemente possuem I/O por natureza.

---

# 7. Type Hints

Type hints devem ser introduzidos progressivamente.

Interfaces públicas DEVEM evoluir para possuir tipagem explícita.

Exemplo:

```python
def collect_csv(path: Path) -> list[Path]:
    ...
```

Typing deve comunicar contratos.

O objetivo NÃO é apenas satisfazer um type checker.

Ao utilizar typing, perguntar:

* O input esperado está claro?
* O retorno está claro?
* `None` é possível?
* Existem diferentes tipos possíveis?
* O contrato está mais compreensível?

Evitar tipos excessivamente genéricos quando informações melhores estiverem disponíveis.

Por exemplo:

```python
Any
```

NÃO DEVE ser utilizado automaticamente para eliminar dificuldades de tipagem.

---

# 8. Variable Annotations

PEP 526 deve ser aplicada quando annotations melhorarem compreensão ou contrato.

Exemplo:

```python
files: list[Path] = []
```

Annotations não precisam ser adicionadas a toda variável local quando o tipo for evidente.

Preferir informação útil a ruído.

---

# 9. Docstrings

PEP 257 deve orientar documentação de:

* módulos relevantes;
* classes públicas;
* funções públicas;
* métodos públicos.

Docstrings devem explicar principalmente:

* propósito;
* parâmetros quando não forem evidentes;
* retorno;
* exceptions relevantes;
* comportamento importante.

Docstrings NÃO DEVEM simplesmente repetir o código.

Evitar:

```python
def collect_files():
    """Collect files."""
```

quando isso não adiciona informação.

Comentários e docstrings devem explicar principalmente:

```text
POR QUÊ
```

quando o:

```text
O QUÊ
```

já estiver claro no código.

---

# 10. Exceptions

Exceptions devem representar falhas significativas.

Preferir exceptions específicas a erros genéricos.

O código deve progressivamente distinguir problemas como:

```text
entrada inválida
arquivo inexistente
diretório inválido
falha de parsing
schema inválido
falha HTTP
timeout
falha de persistência
```

Não utilizar:

```python
except Exception:
    pass
```

para esconder falhas.

Capturar exceptions apenas quando houver motivo para:

* adicionar contexto;
* recuperar;
* converter para erro de domínio;
* realizar retry;
* liberar recursos;
* registrar informação útil.

Falhas devem permanecer diagnosticáveis.

---

# 11. Filesystem

Utilizar preferencialmente:

```python
pathlib.Path
```

para operações modernas de filesystem.

Conceitos fundamentais incluem:

* paths;
* arquivos;
* diretórios;
* extensão;
* metadata;
* existência;
* navegação;
* leitura;
* escrita.

Antes de ler conteúdo, verificar se metadata é suficiente.

Distinguir:

```text
DESCOBRIR UM ARQUIVO
```

de:

```text
LER O CONTEÚDO DO ARQUIVO
```

pois possuem custos de I/O diferentes.

---

# 12. Iterables, Iterators e Generators

O aluno deve compreender progressivamente:

```text
iterable
≠
iterator
≠
generator
≠
materialized collection
```

Antes de converter um iterable para:

```python
list(...)
```

perguntar se materialização é necessária.

Avaliar:

* memória;
* quantidade de elementos;
* necessidade de múltiplas iterações;
* processamento streaming;
* legibilidade.

Generators devem ser utilizados quando resolverem um problema concreto.

Não devem ser introduzidos apenas porque parecem mais eficientes.

---

# 13. Classes

Classes devem representar responsabilidades, estado ou comportamento coerente.

Uma classe NÃO DEVE existir apenas para agrupar funções.

Antes de criar uma classe, responder:

1. O que ela representa?
2. Qual responsabilidade possui?
3. Qual estado mantém?
4. Quais comportamentos pertencem a esse estado?
5. Por que funções deixaram de ser suficientes?
6. Quais dependências possui?
7. Como será testada?

Preferir funções enquanto elas forem suficientes.

---

# 14. Encapsulamento

Encapsulamento deve proteger responsabilidades e invariantes.

Não deve ser reduzido à ideia de atributos privados.

O aluno deve compreender:

* estado interno;
* interface pública;
* invariantes;
* comportamento;
* detalhes de implementação.

Convenções como:

```python
_internal_value
```

e propriedades devem ser utilizadas quando houver justificativa.

---

# 15. Dataclasses

PEP 557 deve ser utilizada quando objetos forem predominantemente estruturas de dados.

Antes de utilizar `@dataclass`, perguntar:

> Estou representando dados ou comportamento complexo?

Casos possíveis:

* configurações;
* DTOs;
* metadata;
* resultados estruturados;
* value objects simples.

`dataclass` NÃO é substituto automático para classes tradicionais.

---

# 16. Composition Before Inheritance

Composição deve ser considerada antes de herança.

Preferir conceitualmente:

```text
A POSSUI B
```

quando essa for a relação real.

Herança deve representar uma relação de substituição coerente.

Antes de utilizar herança:

* identificar a relação entre tipos;
* avaliar substituição;
* avaliar acoplamento;
* considerar composição;
* avaliar testabilidade.

Herança NÃO deve ser utilizada apenas para evitar duplicação.

---

# 17. ABC, Protocol e Duck Typing

Esses mecanismos representam formas diferentes de estabelecer contratos.

O aluno deve aprender a distinguir:

```text
duck typing
ABC
Protocol
nenhuma abstração formal
```

`ABC` deve ser considerada quando existir uma abstração nominal justificável.

`Protocol`, baseado na PEP 544, deve ser considerado quando structural typing resolver um problema concreto.

Protocol NÃO deve ser criado automaticamente para toda dependência.

Primeiro identificar a necessidade de contrato.

Depois escolher o mecanismo.

---

# 18. SOLID

SOLID deve ser aprendido através de problemas observados no código.

```text
S — Single Responsibility Principle
O — Open/Closed Principle
L — Liskov Substitution Principle
I — Interface Segregation Principle
D — Dependency Inversion Principle
```

A sequência preferencial é:

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

SOLID NÃO é checklist obrigatório.

Uma solução simples pode ser melhor do que uma arquitetura que aplica mecanicamente todos os princípios.

---

# 19. Dependency Inversion e Dependency Injection

Os conceitos NÃO são sinônimos.

Dependency Inversion é um princípio de design.

Dependency Injection é uma possível técnica de fornecimento de dependências.

O aluno deve aprender a diferenciar:

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

Frameworks de Dependency Injection não devem ser introduzidos quando passagem explícita de dependências for suficiente.

---

# 20. Design Patterns

Patterns devem possuir motivação concreta.

Possíveis patterns que podem surgir durante o programa:

* Strategy;
* Adapter;
* Factory;
* Repository;
* Template Method;
* Facade;
* Builder.

A presença nesta lista NÃO significa que devem ser utilizados.

Antes de aplicar um pattern:

```text
PROBLEMA
↓
SOLUÇÃO SIMPLES
↓
LIMITAÇÃO OBSERVADA
↓
PATTERN CANDIDATO
↓
REFATORAÇÃO
↓
COMPARAÇÃO
```

O aluno deve conseguir explicar o problema resolvido sem depender do nome do pattern.

---

# 21. Logging

`print()` pode ser utilizado em exercícios iniciais para aprendizado.

Pipelines devem evoluir para logging.

Logs devem fornecer contexto operacional útil.

Possíveis informações:

```text
pipeline
step
source
records
bytes
elapsed
status
error
attempt
```

Evitar logs sem contexto.

Exemplo conceitualmente fraco:

```text
Error occurred
```

Preferir informação suficiente para investigação.

Secrets e dados sensíveis NÃO devem ser registrados.

---

# 22. Configuration

Configuração deve ser separada de regras de negócio quando a complexidade justificar.

Possíveis configurações:

* paths;
* URLs;
* timeouts;
* batch sizes;
* environment;
* feature flags;
* parâmetros de execução.

Valores específicos de ambiente não devem ficar espalhados pelo código.

Não criar sistemas complexos de configuração antes da necessidade.

---

# 23. Secrets

Secrets NÃO devem ser commitados.

Exemplos:

* passwords;
* API keys;
* client secrets;
* tokens;
* connection strings contendo credenciais.

Ambientes locais podem utilizar environment variables ou `.env` ignorado pelo Git.

Ambientes reais devem utilizar mecanismos adequados de gerenciamento de secrets.

---

# 24. Testing

Testes devem verificar comportamento.

Priorizar perguntas como:

> Dado determinado input, qual comportamento espero?

Testar progressivamente:

* happy path;
* edge cases;
* entradas inválidas;
* exceptions;
* comportamento repetido;
* idempotência quando aplicável;
* falhas parciais quando aplicável.

Evitar testes excessivamente acoplados à implementação interna.

Refatoração interna não deveria quebrar testes se o comportamento público continuar correto.

---

# 25. I/O

Código de Engenharia de Dados deve tornar operações de I/O compreensíveis.

Identificar:

```text
READ
WRITE
NETWORK
DATABASE
OBJECT STORAGE
MEMORY MATERIALIZATION
```

Quando relevante, medir:

```text
bytes_read
bytes_written
rows_read
rows_written
elapsed_seconds
throughput_mb_s
peak_memory_mb
```

Não assumir que determinada implementação é mais rápida sem medição.

---

# 26. Performance

A ordem padrão é:

```text
CORREÇÃO
↓
TESTE
↓
BASELINE
↓
MEDIÇÃO
↓
GARGALO
↓
HIPÓTESE
↓
OTIMIZAÇÃO
↓
NOVA MEDIÇÃO
```

Evitar micro-otimizações sem impacto demonstrável.

Em Engenharia de Dados, considerar especialmente:

* I/O;
* serialização;
* parsing;
* network;
* memory;
* database operations;
* materialização;
* quantidade de requests.

---

# 27. Public Interfaces

Interfaces públicas devem ser pequenas, compreensíveis e estáveis quando possível.

Ao projetar uma interface, perguntar:

* O consumidor precisa conhecer detalhes internos?
* Os parâmetros expressam intenção?
* O retorno é previsível?
* Os erros são compreensíveis?
* A implementação pode mudar sem quebrar o consumidor?

Interfaces devem esconder detalhes apenas quando essa ocultação reduz acoplamento real.

---

# 28. Imports e Dependencies

Imports devem tornar dependências compreensíveis.

Evitar dependências circulares.

Bibliotecas externas devem ser adicionadas quando resolverem um problema concreto.

Antes de adicionar uma dependência, considerar:

* problema resolvido;
* manutenção;
* maturidade;
* custo operacional;
* segurança;
* peso;
* alternativas da standard library.

A standard library deve ser considerada quando for suficiente.

---

# 29. Refactoring

Refatoração deve preservar comportamento observável.

Preferencialmente:

```text
CÓDIGO FUNCIONANDO
↓
TESTES
↓
PROBLEMA IDENTIFICADO
↓
REFATORAÇÃO
↓
TESTES
↓
COMPARAÇÃO
```

Não refatorar apenas porque existe uma forma mais sofisticada de escrever o mesmo código.

Refatorações relevantes devem possuir motivação.

---

# 30. Definition of Good Python

Durante este programa, "bom Python" NÃO significa:

```text
mais classes
mais patterns
mais abstrações
menos linhas
mais bibliotecas
código mais inteligente
```

Bom Python significa, no contexto do problema:

```text
CORRETO
+
CLARO
+
TESTÁVEL
+
OBSERVÁVEL
+
MANUTENÍVEL
+
ADEQUADO AO VOLUME
+
COM COMPLEXIDADE JUSTIFICADA
```

A melhor implementação pode ser:

* uma função;
* um generator;
* uma dataclass;
* uma classe;
* uma composição de objetos;
* uma interface;
* ou nenhuma abstração adicional.

A decisão deve decorrer do problema.

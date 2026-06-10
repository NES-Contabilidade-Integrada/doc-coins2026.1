# Documentação do Modelo de Dados – Sistema COIN'S

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 27/09 | Criação do documento com introdução, DER e script | Fernanda Pessoa |
| 1.1 | 22/10 | Pequena correção no atributo parent\_classification | Pedro Nicoletti Sotoma |
| 1.2 | 06/05 | Atualização do modelo: novas tabelas (account\_types, actors, apuracoes), renomeação de tabelas e novos campos | Fernanda Pessoa |
| 2.0 | 01/06/2026 | Reconciliação com as migrations reais da branch develop: DBML corrigido com nomes e tipos reais, tabelas dre\_groups e dre\_group\_account\_roots adicionadas, divergências da v1.2 documentadas | Lohan Toledo Tosta |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | 29/09 | Pedro Nicoletti Sotoma | Aprovada |
| 2.0 | — | — | Pendente de revisão |

**Sumário**

[1\. Introdução 	1](#introdução)

[2\. DER (Diagrama entidade relacionamento)	2](#der-\(diagrama-entidade-relacionamento\))

[3\. Script para criação das tabelas	2](#script-para-criação-das-tabelas)

[**4\. Regras de Negócio no Modelo	2**](#regras-de-negócio-no-modelo)

## Introdução {#introdução}
O banco de dados do Sistema COIN'S foi desenvolvido para dar suporte ao gerenciamento de informações contábeis de empresas.

> **Nota (v2.0 — Reconciliação com as migrations reais):**
>
> A versão 1.2 deste documento descrevia 7 tabelas de negócio com base em um modelo planejado. A análise das migrations efetivamente implementadas na branch `develop` revelou divergências significativas entre documentação e código:
>
> | Divergência | v1.2 (documentado) | v2.0 (implementado) |
> | :--- | :--- | :--- |
> | Nome da tabela de apurações | `apuracoes` | `apuration` |
> | Campo de data | `data_apuracao` | `apuration_date` |
> | Campo de tipo | `tipo` | `type` |
> | Campo de valor | `valor` | `amount` |
> | Campo de conta destino | `conta_destino_id` | `destination_account_id` |
> | Valores aceitos em `type` | 1 ou 2 | 1 (Lucro), 2 (Prejuízo) ou **3 (Resultado Nulo)** |
> | `destination_account_id` | NOT NULL | **Nullable** (quando `type = 3`) |
> | Tabelas não documentadas | — | `dre_groups`, `dre_group_account_roots` |
> | `account_types` (valores seed) | não especificado | 8 tipos definidos na migration |
> | `actors` (valores seed) | não especificado | 2 atores: Usuário e Sistema de Apuração |
>
> O DBML desta seção foi reescrito para refletir o schema **real e atual** da branch `develop`.

Sua estrutura atual é composta por nove tabelas de negócio:

- **account\_types:** cadastro dos tipos de conta contábil (ex: Ativo, Passivo, Receita). Pré-populada com 8 tipos via migration.
- **actors:** cadastro dos atores responsáveis pelos lançamentos. Pré-populada com 2 atores via migration.
- **chart\_of\_account:** armazena os dados do Plano de Contas, incluindo hierarquia, tipo contábil e identificação de contas analíticas e sintéticas.
- **company:** armazena as empresas cadastradas, incluindo informações básicas de identificação.
- **apuration:** registra apurações contábeis vinculadas a contas de destino (resultado nulo não possui conta destino).
- **journal\_entry**: registra os lançamentos contábeis realizados por cada empresa, com rastreabilidade do ator responsável.
- **journal\_entry\_line**: detalha as partidas de cada lançamento, indicando valores de débito e crédito.
- **dre\_groups:** define os grupos da Demonstração do Resultado do Exercício (DRE). Pré-populado com 11 grupos via migration.
- **dre\_group\_account\_roots:** associa contas raiz do Plano de Contas a grupos de DRE.

## Diagrama ER (Diagrama de relacionamento de entidade) 

![Diagrama ERD do Sistema COIN'S](assets/Diagrama%20ERD.png)

### 3.1 DBML Atual (v2.0 — estado real da branch develop)

O DBML abaixo representa o schema **implementado nas migrations** da branch `develop`. É o estado real do banco de dados ao rodar a aplicação.

```dbml
// ---- account_types ----
// Seed: 8 tipos pré-populados (Ativo, Passivo, Patrimônio Líquido,
//       Resultado-Receita, Resultado-Custo/Despesa, ARE, Lucros Ac., Prejuízos Ac.)
Table account_types {
  id        integer [pk]
  descricao text    [not null, unique]
}

// ---- actors ----
// Seed: 1=Usuário, 2=Sistema de Apuração
Table actors {
  id        integer [pk]
  descricao text    [not null, unique]
}

// ---- company ----
Table company {
  id         text      [pk]
  name       text      [not null]
  cnpj       text      [not null, unique]
  created_at timestamp [default: `CURRENT_TIMESTAMP`]
  updated_at timestamp [default: `CURRENT_TIMESTAMP`]

  Indexes {
    (cnpj) [name: 'idx_company_cnpj']
    (name) [name: 'idx_company_name']
  }
}

// ---- chart_of_account ----
// account_type_id adicionado na migration add_apuration e populado automaticamente
// com base na classificação hierárquica da conta.
Table chart_of_account {
  id                    text      [pk]
  code                  text      [not null, unique]
  classification        text      [not null, unique]
  description           text      [not null]
  is_analytic           boolean   [not null, default: false, note: 'true=Analítica | false=Sintética']
  created_at            timestamp [default: `CURRENT_TIMESTAMP`]
  updated_at            timestamp [default: `CURRENT_TIMESTAMP`]
  parent_classification text      [ref: > chart_of_account.classification]
  account_type_id       integer   [null, ref: > account_types.id]

  Indexes {
    (code)            [name: 'idx_chart_of_account_code']
    (account_type_id) [name: 'idx_chart_of_account_account_type_id']
  }
}

// ---- apuration ----
// ATENÇÃO: documentada na v1.2 como "apuracoes" com campos em português.
// O nome real da tabela é "apuration" com campos em inglês.
// destination_account_id é nullable: type=3 (Resultado Nulo) não possui conta destino.
// type aceita: 1=Lucro, 2=Prejuízo, 3=Resultado Nulo
Table apuration {
  id                     text        [pk]
  created_at             datetime    [default: `CURRENT_TIMESTAMP`]
  apuration_date         date        [not null]
  type                   integer     [not null, note: 'CHECK: IN (1, 2, 3) — 1=Lucro, 2=Prejuízo, 3=Nulo']
  amount                 decimal(14,2) [not null]
  destination_account_id text        [null, ref: > chart_of_account.id, note: 'Nullable quando type=3']

  Indexes {
    (apuration_date)        [name: 'idx_apuration_apuration_date']
    (type)                  [name: 'idx_apuration_type']
    (destination_account_id)[name: 'idx_apuration_destination_account_id']
  }
}

// ---- journal_entry ----
// actor_id: NOT NULL — lançamentos manuais usam 1 (Usuário), apurações usam 2 (Sistema)
// description: nullable no banco, mas obrigatório na camada de aplicação (HTTP 400 se ausente)
Table journal_entry {
  id           text          [pk]
  company_id   text          [not null, ref: > company.id]
  description  text          [note: 'Nullable no DB; obrigatório na aplicação']
  amount       decimal(14,2) [not null, note: 'CHECK: > 0']
  is_compound  integer       [not null, default: 0, note: '1=composto | 0=simples']
  created_at   timestamp     [default: `CURRENT_TIMESTAMP`]
  updated_at   timestamp     [default: `CURRENT_TIMESTAMP`]
  actor_id     integer       [not null, ref: > actors.id]
  apuration_id integer       [null, ref: > apuration.id]

  Indexes {
    (company_id) [name: 'idx_journal_company']
  }
}

// ---- journal_entry_line ----
Table journal_entry_line {
  id               text          [pk]
  journal_entry_id text          [not null, ref: > journal_entry.id]
  account_code     text          [not null, ref: > chart_of_account.id]
  entry_type       varchar       [not null, note: "D=Débito | C=Crédito"]
  amount           decimal(14,2) [not null, note: '> 0']
  created_at       timestamp     [default: `CURRENT_TIMESTAMP`]

  Indexes {
    (journal_entry_id) [name: 'idx_jel_entry']
  }
}

// ---- dre_groups ----
// Não documentada na v1.2. Armazena os grupos da DRE.
// Seed: 11 grupos pré-populados (gross_revenue, revenue_deductions, cmv_cpv, etc.)
Table dre_groups {
  id         text      [pk, note: 'Slug textual, ex: gross_revenue']
  key        text      [not null, unique]
  title      text      [not null]
  nature     text      [not null, note: "CHECK: IN ('revenue', 'expense', 'mixed')"]
  created_at timestamp [default: `CURRENT_TIMESTAMP`]
  updated_at timestamp [default: `CURRENT_TIMESTAMP`]

  Indexes {
    (key) [name: 'idx_dre_groups_key']
  }
}

// ---- dre_group_account_roots ----
// Não documentada na v1.2. Associa contas raiz do Plano de Contas a grupos de DRE.
Table dre_group_account_roots {
  id                   integer   [pk, increment]
  dre_group_id         text      [not null, ref: > dre_groups.id]
  chart_of_account_id  text      [not null, ref: > chart_of_account.id]
  include_descendants  boolean   [not null, default: true]
  created_at           timestamp [default: `CURRENT_TIMESTAMP`]
  updated_at           timestamp [default: `CURRENT_TIMESTAMP`]

  Indexes {
    (dre_group_id)        [name: 'idx_dre_group_account_roots_group']
    (chart_of_account_id) [name: 'idx_dre_group_account_roots_account']
  }
}
```

### 3.2 DBML Histórico (v1.2 — modelo planejado original)

O DBML abaixo é preservado para referência histórica. Ele reflete o modelo pretendido na v1.2 e **não corresponde ao schema implementado** — ver tabela de divergências na Introdução.

```dbml
// ---- account_types ----
Table account_types {
  id        integer [pk]
  descricao text    [not null, unique]
}

// ---- actors ----
Table actors {
  id        integer [pk]
  descricao text    [not null, unique]
}

// ---- company ----
Table company {
  id         text      [pk]
  name       text      [not null]
  cnpj       text      [not null, unique]
  created_at timestamp [default: `CURRENT_TIMESTAMP`]
  updated_at timestamp [default: `CURRENT_TIMESTAMP`]

  Indexes {
    (cnpj) [name: 'idx_company_cnpj']
    (name) [name: 'idx_company_name']
  }
}

// ---- chart_of_account ----
Table chart_of_account {
  id                    text      [pk]
  code                  text      [not null, unique]
  classification        text      [not null, unique]
  description           text      [not null]
  is_analytic           boolean   [not null, default: false, note: 'true=Analítica | false=Sintética']
  created_at            timestamp [default: `CURRENT_TIMESTAMP`]
  updated_at            timestamp [default: `CURRENT_TIMESTAMP`]
  parent_classification text      [ref: > chart_of_account.classification]
  account_type_id       integer   [null, ref: > account_types.id]

  Indexes {
    (code)            [name: 'idx_chart_of_account_code']
    (account_type_id) [name: 'idx_chart_of_account_account_type_id']
  }
}

// ---- apuracoes ----
Table apuracoes {
  id               text     [pk]
  created_at       datetime [default: `CURRENT_TIMESTAMP`]
  data_apuracao    date     [not null]
  tipo             integer  [not null, note: 'CHECK: IN (1, 2)']
  valor            float    [not null]
  conta_destino_id text     [not null, ref: > chart_of_account.id]

  Indexes {
    (data_apuracao)    [name: 'idx_apuracoes_data_apuracao']
    (tipo)             [name: 'idx_apuracoes_tipo']
    (conta_destino_id) [name: 'idx_apuracoes_conta_destino_id']
  }
}

// ---- journal_entry ----
Table journal_entry {
  id            text      [pk]
  company_id    text      [not null, ref: > company.id]
  description   text
  amount        float     [not null, note: 'CHECK: > 0']
  is_compound   integer   [not null, default: 0, note: '1=composto | 0=simples']
  created_at    timestamp [default: `CURRENT_TIMESTAMP`]
  updated_at    timestamp [default: `CURRENT_TIMESTAMP`]
  actor_id      integer   [not null, ref: > actors.id]
  apuration_id  integer   [null, ref: > apuracoes.id]

  Indexes {
    (company_id) [name: 'idx_journal_company']
  }
}

// ---- journal_entry_line ----
Table journal_entry_line {
  id               text      [pk]
  journal_entry_id text      [not null, ref: > journal_entry.id]
  account_code     text      [not null, ref: > chart_of_account.id]
  entry_type       varchar   [not null, note: "D=Débito | C=Crédito"]
  amount           float     [not null, note: '> 0']
  created_at       timestamp [default: `CURRENT_TIMESTAMP`]

  Indexes {
    (journal_entry_id) [name: 'idx_jel_entry']
  }
}
```

## Regras de Negócio no Modelo {#regras-de-negócio-no-modelo}
O modelo de dados incorpora regras de negócio diretamente na estrutura das tabelas, por meio de restrições (CHECK) e chaves estrangeiras (FKs).

*  **is\_compound** (tabela journal\_entry)

  Tipo: inteiro com restrição CHECK (is\_compound IN (0,1)).

  Finalidade: define se um lançamento contábil é simples (0) ou composto (1).

  Relevância: garante que cada lançamento seja classificado corretamente, evitando ambiguidades entre partidas únicas e múltiplas.

*  **amount** (tabela journal\_entry)

  Tipo: DECIMAL(14,2) com restrição CHECK (amount \> 0).

  Finalidade: assegura que o valor total de um lançamento seja sempre positivo.

  Relevância: impede o registro de lançamentos com valor zero ou negativo, mantendo a integridade dos dados contábeis.

*  **entry\_type** (tabela journal\_entry\_line)

  Tipo: texto com restrição CHECK (entry\_type IN ('D','C')).  
  Finalidade: define se a linha de lançamento é um débito (D) ou um crédito (C).  
  Relevância: mantém a consistência contábil, evitando registros inválidos.

*  **is\_analytic** (tabela chart\_of\_account)

  Tipo: boolean.

  Finalidade: distingue se a conta é analítica (true) — usada para lançamentos diretos — ou sintética (false) — usada apenas para agrupar contas.

  Relevância: garante que lançamentos só possam ser feitos em contas analíticas, respeitando a estrutura hierárquica do plano de contas.

* **parent\_classification** (tabela chart\_of\_account)

  Tipo: chave estrangeira autorrelacional (parent\_classification → chart\_of\_account.classification).

  Finalidade: estabelece hierarquia de contas, permitindo que contas tenham subcontas.

  Relevância: reflete a forma como a contabilidade organiza contas sintéticas e analíticas.

* **description** (tabela journal\_entry) — *regra de aplicação, não de banco*

  Tipo: texto nullable no banco de dados.

  Finalidade: registrar o histórico/observação do lançamento contábil.

  Relevância: embora o banco permita `NULL`, a camada de aplicação (Service + Controller) torna este campo **obrigatório** — HTTP 400 se ausente. A restrição vive exclusivamente em código.

* **type** (tabela apuration)

  Tipo: inteiro com restrição CHECK (type IN (1, 2, 3)).

  Finalidade: classifica a apuração em Lucro (1), Prejuízo (2) ou Resultado Nulo (3).

  Relevância: garante consistência nos dados de fechamento contábil. O valor 3 foi adicionado para suportar o caso de resultado zero, que não possui conta de destino.

* **destination\_account\_id** (tabela apuration)

  Tipo: chave estrangeira nullable.

  Finalidade: aponta a conta contábil de destino da transferência de resultado.

  Relevância: é `NULL` quando `type = 3` (resultado nulo), pois não há conta de destino a debitar/creditar.

* **nature** (tabela dre\_groups)

  Tipo: texto com restrição CHECK (nature IN ('revenue', 'expense', 'mixed')).

  Finalidade: classifica o grupo de DRE como de receita, despesa ou misto.

  Relevância: direciona o sinal e a posição do grupo na Demonstração do Resultado do Exercício.

* **include\_descendants** (tabela dre\_group\_account\_roots)

  Tipo: boolean, padrão true.

  Finalidade: define se as contas filhas da conta raiz também pertencem ao grupo de DRE.

  Relevância: evita a necessidade de mapear cada conta analítica individualmente — a conta raiz sintética representa toda a sua árvore.

[image1]: <data:image/png;base64,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>
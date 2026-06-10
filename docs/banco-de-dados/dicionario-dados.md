# Dicionário de Dados

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 19/08 | Criação inicial do documento de Dicionário de Dados  | Fernanda Pessoa |
| 1.1 | 22/10 | Pequenas correções de definições de atributos | Pedro Nicoletti Sotoma |
| 1.2 | 06/05 | Atualização do esquema: novas tabelas account\_types, actors e apuracoes; renomeação de tabelas; novos campos | Fernanda Pessoa |
| 2.0 | 01/06/2026 | Reconciliação com as migrations reais da branch develop: documentação das tabelas implementadas, correção de nomes e campos divergentes, adição das tabelas dre\_groups e dre\_group\_account\_roots; nota sobre estado da branch main | Claude (revisão técnica automatizada) |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.1 | 09/11 | Fernanda Pessoa | Aprovada |
| 2.0 | — | — | Pendente de revisão |

**Sumário**

[1\. Introdução	2](#introdução)

[2\. Estrutura de Tabelas	2](#estrutura-de-tabelas)

[3\. Relacionamentos entre Tabelas	6](#relacionamentos-entre-tabelas)

## Introdução {#introdução}
O banco de dados do Sistema COIN'S (Contabilidade Integrada) foi desenvolvido para gerenciar informações contábeis de empresas, permitindo o registro de lançamentos no Livro Diário e Livro Razão.

> **Nota (v2.0 — Reconciliação com as migrations reais):**
>
> Este documento foi atualizado com base nas migrations presentes na **branch `develop`** (`my-app/main/migrations/`). A v1.2 descrevia 7 tabelas de negócio, mas divergia da implementação real em múltiplos pontos. A seguir, um resumo do estado atual:
>
> **Branch `main`** (4 migrations antigas, em processo de substituição pela baseline):
> Apenas `chart_of_account`, `company`, `journal_entry` e `journal_entry_line` existem.
>
> **Branch `develop`** (5 migrations novas, baseline + evoluções):
> Schema completo com **9 tabelas implementadas**, conforme descrito nas seções abaixo.
>
> **Divergências encontradas entre a v1.2 e a implementação real:**
> - A tabela documentada como `apuracoes` foi implementada com o nome **`apuration`**
> - Os campos da tabela foram renomeados (ex: `data_apuracao` → `apuration_date`, `tipo` → `type`, `valor` → `amount`, `conta_destino_id` → `destination_account_id`)
> - `apuration.type` aceita os valores 1 (Lucro), 2 (Prejuízo) e **3 (Nulo)** — a v1.2 documentava apenas 1 e 2
> - `apuration.destination_account_id` é **nullable** — a v1.2 documentava como NOT NULL
> - `account_types` foi criada com **8 tipos** seed (a v1.2 não especificava os valores)
> - `actors` foi criada com **2 atores** seed (Usuário e Sistema de Apuração)
> - Duas tabelas completamente novas, **não documentadas na v1.2**: `dre_groups` e `dre_group_account_roots`
>
> Além das tabelas de infraestrutura (`knex_migrations`, `knex_migrations_lock`, `app_data_migrations`), não há outras tabelas implementadas.

## Estrutura de Tabelas {#estrutura-de-tabelas}

---

Tabela: account\_types

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | INTEGER | Não | PK | \- | Identificador único do tipo de conta. |
| descricao | TEXT | Não | Único | \- | Descrição do tipo de conta. |

Valores pré-populados (seed):

| id | descricao |
| :---: | :--- |
| 1 | Ativo |
| 2 | Passivo |
| 3 | Patrimônio Líquido |
| 4 | Resultado - Receita |
| 5 | Resultado - Custo e Despesa |
| 6 | Apuração do Resultado do Exercício (ARE) |
| 7 | Lucros Acumulados |
| 8 | Prejuízos Acumulados |

---

Tabela: actors

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | INTEGER | Não | PK | \- | Identificador único do ator. |
| descricao | TEXT | Não | Único | \- | Descrição do ator responsável pelos lançamentos. |

Valores pré-populados (seed):

| id | descricao |
| :---: | :--- |
| 1 | Usuário |
| 2 | Sistema de Apuração |

---

Tabela: chart\_of\_account

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da conta (UUID). |
| code | TEXT | Não | Único | \- | Código contábil da conta (ex: 1). |
| classification | TEXT | Não | Único | \- | Classificação hierárquica da conta (ex: 1.01.001). |
| description | TEXT | Não | \- | \- | Descrição textual do nome da conta. |
| is\_analytic | BOOLEAN | Não | \- | false | Indica se a conta é analítica (true) ou sintética (false). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data da última atualização. |
| parent\_classification | TEXT | Sim | FK → chart\_of\_account.classification | \- | Classificação da conta pai (hierarquia). |
| account\_type\_id | INTEGER | Sim | FK → account\_types.id | \- | Tipo de conta contábil associado. Populado automaticamente pela migration com base na classificação hierárquica. |

---

Tabela: company

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da empresa (UUID). |
| name | TEXT | Não | \- | \- | Nome da empresa. |
| cnpj | TEXT | Não | Único | \- | CNPJ da empresa. |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Última atualização. |

---

Tabela: apuration

> **Nota (v2.0):** A v1.2 documentava esta tabela com o nome `apuracoes` e campos em português. A implementação usa o nome `apuration` com campos em inglês. A tabela também passou por uma evolução posterior (migration `20260508000000_apuracao_nula_support`) que tornou `destination_account_id` nullable e ampliou `type` para aceitar o valor 3.

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da apuração (UUID). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| apuration\_date | DATE | Não | \- | \- | Data de referência da apuração. |
| type | INTEGER | Não | \- | \- | Tipo da apuração: 1 (Lucro), 2 (Prejuízo) ou 3 (Resultado Nulo). |
| amount | DECIMAL(14,2) | Não | \- | \- | Valor apurado. |
| destination\_account\_id | TEXT | **Sim** | FK → chart\_of\_account.id | \- | Conta contábil de destino da apuração. Nullable quando `type = 3` (resultado nulo não possui conta destino). |

---

Tabela: journal\_entry

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único do lançamento (UUID). |
| company\_id | TEXT | Não | FK → company.id | \- | Empresa relacionada ao lançamento. |
| description | TEXT | **Sim*** | \- | \- | Histórico ou observação do lançamento. |
| amount | DECIMAL(14,2) | Não | \- | \- | Valor total do lançamento (deve ser \> 0). |
| is\_compound | INTEGER | Não | \- | 0 | Define se é lançamento simples (0) ou composto (1). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Última atualização do registro. |
| actor\_id | INTEGER | Não | FK → actors.id | \- | Ator responsável pelo lançamento. Lançamentos manuais usam actor\_id = 1 (Usuário); apurações automáticas usam actor\_id = 2 (Sistema de Apuração). |
| apuration\_id | INTEGER | Sim | FK → apuration.id | \- | Apuração associada ao lançamento, quando aplicável. |

> **\*Nota (v2.0 — `description`):** A coluna `description` é **nullable no banco de dados** (não há migration que a torne `NOT NULL`). No entanto, a camada de aplicação torna este campo **obrigatório**: o Service e o Controller rejeitam lançamentos sem histórico com HTTP 400. Nenhum lançamento sem `description` pode ser criado pela API.

---

Tabela: journal\_entry\_line

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da linha (UUID). |
| journal\_entry\_id | TEXT | Não | FK → journal\_entry.id | \- | Referência ao lançamento principal. |
| account\_code | TEXT | Não | FK → chart\_of\_account.id | \- | Conta contábil vinculada ao lançamento. |
| entry\_type | TEXT | Não | \- | \- | Tipo da partida: 'D' (Débito) ou 'C' (Crédito). |
| amount | DECIMAL(14,2) | Não | \- | \- | Valor da movimentação (\> 0). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |

---

Tabela: dre\_groups *(adicionada na v2.0 — não documentada na v1.2)*

Esta tabela armazena os grupos da Demonstração do Resultado do Exercício (DRE), permitindo classificar contas contábeis em categorias para fins de apuração e exibição do resultado.

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único do grupo (slug textual, ex: `gross_revenue`). |
| key | TEXT | Não | Único | \- | Chave funcional do grupo, usada para lookup no código. |
| title | TEXT | Não | \- | \- | Título legível do grupo (ex: "Receita Bruta"). |
| nature | TEXT | Não | \- | \- | Natureza do grupo: `revenue` (receita), `expense` (despesa) ou `mixed`. |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data da última atualização. |

Grupos pré-populados (seed): `gross_revenue`, `revenue_deductions`, `cmv_cpv`, `operational_expenses`, `other_operational_revenue`, `other_operational_expenses`, `financial_revenue`, `financial_expenses`, `non_operational_revenue`, `non_operational_expenses`, `income_taxes`.

---

Tabela: dre\_group\_account\_roots *(adicionada na v2.0 — não documentada na v1.2)*

Tabela de associação entre grupos de DRE e as contas raiz do Plano de Contas que os compõem. Permite configurar quais contas (e seus descendentes) pertencem a cada grupo.

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | INTEGER | Não | PK (auto-increment) | \- | Identificador único da associação. |
| dre\_group\_id | TEXT | Não | FK → dre\_groups.id | \- | Grupo de DRE ao qual a conta raiz pertence. |
| chart\_of\_account\_id | TEXT | Não | FK → chart\_of\_account.id | \- | Conta contábil raiz do grupo. |
| include\_descendants | BOOLEAN | Não | \- | true | Se verdadeiro, todas as contas filhas da raiz também pertencem ao grupo. |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data da última atualização. |

---

## Relacionamentos entre Tabelas {#relacionamentos-entre-tabelas}

| Origem | Destino | Tipo | Descrição |
| :---- | :---- | :---- | :---- |
| company.id | journal\_entry.company\_id | 1:N | Uma empresa possui vários lançamentos contábeis. |
| journal\_entry.id | journal\_entry\_line.journal\_entry\_id | 1:N | Um lançamento possui várias linhas de partidas. |
| chart\_of\_account.id | journal\_entry\_line.account\_code | 1:N | Uma conta pode estar em várias partidas. |
| chart\_of\_account.classification | chart\_of\_account.parent\_classification | 1:N | Autorrelacionamento hierárquico do plano de contas. |
| account\_types.id | chart\_of\_account.account\_type\_id | 1:N | Um tipo de conta pode ser associado a várias contas contábeis. |
| actors.id | journal\_entry.actor\_id | 1:N | Um ator pode ser responsável por vários lançamentos. |
| apuration.id | journal\_entry.apuration\_id | 1:N | Uma apuração pode estar associada a vários lançamentos. |
| chart\_of\_account.id | apuration.destination\_account\_id | 1:N | Uma conta pode ser destino de várias apurações (quando type ≠ 3). |
| dre\_groups.id | dre\_group\_account\_roots.dre\_group\_id | 1:N | Um grupo de DRE possui várias contas raiz. |
| chart\_of\_account.id | dre\_group\_account\_roots.chart\_of\_account\_id | 1:N | Uma conta pode ser raiz em vários grupos de DRE. |

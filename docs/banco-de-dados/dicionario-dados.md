# Dicionário de Dados

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 19/08 | Criação inicial do documento de Dicionário de Dados  | Fernanda Pessoa |
| 1.1 | 22/10 | Pequenas correções de definições de atributos | Pedro Nicoletti Sotoma |
| 1.2 | 06/05 | Atualização do esquema: novas tabelas account\_types, actors e apuracoes; renomeação de tabelas; novos campos | Fernanda Pessoa |

**Histórico de Revisões (tamanho 14\)**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.1 | 09/11 | Fernanda Pessoa | Aprovada |
|  |  |  |  |
|  |  |  |  |

**Sumário**

[1\. Introdução	2](#introdução)

[2\. Estrutura de Tabelas	2](#estrutura-de-tabelas)

[3\. Relacionamentos entre Tabelas	6](#relacionamentos-entre-tabelas)

## Introdução {#introdução}
O banco de dados do Sistema COIN'S (Contabilidade Integrada Simplificada) foi desenvolvido para gerenciar informações contábeis de empresas, permitindo o registro de lançamentos no Livro Diário e Livro Razão.  
O modelo é composto por sete tabelas de negócio: `account_types`, `actors`, `chart_of_account`, `company`, `apuracoes`, `journal_entry` e `journal_entry_line`. Além dessas, existem tabelas de infraestrutura de migração (`knex_migrations`, `knex_migrations_lock` e `app_data_migrations`), gerenciadas pelo framework e não documentadas neste dicionário.

## Estrutura de Tabelas {#estrutura-de-tabelas}

Tabela: account\_types

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | INTEGER | Não | PK | \- | Identificador único do tipo de conta. |
| descricao | TEXT | Não | Único | \- | Descrição do tipo de conta (ex: Ativo, Passivo). |

Tabela: actors

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | INTEGER | Não | PK | \- | Identificador único do ator. |
| descricao | TEXT | Não | Único | \- | Descrição do ator responsável pelos lançamentos. |

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
| account\_type\_id | INTEGER | Sim | FK → account\_types.id | \- | Tipo de conta contábil associado. |

Tabela: company

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da empresa (UUID). |
| name | TEXT | Não | \- | \- | Nome da empresa. |
| cnpj | TEXT | Não | Único | \- | CNPJ da empresa. |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Última atualização. |

Tabela: apuracoes

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da apuração (UUID). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| data\_apuracao | DATE | Não | \- | \- | Data de referência da apuração. |
| tipo | INTEGER | Não | \- | \- | Tipo da apuração: 1 ou 2. |
| valor | FLOAT | Não | \- | \- | Valor apurado. |
| conta\_destino\_id | TEXT | Não | FK → chart\_of\_account.id | \- | Conta contábil de destino da apuração. |

Tabela: journal\_entry

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único do lançamento (UUID). |
| company\_id | TEXT | Não | FK → company.id | \- | Empresa relacionada ao lançamento. |
| description | TEXT | Sim | \- | \- | Histórico ou observação do lançamento. |
| amount | FLOAT | Não | \- | \- | Valor total do lançamento (deve ser \> 0). |
| is\_compound | INTEGER | Não | \- | 0 | Define se é lançamento simples (0) ou composto (1). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Última atualização do registro. |
| actor\_id | INTEGER | Não | FK → actors.id | \- | Ator responsável pelo lançamento. |
| apuration\_id | INTEGER | Sim | FK → apuracoes.id | \- | Apuração associada ao lançamento, quando aplicável. |

Tabela: journal\_entry\_line

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da linha (UUID). |
| journal\_entry\_id | TEXT | Não | FK → journal\_entry.id | \- | Referência ao lançamento principal. |
| account\_code | TEXT | Não | FK → chart\_of\_account.id | \- | Conta contábil vinculada ao lançamento. |
| entry\_type | TEXT | Não | \- | \- | Tipo da partida: 'D' (Débito) ou 'C' (Crédito). |
| amount | FLOAT | Não | \- | \- | Valor da movimentação (\> 0). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |

## Relacionamentos entre Tabelas {#relacionamentos-entre-tabelas}
| Origem | Destino | Tipo | Descrição |
| :---- | :---- | :---- | :---- |
| company.id | journal\_entry.company\_id | 1:N | Uma empresa possui vários lançamentos contábeis. |
| journal\_entry.id | journal\_entry\_line.journal\_entry\_id | 1:N | Um lançamento possui várias linhas de partidas. |
| chart\_of\_account.id | journal\_entry\_line.account\_code | 1:N | Uma conta pode estar em várias partidas. |
| chart\_of\_account.classification | chart\_of\_account.parent\_classification | 1:N | Autorrelacionamento hierárquico do plano de contas. |
| account\_types.id | chart\_of\_account.account\_type\_id | 1:N | Um tipo de conta pode ser associado a várias contas contábeis. |
| actors.id | journal\_entry.actor\_id | 1:N | Um ator pode ser responsável por vários lançamentos. |
| apuracoes.id | journal\_entry.apuration\_id | 1:N | Uma apuração pode estar associada a vários lançamentos. |
| chart\_of\_account.id | apuracoes.conta\_destino\_id | 1:N | Uma conta pode ser destino de várias apurações. |

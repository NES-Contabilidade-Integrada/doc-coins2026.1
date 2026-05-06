**Dicionário de Dados – Sistema COIN’S**

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 19/08 | Criação inicial do documento de Dicionário de Dados  | Fernanda Pessoa |
| 1.1 | 22/10 | Pequenas correções de definições de atributos | Pedro Nicoletti Sotoma |
|  |  |  |  |

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

1. # **Introdução**  {#introdução}

O banco de dados do Sistema COIN’S (Contabilidade Integrada Simplificada) foi desenvolvido para gerenciar informações contábeis de empresas, permitindo o registro de lançamentos no Livro Diário e Livro Razão.  
O modelo é composto por quatro tabelas principais: chart\_of\_account, companies, journal\_entries e journal\_entry\_lines.

2. # **Estrutura de Tabelas** {#estrutura-de-tabelas}

Tabela: chart\_of\_account

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da conta (UUID). |
| code | TEXT | Não | \- | \- | Código contábil da conta (ex: 1). |
| classification | TEXT | Não | \- | \- | Classificação hierárquica da conta. (ex: 1.01.001). |
| description | TEXT | Não | \- | \- | Descrição textual do nome da conta. |
| is\_analytic | INTEGER | Não | \- | \- | Indica se a conta é analítica (1) ou sintética (0). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data da última atualização. |
| parent\_classification | TEXT | Sim | FK → chart\_of\_account.classification | \- | Classificação da conta pai (hierarquia). |

Tabela: companies

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da empresa (UUID). |
| name | TEXT | Não | \- | \- | Nome da empresa. |
| cnpj | TEXT | Não | Único | \- | CNPJ da empresa. |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Última atualização. |

Tabela: journal\_entries

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único do lançamento (UUID). |
| company\_id | TEXT | Não | FK → companies.id | \- | Empresa relacionada ao lançamento. |
| description | TEXT | Sim | \- | \- | Histórico ou observação do lançamento. |
| amount | NUMERIC(14,2) | Não | \- | \- | Valor total do lançamento. |
| is\_compound | INTEGER | Não | \- | 0 | Define se é lançamento simples (0) ou composto (1). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |
| updated\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Última atualização do registro. |

Tabela: journal\_entry\_lines

| Campo | Tipo | Nulo | Chave | Padrão | Descrição |
| :---- | :---- | :---- | :---- | :---- | :---- |
| id | TEXT | Não | PK | \- | Identificador único da linha (UUID). |
| journal\_entry\_id | TEXT | Não | FK → journal\_entries.id | \- | Referência ao lançamento principal. |
| account\_id | TEXT | Não | FK → chart\_of\_account.id | \- | Conta contábil vinculada ao lançamento. |
| entry\_type | TEXT | Não | \- | \- | Tipo da partida: 'D' (Débito) ou 'C' (Crédito). |
| amount | NUMERIC(14,2) | Não | \- | \- | Valor da movimentação (\> 0). |
| created\_at | DATETIME | Sim | \- | CURRENT\_TIMESTAMP | Data de criação do registro. |

3. # **Relacionamentos entre Tabelas** {#relacionamentos-entre-tabelas}

| Origem | Destino | Tipo | Descrição |
| :---- | :---- | :---- | :---- |
| companies.id | journal\_entries.company\_id | 1:N | Uma empresa possui vários lançamentos contábeis. |
| journal\_entries.id | journal\_entry\_lines.journal\_entry\_id | 1:N | Um lançamento possui várias linhas de partidas. |
| chart\_of\_account.id | journal\_entry\_lines.account\_id | 1:N | Uma conta pode estar em várias partidas. |
| chart\_of\_account.classification | chart\_of\_account.parent\_classification | 1:N | Autorrelacionamento hierárquico do plano de contas. |


# Documento de Visão de Implementação

**Histórico de Versões** 

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 28/10 | Adiciona versão inicial do documento de Visão de Implementação | Pedro Nicoletti Sotoma |
| 1.1 | 11/11 | Ajustando links do Sumário | Pedro Nicoletti Sotoma |
| 2.0 | 01/06/2026 | Atualização com base no working directory (branch develop): novas camadas do frontend (Stores, Utils/Composables, Types, Constants, Layout, Plugins); novos módulos de domínio backend e frontend (Apuração, DRE, Balanço Patrimonial); decomposição da camada de banco de dados; reorganização dos testes E2E para `playwright/` | Lohan Toledo Tosta |

**Histórico de Revisões** 

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.1 | 25/11/2025 | Fernanda Pessoa | Aprovada |
| 2.0 | — | — | Pendente de revisão |

**Sumário**

[1\. Introdução	1](#introdução)

[2\. Arquitetura Geral do Sistema	2](#arquitetura-geral-do-sistema)

[2.1 Arquitetura do Backend	2](#2.1-arquitetura-do-backend)

[2.2 Arquitetura do Frontend	3](#2.2-arquitetura-do-frontend)

[2.3 Camada de Testes E2E	4](#2.3-camada-de-testes-e2e)

[3\. Conclusão	5](#conclusão)

## Introdução
Esse documento tem por objetivo especificar a estrutura organizacional do código-fonte do software COIN'S, desenvolvido na disciplina de Núcleo de Práticas de Engenharia de Software 2025/2.

Ele serve como um guia para a equipe de desenvolvimento, detalhando a responsabilidade de cada camada e diretório principal. O objetivo é facilitar a manutenção e a implementação de novas funcionalidades, garantindo que a estrutura do código seja preservada.

As decisões arquiteturais de alto nível estão registradas no Documento de Registro de Decisões (ADRs), e a visão geral dos componentes pode ser vista nos diagramas C4 do projeto. Este documento foca exclusivamente na Visão de Implementação.

## Arquitetura Geral do Sistema
O sistema em geral é constituído por uma arquitetura monolítica modular baseada em camadas. Essa decisão foi tomada por conta do contexto de que a solução desenvolvida seria um sistema desktop offline, facilitando a integração frontend/backend/banco de dados local.  
Essa arquitetura consiste basicamente em agrupar todo o sistema em um único repositório, separando os componentes em camadas de acordo com suas responsabilidades.   
Mais adiante será detalhado como separamos nossas camadas tanto para o frontend quanto para o backend.

### 2.1 Arquitetura do Backend
Para o backend (diretório `main`), separamos nosso código em camadas principais:

* **Database:** Essa camada fica responsável por configurar e inicializar o banco de dados local.

> **Nota (v2.0 — Decomposição da camada Database):** A camada de banco de dados foi decomposta em múltiplos arquivos com responsabilidades dedicadas, deixando de ser um único arquivo de configuração:
>
> | Arquivo | Responsabilidade |
> | :--- | :--- |
> | `database/connection.ts` | Instância do Knex e conexão com o SQLite3 |
> | `database/migrateDatabase.ts` | Execução das migrations pendentes |
> | `database/seedDatabase.ts` | Execução das seeds de dados iniciais |
> | `database/detectDatabaseState.ts` | Detecção do estado do banco (novo, migrado, corrompido) |
> | `database/runDatabaseRoutine.ts` | Orquestra toda a inicialização: detect → migrate → seed |

* **Migrations:** Alinhada à database, essa camada tem como objetivo gerar as tabelas do banco de dados em conformidade com o modelo de dados do código.

> **Nota (v2.0 — Reorganização das migrations):** As 4 migrations originais (criadas na branch `main`) foram consolidadas em uma única **migration de baseline** (`20260331195800_baseline.ts`), seguida de migrations incrementais para cada evolução do schema. A estrutura atual é:
>
> | Migration | Responsabilidade |
> | :--- | :--- |
> | `20260331195800_baseline.ts` | Cria as 4 tabelas originais (`chart_of_account`, `company`, `journal_entry`, `journal_entry_line`) |
> | `20260408232842_add_apuration.ts` | Cria `account_types`, `actors`, `apuration`; adiciona `account_type_id` em `chart_of_account` |
> | `20260416003754_actor_and_appuration_into_journal.ts` | Adiciona `actor_id` e `apuration_id` em `journal_entry` |
> | `20260507000000_add_dre_groups.ts` | Cria `dre_groups` e `dre_group_account_roots` |
> | `20260508000000_apuracao_nula_support.ts` | Torna `destination_account_id` nullable; amplia `type` para aceitar valor 3 (Resultado Nulo) |

* **Seed:** Essa camada é responsável por popular o banco com dados que devem ser instanciados assim que o sistema é gerado.

> **Nota (v2.0):** Adicionada seed `InsertDreRoots.ts` para popular os vínculos entre grupos de DRE e as contas raiz do Plano de Contas padrão.

* **Entities:** Essa camada é responsável por representar as tabelas do banco de dados no código.

* **Repositories:** Essa camada é responsável por acessar e realizar operações no banco de dados.

> **Nota (v2.0):** Adicionado `ApurationRepository` para o módulo de apuração. Os demais módulos novos (DRE, BalanceSheetStatement) não possuem repository próprio — operam diretamente via queries no Service.

* **Services:** Essa camada é responsável por gerenciar as regras de negócio da aplicação.

> **Nota (v2.0 — Novos Services):**
>
> | Service | Módulo | Responsabilidade |
> | :--- | :--- | :--- |
> | `ApurationService` | Apuração | Lógica de apuração contábil (lançamentos de encerramento) |
> | `DreService` | DRE | Cálculo da Demonstração do Resultado do Exercício |
> | `BalanceSheetStatementService` | Balanço Patrimonial | Geração do demonstrativo do balanço patrimonial |
> | `BalanceSheetStatementCsvService` | Balanço Patrimonial | Exportação do balanço patrimonial em formato CSV |

* **Controllers:** Essa camada é responsável por disponibilizar rotas de acesso aos dados do backend para o frontend.

> **Nota (v2.0 — Novos Controllers):**
>
> | Controller | Módulo | Rotas |
> | :--- | :--- | :--- |
> | `ApurationController` / `ApurationRoutes` | Apuração | Endpoints de apuração contábil |
> | `DreController` / `DreRoutes` | DRE | Endpoints da Demonstração do Resultado |
> | `BalanceSheetStatementController` / `BalanceSheetStatementRoutes` | Balanço Patrimonial | Endpoints do demonstrativo e exportação |

* **Helpers:** Camada de funções utilitárias compartilhadas entre Services e Controllers, sem estado (ex: `formatDateToSqlString`, `JournalEntryHelpers`, `NormalizeToFilter`, `getResourcePath`).

* **Tests:** Essa camada engloba os testes unitários da aplicação, executados via Vitest.

> **Nota (v2.0):** Adicionados testes para os novos módulos (`Apuration`, `Dre`, `BalanceSheetStatement`) e para os helpers (`JournalEntryHelpers`, `NormalizeToFilter`, `formatDateToSqlString`).

### 2.2 Arquitetura do Frontend
Para o frontend (diretório `renderer`), separamos nosso código em camadas principais:

* **Components:** Essa camada fica responsável por armazenar os componentes reutilizáveis e as seções visuais do sistema, organizados por módulo de negócio e por componentes globais.

> **Nota (v2.0 — Novos módulos de componentes):** Três novos grupos de componentes foram adicionados, cada um correspondendo a um módulo de domínio:
>
> | Módulo | Diretório | Componentes |
> | :--- | :--- | :--- |
> | Apuração | `components/Apuracao/` | `ApuracaoAccounts`, `ApuracaoClosingEntries`, `ApuracaoFinalResult`, `ApuracaoHistoryModal`, `ApuracaoFilter`, `ApuracaoResume` |
> | Balanço Patrimonial | `components/BalancoPatrimonial/` | `BalancoPatrimonialSection`, `BalancoPatrimonialResumo`, `BalancoPatrimonialFilter`, `BalancoPatrimonialConferencia`, `BalancoPatrimonialExportDialog` |
> | DRE (Demonstração) | `components/Demonstracao/` | `DemonstracaoDRE`, `DemonstracaoContas`, `DemonstracaoFinalResult`, `DemonstracaoFilter`, `DemonstracaoExportDialog`, `DemonstracaoResume` |

* **Pages:** Essa camada fica responsável por renderizar as páginas da aplicação.

> **Nota (v2.0 — Novas páginas):** `ApuracaoPage.vue`, `BalancoPatrimonialPage.vue` e `DemonstracaoPage.vue` foram adicionadas, uma por módulo de domínio novo.

* **Layout:** Essa camada é responsável por definir o layout estrutural da aplicação (`MainLayout.vue`), integrando os componentes de navegação (AppBar, SideBar) e os sistemas globais de notificação.

* **Router:** Essa camada é responsável por gerenciar as rotas da aplicação.

* **Services:** Essa camada estabelece a comunicação com o backend para retorno dos endpoints.


* **Schemas:** Essa camada é responsável por definir as estruturas de dados que serão utilizadas nos componentes.

* **Stores (`stores/`):** Camada de gerenciamento de estado global da aplicação, implementada com **Pinia**. Cada store encapsula estado, ações e lógica de inicialização de um agregado de domínio (ex: `companyStore.ts`).

* **Utils / Composables (`utils/`):** Camada de lógica reutilizável entre componentes, implementada como **Vue Composables**. Exemplos: `useAlert.ts`, `useBalanceAlert.ts`, `format.ts`.


* **Types (`types/`):** Camada de definições de tipos TypeScript compartilhadas entre componentes e services do frontend.


* **Constants (`constants/`):** Camada de constantes globais do frontend.

* **Plugins (`plugins/`):** Camada de configuração e registro de plugins do Vue (ex: Vuetify).

### 2.3 Camada de Testes E2E

Além das camadas de backend e frontend, o projeto conta com uma camada independente de **Testes End-to-End** (diretório `playwright/`), baseada em **Playwright**. Essa camada é externa ao código de produção e atua sobre a aplicação compilada como um usuário real faria.

> **Nota (v2.0 — Renomeação):** A pasta de testes E2E foi renomeada de `e2e/` para `playwright/`. A estrutura interna foi mantida, com as seguintes mudanças adicionais: a categoria `regression/` foi renomeada para `acceptance/`; novos page objects e specs foram adicionados para os módulos de Apuração e DRE.

A camada de testes E2E é organizada em 4 subcamadas:

* **Pages (`playwright/pages/`):** Implementa o padrão **Page Object Model (POM)**. Cada arquivo encapsula as interações com um módulo específico da UI.


* **Fixtures (`playwright/fixtures/`):** Armazena dados de teste em formato JSON.


* **Utils (`playwright/utils/`):** Contém utilitários compartilhados entre os specs (`app.fixture.ts`, `globalFunctions.ts`).

* **Specs (`playwright/specs/`):** Contém os casos de teste, organizados em cinco categorias:

  | Categoria | Diretório | O que valida |
  | :--- | :--- | :--- |
  | **Functional** | `specs/functional/` | Comportamento de UI por módulo (inclui novos: `apuracao/`, `dre/`) |
  | **Integration** | `specs/integration/` | Respostas da API REST do backend (inclui novos: `apuracao/`, `dre/`) |
  | **E2E** | `specs/e2e/` | Fluxos contábeis completos ponta a ponta (inclui novos: `apuracao-workflow`, `dre-workflow`) |
  | **Acceptance** | `specs/acceptance/` | Regras de negócio e integridade de dados (renomeado de `regression/`) |

## Conclusão
A arquitetura definida pelo time entrega uma estrutura robusta e organizada para o escopo do projeto, garantindo clareza no desenvolvimento e manutenção do software.

> **Conclusão atualizada (v2.0):** A evolução entre a v1.1 e a v2.0 não alterou as decisões arquiteturais fundamentais — o sistema permanece monolítico modular, desktop, offline, com separação entre `main` (backend) e `renderer` (frontend). As principais adições foram: (1) três novos módulos de domínio completos — **Apuração**, **DRE** e **Balanço Patrimonial** — com representação em todas as camadas; (2) decomposição da camada `database/` em arquivos dedicados por responsabilidade; (3) consolidação das migrations em baseline + incrementais; (4) formalização das camadas de frontend que existiam mas não estavam documentadas (Stores, Utils/Composables, Types, Constants, Plugins); (5) reorganização dos testes E2E de `e2e/` para `playwright/` com cobertura dos novos módulos.

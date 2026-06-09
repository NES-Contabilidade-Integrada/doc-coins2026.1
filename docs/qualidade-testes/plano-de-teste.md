# Plano de Teste — NES Coins 2026.1

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 25/03/2026 | Criação do plano inicial com análise da situação atual | Amanda Gois |
| 1.1 | 15/04/2026 | Atualização do conteúdo sobre o plano | Amanda Gois |
| 1.2 | 09/06/2026 | Reestruturação no padrão do MKdocs; cobertura completa dos 466 testes automatizados | Amanda Gois |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |
| 1.0 | 09/06/2026 | Eduardo Henrique | Aprovado |

---

## Sumário

[1. Introdução](#introdução)

[2. Análise da Situação Atual](#análise-da-situação-atual)

[3. Itens de Teste](#itens-de-teste)

[4. Funcionalidades a Testar](#funcionalidades-a-testar)

[5. Abordagem de Teste](#abordagem-de-teste)

[6. Arquitetura dos Testes](#arquitetura-dos-testes)

[7. Critérios de Entrada e Saída](#critérios-de-entrada-e-saída)

[8. Critérios de Aprovação e Reprovação](#critérios-de-aprovação-e-reprovação)

[9. Critérios de Suspensão e Retomada](#critérios-de-suspensão-e-retomada)

## Introdução {#introdução}

### Objetivo

Este documento descreve o planejamento e a abordagem de teste do sistema NES Coins 2026.1. O objetivo é definir o escopo, a estratégia e os critérios de qualidade associados às atividades de verificação e validação do software.

### Escopo

O plano cobre todos os módulos funcionais da aplicação desktop (Electron + Vue.js), validando comportamento de interface, integridade de dados contábeis, cálculos financeiros e fluxos de negócio de ponta a ponta.

## Análise da Situação Atual {#análise-da-situação-atual}

Antes da implementação da suite Playwright, a cobertura de testes do sistema era composta exclusivamente por testes unitários desenvolvidos com Jest. Esses testes validavam funções isoladas, cálculos e componentes do React, mas deixavam uma lacuna na validação de fluxos completos de usuário e na integração real entre o frontend (Renderer) e o backend (Main/Electron).

A introdução do Playwright como ferramenta de automação de interface endereçou essa lacuna, viabilizando testes funcionais, de integração, de sistema e E2E diretamente sobre o aplicativo Electron empacotado.

## Itens de Teste {#itens-de-teste}

### Sistema sob Teste

**NES Coins 2026.1** é uma aplicação desktop de contabilidade empresarial:

- **Frontend:** Vue.js 3 + Vuetify (Electron App)
- **Backend:** Node.js (processo main do Electron)
- **Banco de Dados:** SQLite (local)

### Módulos Cobertos

| Módulo | Sigla | Descrição |
| :--- | :---: | :--- |
| Diário Geral | GJ | Registro, edição e exclusão de lançamentos contábeis |
| Razão Geral | GL | Visualização de movimentações por conta |
| Balancete de Verificação | BS | Demonstrativo de saldos devedores e credores |
| Balanço Patrimonial | BP | Demonstração do Ativo, Passivo e Patrimônio Líquido |
| DRE | DRE | Demonstração do Resultado do Exercício |
| Apuração de Resultado | AP | Apuração e encerramento de contas de resultado |
| Plano de Contas | COA | Cadastro e manutenção do plano de contas |
| Empresa | CO | Configuração e identificação da empresa |
| Menu de Navegação | MENU | Estrutura de abas e navegação entre módulos |

### Versões e Configurações

| Item | Versão/Configuração |
| :--- | :--- |
| Node.js | conforme `.nvmrc` do projeto |
| Playwright | conforme `package.json` |
| Jest | conforme `jest.config.js` |
| Browser (Playwright) | Electron (Chromium embutido) |

## Funcionalidades a Testar {#funcionalidades-a-testar}

### Testes Funcionais — Interface e Comportamento

Verificam comportamento visual, navegação, filtros e exibição de dados em cada módulo.

| Módulo | Arquivos | Casos |
| :--- | :---: | :---: |
| Apuração | 4 | 31 |
| Balancete | 3 | 12 |
| Balanço Patrimonial | 1 | 9 |
| Plano de Contas | 1 | 8 |
| Empresa | 1 | 1 |
| DRE | 4 | 35 |
| Diário Geral | 4 | 14 |
| Razão Geral | 3 | 14 |
| Menu | 1 | 2 |
| **Total Funcional** | **22** | **126** |

### Testes de Sistema

Validam regras de negócio críticas e integridade de dados contábeis.

| Módulo | Arquivos | Casos |
| :--- | :---: | :---: |
| Plano de Contas — Integridade | 1 | 2 |
| Diário Geral — Validações | 1 | 11 |
| **Total Sistema** | **2** | **13** |

### Testes E2E 

Simulam fluxos completos de trabalho do usuário real.

| Fluxo | Arquivo | Casos |
| :--- | :--- | :---: |
| Fluxo Contábil Completo | `accounting-workflow.spec.ts` | 3 |
| Fluxo de Apuração | `apuracao-workflow.spec.ts` | 2 |
| Fluxo de DRE | `dre-workflow.spec.ts` | 2 |
| **Total E2E** | **3** | **7** |

### Testes de Integração

Verificam comportamento da UI quando a API retorna erros.

| Módulo | Arquivo | Casos |
| :--- | :--- | :---: |
| Apuração | `apuracao/api-errors.spec.ts` | 4 |
| Balancete | `balance-sheet/api-errors.spec.ts` | 2 |
| DRE | `dre/api-errors.spec.ts` | 10 |
| Diário Geral | `general-journal/api-errors.spec.ts` | 3 |
| Razão Geral | `general-ledger/api-errors.spec.ts` | 1 |
| **Total Integração** | **5** | **20** |

### Testes Unitários

Cobrem lógica de negócio, serviços e controllers do processo main.

| Módulo | Arquivos | Casos |
| :--- | :---: | :---: |
| Apuração | 2 | 40 |
| Balanço Patrimonial | 5 | 22 |
| Demonstração BP | 3 | 35 |
| Plano de Contas | 2 | 13 |
| Empresa | 2 | 12 |
| DRE | 2 | 71 |
| Razão Geral | 2 | 15 |
| Diário Geral | 2 | 56 |
| Helpers / Utilitários | 3 | 36 |
| **Total Unitários** | **23** | **300** |

## Abordagem de Teste {#abordagem-de-teste}

### Estratégia Geral

A estratégia adota a pirâmide de testes:

- **Base (Unitários — 300 casos):** cobre lógica isolada de serviços e controllers.
- **Camada intermediária (Funcional/Integração — 146 casos):** cobre comportamento da UI e integração com API.
- **Topo (E2E — 7 casos):** cobre fluxos críticos de negócio de ponta a ponta.

### Tipos de Teste

| Tipo | Ferramenta | Escopo |
| :--- | :--- | :--- |
| Unitário | Jest + TypeScript | Serviços, Controllers, Helpers |
| Funcional | Playwright + Electron | Interface, filtros, cálculos, exibição |
| Integração | Playwright + Electron | Comportamento UI com erros de API |
| Sistema | Playwright + Electron | Regras de negócio contábeis |
| E2E | Playwright + Electron | Fluxos de trabalho completos |

### Abordagem de Dados de Teste

- **Fixtures JSON:** dados contábeis padronizados em `playwright/fixtures/`.
- **Setup/Teardown:** cada suite cria e remove seus próprios lançamentos via `beforeAll`/`afterAll` através do script `e2e/utils/app.fixture.ts`.
- **Estado isolado:** testes não dependem de dados persistentes entre suites.
- **Page Objects (`e2e/pages/`):** 7 classes que centralizam seletores da interface (ex: `JournalPage`, `CompanyPage`), permitindo atualizações de UI sem quebrar múltiplos testes.
- **Funções globais (`e2e/utils/globalFunctions.ts`):** central de utilitários compartilhados por toda a suite.

### Ferramentas

| Ferramenta | Finalidade |
| :--- | :--- |
| Jest | Execução de testes unitários |
| Playwright | Automação de interface (Electron) |
| TypeScript | Linguagem dos testes |
| Page Object Model | Abstração de locators Playwright |
| GitHub Actions | Execução automatizada em pipeline |

### Execução na Pipeline de CI/CD

O projeto possui dois workflows independentes no GitHub Actions, ambos ativados por Pull Request ou Push nas branches principais.

**Workflow 1 — CI: Testes Unitários Backend (`ci.yml`)**

| Gatilho | Branches | Paths observados |
| :--- | :--- | :--- |
| Pull Request / Push | `main`, `develop`, `release-candidate`, `Subtask/**` | `my-app/main/**`, `package.json`, `jest.config.js` |

Etapas executadas:

1. Checkout do código e configuração do Node.js 20
2. Instalação de dependências (`npm ci`)
3. Execução dos testes unitários com cobertura (`npm run test:unit -- --coverage`)
4. Análise do relatório de cobertura (threshold: **80%** para statements, branches, functions e lines)
5. Comentário automático no PR com relatório de cobertura e dicas contextuais de melhoria

**Workflow 2 — CI: Testes Playwright (`ci-e2e.yml`)**

| Gatilho | Branches | Paths observados |
| :--- | :--- | :--- |
| Pull Request / Push | `main`, `develop`, `release-candidate`, `Subtask/**` | `my-app/playwright/**`, `my-app/renderer/**`, `my-app/main/**` |

Etapas executadas:

1. Checkout (com `fetch-depth: 0` para análise de diff)
2. Configuração do Node.js 20 e `npm ci`
3. Instalação do Playwright e Chromium (`npx playwright install --with-deps chromium`)
4. Configuração do display virtual Xvfb (1920x1080) e permissões do `chrome-sandbox` para Electron
5. Build completo da aplicação (`npx electron-forge package`)
6. Reset do banco de dados (`npm run reset:db`)
7. Determinação da estratégia de execução (ver abaixo)
8. Execução dos testes conforme estratégia
9. Upload de artefatos `.playwright-results/` (retenção: 7 dias)
10. Comentário automático no PR com resultado e link para download dos artefatos

**Estratégia de Execução Playwright**

| Branch | Estratégia | Suites executadas |
| :--- | :--- | :--- |
| `main` / `release-candidate` | Completa | `functional`, `integration`, `regression`, `e2e` |
| Feature / Subtask | Seletiva (path-based) | Apenas módulos afetados pelos arquivos alterados + `regression` |

Na estratégia seletiva, alterações em `playwright/pages/`, `playwright/utils/` ou `playwright/fixtures/` disparam a suite completa, pois impactam todos os módulos.

### Critérios de Cobertura

- Cobertura de código unitário: mínimo **80%** de linhas nos módulos críticos (DRE, GJ, AP).
- Cobertura funcional: todos os IDs de caso documentados devem ter teste implementado.
- Regressão: suites completas executadas antes de cada merge para `release-candidate`.

## Arquitetura dos Testes {#arquitetura-dos-testes}

### Estrutura de Diretórios

```
my-app/
├── playwright/
│   ├── specs/
│   │   ├── functional/        # testes funcionais por módulo
│   │   │   ├── apuracao/
│   │   │   ├── balance-sheet/
│   │   │   ├── balanco-patrimonial/
│   │   │   ├── chart-of-accounts/
│   │   │   ├── company/
│   │   │   ├── dre/
│   │   │   ├── general-journal/
│   │   │   ├── general-ledger/
│   │   │   └── menu/
│   │   ├── acceptance/        # testes de sistema (regras de negócio)
│   │   ├── integration/       # testes de integração (erros de API)
│   │   └── e2e/               # fluxos completos de negócio
│   ├── pages/                 # Page Objects (7 classes)
│   ├── fixtures/              # dados contábeis padronizados
│   └── utils/
│       ├── app.fixture.ts     # setup e teardown de banco
│       └── globalFunctions.ts # utilitários compartilhados
└── main/
    └── tests/                 # testes unitários Jest
```

### Camadas de Suporte

**Page Objects (`playwright/pages/`):** cada módulo tem uma classe que centraliza todos os seletores e ações da interface (ex: `JournalPage`, `CompanyPage`, `DREPage`). Quando a UI muda, apenas o Page Object precisa ser atualizado — os testes não quebram.

**Fixtures (`playwright/fixtures/`):** dados contábeis em JSON (plano de contas, lançamentos padrão) usados como base para setup dos testes. São versionados no repositório para garantir reprodutibilidade.

**app.fixture.ts:** script de setup e teardown executado em `beforeAll`/`afterAll`. Cria os lançamentos necessários via `window.request` e os remove ao final, garantindo isolamento entre suites.

**globalFunctions.ts:** funções utilitárias compartilhadas (ex: esperar por elemento, formatar datas, limpar banco) que evitam duplicação entre arquivos de teste.

### Execução Estratégica

O script `select-tests.sh` determina dinamicamente quais suites executar com base no diff da branch:

1. **Detecção de mudanças:** executa `git diff main...HEAD` para listar os arquivos alterados.
2. **Mapeamento de módulos:** arquivos em `specs/functional/dre/` → suite `dre`; em `specs/functional/general-journal/` → suite `general-journal`; e assim por diante.
3. **Regressão obrigatória:** independentemente do que foi alterado, os testes de regressão (`regression`) sempre são incluídos para proteger as regras contábeis críticas.
4. **Arquivos globais disparam suite completa:** mudanças em `pages/`, `utils/` ou `fixtures/` impactam potencialmente todas as suites — nesse caso o script ignora a seletividade e executa tudo.
5. **Branches de entrega sempre executam tudo:** em `main` e `release-candidate`, a estratégia é forçosamente `all`, sem passar pelo script de seleção.

## Critérios de Entrada e Saída {#critérios-de-entrada-e-saída}

### Critérios de Entrada

- Código compilado sem erros em `main` e `renderer`.
- Banco de dados local inicializado com dados de seed do plano de contas padrão.
- Dependências instaladas (`npm install`).

### Critérios de Saída

- 100% dos testes Jest e Playwright devem passar.
- Relatório de testes gerado e revisado.

## Critérios de Aprovação e Reprovação {#critérios-de-aprovação-e-reprovação}

O ciclo de testes é aprovado quando **100% dos testes Jest e Playwright passam** — sem exceção. Qualquer falha em testes unitários (Jest) ou de interface (Playwright) bloqueia a aprovação do ciclo.

## Critérios de Suspensão e Retomada {#critérios-de-suspensão-e-retomada}

Em caso de defeito de infraestrutura — onde os testes passam localmente mas reprovam nas GitHub Actions — é possível mergear a PR, desde que haja o veredito explícito do QA autorizando o merge nessas condições.

Em caso de falha por mudança de regra de negócio — onde o comportamento do sistema foi intencionalmente alterado e o teste reflete a regra antiga — a mitigação é atualizar o teste para refletir o novo comportamento esperado antes do merge. O teste não deve ser removido nem ignorado; deve ser corrigido para validar a nova regra. Essa situação requer revisão do QA para confirmar que a mudança de expectativa está alinhada com a especificação. Dependendo da complexidade e tempo para corrigir, o QA pode executar manualmente os casos de teste que falharam na pipeline para validar o comportamento esperado e aprovar o merge sem a necessidade de aprovação do CI.

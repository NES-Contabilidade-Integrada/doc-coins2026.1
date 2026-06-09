# Plano de Teste — NES Coins 2026.1

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 09/06/2026 | Criação do documento | Squad SIA2 |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |
| 1.0 | 09/06/2026 | — | Pendente |

---

## Sumário

[1. Identificação](#identificação)

[2. Introdução](#introdução)

[3. Itens de Teste](#itens-de-teste)

[4. Funcionalidades a Testar](#funcionalidades-a-testar)

[5. Funcionalidades a Não Testar](#funcionalidades-a-não-testar)

[6. Abordagem de Teste](#abordagem-de-teste)

[7. Critérios de Entrada e Saída](#critérios-de-entrada-e-saída)

[8. Critérios de Aprovação e Reprovação](#critérios-de-aprovação-e-reprovação)

[9. Critérios de Suspensão e Retomada](#critérios-de-suspensão-e-retomada)

[10. Entregas do Teste](#entregas-do-teste)

[11. Ambiente de Teste](#ambiente-de-teste)

[12. Responsabilidades](#responsabilidades)

[13. Riscos e Mitigações](#riscos-e-mitigações)

[14. Cronograma](#cronograma)

[15. Aprovação](#aprovação)

## Identificação {#identificação}

| Campo | Valor |
| :--- | :--- |
| Projeto | NES Coins 2026.1 — Sistema Contábil Integrado |
| Versão do Sistema | 2026.1 |
| Branch de Referência | release-candidate |
| Equipe Responsável | Squad SIA2 |
| Contato | squad-sia2@seazone.com.br |

## Introdução {#introdução}

### Objetivo

Este documento descreve o planejamento e a abordagem de teste do sistema NES Coins 2026.1. O objetivo é definir o escopo, a estratégia, os critérios de qualidade e as responsabilidades associadas às atividades de verificação e validação do software.

### Escopo

O plano cobre todos os módulos funcionais da aplicação desktop (Electron + Vue.js), validando comportamento de interface, integridade de dados contábeis, cálculos financeiros e fluxos de negócio de ponta a ponta.

### Público-Alvo

- Equipe de desenvolvimento (Squad SIA2)
- QA e revisores de qualidade
- Stakeholders do produto

### Referências

- IEEE 829: Standard for Software Test Documentation
- Playwright Testing Library Documentation
- Jest Testing Framework Documentation
- Código-fonte: `my-app/playwright/specs/` e `my-app/main/tests/`

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

### Testes de Aceitação

Validam regras de negócio críticas e integridade de dados contábeis.

| Módulo | Arquivos | Casos |
| :--- | :---: | :---: |
| Plano de Contas — Integridade | 1 | 2 |
| Diário Geral — Validações | 1 | 11 |
| **Total Aceitação** | **2** | **13** |

### Testes E2E — Fluxos Completos

Simulam fluxos completos de trabalho do usuário real.

| Fluxo | Arquivo | Casos |
| :--- | :--- | :---: |
| Fluxo Contábil Completo | `accounting-workflow.spec.ts` | 3 |
| Fluxo de Apuração | `apuracao-workflow.spec.ts` | 2 |
| Fluxo de DRE | `dre-workflow.spec.ts` | 2 |
| **Total E2E** | **3** | **7** |

### Testes de Integração — Erros de API

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

## Funcionalidades a Não Testar {#funcionalidades-a-não-testar}

| Funcionalidade | Justificativa |
| :--- | :--- |
| Autenticação / Login | Módulo não implementado na versão atual |
| Múltiplas empresas simultâneas | Fora do escopo desta versão |
| Integração com sistemas externos | Não previsto para 2026.1 |
| Testes de carga / performance | Sistema desktop mono-usuário |
| Testes de segurança (pentest) | Cobertos por processo separado |
| Backup e restauração de banco | Fora do escopo desta iteração |

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
| Aceitação | Playwright + Electron | Regras de negócio contábeis |
| E2E | Playwright + Electron | Fluxos de trabalho completos |

### Abordagem de Dados de Teste

- **Fixtures JSON:** dados contábeis padronizados em `playwright/fixtures/`.
- **Setup/Teardown:** cada suite cria e remove seus próprios lançamentos via `beforeAll`/`afterAll`.
- **Estado isolado:** testes não dependem de dados persistentes entre suites.

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

## Critérios de Entrada e Saída {#critérios-de-entrada-e-saída}

### Critérios de Entrada

- Código compilado sem erros em `main` e `renderer`.
- Banco de dados local inicializado com dados de seed do plano de contas padrão.
- Dependências instaladas (`npm install`).

### Critérios de Saída

- Todos os casos de teste executados.
- Taxa de aprovação ≥ 95% nos testes funcionais.
- 100% de aprovação nos testes de aceitação e E2E.
- Nenhum defeito bloqueante (severity 1) em aberto.
- Relatório de testes gerado e revisado.

## Critérios de Aprovação e Reprovação {#critérios-de-aprovação-e-reprovação}

### Aprovação do Ciclo de Teste

| Critério | Threshold |
| :--- | :---: |
| Taxa de aprovação — Unitários | ≥ 98% |
| Taxa de aprovação — Funcional | ≥ 95% |
| Taxa de aprovação — Integração | ≥ 95% |
| Taxa de aprovação — Aceitação | 100% |
| Taxa de aprovação — E2E | 100% |
| Defeitos Severity 1 abertos | 0 |
| Defeitos Severity 2 abertos | ≤ 2 (com mitigação documentada) |

### Severidade de Defeitos

| Severity | Descrição | Exemplos |
| :---: | :--- | :--- |
| S1 — Bloqueante | Impede operação central do sistema | Lançamento não salva, DRE não exibe |
| S2 — Crítico | Comportamento incorreto em função principal | Cálculo errado, filtro não funciona |
| S3 — Moderado | Funcionalidade degradada, workaround possível | Layout quebrado, tooltip ausente |
| S4 — Menor | Problema cosmético sem impacto funcional | Espaçamento, texto truncado |

## Critérios de Suspensão e Retomada {#critérios-de-suspensão-e-retomada}

### Suspensão

Os testes serão suspensos quando:

- Mais de 20% dos casos bloquearem por defeito único de infraestrutura.
- A aplicação não inicializar corretamente no ambiente de teste.
- O banco de dados estiver corrompido ou inacessível.

### Retomada

Os testes serão retomados quando:

- O defeito bloqueante for corrigido e validado.
- O ambiente de teste for restabelecido.
- A suite de smoke test (E2E) passar integralmente.

## Entregas do Teste {#entregas-do-teste}

| Entrega | Descrição |
| :--- | :--- |
| Plano de Teste | Este documento |
| Casos de Teste Funcionais | `casos-de-teste-funcionais.md` |
| Relatório de Testes | `relatorio-de-testes.md` |
| Evidências de Execução | Screenshots / vídeos Playwright (`.playwright-results/`) |
| Relatório de Cobertura Jest | `coverage/` |

## Ambiente de Teste {#ambiente-de-teste}

### Ambiente Local

| Componente | Especificação |
| :--- | :--- |
| SO | Linux (Ubuntu 22.04+) / Windows 11 / macOS 13+ |
| Runtime | Node.js 20+ |
| Banco de Dados | SQLite — arquivo local gerado automaticamente |
| Playwright workers | 1 (serial — Electron não suporta paralelo nativo) |

### Ambiente CI/CD

| Componente | Especificação |
| :--- | :--- |
| Plataforma | GitHub Actions |
| Runner | ubuntu-latest |
| Artefatos | `.playwright-results/`, `coverage/` |
| Trigger | Pull Request → `release-candidate`, `main` |

## Responsabilidades {#responsabilidades}

| Papel | Responsabilidade |
| :--- | :--- |
| Desenvolvedor | Escrever testes unitários; corrigir defeitos encontrados |
| QA / Squad SIA2 | Manter testes Playwright; documentar casos; executar ciclos de teste |
| Tech Lead | Revisar plano e relatório; aprovar critérios de qualidade |
| CI/CD | Executar suites automaticamente em cada PR |

## Riscos e Mitigações {#riscos-e-mitigações}

| Risco | Probabilidade | Impacto | Mitigação |
| :--- | :---: | :---: | :--- |
| Flakiness em testes Playwright (timeouts) | Média | Médio | Revisão de timeouts e locators; retry configurado |
| Dados de seed inconsistentes | Baixa | Alto | Fixtures versionadas no repositório |
| Regressão em módulo não coberto | Baixa | Alto | Ampliar cobertura funcional progressivamente |
| Demora no setup E2E (beforeAll pesado) | Alta | Baixo | Paralelismo controlado; teardown garantido |

## Cronograma {#cronograma}

| Atividade | Status |
| :--- | :--- |
| Implementação de testes unitários | Concluído |
| Implementação de testes funcionais Playwright | Concluído |
| Implementação de testes de aceitação | Concluído |
| Implementação de testes E2E | Concluído |
| Implementação de testes de integração | Concluído |
| Execução do ciclo de testes — release-candidate | Em andamento |
| Geração do relatório final | Em andamento |

## Aprovação {#aprovação}

| Papel | Data | Assinatura |
| :--- | :---: | :--- |
| QA Responsável (Squad SIA2) | 09/06/2026 | |
| Tech Lead | | |
| Product Owner | | |

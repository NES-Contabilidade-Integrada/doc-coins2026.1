# Plano de Teste — NES Coins 2026.1

**Versão:** 1.0
**Data:** 09/06/2026
**Autor:** Squad SIA2
**Referência:** IEEE 829 — Standard for Software Test Documentation

---

## 1. Identificação do Documento

| Campo | Valor |
|---|---|
| Projeto | NES Coins 2026.1 — Sistema Contábil Integrado |
| Versão do Sistema | 2026.1 |
| Branch de Referência | release-candidate |
| Documento | Plano de Teste v1.0 |
| Data de Criação | 09/06/2026 |
| Equipe Responsável | Squad SIA2 |
| Contato | squad-sia2@seazone.com.br |

---

## 2. Introdução

### 2.1 Objetivo

Este documento descreve o planejamento e a abordagem de teste do sistema NES Coins 2026.1, um sistema de contabilidade integrada. O objetivo é definir o escopo, a estratégia, os critérios de qualidade e as responsabilidades associadas às atividades de verificação e validação do software.

### 2.2 Escopo

O plano cobre todos os módulos funcionais da aplicação desktop (Electron + Vue.js), validando comportamento de interface, integridade de dados contábeis, cálculos financeiros e fluxos de negócio de ponta a ponta.

### 2.3 Público-Alvo

- Equipe de desenvolvimento (Squad SIA2)
- QA e revisores de qualidade
- Stakeholders do produto

### 2.4 Referências

- IEEE 829: Standard for Software Test Documentation
- IEEE 830: Software Requirements Specifications
- Playwright Testing Library Documentation
- Jest Testing Framework Documentation
- Código-fonte: `my-app/playwright/specs/` e `my-app/main/tests/`

---

## 3. Itens de Teste

### 3.1 Sistema sob Teste

**NES Coins 2026.1** é uma aplicação desktop de contabilidade empresarial construída com:

- **Frontend:** Vue.js 3 + Vuetify (Electron App)
- **Backend:** Node.js (processo main do Electron)
- **Banco de Dados:** SQLite (local)

### 3.2 Módulos Cobertos

| Módulo | Sigla | Descrição |
|---|---|---|
| Diário Geral | GJ | Registro, edição e exclusão de lançamentos contábeis |
| Razão Geral | GL | Visualização de movimentações por conta |
| Balancete de Verificação | BS | Demonstrativo de saldos devedores e credores |
| Balanço Patrimonial | BP | Demonstração do Ativo, Passivo e Patrimônio Líquido |
| DRE | DRE | Demonstração do Resultado do Exercício |
| Apuração de Resultado | AP | Apuração e encerramento de contas de resultado |
| Plano de Contas | COA | Cadastro e manutenção do plano de contas |
| Empresa | CO | Configuração e identificação da empresa |
| Menu de Navegação | MENU | Estrutura de abas e navegação entre módulos |

### 3.3 Versões e Configurações

| Item | Versão/Configuração |
|---|---|
| Node.js | conforme `.nvmrc` do projeto |
| Playwright | conforme `package.json` |
| Jest | conforme `jest.config.js` |
| SO de Execução | Linux / Windows / macOS |
| Browser (Playwright) | Electron (Chromium embutido) |

---

## 4. Funcionalidades a Testar

### 4.1 Testes Funcionais — Interface e Comportamento (Playwright)

Verificam comportamento visual, navegação, filtros e exibição de dados em cada módulo.

| Módulo | Arquivos | Casos |
|---|---|---|
| Apuração | 4 spec files | 31 casos |
| Balancete | 3 spec files | 12 casos |
| Balanço Patrimonial | 1 spec file | 9 casos |
| Plano de Contas | 1 spec file | 8 casos |
| Empresa | 1 spec file | 1 caso |
| DRE | 4 spec files | 35 casos |
| Diário Geral | 4 spec files | 14 casos |
| Razão Geral | 3 spec files | 14 casos |
| Menu | 1 spec file | 2 casos |
| **Total Funcional** | **22 arquivos** | **128 casos** |

### 4.2 Testes de Aceitação (Playwright)

Validam regras de negócio críticas e integridade de dados contábeis.

| Módulo | Arquivos | Casos |
|---|---|---|
| Plano de Contas — Integridade | 1 spec file | 2 casos |
| Diário Geral — Validações de Lançamento | 1 spec file | 11 casos |
| **Total Aceitação** | **2 arquivos** | **13 casos** |

### 4.3 Testes E2E — Fluxos Completos (Playwright)

Simulam fluxos completos de trabalho do usuário real.

| Fluxo | Arquivo | Casos |
|---|---|---|
| Fluxo Contábil Completo | `accounting-workflow.spec.ts` | 3 casos |
| Fluxo de Apuração | `apuracao-workflow.spec.ts` | 2 casos |
| Fluxo de DRE | `dre-workflow.spec.ts` | 2 casos |
| **Total E2E** | **3 arquivos** | **7 casos** |

### 4.4 Testes de Integração — Tratamento de Erros de API (Playwright)

Verificam comportamento da UI quando a API retorna erros.

| Módulo | Arquivo | Casos |
|---|---|---|
| Apuração | `apuracao/api-errors.spec.ts` | 4 casos |
| Balancete | `balance-sheet/api-errors.spec.ts` | 2 casos |
| DRE | `dre/api-errors.spec.ts` | 10 casos |
| Diário Geral | `general-journal/api-errors.spec.ts` | 3 casos |
| Razão Geral | `general-ledger/api-errors.spec.ts` | 1 caso |
| **Total Integração** | **5 arquivos** | **20 casos** |

### 4.5 Testes Unitários (Jest)

Cobrem lógica de negócio, serviços e controllers do processo main.

| Módulo | Arquivos | Casos |
|---|---|---|
| Apuração | 2 arquivos | 40 casos |
| Balanço Patrimonial | 5 arquivos | 22 casos |
| Demonstração BP (Statement) | 3 arquivos | 35 casos |
| Plano de Contas | 2 arquivos | 13 casos |
| Empresa | 2 arquivos | 12 casos |
| DRE | 2 arquivos | 71 casos |
| Razão Geral | 2 arquivos | 15 casos |
| Diário Geral | 2 arquivos | 56 casos |
| Helpers / Utilitários | 3 arquivos | 36 casos |
| **Total Unitários** | **23 arquivos** | **300 casos** |

---

## 5. Funcionalidades a Não Testar

| Funcionalidade | Justificativa |
|---|---|
| Autenticação / Login | Módulo não implementado na versão atual |
| Múltiplas empresas simultâneas | Fora do escopo desta versão |
| Integração com sistemas externos (ERP, bancos) | Não previsto para 2026.1 |
| Testes de carga / performance | Fora do escopo; sistema desktop mono-usuário |
| Testes de segurança (pentest) | Cobertos por processo separado |
| Backup e restauração de banco | Fora do escopo desta iteração |

---

## 6. Abordagem de Teste

### 6.1 Estratégia Geral

A estratégia adota a pirâmide de testes:

```
        [E2E — 7 casos]
       [Aceitação — 13 casos]
     [Funcional — 128 casos]
    [Integração — 20 casos]
  [Unitários — 300 casos]
```

- **Base larga (unitários):** cobre lógica isolada de serviços e controllers
- **Camada intermediária (funcional/integração):** cobre comportamento da UI e integração com API
- **Topo estreito (E2E):** cobre fluxos críticos de negócio completos

### 6.2 Tipos de Teste

| Tipo | Ferramenta | Escopo |
|---|---|---|
| Unitário | Jest + TypeScript | Serviços, Controllers, Helpers — processo main |
| Funcional | Playwright + Electron | Interface, filtros, cálculos, exibição de dados |
| Integração | Playwright + Electron | Comportamento UI com erros de API (HTTP mocking) |
| Aceitação | Playwright + Electron | Regras de negócio e validações contábeis |
| E2E | Playwright + Electron | Fluxos de trabalho completos do usuário |

### 6.3 Abordagem de Dados de Teste

- **Fixtures JSON:** dados contábeis padronizados em `playwright/fixtures/`
- **Setup/Teardown:** cada suite cria e remove seus próprios lançamentos via `beforeAll`/`afterAll`
- **Estado isolado:** testes não dependem de dados persistentes de outras suites
- **Dados reais:** fixtures utilizam contas do plano de contas padrão da empresa configurada

### 6.4 Ferramentas

| Ferramenta | Finalidade |
|---|---|
| Jest | Execução de testes unitários |
| Playwright | Automação de interface (Electron) |
| TypeScript | Linguagem dos testes |
| Page Object Model | Abstração de locators Playwright |
| GitHub Actions / CI | Execução automatizada em pipeline |

### 6.5 Critérios de Cobertura

- Cobertura de código unitário: mínimo **80%** de linhas nos módulos críticos (DRE, GJ, AP)
- Cobertura funcional: todos os IDs de caso documentados devem ter teste implementado
- Regressão: suites completas executadas antes de cada merge para `release-candidate`

---

## 7. Critérios de Entrada e Saída

### 7.1 Critérios de Entrada (pré-requisitos para iniciar os testes)

- Código compilado sem erros em `main` e `renderer`
- Banco de dados local inicializado com dados de seed do plano de contas padrão
- Variáveis de ambiente de teste configuradas
- Dependências instaladas (`npm install`)

### 7.2 Critérios de Saída (conclusão dos testes)

- Todos os casos de teste executados
- Taxa de aprovação ≥ 95% nos testes funcionais
- 100% de aprovação nos testes de aceitação e E2E
- Nenhum defeito bloqueante (severity 1) em aberto
- Relatório de testes gerado e revisado

---

## 8. Critérios de Aprovação e Reprovação

### 8.1 Aprovação do Ciclo de Teste

| Critério | Threshold |
|---|---|
| Taxa de aprovação — Unitários | ≥ 98% |
| Taxa de aprovação — Funcional | ≥ 95% |
| Taxa de aprovação — Integração | ≥ 95% |
| Taxa de aprovação — Aceitação | 100% |
| Taxa de aprovação — E2E | 100% |
| Defeitos Severity 1 abertos | 0 |
| Defeitos Severity 2 abertos | ≤ 2 (com mitigação documentada) |

### 8.2 Severidade de Defeitos

| Severity | Descrição | Exemplos |
|---|---|---|
| S1 — Bloqueante | Impede operação central do sistema | Lançamento não salva, DRE não exibe |
| S2 — Crítico | Comportamento incorreto em função principal | Cálculo errado no resultado, filtro não funciona |
| S3 — Moderado | Funcionalidade degradada, workaround possível | Layout quebrado, tooltip ausente |
| S4 — Menor | Problema cosmético sem impacto funcional | Espaçamento, texto truncado |

---

## 9. Critérios de Suspensão e Retomada

### 9.1 Suspensão

Os testes serão suspensos quando:
- Mais de 20% dos casos bloquearem por defeito único de infraestrutura
- Aplicação não inicializar corretamente no ambiente de teste
- Banco de dados corrompido ou inacessível

### 9.2 Retomada

Os testes serão retomados quando:
- Defeito bloqueante for corrigido e validado
- Ambiente de teste restabelecido
- Suite de smoke test (E2E) passar integralmente

---

## 10. Entregas do Teste

| Entrega | Descrição | Responsável |
|---|---|---|
| Plano de Teste | Este documento | Squad SIA2 |
| Casos de Teste Funcionais | `casos-de-teste-funcionais.md` | Squad SIA2 |
| Relatório de Testes | `relatorio-de-testes.md` | Squad SIA2 |
| Evidências de Execução | Screenshots / vídeos Playwright (`.playwright-results/`) | CI/CD |
| Relatório de Cobertura Jest | `coverage/` | CI/CD |

---

## 11. Ambiente de Teste

### 11.1 Ambiente Local (desenvolvimento)

| Componente | Especificação |
|---|---|
| SO | Linux (Ubuntu 22.04+) / Windows 11 / macOS 13+ |
| Runtime | Node.js 20+ |
| Electron | conforme `package.json` (devDependencies) |
| Banco de Dados | SQLite — arquivo local gerado automaticamente |
| Playwright workers | 1 (serial — Electron não suporta paralelo nativo) |

### 11.2 Ambiente CI/CD

| Componente | Especificação |
|---|---|
| Plataforma | GitHub Actions |
| Runner | ubuntu-latest |
| Artefatos | `.playwright-results/`, `coverage/` |
| Trigger | Pull Request → `release-candidate`, `main` |

### 11.3 Dados de Teste

- Plano de contas padrão pré-carregado via seed no banco
- Fixtures em `playwright/fixtures/*.json`
- Nenhum dado sensível ou de produção utilizado

---

## 12. Responsabilidades

| Papel | Responsabilidade |
|---|---|
| Desenvolvedor | Escrever testes unitários; corrigir defeitos encontrados |
| QA / Squad SIA2 | Manter testes Playwright; documentar casos; executar ciclos de teste |
| Tech Lead | Revisar plano e relatório; aprovar critérios de qualidade |
| CI/CD | Executar suites automaticamente em cada PR |

---

## 13. Riscos e Mitigações

| Risco | Probabilidade | Impacto | Mitigação |
|---|---|---|---|
| Flakiness em testes Playwright (timeouts) | Média | Médio | Revisão de timeouts e locators; retry configurado |
| Dados de seed inconsistentes entre ambientes | Baixa | Alto | Fixtures versionadas no repositório |
| Ambiente CI diferente do local | Média | Médio | Containerização; testes de smoke no CI |
| Regressão em módulo não coberto por testes | Baixa | Alto | Ampliar cobertura funcional progressivamente |
| Demora no setup E2E (beforeAll pesado) | Alta | Baixo | Paralelismo controlado; teardown garantido |

---

## 14. Cronograma

| Atividade | Responsável | Status |
|---|---|---|
| Escrita do plano de teste | Squad SIA2 | Concluído |
| Implementação de testes unitários | Squad SIA2 | Concluído |
| Implementação de testes funcionais Playwright | Squad SIA2 | Concluído |
| Implementação de testes de aceitação | Squad SIA2 | Concluído |
| Implementação de testes E2E | Squad SIA2 | Concluído |
| Implementação de testes de integração | Squad SIA2 | Concluído |
| Execução do ciclo de testes — release-candidate | Squad SIA2 | Em andamento |
| Geração do relatório final | Squad SIA2 | Em andamento |

---

## 15. Aprovação

| Papel | Nome | Data | Assinatura |
|---|---|---|---|
| Tech Lead | | | |
| QA Responsável | Squad SIA2 | 09/06/2026 | |
| Product Owner | | | |

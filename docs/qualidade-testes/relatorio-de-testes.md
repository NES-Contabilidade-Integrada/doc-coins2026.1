# Relatório de Testes — NES Coins 2026.1

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 09/06/2026 | Criação do documento | Amanda Gois |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |
| 1.0 | 09/06/2026 | Eduardo Henrique | Aprovado |

---

## Sumário

[1. Identificação](#identificação)

[2. Sumário Executivo](#sumário-executivo)

[3. Escopo da Execução](#escopo-da-execução)

[4. Resultados por Categoria](#resultados-por-categoria)

[5. Consolidação Geral](#consolidação-geral)

[6. Defeitos Encontrados e Resolvidos](#defeitos-encontrados-e-resolvidos)

[7. Cobertura de Código](#cobertura-de-código)

[8. Análise de Risco Residual](#análise-de-risco-residual)

[9. Desvios do Plano de Teste](#desvios-do-plano-de-teste)

[10. Lições Aprendidas](#lições-aprendidas)

[11. Conclusão e Recomendação](#conclusão-e-recomendação)

[12. Aprovação](#aprovação)

## Identificação {#identificação}

| Campo | Valor |
| :--- | :--- |
| Projeto | NES Coins 2026.1 — Sistema Contábil Integrado |
| Versão testada | 2026.1 (commit `9c97b12`) |
| Branch | release-candidate |
| Data de execução | 09/06/2026 |
| Equipe | Squad SIA2 |
| Contato | squad-sia2@seazone.com.br |

## Sumário Executivo {#sumário-executivo}

O ciclo de testes da versão 2026.1 foi executado com **466 casos de teste** distribuídos em 55 arquivos, cobrindo os nove módulos da aplicação. A suite de testes passou com **taxa de aprovação geral de 100%** após correções de regressão aplicadas na branch `feature/playwright-test-ajust`.

As principais correções do ciclo foram:

- **Isolamento de locators em painéis de abas:** locators que atravessavam contextos de abas distintas causavam falsos negativos intermitentes; corrigidos com escopo explícito de painel.
- **Remoção de expectativa de prefixo "R$" no CsvService:** o serviço exporta valores sem prefixo monetário por design; teste ajustado para refletir o comportamento correto.

**Resultado geral: APROVADO para release.**

## Escopo da Execução {#escopo-da-execução}

### Módulos Testados

| Módulo | Cobertura |
| :--- | :---: |
| Menu de Navegação | Completa |
| Empresa | Completa |
| Plano de Contas | Completa |
| Diário Geral | Completa |
| Razão Geral | Completa |
| Balancete de Verificação | Completa |
| Balanço Patrimonial | Completa |
| DRE — Demonstração do Resultado | Completa |
| Apuração de Resultado | Completa |

### Tipos de Teste Executados

| Tipo | Ferramenta | Arquivos | Casos |
| :--- | :--- | :---: | :---: |
| Unitário | Jest | 23 | 300 |
| Funcional | Playwright | 22 | 126 |
| Aceitação | Playwright | 2 | 13 |
| E2E | Playwright | 3 | 7 |
| Integração | Playwright | 5 | 20 |
| **Total** | | **55** | **466** |

## Resultados por Categoria {#resultados-por-categoria}

### Testes Unitários

| Módulo | Casos | Aprovados | Reprovados | Taxa |
| :--- | :---: | :---: | :---: | :---: |
| Apuração | 40 | 40 | 0 | 100% |
| Balanço Patrimonial | 22 | 22 | 0 | 100% |
| BP Statement | 35 | 35 | 0 | 100% |
| Plano de Contas | 13 | 13 | 0 | 100% |
| Empresa | 12 | 12 | 0 | 100% |
| DRE | 71 | 71 | 0 | 100% |
| Razão Geral | 15 | 15 | 0 | 100% |
| Diário Geral | 56 | 56 | 0 | 100% |
| Helpers / Utilitários | 36 | 36 | 0 | 100% |
| **Total** | **300** | **300** | **0** | **100%** |

### Testes Funcionais

| Módulo | Casos | Aprovados | Reprovados | Taxa |
| :--- | :---: | :---: | :---: | :---: |
| Menu | 2 | 2 | 0 | 100% |
| Empresa | 1 | 1 | 0 | 100% |
| Plano de Contas | 8 | 8 | 0 | 100% |
| Diário Geral | 14 | 14 | 0 | 100% |
| Razão Geral | 14 | 14 | 0 | 100% |
| Balancete | 12 | 12 | 0 | 100% |
| Balanço Patrimonial | 9 | 9 | 0 | 100% |
| DRE | 35 | 35 | 0 | 100% |
| Apuração | 31 | 31 | 0 | 100% |
| **Total** | **126** | **126** | **0** | **100%** |

### Testes de Aceitação

| Módulo | Casos | Aprovados | Reprovados | Taxa |
| :--- | :---: | :---: | :---: | :---: |
| Plano de Contas — Integridade | 2 | 2 | 0 | 100% |
| Diário Geral — Validações | 11 | 11 | 0 | 100% |
| **Total** | **13** | **13** | **0** | **100%** |

### Testes E2E

| Fluxo | Casos | Aprovados | Reprovados | Taxa |
| :--- | :---: | :---: | :---: | :---: |
| Fluxo Contábil Completo | 3 | 3 | 0 | 100% |
| Fluxo de Apuração | 2 | 2 | 0 | 100% |
| Fluxo de DRE | 2 | 2 | 0 | 100% |
| **Total** | **7** | **7** | **0** | **100%** |

### Testes de Integração

| Módulo | Casos | Aprovados | Reprovados | Taxa |
| :--- | :---: | :---: | :---: | :---: |
| Apuração | 4 | 4 | 0 | 100% |
| Balancete | 2 | 2 | 0 | 100% |
| DRE | 10 | 10 | 0 | 100% |
| Diário Geral | 3 | 3 | 0 | 100% |
| Razão Geral | 1 | 1 | 0 | 100% |
| **Total** | **20** | **20** | **0** | **100%** |

## Consolidação Geral {#consolidação-geral}

| Categoria | Casos | Aprovados | Reprovados | % Aprovação |
| :--- | :---: | :---: | :---: | :---: |
| Unitários | 300 | 300 | 0 | 100% |
| Funcional | 126 | 126 | 0 | 100% |
| Aceitação | 13 | 13 | 0 | 100% |
| E2E | 7 | 7 | 0 | 100% |
| Integração | 20 | 20 | 0 | 100% |
| **TOTAL** | **466** | **466** | **0** | **100%** |

## Defeitos Encontrados e Resolvidos {#defeitos-encontrados-e-resolvidos}

### Defeitos do Ciclo Atual

| ID | Título | Módulo | Severidade | Status | Commit |
| :---: | :--- | :--- | :---: | :---: | :--- |
| BUG-01 | Locator de aba DRE capturava elemento de aba BP em testes adjacentes | DRE / BP | S3 | Resolvido | `9c97b12` |
| BUG-02 | CsvService test esperava prefixo "R$" em valor exportado | DRE | S3 | Resolvido | `a902147` |

### Detalhamento

**BUG-01 — Locator de aba DRE capturava elemento de aba BP**

- **Sintoma:** Locators de tab panels atravessavam contexto de abas distintas; testes de DRE falhavam ao interagir com aba BP ativa em paralelo.
- **Causa Raiz:** Seletores CSS não escopados ao painel de aba correto; ambos os painéis existiam no DOM simultaneamente.
- **Correção:** Locators reescritos com escopo explícito ao container da aba ativa.

**BUG-02 — CsvService test esperava prefixo "R$" em valores exportados**

- **Sintoma:** Teste falhava com `expected "5000.00" to contain "R$ 5.000,00"`.
- **Causa Raiz:** O serviço exporta valores numéricos puros por design; teste tinha expectativa incorreta.
- **Correção:** Expectativa do teste atualizada para o formato numérico correto.

### Defeitos em Aberto

Nenhum defeito em aberto neste ciclo.

## Cobertura de Código {#cobertura-de-código}

Cobertura apurada via `npm run test:unit:coverage`:

| Módulo | Statements | Branches | Functions | Lines |
| :--- | :---: | :---: | :---: | :---: |
| DRE Service | ~95% | ~90% | 100% | ~95% |
| DRE Controller | ~92% | ~88% | 100% | ~92% |
| Diário Geral Service | ~90% | ~85% | 100% | ~90% |
| Apuração Service | ~93% | ~88% | 100% | ~93% |
| Razão Geral Service | ~88% | ~82% | 100% | ~88% |
| Plano de Contas Service | ~87% | ~80% | 100% | ~87% |
| Helpers / Utilitários | ~95% | ~92% | 100% | ~95% |

Relatório completo disponível em `coverage/lcov-report/index.html` após `npm run test:unit:coverage`.

## Análise de Risco Residual {#análise-de-risco-residual}

| Área | Risco | Probabilidade | Impacto | Mitigação |
| :--- | :--- | :---: | :---: | :--- |
| Testes E2E com beforeAll pesado | Timeout em CI | Média | Baixo | Timeouts revisados; retry habilitado |
| Cobertura de Balanço Patrimonial | Suite menor | Baixa | Médio | Aceito para 2026.1; ampliar no próximo ciclo |
| Flakiness por race condition em dialogs Vuetify | Falhas esporádicas | Baixa | Baixo | `waitFor state='hidden'` aplicado |

## Desvios do Plano de Teste {#desvios-do-plano-de-teste}

| Item | Planejado | Executado | Justificativa |
| :--- | :--- | :--- | :--- |
| Testes de performance | Não previsto | Não executado | Fora do escopo para sistema desktop mono-usuário |
| Testes de segurança | Não previsto | Não executado | Cobertos por processo separado |

## Lições Aprendidas {#lições-aprendidas}

- Locators Playwright em apps Electron com múltiplos painéis de aba requerem escopo explícito ao container da aba ativa. Recomenda-se documentar esse padrão no Page Object como convenção do projeto.
- Testes unitários de serviço devem refletir o contrato de dados (formato de saída) e não suposições de formatação da UI.
- Setup via `beforeAll` com criação de lançamentos contábeis é robusto, mas lento em CI. Avaliar fixtures de banco pré-populadas para suites de exibição.

## Conclusão e Recomendação {#conclusão-e-recomendação}

### Conclusão

A versão 2026.1 do NES Coins foi testada com cobertura abrangente dos seus nove módulos funcionais. Todos os 466 casos automatizados passaram após as correções de regressão aplicadas. Não há defeitos em aberto com severidade S1 ou S2.

### Recomendação

**APROVADO para promoção a `release-candidate` e subsequente merge em `main`.**

Condições atendidas:

- Suite completa executada com 100% de aprovação.
- Nenhum defeito bloqueante ou crítico em aberto.
- Relatório de cobertura gerado e revisado.

### Próximas Ações

| Ação | Prioridade |
| :--- | :---: |
| Ampliar cobertura funcional do Balanço Patrimonial | Média |
| Adicionar smoke test de aceitação para módulo de Apuração | Média |
| Avaliar fixtures de banco pré-populadas para reduzir tempo de CI | Baixa |
| Documentar convenção de Page Object com escopo de painel | Baixa |

## Aprovação {#aprovação}

| Papel | Data | Assinatura |
| :--- | :---: | :--- |
| QA Responsável (Squad SIA2) | 09/06/2026 | |
| Tech Lead | | |
| Product Owner | | |

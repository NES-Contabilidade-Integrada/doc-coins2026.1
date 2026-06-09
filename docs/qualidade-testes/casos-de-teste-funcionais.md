# Casos de Teste Funcionais — NES Coins 2026.1

**Versão:** 1.0
**Data:** 09/06/2026
**Autor:** Squad SIA2
**Referência:** IEEE 829 — Test Case Specification

---

## Convenções

### Prioridade
- **Alta:** funcionalidade central do negócio contábil; falha impede uso do sistema
- **Média:** funcionalidade importante; falha degrada a experiência mas há workaround
- **Baixa:** funcionalidade auxiliar; falha cosmética ou raramente exercitada

### Tipo
- **Funcional:** verifica comportamento esperado da interface e dados
- **Aceitação:** valida regra de negócio contábil
- **E2E:** simula fluxo completo do usuário real
- **Integração:** verifica comportamento da UI diante de erros de API

### Status
- **Automatizado:** caso coberto por teste Playwright ou Jest
- **Manual:** caso sem automação

---

## Índice de Módulos

1. [Menu de Navegação](#1-menu-de-navegação)
2. [Empresa](#2-empresa)
3. [Plano de Contas](#3-plano-de-contas)
4. [Diário Geral](#4-diário-geral)
5. [Razão Geral](#5-razão-geral)
6. [Balancete de Verificação](#6-balancete-de-verificação)
7. [Balanço Patrimonial](#7-balanço-patrimonial)
8. [DRE — Demonstração do Resultado](#8-dre--demonstração-do-resultado)
9. [Apuração de Resultado](#9-apuração-de-resultado)
10. [Testes de Aceitação](#10-testes-de-aceitação)
11. [Testes E2E — Fluxos Completos](#11-testes-e2e--fluxos-completos)
12. [Testes de Integração — Erros de API](#12-testes-de-integração--erros-de-api)

---

## 1. Menu de Navegação

**Arquivo:** `playwright/specs/functional/menu/menu.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| MENU-01 | Menu principal exibe todas as abas esperadas | Alta | Funcional | Automatizado |
| MENU-02 | Navegação entre abas altera o conteúdo exibido | Alta | Funcional | Automatizado |

### Detalhamento

---

**MENU-01 — Menu principal exibe todas as abas esperadas**

| Campo | Descrição |
|---|---|
| Pré-condições | Aplicação iniciada com empresa configurada |
| Dados de entrada | N/A |
| Passos | 1. Iniciar a aplicação; 2. Observar o menu lateral/superior de abas |
| Resultado Esperado | As abas Diário Geral, Razão Geral, Balancete, Apuração, Demonstrações e Plano de Contas estão visíveis |
| Critério de Aprovação | Todos os itens de menu estão presentes e clicáveis |

---

**MENU-02 — Navegação entre abas altera o conteúdo exibido**

| Campo | Descrição |
|---|---|
| Pré-condições | Aplicação iniciada |
| Dados de entrada | N/A |
| Passos | 1. Clicar em cada aba do menu; 2. Verificar que o conteúdo do painel muda |
| Resultado Esperado | Cada aba exibe seu respectivo módulo sem erros de renderização |
| Critério de Aprovação | Nenhuma aba exibe tela em branco ou erro de componente |

---

## 2. Empresa

**Arquivo:** `playwright/specs/functional/company/company.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| CO-01 | Dados da empresa são exibidos corretamente | Alta | Funcional | Automatizado |

### Detalhamento

---

**CO-01 — Dados da empresa são exibidos corretamente**

| Campo | Descrição |
|---|---|
| Pré-condições | Empresa cadastrada no banco de dados |
| Dados de entrada | N/A |
| Passos | 1. Navegar até o módulo de Empresa; 2. Verificar campos exibidos |
| Resultado Esperado | Nome, CNPJ e demais dados da empresa são exibidos sem erros |
| Critério de Aprovação | Campos obrigatórios preenchidos e formatados corretamente |

---

## 3. Plano de Contas

**Arquivo:** `playwright/specs/functional/chart-of-accounts/chart-of-accounts.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| COA-01 | Módulo Plano de Contas é acessível pelo menu | Alta | Funcional | Automatizado |
| COA-02 | Lista de contas é exibida com colunas corretas | Alta | Funcional | Automatizado |
| COA-03 | Contas são agrupadas por classe (Ativo, Passivo, etc.) | Alta | Funcional | Automatizado |
| COA-04 | Código e descrição de cada conta são exibidos | Alta | Funcional | Automatizado |
| COA-05 | Natureza D/C de cada conta é exibida | Média | Funcional | Automatizado |
| COA-06 | Filtro ou busca de conta por código funciona | Média | Funcional | Automatizado |
| COA-07 | Hierarquia de contas (pai/filho) é exibida corretamente | Alta | Funcional | Automatizado |
| COA-08 | Contas analíticas são distinguíveis das sintéticas | Média | Funcional | Automatizado |

---

## 4. Diário Geral

**Arquivos:** `playwright/specs/functional/general-journal/*.spec.ts`

### 4.1 Exibição

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| GJ-01 | Módulo Diário Geral exibe tabela de lançamentos | Alta | Funcional | Automatizado |
| GJ-02 | Tabela exibe colunas Data, Débito, Crédito, Histórico, Valor | Alta | Funcional | Automatizado |

### 4.2 CRUD de Lançamentos

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| GJ-03 | Adicionar lançamento simples com sucesso | Alta | Funcional | Automatizado |
| GJ-04 | Adicionar lançamento múltiplo com sucesso | Alta | Funcional | Automatizado |
| GJ-05 | Editar lançamento — alterar valor e histórico | Alta | Funcional | Automatizado |
| GJ-06 | Editar lançamento — adicionar e remover conta | Alta | Funcional | Automatizado |
| GJ-07 | Excluir lançamento individual | Alta | Funcional | Automatizado |
| GJ-08 | Excluir todos os lançamentos | Alta | Funcional | Automatizado |

### 4.3 Funcionalidades Avançadas

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| GJ-09 | Exportar lançamentos para CSV | Média | Funcional | Automatizado |
| GJ-10 | Filtrar lançamentos por período | Média | Funcional | Automatizado |
| GJ-11 | Ordenar lançamentos por coluna | Baixa | Funcional | Automatizado |

### 4.4 Integração Cross-Module

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| GJ-12 | Lançamento criado reflete no Razão Geral | Alta | Funcional | Automatizado |
| GJ-13 | Lançamento criado reflete no Balancete | Alta | Funcional | Automatizado |
| GJ-14 | Lançamento criado reflete na Apuração | Alta | Funcional | Automatizado |

### Detalhamento — Casos Críticos

---

**GJ-03 — Adicionar lançamento simples com sucesso**

| Campo | Descrição |
|---|---|
| Pré-condições | Módulo Diário Geral aberto; plano de contas com contas de débito e crédito disponíveis |
| Dados de entrada | Data: data atual; Débito: código de conta de despesa; Crédito: código de conta de ativo; Valor: R$ 100,00; Histórico: texto livre |
| Passos | 1. Clicar em "Adicionar Lançamento"; 2. Preencher data, conta débito, conta crédito, valor e histórico; 3. Clicar em "Salvar" |
| Resultado Esperado | Toast de sucesso exibido; nova linha aparece na tabela com o histórico informado |
| Critério de Aprovação | `successToast` visível em até 10s; linha com o histórico encontrada na tabela |

---

**GJ-05 — Editar lançamento — alterar valor e histórico**

| Campo | Descrição |
|---|---|
| Pré-condições | Pelo menos um lançamento existente na tabela |
| Dados de entrada | Novo valor: R$ 500,00; Novo histórico: "LANÇAMENTO EDITADO" |
| Passos | 1. Localizar o lançamento na tabela; 2. Clicar no ícone de edição; 3. Alterar valor e histórico; 4. Clicar em "Salvar" |
| Resultado Esperado | Toast "Salvo" ou "Editado com sucesso" exibido; linha atualizada exibe novo valor e histórico |
| Critério de Aprovação | Linha com histórico "LANÇAMENTO EDITADO" e valor "500,00" visível na tabela |

---

**GJ-07 — Excluir lançamento individual**

| Campo | Descrição |
|---|---|
| Pré-condições | Lançamento de teste criado previamente |
| Dados de entrada | N/A |
| Passos | 1. Localizar o lançamento na tabela; 2. Clicar no ícone de exclusão; 3. Confirmar exclusão no dialog |
| Resultado Esperado | Toast de exclusão exibido; linha removida da tabela |
| Critério de Aprovação | `deletedToast` visível; linha do lançamento não encontrada na tabela |

---

**GJ-08 — Excluir todos os lançamentos**

| Campo | Descrição |
|---|---|
| Pré-condições | Pelo menos um lançamento existente |
| Dados de entrada | N/A |
| Passos | 1. Clicar no ícone de engrenagem (opções); 2. Clicar em "Excluir Todos os Lançamentos"; 3. Confirmar no dialog |
| Resultado Esperado | Toast de confirmação exibido; tabela exibe 0 linhas e mensagem de "sem dados" |
| Critério de Aprovação | `allDeletedToast` visível; `tableRows` com count = 0; `noDataMessage` visível |

---

## 5. Razão Geral

**Arquivos:** `playwright/specs/functional/general-ledger/*.spec.ts`

### 5.1 Exibição

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| GL-01 | Módulo Razão Geral é acessível pelo menu | Alta | Funcional | Automatizado |
| GL-02 | Lista de contas com movimentação é exibida | Alta | Funcional | Automatizado |
| GL-03 | Detalhe de movimentações de uma conta é exibido | Alta | Funcional | Automatizado |
| GL-04 | Saldo final de cada conta é exibido | Alta | Funcional | Automatizado |

### 5.2 Filtros

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| GL-05 | Filtro por conta específica funciona | Alta | Funcional | Automatizado |
| GL-06 | Filtro por período (data início) funciona | Alta | Funcional | Automatizado |
| GL-07 | Filtro por período (data fim) funciona | Alta | Funcional | Automatizado |
| GL-08 | Filtro combinado conta + período funciona | Alta | Funcional | Automatizado |
| GL-09 | Limpar filtros restaura listagem completa | Média | Funcional | Automatizado |
| GL-10 | Estado vazio exibido quando nenhum resultado | Média | Funcional | Automatizado |

### 5.3 Cálculos

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| GL-11 | Saldo devedor calculado corretamente | Alta | Funcional | Automatizado |
| GL-12 | Saldo credor calculado corretamente | Alta | Funcional | Automatizado |
| GL-13 | Saldo acumulado por lançamento está correto | Alta | Funcional | Automatizado |
| GL-14 | Saldo final bate com soma dos lançamentos | Alta | Funcional | Automatizado |

---

## 6. Balancete de Verificação

**Arquivos:** `playwright/specs/functional/balance-sheet/*.spec.ts`

### 6.1 Exibição

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| BS-01 | Módulo Balancete é acessível pelo menu | Alta | Funcional | Automatizado |
| BS-02 | Tabela exibe colunas Conta, Saldo Devedor, Saldo Credor | Alta | Funcional | Automatizado |
| BS-03 | Contas com movimentação aparecem na listagem | Alta | Funcional | Automatizado |

### 6.2 Filtros

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| BS-04 | Filtro por período inicial funciona | Alta | Funcional | Automatizado |
| BS-05 | Filtro por período final funciona | Alta | Funcional | Automatizado |
| BS-06 | Filtro combinado de período funciona | Alta | Funcional | Automatizado |
| BS-07 | Filtro por conta funciona | Média | Funcional | Automatizado |
| BS-08 | Filtro por tipo de conta funciona | Média | Funcional | Automatizado |
| BS-09 | Limpar filtros restaura visualização padrão | Baixa | Funcional | Automatizado |

### 6.3 Resumo

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| BS-10 | Seção de resumo exibe totais de débito e crédito | Alta | Funcional | Automatizado |
| BS-11 | Total Devedor = Total Credor (equilíbrio contábil) | Alta | Funcional | Automatizado |
| BS-12 | Exportação do balancete está disponível | Média | Funcional | Automatizado |

### Detalhamento — Caso Crítico

---

**BS-11 — Total Devedor = Total Credor (equilíbrio contábil)**

| Campo | Descrição |
|---|---|
| Pré-condições | Lançamentos contábeis registrados com débito e crédito balanceados |
| Dados de entrada | N/A |
| Passos | 1. Navegar ao Balancete; 2. Verificar seção de resumo; 3. Comparar total devedor com total credor |
| Resultado Esperado | Total Devedor == Total Credor |
| Critério de Aprovação | Valores numéricos dos totais são iguais; não exibe alerta de desbalanceamento |
| Observação | Falha indica lançamento inválido no banco ou bug de cálculo — severity S1 |

---

## 7. Balanço Patrimonial

**Arquivo:** `playwright/specs/functional/balanco-patrimonial/display.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| BP-01 | Aba Balanço Patrimonial está visível em Demonstrações | Alta | Funcional | Automatizado |
| BP-02 | Seção ATIVO é exibida com seus grupos | Alta | Funcional | Automatizado |
| BP-03 | Seção PASSIVO é exibida com seus grupos | Alta | Funcional | Automatizado |
| BP-04 | Seção PATRIMÔNIO LÍQUIDO é exibida | Alta | Funcional | Automatizado |
| BP-05 | Total do Ativo exibido corretamente | Alta | Funcional | Automatizado |
| BP-06 | Total do Passivo + PL exibido corretamente | Alta | Funcional | Automatizado |
| BP-07 | Ativo Total = Passivo Total + PL (equação contábil) | Alta | Funcional | Automatizado |
| BP-08 | Botão Exportar CSV está visível | Média | Funcional | Automatizado |
| BP-09 | Botão Exportar PDF está visível | Média | Funcional | Automatizado |

### Detalhamento — Caso Crítico

---

**BP-07 — Ativo Total = Passivo Total + PL (equação contábil)**

| Campo | Descrição |
|---|---|
| Pré-condições | Apuração de resultado executada; lançamentos balanceados existentes |
| Dados de entrada | N/A |
| Passos | 1. Navegar a Demonstrações → Balanço Patrimonial; 2. Verificar totais de Ativo e Passivo+PL |
| Resultado Esperado | Ativo Total == Passivo Total + Patrimônio Líquido |
| Critério de Aprovação | Valores numéricos iguais; nenhum alerta de desequilíbrio exibido |
| Observação | Equação fundamental da contabilidade; falha indica bug grave — severity S1 |

---

## 8. DRE — Demonstração do Resultado

**Arquivos:** `playwright/specs/functional/dre/*.spec.ts`

### 8.1 Interface e Navegação

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| DRE-UI-01 | Aba DEMONSTRAÇÕES visível no menu | Alta | Funcional | Automatizado |
| DRE-UI-02 | Aba DRE ativa por padrão ao entrar em Demonstrações | Alta | Funcional | Automatizado |
| DRE-UI-03 | Aba BALANÇO PATRIMONIAL visível na seção Demonstrações | Alta | Funcional | Automatizado |
| DRE-UI-04 | Filtro Período Inicial carregado com primeiro dia do ano atual | Média | Funcional | Automatizado |
| DRE-UI-05 | Filtro Período Final carregado com último dia do ano atual | Média | Funcional | Automatizado |
| DRE-UI-06 | Tabela DRE visível com 14 linhas | Alta | Funcional | Automatizado |
| DRE-UI-07 | Tabela DRE tem colunas Ord. / Descrição / Valor / D/C | Alta | Funcional | Automatizado |
| DRE-UI-08 | Linhas de subtotal estão destacadas (highlighted) | Média | Funcional | Automatizado |
| DRE-UI-09 | Linhas da DRE na ordem correta (Receita Bruta → Resultado Líquido) | Alta | Funcional | Automatizado |
| DRE-UI-10 | Card Receita Líquida visível | Alta | Funcional | Automatizado |
| DRE-UI-11 | Card Lucro Bruto visível | Alta | Funcional | Automatizado |
| DRE-UI-12 | Card LAJIR visível | Alta | Funcional | Automatizado |
| DRE-UI-13 | Card LAIR visível | Alta | Funcional | Automatizado |
| DRE-UI-14 | Seção de resultado final visível | Alta | Funcional | Automatizado |
| DRE-UI-15 | Resultado final exibe label do tipo (Lucro, Prejuízo ou Nulo) | Alta | Funcional | Automatizado |
| DRE-UI-16 | Botão Exportar CSV visível | Média | Funcional | Automatizado |
| DRE-UI-17 | Botão Exportar PDF visível | Média | Funcional | Automatizado |
| DRE-UI-18 | Aba BP exibe Balanço Patrimonial ou estado vazio | Alta | Funcional | Automatizado |
| DRE-UI-19 | Seção "COMPOSIÇÃO DAS CONTAS" é exibida | Alta | Funcional | Automatizado |
| DRE-UI-20 | Clique em "Exportar PDF" abre dialog de preview | Média | Funcional | Automatizado |
| DRE-UI-21 | Dialog de preview fecha ao clicar Cancelar | Média | Funcional | Automatizado |

### 8.2 Cálculos

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| DRE-CALC-01 | Receita Bruta exibe soma das receitas brutas | Alta | Funcional | Automatizado |
| DRE-CALC-02 | Deduções calculadas corretamente | Alta | Funcional | Automatizado |
| DRE-CALC-03 | Receita Líquida = Receita Bruta − Deduções | Alta | Funcional | Automatizado |
| DRE-CALC-04 | Custo dos Produtos Vendidos exibido corretamente | Alta | Funcional | Automatizado |
| DRE-CALC-05 | Lucro Bruto = Receita Líquida − CPV | Alta | Funcional | Automatizado |
| DRE-CALC-06 | LAJIR calculado após despesas operacionais | Alta | Funcional | Automatizado |
| DRE-CALC-07 | Resultado Líquido do Período calculado corretamente | Alta | Funcional | Automatizado |
| DRE-CALC-08 | Linha 7 da DRE com dados reais | Alta | Funcional | Automatizado |
| DRE-CALC-09 | Linha 9 da DRE com dados reais | Alta | Funcional | Automatizado |
| DRE-CALC-10 | Linha 11 da DRE com dados reais | Alta | Funcional | Automatizado |
| DRE-CALC-11 | Linha 12 da DRE com dados reais | Alta | Funcional | Automatizado |

### 8.3 Filtros

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| DRE-FLT-01 | Filtro por período inicial altera valores da DRE | Alta | Funcional | Automatizado |
| DRE-FLT-02 | Filtro por período final altera valores da DRE | Alta | Funcional | Automatizado |
| DRE-FLT-03 | Filtro de período completo funciona corretamente | Alta | Funcional | Automatizado |
| DRE-FLT-04 | Filtro com período sem lançamentos exibe zeros | Média | Funcional | Automatizado |
| DRE-FLT-05 | Filtro reseta para padrão (ano atual) ao limpar | Média | Funcional | Automatizado |
| DRE-FLT-06 | Data inválida no filtro exibe mensagem de erro | Média | Funcional | Automatizado |

### Detalhamento — Casos Críticos

---

**DRE-UI-06 — Tabela DRE visível com 14 linhas**

| Campo | Descrição |
|---|---|
| Pré-condições | Apuração executada; lançamentos de receita e despesa existentes |
| Dados de entrada | N/A |
| Passos | 1. Navegar a Demonstrações → DRE; 2. Aguardar carregamento da tabela |
| Resultado Esperado | Tabela visível com exatamente 14 linhas representando as rubricas da DRE |
| Critério de Aprovação | `dreTableRows.count() === 14` |

---

**DRE-UI-09 — Linhas da DRE na ordem correta**

| Campo | Descrição |
|---|---|
| Pré-condições | DRE carregada com dados |
| Dados de entrada | N/A |
| Passos | 1. Verificar conteúdo de cada linha pela posição (index 0, 2, 4, 7, 9, 13) |
| Resultado Esperado | Linha 0: "Receita Bruta"; Linha 2: "Receita Líquida"; Linha 4: "Lucro Bruto"; Linha 7: "LAJIR"; Linha 9: "LAIR"; Linha 13: "Resultado Líquido" |
| Critério de Aprovação | Cada posição contém o texto esperado |

---

**DRE-CALC-07 — Resultado Líquido do Período calculado corretamente**

| Campo | Descrição |
|---|---|
| Pré-condições | Lançamentos de receita (R$ 5.000,00) e despesa (R$ 2.000,00) registrados e apurados |
| Dados de entrada | Receita: R$ 5.000,00; Despesa: R$ 2.000,00 |
| Passos | 1. Navegar à DRE; 2. Verificar linha "Resultado Líquido do Período" |
| Resultado Esperado | Resultado Líquido = R$ 3.000,00 (Lucro) |
| Critério de Aprovação | Linha 13 exibe valor R$ 3.000,00; classificação "C" (credor) |

---

## 9. Apuração de Resultado

**Arquivos:** `playwright/specs/functional/apuracao/*.spec.ts`

### 9.1 Exibição do Módulo

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| AP-01 | Aba APURAÇÃO está visível no menu de abas | Alta | Funcional | Automatizado |
| AP-02 | Card de filtro exibe campo de data e botão de histórico | Alta | Funcional | Automatizado |
| AP-03 | Seção RESUMO DO RESULTADO exibe os três cards de totais | Alta | Funcional | Automatizado |
| AP-04 | Tabela CONTAS DE RESULTADO exibe as cinco colunas corretas | Alta | Funcional | Automatizado |
| AP-05 | Tabela CONTAS DE RESULTADO exibe pelo menos uma linha | Alta | Funcional | Automatizado |
| AP-06 | Seção RESULTADO FINAL exibe tipo e conta destino | Alta | Funcional | Automatizado |
| AP-07 | Botão "Realizar Apuração" está visível e habilitado | Alta | Funcional | Automatizado |
| AP-08 | Modal de histórico abre e fecha corretamente | Média | Funcional | Automatizado |

### 9.2 Cálculos e Lógica

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| AP-CAL-01 | Total de Receitas exibe o valor correto | Alta | Funcional | Automatizado |
| AP-CAL-02 | Total de Custos e Despesas exibe o valor correto | Alta | Funcional | Automatizado |
| AP-CAL-03 | Resultado do período calculado corretamente (receitas − custos) | Alta | Funcional | Automatizado |
| AP-CAL-04 | Tipo de resultado exibido como "Lucro" quando receitas > despesas | Alta | Funcional | Automatizado |
| AP-CAL-05 | Conta destino exibida como "Lucros Acumulados" para resultado positivo | Alta | Funcional | Automatizado |
| AP-CAL-06 | Conta de receita aparece na tabela de contas de resultado | Alta | Funcional | Automatizado |
| AP-CAL-07 | Conta de despesa aparece na tabela de contas de resultado | Alta | Funcional | Automatizado |
| AP-CAL-08 | Tipo de conta exibido como "Receita" e "Custo e Despesa" nas linhas | Média | Funcional | Automatizado |
| AP-CAL-09 | Card Resultado do Período exibe label "Lucro" ou "Prejuízo" | Alta | Funcional | Automatizado |

### 9.3 Cenário de Prejuízo

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| AP-PRE-01 | Resultado negativo exibido como "Prejuízo" | Alta | Funcional | Automatizado |
| AP-PRE-02 | Conta destino para prejuízo é "Prejuízos Acumulados" | Alta | Funcional | Automatizado |
| AP-PRE-03 | Total de Custos supera Total de Receitas nos cards | Alta | Funcional | Automatizado |
| AP-PRE-04 | Resultado do Período exibe valor negativo | Alta | Funcional | Automatizado |
| AP-PRE-05 | Label do card de resultado exibe "Prejuízo" | Alta | Funcional | Automatizado |

### 9.4 Estado Vazio (sem lançamentos)

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| AP-EMPTY-01 | Módulo exibe estado vazio quando não há lançamentos | Média | Funcional | Automatizado |
| AP-EMPTY-02 | Botão "Realizar Apuração" está desabilitado sem lançamentos | Alta | Funcional | Automatizado |
| AP-EMPTY-03 | Cards de totais exibem zero sem lançamentos | Média | Funcional | Automatizado |

### 9.5 Fluxo de Apuração

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| AP-FLOW-01 | Clicar em "Realizar Apuração" abre dialog de confirmação | Alta | Funcional | Automatizado |
| AP-FLOW-02 | Confirmar apuração executa o processo com sucesso | Alta | Funcional | Automatizado |
| AP-FLOW-03 | Após apuração, contas de resultado mostram saldo zerado | Alta | Funcional | Automatizado |
| AP-FLOW-04 | Após apuração, registro aparece no histórico de apurações | Alta | Funcional | Automatizado |
| AP-FLOW-05 | Desfazer apuração restaura contas de resultado | Alta | Funcional | Automatizado |
| AP-FLOW-06 | Cancelar dialog de apuração não executa o processo | Alta | Funcional | Automatizado |

### Detalhamento — Casos Críticos

---

**AP-CAL-03 — Resultado do período calculado corretamente**

| Campo | Descrição |
|---|---|
| Pré-condições | Lançamento de receita (R$ 5.000,00) e despesa (R$ 2.000,00) criados via beforeAll |
| Dados de entrada | Receita: R$ 5.000,00 (VENDA DE PRODUTOS); Despesa: R$ 2.000,00 (SALÁRIOS E ORDENADOS) |
| Passos | 1. Navegar à Apuração; 2. Aguardar carregamento; 3. Verificar card "Resultado do Período" |
| Resultado Esperado | Card exibe R$ 3.000,00 |
| Critério de Aprovação | `getResultAmount()` contém "3.000,00" |

---

**AP-FLOW-02 — Confirmar apuração executa o processo com sucesso**

| Campo | Descrição |
|---|---|
| Pré-condições | Contas de resultado com saldos; data de apuração preenchida |
| Dados de entrada | Data: data atual |
| Passos | 1. Clicar em "Realizar Apuração"; 2. Confirmar no dialog; 3. Aguardar conclusão |
| Resultado Esperado | Módulo exibe "Não há valores a serem apurados"; contas de resultado zeradas |
| Critério de Aprovação | `emptyState` contém texto "Não há valores a serem apurados" em até 20s |

---

**AP-FLOW-05 — Desfazer apuração restaura contas de resultado**

| Campo | Descrição |
|---|---|
| Pré-condições | Pelo menos uma apuração registrada no histórico |
| Dados de entrada | N/A |
| Passos | 1. Abrir modal de histórico; 2. Clicar em "Desfazer" na última apuração; 3. Confirmar |
| Resultado Esperado | Modal fecha; contas de resultado restauradas com saldos anteriores |
| Critério de Aprovação | Modal de histórico fecha em até 15s; módulo retorna ao estado com contas de resultado |

---

## 10. Testes de Aceitação

### 10.1 Plano de Contas — Integridade

**Arquivo:** `playwright/specs/acceptance/chart-of-accounts/account-integrity.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| ACC-COA-01 | Contas do plano atendem às regras de integridade referencial | Alta | Aceitação | Automatizado |
| ACC-COA-02 | Estrutura hierárquica do plano de contas é válida | Alta | Aceitação | Automatizado |

### 10.2 Diário Geral — Validações de Lançamento

**Arquivo:** `playwright/specs/acceptance/general-journal/journal-entry-validations.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| REG-GJ-01 | Lançamento com débito diferente de crédito é rejeitado | Alta | Aceitação | Automatizado |
| REG-GJ-02 | Lançamento sem data é rejeitado | Alta | Aceitação | Automatizado |
| REG-GJ-03 | Lançamento sem histórico é rejeitado | Média | Aceitação | Automatizado |
| REG-GJ-04 | Lançamento com conta inválida é rejeitado | Alta | Aceitação | Automatizado |
| REG-GJ-05 | Lançamento com valor zero é rejeitado | Alta | Aceitação | Automatizado |
| REG-GJ-06 | Lançamento com valor negativo é rejeitado | Alta | Aceitação | Automatizado |
| REG-GJ-07 | Lançamento com uma só conta (sem par D/C) é rejeitado | Alta | Aceitação | Automatizado |
| REG-GJ-08 | Lançamento múltiplo balanceado é aceito | Alta | Aceitação | Automatizado |
| REG-GJ-09 | Lançamento múltiplo desbalanceado é rejeitado | Alta | Aceitação | Automatizado |
| REG-GJ-10 | Data futura em lançamento é tratada corretamente | Média | Aceitação | Automatizado |
| REG-GJ-11 | Data inválida (formato errado) é rejeitada | Média | Aceitação | Automatizado |

---

## 11. Testes E2E — Fluxos Completos

### 11.1 Fluxo Contábil Completo

**Arquivo:** `playwright/specs/e2e/accounting-workflow.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| E2E-01 | Fluxo: criar lançamento → verificar Razão Geral | Alta | E2E | Automatizado |
| E2E-02 | Fluxo: criar lançamento → verificar Balancete | Alta | E2E | Automatizado |
| E2E-03 | Fluxo: criar lançamentos → verificar DRE atualizada | Alta | E2E | Automatizado |

### 11.2 Fluxo de Apuração

**Arquivo:** `playwright/specs/e2e/apuracao-workflow.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| E2E-AP-01 | Fluxo completo: lançamentos → apuração → DRE reflete resultado | Alta | E2E | Automatizado |
| E2E-AP-02 | Fluxo: apuração → desfazer → contas restauradas | Alta | E2E | Automatizado |

### 11.3 Fluxo de DRE

**Arquivo:** `playwright/specs/e2e/dre-workflow.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| E2E-DRE-01 | Fluxo: lançamentos de receita e despesa → DRE exibe lucro | Alta | E2E | Automatizado |
| E2E-DRE-02 | Fluxo: lançamentos com despesa > receita → DRE exibe prejuízo | Alta | E2E | Automatizado |

---

## 12. Testes de Integração — Erros de API

### 12.1 Apuração

**Arquivo:** `playwright/specs/integration/apuracao/api-errors.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| AP-INT-01 | Erro de API na carga do módulo exibe mensagem de erro | Alta | Integração | Automatizado |
| AP-INT-02 | Erro de API ao realizar apuração exibe feedback ao usuário | Alta | Integração | Automatizado |
| AP-INT-03 | Erro de API ao carregar histórico exibe estado de erro | Média | Integração | Automatizado |
| AP-INT-04 | Erro de API ao desfazer apuração exibe mensagem | Alta | Integração | Automatizado |

### 12.2 Balancete

**Arquivo:** `playwright/specs/integration/balance-sheet/api-errors.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| INT-BS-01 | Erro de API na carga do Balancete exibe estado de erro | Alta | Integração | Automatizado |
| INT-BS-02 | Erro de API com filtro aplicado exibe mensagem adequada | Média | Integração | Automatizado |

### 12.3 DRE

**Arquivo:** `playwright/specs/integration/dre/api-errors.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| DRE-INT-01 | Erro de API na carga inicial da DRE exibe estado de erro | Alta | Integração | Automatizado |
| DRE-INT-02 | Erro 500 exibe mensagem genérica de erro | Alta | Integração | Automatizado |
| DRE-INT-03 | Erro de rede exibe feedback ao usuário | Alta | Integração | Automatizado |
| DRE-INT-04 | Erro ao exportar CSV exibe mensagem de falha | Média | Integração | Automatizado |
| DRE-INT-05 | Erro ao exportar PDF exibe mensagem de falha | Média | Integração | Automatizado |
| DRE-INT-06 | Timeout de API exibe indicador de carregamento e erro | Média | Integração | Automatizado |
| DRE-INT-07 | Erro em filtro de período exibe mensagem | Média | Integração | Automatizado |
| DRE-INT-08 | Erro 404 exibe estado vazio com mensagem | Média | Integração | Automatizado |
| DRE-INT-09 | Retry após erro funciona corretamente | Baixa | Integração | Automatizado |
| DRE-INT-10 | Múltiplos erros consecutivos mantêm UI estável | Baixa | Integração | Automatizado |

### 12.4 Diário Geral

**Arquivo:** `playwright/specs/integration/general-journal/api-errors.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| INT-GJ-01 | Erro ao salvar lançamento exibe mensagem de falha | Alta | Integração | Automatizado |
| INT-GJ-02 | Erro ao excluir lançamento exibe mensagem de falha | Alta | Integração | Automatizado |
| INT-GJ-03 | Erro na carga da lista de lançamentos exibe estado de erro | Alta | Integração | Automatizado |

### 12.5 Razão Geral

**Arquivo:** `playwright/specs/integration/general-ledger/api-errors.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
|---|---|---|---|---|
| INT-GL-01 | Erro de API no Razão Geral exibe estado de erro | Alta | Integração | Automatizado |

---

## Resumo Geral

| Categoria | Módulo | Casos |
|---|---|---|
| Funcional | Menu | 2 |
| Funcional | Empresa | 1 |
| Funcional | Plano de Contas | 8 |
| Funcional | Diário Geral | 14 |
| Funcional | Razão Geral | 14 |
| Funcional | Balancete | 12 |
| Funcional | Balanço Patrimonial | 9 |
| Funcional | DRE | 35 |
| Funcional | Apuração | 31 |
| **Subtotal Funcional** | | **126** |
| Aceitação | Plano de Contas | 2 |
| Aceitação | Diário Geral | 11 |
| **Subtotal Aceitação** | | **13** |
| E2E | Fluxo Contábil | 3 |
| E2E | Fluxo Apuração | 2 |
| E2E | Fluxo DRE | 2 |
| **Subtotal E2E** | | **7** |
| Integração | Apuração | 4 |
| Integração | Balancete | 2 |
| Integração | DRE | 10 |
| Integração | Diário Geral | 3 |
| Integração | Razão Geral | 1 |
| **Subtotal Integração** | | **20** |
| **TOTAL PLAYWRIGHT** | | **166** |
| Unitários | Todos os módulos | 300 |
| **TOTAL GERAL** | | **466** |

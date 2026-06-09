# Casos de Teste Funcionais — NES Coins 2026.1

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

[1. Convenções](#convenções)

[2. Menu de Navegação](#menu-de-navegação)

[3. Empresa](#empresa)

[4. Plano de Contas](#plano-de-contas)

[5. Diário Geral](#diário-geral)

[6. Razão Geral](#razão-geral)

[7. Balancete de Verificação](#balancete-de-verificação)

[8. Balanço Patrimonial](#balanço-patrimonial)

[9. DRE — Demonstração do Resultado](#dre--demonstração-do-resultado)

[10. Apuração de Resultado](#apuração-de-resultado)

[11. Testes de Aceitação](#testes-de-aceitação)

[12. Testes E2E — Fluxos Completos](#testes-e2e--fluxos-completos)

[13. Testes de Integração — Erros de API](#testes-de-integração--erros-de-api)

[14. Resumo Geral](#resumo-geral)

## Convenções {#convenções}

### Prioridade

- **Alta:** funcionalidade central do negócio contábil; falha impede uso do sistema.
- **Média:** funcionalidade importante; falha degrada a experiência mas há workaround.
- **Baixa:** funcionalidade auxiliar; falha cosmética ou raramente exercitada.

### Tipo

- **Funcional:** verifica comportamento esperado da interface e dados.
- **Aceitação:** valida regra de negócio contábil.
- **E2E:** simula fluxo completo do usuário real.
- **Integração:** verifica comportamento da UI diante de erros de API.

### Status

- **Automatizado:** caso coberto por teste Playwright ou Jest.
- **Manual:** caso sem automação.

## Menu de Navegação {#menu-de-navegação}

**Arquivo:** `playwright/specs/functional/menu/menu.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| MENU-01 | Menu principal exibe todas as abas esperadas | Alta | Funcional | Automatizado |
| MENU-02 | Navegação entre abas altera o conteúdo exibido | Alta | Funcional | Automatizado |

### Detalhamento

**MENU-01 — Menu principal exibe todas as abas esperadas**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Aplicação iniciada com empresa configurada |
| Passos | 1. Iniciar a aplicação; 2. Observar o menu de abas |
| Resultado Esperado | Abas Diário Geral, Razão Geral, Balancete, Apuração, Demonstrações e Plano de Contas visíveis |
| Critério de Aprovação | Todos os itens de menu presentes e clicáveis |

**MENU-02 — Navegação entre abas altera o conteúdo exibido**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Aplicação iniciada |
| Passos | 1. Clicar em cada aba do menu; 2. Verificar que o conteúdo muda |
| Resultado Esperado | Cada aba exibe seu respectivo módulo sem erros de renderização |
| Critério de Aprovação | Nenhuma aba exibe tela em branco ou erro de componente |

## Empresa {#empresa}

**Arquivo:** `playwright/specs/functional/company/company.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| CO-01 | Dados da empresa são exibidos corretamente | Alta | Funcional | Automatizado |

## Plano de Contas {#plano-de-contas}

**Arquivo:** `playwright/specs/functional/chart-of-accounts/chart-of-accounts.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| COA-01 | Módulo Plano de Contas é acessível pelo menu | Alta | Funcional | Automatizado |
| COA-02 | Lista de contas é exibida com colunas corretas | Alta | Funcional | Automatizado |
| COA-03 | Contas são agrupadas por classe (Ativo, Passivo, etc.) | Alta | Funcional | Automatizado |
| COA-04 | Código e descrição de cada conta são exibidos | Alta | Funcional | Automatizado |
| COA-05 | Natureza D/C de cada conta é exibida | Média | Funcional | Automatizado |
| COA-06 | Filtro ou busca de conta por código funciona | Média | Funcional | Automatizado |
| COA-07 | Hierarquia de contas (pai/filho) é exibida corretamente | Alta | Funcional | Automatizado |
| COA-08 | Contas analíticas são distinguíveis das sintéticas | Média | Funcional | Automatizado |

## Diário Geral {#diário-geral}

**Arquivos:** `playwright/specs/functional/general-journal/*.spec.ts`

### Exibição

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| GJ-01 | Módulo Diário Geral exibe tabela de lançamentos | Alta | Funcional | Automatizado |
| GJ-02 | Tabela exibe colunas Data, Débito, Crédito, Histórico, Valor | Alta | Funcional | Automatizado |

### CRUD de Lançamentos

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| GJ-03 | Adicionar lançamento simples com sucesso | Alta | Funcional | Automatizado |
| GJ-04 | Adicionar lançamento múltiplo com sucesso | Alta | Funcional | Automatizado |
| GJ-05 | Editar lançamento — alterar valor e histórico | Alta | Funcional | Automatizado |
| GJ-06 | Editar lançamento — adicionar e remover conta | Alta | Funcional | Automatizado |
| GJ-07 | Excluir lançamento individual | Alta | Funcional | Automatizado |
| GJ-08 | Excluir todos os lançamentos | Alta | Funcional | Automatizado |

### Funcionalidades Avançadas

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| GJ-09 | Exportar lançamentos para CSV | Média | Funcional | Automatizado |
| GJ-10 | Filtrar lançamentos por período | Média | Funcional | Automatizado |
| GJ-11 | Ordenar lançamentos por coluna | Baixa | Funcional | Automatizado |

### Integração Cross-Module

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| GJ-12 | Lançamento criado reflete no Razão Geral | Alta | Funcional | Automatizado |
| GJ-13 | Lançamento criado reflete no Balancete | Alta | Funcional | Automatizado |
| GJ-14 | Lançamento criado reflete na Apuração | Alta | Funcional | Automatizado |

### Detalhamento — Casos Críticos

**GJ-03 — Adicionar lançamento simples com sucesso**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Módulo Diário Geral aberto; plano de contas com contas disponíveis |
| Dados de entrada | Data: data atual; Débito: código de conta de despesa; Crédito: código de conta de ativo; Valor: R$ 100,00; Histórico: texto livre |
| Passos | 1. Clicar em "Adicionar Lançamento"; 2. Preencher campos; 3. Clicar em "Salvar" |
| Resultado Esperado | Toast de sucesso exibido; nova linha aparece na tabela com o histórico informado |
| Critério de Aprovação | `successToast` visível em até 10s; linha com o histórico encontrada na tabela |

**GJ-07 — Excluir lançamento individual**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Lançamento de teste existente na tabela |
| Passos | 1. Localizar o lançamento; 2. Clicar no ícone de exclusão; 3. Confirmar no dialog |
| Resultado Esperado | Toast de exclusão exibido; linha removida da tabela |
| Critério de Aprovação | `deletedToast` visível; linha do lançamento não encontrada na tabela |

**GJ-08 — Excluir todos os lançamentos**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Pelo menos um lançamento existente |
| Passos | 1. Clicar no ícone de engrenagem; 2. Clicar em "Excluir Todos os Lançamentos"; 3. Confirmar |
| Resultado Esperado | Toast de confirmação exibido; tabela exibe 0 linhas e mensagem "sem dados" |
| Critério de Aprovação | `allDeletedToast` visível; `tableRows` count = 0; `noDataMessage` visível |

## Razão Geral {#razão-geral}

**Arquivos:** `playwright/specs/functional/general-ledger/*.spec.ts`

### Exibição

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| GL-01 | Módulo Razão Geral é acessível pelo menu | Alta | Funcional | Automatizado |
| GL-02 | Lista de contas com movimentação é exibida | Alta | Funcional | Automatizado |
| GL-03 | Detalhe de movimentações de uma conta é exibido | Alta | Funcional | Automatizado |
| GL-04 | Saldo final de cada conta é exibido | Alta | Funcional | Automatizado |

### Filtros

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| GL-05 | Filtro por conta específica funciona | Alta | Funcional | Automatizado |
| GL-06 | Filtro por período (data início) funciona | Alta | Funcional | Automatizado |
| GL-07 | Filtro por período (data fim) funciona | Alta | Funcional | Automatizado |
| GL-08 | Filtro combinado conta + período funciona | Alta | Funcional | Automatizado |
| GL-09 | Limpar filtros restaura listagem completa | Média | Funcional | Automatizado |
| GL-10 | Estado vazio exibido quando nenhum resultado | Média | Funcional | Automatizado |

### Cálculos

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| GL-11 | Saldo devedor calculado corretamente | Alta | Funcional | Automatizado |
| GL-12 | Saldo credor calculado corretamente | Alta | Funcional | Automatizado |
| GL-13 | Saldo acumulado por lançamento está correto | Alta | Funcional | Automatizado |
| GL-14 | Saldo final bate com soma dos lançamentos | Alta | Funcional | Automatizado |

## Balancete de Verificação {#balancete-de-verificação}

**Arquivos:** `playwright/specs/functional/balance-sheet/*.spec.ts`

### Exibição

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| BS-01 | Módulo Balancete é acessível pelo menu | Alta | Funcional | Automatizado |
| BS-02 | Tabela exibe colunas Conta, Saldo Devedor, Saldo Credor | Alta | Funcional | Automatizado |
| BS-03 | Contas com movimentação aparecem na listagem | Alta | Funcional | Automatizado |

### Filtros

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| BS-04 | Filtro por período inicial funciona | Alta | Funcional | Automatizado |
| BS-05 | Filtro por período final funciona | Alta | Funcional | Automatizado |
| BS-06 | Filtro combinado de período funciona | Alta | Funcional | Automatizado |
| BS-07 | Filtro por conta funciona | Média | Funcional | Automatizado |
| BS-08 | Filtro por tipo de conta funciona | Média | Funcional | Automatizado |
| BS-09 | Limpar filtros restaura visualização padrão | Baixa | Funcional | Automatizado |

### Resumo

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| BS-10 | Seção de resumo exibe totais de débito e crédito | Alta | Funcional | Automatizado |
| BS-11 | Total Devedor = Total Credor (equilíbrio contábil) | Alta | Funcional | Automatizado |
| BS-12 | Exportação do balancete está disponível | Média | Funcional | Automatizado |

### Detalhamento — Caso Crítico

**BS-11 — Total Devedor = Total Credor (equilíbrio contábil)**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Lançamentos contábeis registrados com débito e crédito balanceados |
| Passos | 1. Navegar ao Balancete; 2. Verificar seção de resumo; 3. Comparar totais devedor e credor |
| Resultado Esperado | Total Devedor == Total Credor |
| Critério de Aprovação | Valores iguais; nenhum alerta de desbalanceamento exibido |
| Observação | Falha indica lançamento inválido ou bug de cálculo — severity S1 |

## Balanço Patrimonial {#balanço-patrimonial}

**Arquivo:** `playwright/specs/functional/balanco-patrimonial/display.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| BP-01 | Aba Balanço Patrimonial está visível em Demonstrações | Alta | Funcional | Automatizado |
| BP-02 | Seção ATIVO é exibida com seus grupos | Alta | Funcional | Automatizado |
| BP-03 | Seção PASSIVO é exibida com seus grupos | Alta | Funcional | Automatizado |
| BP-04 | Seção PATRIMÔNIO LÍQUIDO é exibida | Alta | Funcional | Automatizado |
| BP-05 | Total do Ativo exibido corretamente | Alta | Funcional | Automatizado |
| BP-06 | Total do Passivo + PL exibido corretamente | Alta | Funcional | Automatizado |
| BP-07 | Ativo Total = Passivo Total + PL (equação contábil) | Alta | Funcional | Automatizado |
| BP-08 | Botão Exportar CSV está visível | Média | Funcional | Automatizado |
| BP-09 | Botão Exportar PDF está visível | Média | Funcional | Automatizado |

## DRE — Demonstração do Resultado {#dre--demonstração-do-resultado}

**Arquivos:** `playwright/specs/functional/dre/*.spec.ts`

### Interface e Navegação

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| DRE-UI-01 | Aba DEMONSTRAÇÕES visível no menu | Alta | Funcional | Automatizado |
| DRE-UI-02 | Aba DRE ativa por padrão ao entrar em Demonstrações | Alta | Funcional | Automatizado |
| DRE-UI-03 | Aba BALANÇO PATRIMONIAL visível na seção Demonstrações | Alta | Funcional | Automatizado |
| DRE-UI-04 | Filtro Período Inicial carregado com primeiro dia do ano atual | Média | Funcional | Automatizado |
| DRE-UI-05 | Filtro Período Final carregado com último dia do ano atual | Média | Funcional | Automatizado |
| DRE-UI-06 | Tabela DRE visível com 14 linhas | Alta | Funcional | Automatizado |
| DRE-UI-07 | Tabela DRE tem colunas Ord. / Descrição / Valor / D/C | Alta | Funcional | Automatizado |
| DRE-UI-08 | Linhas de subtotal estão destacadas (highlighted) | Média | Funcional | Automatizado |
| DRE-UI-09 | Linhas da DRE na ordem correta | Alta | Funcional | Automatizado |
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

### Cálculos

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
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

### Filtros

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| DRE-FLT-01 | Filtro por período inicial altera valores da DRE | Alta | Funcional | Automatizado |
| DRE-FLT-02 | Filtro por período final altera valores da DRE | Alta | Funcional | Automatizado |
| DRE-FLT-03 | Filtro de período completo funciona corretamente | Alta | Funcional | Automatizado |
| DRE-FLT-04 | Filtro com período sem lançamentos exibe zeros | Média | Funcional | Automatizado |
| DRE-FLT-05 | Filtro reseta para padrão (ano atual) ao limpar | Média | Funcional | Automatizado |
| DRE-FLT-06 | Data inválida no filtro exibe mensagem de erro | Média | Funcional | Automatizado |

### Detalhamento — Caso Crítico

**DRE-CALC-07 — Resultado Líquido do Período calculado corretamente**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Lançamentos de receita (R$ 5.000,00) e despesa (R$ 2.000,00) registrados e apurados |
| Passos | 1. Navegar à DRE; 2. Verificar linha "Resultado Líquido do Período" |
| Resultado Esperado | Resultado Líquido = R$ 3.000,00 (Lucro) |
| Critério de Aprovação | Linha 13 exibe valor 3.000,00; classificação "C" (credor) |

## Apuração de Resultado {#apuração-de-resultado}

**Arquivos:** `playwright/specs/functional/apuracao/*.spec.ts`

### Exibição do Módulo

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| AP-01 | Aba APURAÇÃO está visível no menu de abas | Alta | Funcional | Automatizado |
| AP-02 | Card de filtro exibe campo de data e botão de histórico | Alta | Funcional | Automatizado |
| AP-03 | Seção RESUMO DO RESULTADO exibe os três cards de totais | Alta | Funcional | Automatizado |
| AP-04 | Tabela CONTAS DE RESULTADO exibe as cinco colunas corretas | Alta | Funcional | Automatizado |
| AP-05 | Tabela CONTAS DE RESULTADO exibe pelo menos uma linha | Alta | Funcional | Automatizado |
| AP-06 | Seção RESULTADO FINAL exibe tipo e conta destino | Alta | Funcional | Automatizado |
| AP-07 | Botão "Realizar Apuração" está visível e habilitado | Alta | Funcional | Automatizado |
| AP-08 | Modal de histórico abre e fecha corretamente | Média | Funcional | Automatizado |

### Cálculos e Lógica

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| AP-CAL-01 | Total de Receitas exibe o valor correto | Alta | Funcional | Automatizado |
| AP-CAL-02 | Total de Custos e Despesas exibe o valor correto | Alta | Funcional | Automatizado |
| AP-CAL-03 | Resultado do período calculado corretamente (receitas − custos) | Alta | Funcional | Automatizado |
| AP-CAL-04 | Tipo de resultado exibido como "Lucro" quando receitas > despesas | Alta | Funcional | Automatizado |
| AP-CAL-05 | Conta destino exibida como "Lucros Acumulados" para resultado positivo | Alta | Funcional | Automatizado |
| AP-CAL-06 | Conta de receita aparece na tabela de contas de resultado | Alta | Funcional | Automatizado |
| AP-CAL-07 | Conta de despesa aparece na tabela de contas de resultado | Alta | Funcional | Automatizado |
| AP-CAL-08 | Tipo de conta exibido como "Receita" e "Custo e Despesa" nas linhas | Média | Funcional | Automatizado |
| AP-CAL-09 | Card Resultado do Período exibe label "Lucro" ou "Prejuízo" | Alta | Funcional | Automatizado |

### Cenário de Prejuízo

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| AP-PRE-01 | Resultado negativo exibido como "Prejuízo" | Alta | Funcional | Automatizado |
| AP-PRE-02 | Conta destino para prejuízo é "Prejuízos Acumulados" | Alta | Funcional | Automatizado |
| AP-PRE-03 | Total de Custos supera Total de Receitas nos cards | Alta | Funcional | Automatizado |
| AP-PRE-04 | Resultado do Período exibe valor negativo | Alta | Funcional | Automatizado |
| AP-PRE-05 | Label do card de resultado exibe "Prejuízo" | Alta | Funcional | Automatizado |

### Estado Vazio

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| AP-EMPTY-01 | Módulo exibe estado vazio quando não há lançamentos | Média | Funcional | Automatizado |
| AP-EMPTY-02 | Botão "Realizar Apuração" está desabilitado sem lançamentos | Alta | Funcional | Automatizado |
| AP-EMPTY-03 | Cards de totais exibem zero sem lançamentos | Média | Funcional | Automatizado |

### Fluxo de Apuração

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| AP-FLOW-01 | Clicar em "Realizar Apuração" abre dialog de confirmação | Alta | Funcional | Automatizado |
| AP-FLOW-02 | Confirmar apuração executa o processo com sucesso | Alta | Funcional | Automatizado |
| AP-FLOW-03 | Após apuração, contas de resultado mostram saldo zerado | Alta | Funcional | Automatizado |
| AP-FLOW-04 | Após apuração, registro aparece no histórico de apurações | Alta | Funcional | Automatizado |
| AP-FLOW-05 | Desfazer apuração restaura contas de resultado | Alta | Funcional | Automatizado |
| AP-FLOW-06 | Cancelar dialog de apuração não executa o processo | Alta | Funcional | Automatizado |

### Detalhamento — Casos Críticos

**AP-CAL-03 — Resultado do período calculado corretamente**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Lançamento de receita (R$ 5.000,00) e despesa (R$ 2.000,00) criados |
| Passos | 1. Navegar à Apuração; 2. Aguardar carregamento; 3. Verificar card "Resultado do Período" |
| Resultado Esperado | Card exibe R$ 3.000,00 |
| Critério de Aprovação | `getResultAmount()` contém "3.000,00" |

**AP-FLOW-02 — Confirmar apuração executa o processo com sucesso**

| Campo | Descrição |
| :--- | :--- |
| Pré-condições | Contas de resultado com saldos; data de apuração preenchida |
| Passos | 1. Clicar em "Realizar Apuração"; 2. Confirmar no dialog; 3. Aguardar conclusão |
| Resultado Esperado | Módulo exibe "Não há valores a serem apurados" |
| Critério de Aprovação | `emptyState` contém texto esperado em até 20s |

## Testes de Aceitação {#testes-de-aceitação}

### Plano de Contas — Integridade

**Arquivo:** `playwright/specs/acceptance/chart-of-accounts/account-integrity.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| ACC-COA-01 | Contas do plano atendem às regras de integridade referencial | Alta | Aceitação | Automatizado |
| ACC-COA-02 | Estrutura hierárquica do plano de contas é válida | Alta | Aceitação | Automatizado |

### Diário Geral — Validações de Lançamento

**Arquivo:** `playwright/specs/acceptance/general-journal/journal-entry-validations.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
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

## Testes E2E — Fluxos Completos {#testes-e2e--fluxos-completos}

### Fluxo Contábil Completo

**Arquivo:** `playwright/specs/e2e/accounting-workflow.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| E2E-01 | Fluxo: criar lançamento → verificar Razão Geral | Alta | E2E | Automatizado |
| E2E-02 | Fluxo: criar lançamento → verificar Balancete | Alta | E2E | Automatizado |
| E2E-03 | Fluxo: criar lançamentos → verificar DRE atualizada | Alta | E2E | Automatizado |

### Fluxo de Apuração

**Arquivo:** `playwright/specs/e2e/apuracao-workflow.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| E2E-AP-01 | Fluxo completo: lançamentos → apuração → DRE reflete resultado | Alta | E2E | Automatizado |
| E2E-AP-02 | Fluxo: apuração → desfazer → contas restauradas | Alta | E2E | Automatizado |

### Fluxo de DRE

**Arquivo:** `playwright/specs/e2e/dre-workflow.spec.ts`

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| E2E-DRE-01 | Fluxo: lançamentos de receita e despesa → DRE exibe lucro | Alta | E2E | Automatizado |
| E2E-DRE-02 | Fluxo: lançamentos com despesa > receita → DRE exibe prejuízo | Alta | E2E | Automatizado |

## Testes de Integração — Erros de API {#testes-de-integração--erros-de-api}

### Apuração

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| AP-INT-01 | Erro de API na carga do módulo exibe mensagem de erro | Alta | Integração | Automatizado |
| AP-INT-02 | Erro de API ao realizar apuração exibe feedback ao usuário | Alta | Integração | Automatizado |
| AP-INT-03 | Erro de API ao carregar histórico exibe estado de erro | Média | Integração | Automatizado |
| AP-INT-04 | Erro de API ao desfazer apuração exibe mensagem | Alta | Integração | Automatizado |

### Balancete

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| INT-BS-01 | Erro de API na carga do Balancete exibe estado de erro | Alta | Integração | Automatizado |
| INT-BS-02 | Erro de API com filtro aplicado exibe mensagem adequada | Média | Integração | Automatizado |

### DRE

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
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

### Diário Geral

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| INT-GJ-01 | Erro ao salvar lançamento exibe mensagem de falha | Alta | Integração | Automatizado |
| INT-GJ-02 | Erro ao excluir lançamento exibe mensagem de falha | Alta | Integração | Automatizado |
| INT-GJ-03 | Erro na carga da lista de lançamentos exibe estado de erro | Alta | Integração | Automatizado |

### Razão Geral

| ID | Título | Prioridade | Tipo | Status |
| :---: | :--- | :---: | :--- | :---: |
| INT-GL-01 | Erro de API no Razão Geral exibe estado de erro | Alta | Integração | Automatizado |

## Resumo Geral {#resumo-geral}

| Categoria | Módulo | Casos |
| :--- | :--- | :---: |
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
| Unitários | Todos os módulos | 300 |
| **TOTAL GERAL** | | **466** |

## DRE – Regras de composição

A Demonstração do Resultado do Exercício (DRE) é um relatório contábil que apresenta o desempenho da empresa em determinado período, evidenciando receitas, custos, despesas e o resultado final (lucro ou prejuízo).

A DRE deve considerar apenas os valores **apurados** no período, ou seja, receitas e despesas já reconhecidas contabilmente conforme o regime de competência. Não devem ser considerados saldos patrimoniais, mas apenas contas de resultado.

---

## Filtros da tela

A tela da DRE deve possuir os filtros:

**Período Inicial**
Data inicial considerada para a apuração da DRE.

**Período Final**
Data final considerada para a apuração da DRE.

Por padrão, ao acessar a tela, os filtros devem ser carregados automaticamente com:

* Período Inicial: primeiro dia do ano atual
* Período Final: último dia do ano atual

A tela deve carregar automaticamente a DRE com esses valores, sem necessidade de ação do usuário.

---

## Estrutura da DRE (passo a passo da tela)

### 1. Receita Bruta

Soma de todas as contas analíticas que estão em:
**RECEITA BRUTA DE VENDAS E SERVIÇOS**
(dentro de CONTAS DE RESULTADO – RECEITAS)

---

### 2. (-) Deduções da Receita

Soma de todas as contas analíticas que estão em:
**DEDUÇÕES DA RECEITA BRUTA**
(dentro de CONTAS DE RESULTADO – RECEITAS)

---

### 3. (=) Receita Líquida

Receita Bruta – Deduções

---

### 4. (-) CMV / CPV

**CMV (Custo das Mercadorias Vendidas)**: custo das mercadorias vendidas
**CPV (Custo dos Produtos Vendidos)**: custo dos produtos fabricados e vendidos

Soma de todas as contas analíticas que estão em:
**CUSTOS**
(dentro de CONTAS DE RESULTADO – CUSTOS E DESPESAS)

---

### 5. (=) Lucro Bruto

Receita Líquida – CMV/CPV

---

### 6. (-) Despesas Operacionais

Soma de todas as contas analíticas que estão em:
**DESPESAS OPERACIONAIS**
(dentro de CONTAS DE RESULTADO – CUSTOS E DESPESAS)

Exceto as contas analíticas que estão em:
**DESPESAS FINANCEIRAS**

---

### 7. (+/-) Outras Receitas / Despesas Operacionais

**Outras Receitas Operacionais**
Soma de todas as contas analíticas que estão em:
**OUTRAS RECEITAS OPERACIONAIS**
(dentro de CONTAS DE RESULTADO – RECEITAS)

**Outras Despesas Operacionais**
Soma de todas as contas analíticas que estão em:
**OUTRAS DESPESAS OPERACIONAIS**
(dentro de DESPESAS ADMINISTRATIVAS → DESPESAS OPERACIONAIS → CONTAS DE RESULTADO – CUSTOS E DESPESAS)

---

### 8. (=) LAJIR

**LAJIR = Lucro Antes dos Juros e do Imposto de Renda**

Fórmula:
Lucro Bruto – Despesas Operacionais ± Outras Operacionais

Representa o resultado operacional da empresa, sem considerar efeitos financeiros e impostos.

---

### 9. (+/-) Resultado Financeiro

**Receitas Financeiras**
Soma de todas as contas analíticas que estão em:
**RECEITAS FINANCEIRAS**
(dentro de CONTAS DE RESULTADO – RECEITAS)

**Despesas Financeiras**
Soma de todas as contas analíticas que estão em:
**DESPESAS FINANCEIRAS**
(dentro de DESPESAS ADMINISTRATIVAS → DESPESAS OPERACIONAIS → CONTAS DE RESULTADO – CUSTOS E DESPESAS)

**Valor apresentado na DRE:**
Resultado Financeiro = (Receitas Financeiras) – (Despesas Financeiras)

Ou seja, o valor exibido nesta linha deve ser o resultado líquido entre receitas e despesas financeiras, e não a soma.

* Se o resultado for positivo: apresentar como (+)
* Se o resultado for negativo: apresentar como (-)

---

### 10. (=) LAIR

**LAIR = Lucro Antes do Imposto de Renda**

Fórmula:
LAJIR ± Resultado Financeiro

Representa o lucro antes da incidência de impostos.

---

### 11. (+/-) Resultado Não Operacional

**Receitas Não Operacionais**
Soma de todas as contas analíticas que estão em:
**RECEITAS NÃO OPERACIONAIS**
(dentro de CONTAS DE RESULTADO – RECEITAS)

**Despesas Não Operacionais**
Soma de todas as contas analíticas que estão em:
**DESPESAS NÃO OPERACIONAIS**
(dentro de CONTAS DE RESULTADO – CUSTOS E DESPESAS)

---

### 12. (=) Resultado Antes dos Impostos

LAIR ± Resultado Não Operacional

---

### 13. (-) IR e CSLL

**IR = Imposto de Renda**
**CSLL = Contribuição Social sobre o Lucro Líquido**

Soma de todas as contas analíticas que estão em:
**IMPOSTOS SOBRE O LUCRO (IR/CSLL)**
(dentro de CONTAS DE RESULTADO – RECEITAS ou grupo específico de resultado)

---

### 14. (=) Lucro Líquido

Resultado Antes dos Impostos – Impostos

---

## Resumo da lógica

Receita Bruta
(-) Deduções
= Receita Líquida
(-) CMV/CPV
= Lucro Bruto
(-) Despesas Operacionais
(+/-) Outras Operacionais
= LAJIR
(+/-) Resultado Financeiro
= LAIR
(+/-) Não Operacional
(-) Impostos
= Lucro Líquido

---

## Regra geral

Somar sempre contas analíticas por grupo pai.
A DRE deve seguir a hierarquia do plano de contas, não os códigos.

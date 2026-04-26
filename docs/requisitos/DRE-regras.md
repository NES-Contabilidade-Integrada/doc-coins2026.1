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

Soma de todas as contas analíticas em:
**RECEITA BRUTA DE VENDAS E SERVIÇOS**

---

### 2. (-) Deduções da Receita

Soma de todas as contas analíticas em:
**DEDUÇÕES DA RECEITA BRUTA**

---

### 3. (=) Receita Líquida

Receita Bruta – Deduções

---

### 4. (-) CMV / CPV

**CMV (Custo das Mercadorias Vendidas)**: custo das mercadorias vendidas
**CPV (Custo dos Produtos Vendidos)**: custo dos produtos fabricados e vendidos

Soma de todas as contas analíticas em:
**CUSTOS**

---

### 5. (=) Lucro Bruto

Receita Líquida – CMV/CPV

---

### 6. (-) Despesas Operacionais

Soma de todas as contas analíticas em:
**DESPESAS OPERACIONAIS**
**exceto DESPESAS FINANCEIRAS**

---

### 7. (+/-) Outras Receitas / Despesas Operacionais

**Outras Receitas Operacionais**
Soma das contas em: OUTRAS RECEITAS OPERACIONAIS

**Outras Despesas Operacionais**
Soma das contas em: OUTRAS DESPESAS OPERACIONAIS

---

### 8. (=) LAJIR

**LAJIR = Lucro Antes dos Juros e do Imposto de Renda**

Fórmula:
Lucro Bruto – Despesas Operacionais ± Outras Operacionais

Representa o resultado operacional da empresa, sem considerar efeitos financeiros e impostos.

---

### 9. (+/-) Resultado Financeiro

**Receitas Financeiras**: rendimentos, juros recebidos
**Despesas Financeiras**: juros pagos, encargos financeiros

---

### 10. (=) LAIR

**LAIR = Lucro Antes do Imposto de Renda**

Fórmula:
LAJIR ± Resultado Financeiro

Representa o lucro antes da incidência de impostos.

---

### 11. (+/-) Resultado Não Operacional

Resultados não ligados à atividade principal:

* venda de imobilizado
* eventos não recorrentes

---

### 12. (=) Resultado Antes dos Impostos

LAIR ± Resultado Não Operacional

---

### 13. (-) IR e CSLL

**IR = Imposto de Renda**
**CSLL = Contribuição Social sobre o Lucro Líquido**

Soma das contas de impostos sobre o lucro.

---

### 14. (=) Lucro Líquido

Resultado final da DRE após todos os descontos.

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

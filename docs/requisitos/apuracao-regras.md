# 🧾 Regras da Apuração de Resultado

## 🎯 1. Objetivo
Encerrar (zerar) todas as contas de resultado (Receitas, Custos e Despesas) e transferir seus saldos para a conta de Apuração do Resultado (ARE), apurando o lucro ou prejuízo do período.

---

## 📊 2. Contas consideradas

Contas de resultado:
- Receitas (natureza credora)
- Custos (natureza devedora)
- Despesas (natureza devedora)

Não participam da apuração:
- Ativo
- Passivo
- Patrimônio Líquido (exceto no encerramento final)

---

## 🔄 3. Regra principal
Após a execução da apuração:
- Todas as contas de resultado devem ficar com saldo igual a zero
- A conta ARE deve refletir temporariamente o resultado do período

---

## 💰 4. Encerramento das contas

### Receitas (saldo credor)

Para cada conta de receita:
- Debitar a conta de Receita (para zerar)
- Creditar a conta ARE

Lançamento:
```
D - Receita
C - Apuração do Resultado (ARE)
```

---

### Custos e Despesas (saldo devedor)

Para cada conta de custo ou despesa:
- Creditar a conta de Custo/Despesa (para zerar)
- Debitar a conta ARE

Lançamento:
```
D - Apuração do Resultado (ARE)
C - Custo/Despesa
```

---

## 📈 5. Apuração do resultado na ARE

Após o encerramento:

- Se o saldo da ARE for credor → houve lucro
- Se o saldo da ARE for devedor → houve prejuízo

---

## 🧾 6. Transferência do resultado

### Caso haja lucro (ARE com saldo credor)

- Debitar a ARE (zerando a conta)
- Creditar Lucros Acumulados (Patrimônio Líquido)

```
D - Apuração do Resultado (ARE)
C - Lucros Acumulados
```

---

### Caso haja prejuízo (ARE com saldo devedor)

- Creditar a ARE (zerando a conta)
- Debitar Prejuízos Acumulados (Patrimônio Líquido)

```
D - Prejuízos Acumulados
C - Apuração do Resultado (ARE)
```

---

## ✅ 7. Estado final esperado

Após a apuração:

- Todas as contas de resultado = 0
- Conta ARE = 0
- Resultado transferido para o Patrimônio Líquido
  - Lucros Acumulados ou
  - Prejuízos Acumulados

---

## ⚠️ 8. Validações do sistema

Antes de permitir a apuração:

- Todos os lançamentos devem estar balanceados (débitos = créditos)
- Todas as contas devem possuir classificação correta (Receita, Custo ou Despesa)
- O período de apuração deve estar definido
- Não deve haver inconsistências contábeis

---

## 🧠 9. Regra lógica (para implementação)

```
Para cada conta de Receita:
    debitar conta
    creditar ARE

Para cada conta de Custo/Despesa:
    creditar conta
    debitar ARE

Se saldo ARE > 0 (credor):
    transferir para Lucros Acumulados

Se saldo ARE < 0 (devedor):
    transferir para Prejuízos Acumulados
```

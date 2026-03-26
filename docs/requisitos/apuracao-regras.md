# 🧾 Regras da Apuração de Resultado

## 🎯 1. Objetivo
Encerrar (zerar) todas as contas de resultado (Receitas e Custos/Despesas) e transferir seus saldos para a conta de Apuração do Resultado (ARE), apurando o lucro ou prejuízo do período.

---

## 📊 2. Contas consideradas

**Contas de resultado:**
- Receitas (natureza credora)
- Custos/Despesas (natureza devedora)

**Não participam da apuração:**
- Ativo
- Passivo
- Patrimônio Líquido (exceto no encerramento final)

---

## 🔄 3. Regra principal
Após a apuração:
- Todas as contas de resultado devem ficar com saldo igual a zero
- A conta ARE deve refletir *temporariamente* o resultado do período, pois é uma conta transitória

---

## 💰 4. Encerramento das contas

### Receitas

Para cada conta de receita:

- **Se o saldo for credor (normal):**
  - Debitar a conta de Receita pelo valor total
  - Creditar a conta ARE

- **Se o saldo for devedor (invertido):**
  - Creditar a conta de Receita pelo valor total
  - Debitar a conta ARE

Lançamento (caso padrão):
```
D - Receita (valor total da conta)
C - Apuração do Resultado (ARE)
```

---

### Custos/Despesas

Para cada conta de custo/despesa:

- **Se o saldo for devedor (normal):**
  - Creditar a conta de Custo/Despesa pelo valor total
  - Debitar a conta ARE

- **Se o saldo for credor (invertido):**
  - Debitar a conta de Custo/Despesa pelo valor total
  - Creditar a conta ARE

Lançamento (caso padrão):
```
D - Apuração do Resultado (ARE)
C - Custos/Despesas (valor total da conta)
```

---

## 📈 5. Apuração do resultado na ARE

Após o encerramento:

- Se o saldo da ARE for credor → Lucro
- Se o saldo da ARE for devedor → Prejuízo

---

## 🧾 6. Transferência do resultado

### Caso haja lucro (ARE com saldo credor)

- **Debitar a ARE pelo valor total do lucro (zerando a conta)**
- **Creditar Lucros Acumulados pelo mesmo valor**

```
D - Apuração do Resultado (ARE)
C - Lucros Acumulados
```

---

### Caso haja prejuízo (ARE com saldo devedor)

- **Creditar a ARE pelo valor total do prejuízo (zerando a conta)**
- **Debitar Prejuízos Acumulados pelo mesmo valor**

```
D - Prejuízos Acumulados
C - Apuração do Resultado (ARE)
```

---

## ✅ 7. Estado final esperado

Após a apuração:

- Todas as contas de resultado = 0
- Conta ARE = 0
- Resultado transferido para o Patrimônio Líquido:
  - Lucros Acumulados ou
  - Prejuízos Acumulados

---

## ⚠️ 8. Validações do sistema

Antes de permitir a apuração:

- Débitos = Créditos (balanço consistente)
- Todas as contas possuem classificação correta
- Período definido
- Sem inconsistências contábeis

---

## 🧠 9. Regra lógica (para implementação)

```
Para cada conta de Receita:
    if saldo > 0 (credor):
        debitar conta
        creditar ARE
    else:
        creditar conta
        debitar ARE

Para cada conta de Custos/Despesas:
    if saldo > 0 (devedor):
        creditar conta
        debitar ARE
    else:
        debitar conta
        creditar ARE

Se saldo ARE for credor:
    transferir para Lucros Acumulados

Se saldo ARE for devedor:
    transferir para Prejuízos Acumulados
```

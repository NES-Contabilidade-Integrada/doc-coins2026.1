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
- A conta ARE deve refletir temporariamente o resultado do período

---

## 💰 4. Encerramento das contas

### Receitas (saldo credor)

Para cada conta de receita:

- **Debitar a conta de Receita pelo valor total do saldo (para zerar)**
- **Creditar a conta ARE pelo mesmo valor**

Lançamento:
```
D - Receita (valor total da conta)
C - Apuração do Resultado (ARE)
```

---

### Custos/Despesas (saldo devedor)

Para cada conta de custo/despesa:

- **Creditar a conta de Custo/Despesa pelo valor total do saldo (para zerar)**
- **Debitar a conta ARE pelo mesmo valor**

Lançamento:
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
    debitar pelo valor total
    creditar ARE

Para cada conta de Custos/Despesas:
    creditar pelo valor total
    debitar ARE

Se saldo ARE for credor:
    transferir para Lucros Acumulados

Se saldo ARE for devedor:
    transferir para Prejuízos Acumulados
```

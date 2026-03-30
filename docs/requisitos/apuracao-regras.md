# 🧾 Regras da Apuração de Resultado

## 🎯 1. Objetivo
Encerrar (zerar) todas as contas de resultado e apurar o resultado do período:

- Receitas → natureza credora  
- Custos/Despesas → natureza devedora  

Transferir tudo para a conta:
**Apuração do Resultado (ARE)**

---

## 📊 2. Escopo da apuração

### ✔️ Participam:
- Contas de Receita  
- Contas de Custos/Despesas  

### ❌ Não participam:
- Ativo  
- Passivo  
- Patrimônio Líquido (exceto no encerramento final)  

---

## 📅 3. Regra de período

- A apuração usa uma **data final (data da apuração)**  
- Considera **todos os lançamentos até essa data**  
- A data inicial é:
  → **dia seguinte da última apuração**

Se nunca houve apuração:
→ considera todos os lançamentos históricos

---

## 🔄 4. Regra principal

Após a apuração:

- Todas as contas de resultado devem ficar = **0**
- A conta ARE:
  - acumula temporariamente o resultado
  - depois também deve ser zerada

---

## 💰 5. Encerramento das contas

### 🟢 Receitas

| Situação | Lançamento |
|--------|-----------|
| Saldo credor (normal) | D Receita / C ARE |
| Saldo devedor (invertido) | C Receita / D ARE |

---

### 🔴 Custos/Despesas

| Situação | Lançamento |
|--------|-----------|
| Saldo devedor (normal) | D ARE / C Custo |
| Saldo credor (invertido) | D Custo / C ARE |

---

## 📈 6. Apuração do resultado (ARE)

Após o encerramento:

- ARE credor → **Lucro**
- ARE devedor → **Prejuízo**

---

## 🧾 7. Transferência do resultado

### 🟢 Caso Lucro (ARE credor)

D - ARE  
C - Lucros Acumulados  

---

### 🔴 Caso Prejuízo (ARE devedor)

D - Prejuízos Acumulados  
C - ARE  

---

## ✅ 8. Estado final esperado

Após a apuração:

- Contas de Receita = 0  
- Contas de Custos/Despesas = 0  
- ARE = 0  

Resultado transferido para:

- Lucros Acumulados  
ou  
- Prejuízos Acumulados  

---

## ⚠️ 9. Validações do sistema

Antes de permitir a apuração:

- Débitos = Créditos  
- Todas as contas possuem classificação correta  
- Data da apuração definida  
- Sem inconsistências contábeis  

---

## 🔁 10. Regras de operação do sistema

### 📌 Apuração
- Tela mostra um **resumo antes de executar**
- Cálculo pode ser em tempo real

### 📌 Desfazer apuração
- Só pode desfazer **a última apuração**
- Para desfazer uma anterior:
  → precisa desfazer as mais recentes antes

### 📌 Histórico (recomendado)
- Manter lista de apurações por data
- Permite rastreabilidade

---

## 🧠 11. Regra lógica (pseudocódigo)

```python
# Receitas
for conta in receitas:
    if saldo > 0:  # credor
        debitar(conta)
        creditar(ARE)
    else:
        creditar(conta)
        debitar(ARE)

# Custos/Despesas
for conta in custos:
    if saldo > 0:  # devedor
        creditar(conta)
        debitar(ARE)
    else:
        debitar(conta)
        creditar(ARE)

# Resultado
if ARE.saldo > 0:  # lucro
    debitar(ARE)
    creditar(lucros_acumulados)
else:  # prejuízo
    debitar(prejuizos_acumulados)
    creditar(ARE)

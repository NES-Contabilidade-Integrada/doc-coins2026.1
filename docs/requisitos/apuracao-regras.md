# 📦 Apuração de Resultado

---

## 1. Objetivo da tela

A tela de **Apuração** deve apresentar ao usuário uma **prévia completa** do que será executado no momento da apuração do resultado do período.

A prévia deve permitir visualizar:
- valores considerados;
- contas envolvidas;
- lançamentos de encerramento;
- resultado final (lucro ou prejuízo);
- conta de destino.

---

## 2. Filtro de data da apuração

### 2.1 Campo

Campo obrigatório:
- **Data da Apuração**

### 2.2 Valor padrão

Ao abrir a tela:
- a data deve vir preenchida com o **último dia do ano atual (31/12/YYYY)**

### 2.3 Persistência durante a sessão

Se o usuário alterar a data:
- o valor deve ser mantido durante toda a sessão do app  
- não deve resetar ao navegar entre telas

---

## 3. Regra de consideração dos lançamentos

A apuração deve considerar:

- todos os lançamentos com data **≤ Data da Apuração**
- que **ainda não tenham sido apurados anteriormente**

### ❗ Regra principal

A apuração **NÃO deve ser baseada na data da última apuração**  
e sim em **quais lançamentos ainda não foram apurados**

---

## 4. Primeira apuração

Se não existir apuração anterior:
- considerar todos os lançamentos com data ≤ Data da Apuração

---

## 5. Demais apurações

Se já existir apuração:
- considerar todos os lançamentos com data ≤ Data da Apuração  
- que **não estejam vinculados a nenhuma apuração**

---

## 6. Lançamentos retroativos

Se um lançamento for criado com data anterior à última apuração:

- ele **DEVE entrar na próxima apuração**
- desde que ainda não tenha sido apurado

---

## 7. Controle de apuração

Cada lançamento (ou linha de lançamento) deve:

- ser vinculado a uma apuração ao ser processado  
- permitir identificar se já foi apurado  

Isso evita duplicidade.

---

## 8. Ausência de valores

Se não houver valores:

- exibir mensagem:  
  **"Não há valores a serem apurados."**

- não exibir:
  - contas
  - lançamentos
  - resultado

---

## 9. Estrutura da tela

A tela deve conter:

1. Resumo do Resultado  
2. Contas de Resultado  
3. Lançamentos de Encerramento  
4. Resultado Final  

---

## 10. Resumo do resultado

Exibir:
- Total de Receitas  
- Total de Custos e Despesas  
- Resultado do Período  
- Indicador: Lucro ou Prejuízo  

### 10.1 Regra

Resultado = Receitas - Custos/Despesas

### 10.2 Classificação

- Credor → Lucro  
- Devedor → Prejuízo  

---

## 11. Regra de saldo

Saldo = Créditos - Débitos

---

## 12. Regra de sinal (UI)

Não usar débito/crédito diretamente.

Usar natureza:

- Receita → credora  
- Custo/Despesa → devedora  

Regra:
- saldo normal → positivo  
- saldo invertido → negativo (-)

---

## 13. Contas de resultado

Exibir contas de:
- Receitas  
- Custos e Despesas  

Campos:
- Código  
- Descrição  
- Tipo  
- Saldo Atual  
- D/C  

---

## 14. Lançamentos de encerramento

Exibir prévia dos lançamentos.

---

## 15. Encerramento das Receitas

Se saldo credor:
- Débito → Receita  
- Crédito → Apuração  

Se saldo devedor:
- Crédito → Receita  
- Débito → Apuração  

### Ausência:
"Não há valores a serem apurados nas contas de Receita"

---

## 16. Encerramento de Custos e Despesas

Se saldo devedor:
- Crédito → Custos/Despesas  
- Débito → Apuração  

Se saldo credor:
- Débito → Custos/Despesas  
- Crédito → Apuração  

### Ausência:
"Não há valores a serem apurados nas contas de Custos e Despesas"

---

## 17. Confronto da apuração

Exibir:
- Total de Custos e Despesas  
- Total de Receitas  
- Resultado  

Indicador:
- C → Lucro  
- D → Prejuízo  

---

## 18. Transferência do resultado

### Lucro
- Débito → Apuração  
- Crédito → Lucros Acumulados  

### Prejuízo
- Crédito → Apuração  
- Débito → Prejuízos Acumulados  

---

## 19. Resultado final

Exibir:
- Tipo (Lucro / Prejuízo)  
- Valor  
- Conta destino  

---

## 20. Execução da apuração

Botão: **Realizar Apuração**

Ao confirmar:
- executar exatamente a prévia  
- vincular lançamentos à apuração  

---

## 21. Histórico de apurações

Exibir:
- Data  
- Tipo  
- Valor  
- Conta destino  

Ação:
- Desfazer  

---

## 22. Regras para desfazer

- apenas a última apuração pode ser desfeita  
- deve remover o vínculo dos lançamentos  
- não permitir desfazer fora de ordem  

---

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

### Lucro (sem compensação)
- Débito → Apuração  
- Crédito → Lucros Acumulados  

### Prejuízo (sem compensação)
- Crédito → Apuração  
- Débito → Prejuízos Acumulados  

---

## 18.1 Resultado Nulo

Se o resultado do período for **R$ 0,00**:

- classificar como **Resultado Nulo**
- **não gerar** nenhum lançamento de destinação (nem para Lucros nem para Prejuízos Acumulados)
- registrar no histórico com tipo **Resultado Nulo** e sem conta destino

---

## 18.2 Compensação automática antes da destinação

A compensação ocorre **no momento de efetivar a apuração**, antes de enviar o resultado para a conta de destino.  
O resultado do período exibido na tela e registrado no histórico **não é alterado** — reflete sempre o valor calculado do período.

### Se o resultado do período for **Lucro**:

1. Verificar se existe saldo na conta **Prejuízos Acumulados**
2. Se existir:
   - Utilizar o lucro para abater o saldo de prejuízos acumulados
   - Se **lucro > saldo de Prejuízos Acumulados**:
     - Zerar a conta de Prejuízos Acumulados
     - Enviar o saldo restante (lucro − prejuízo acumulado) para **Lucros Acumulados**
   - Se **lucro ≤ saldo de Prejuízos Acumulados**:
     - Apenas reduzir o saldo de Prejuízos Acumulados pelo valor do lucro
     - Não gerar lançamento para Lucros Acumulados
3. Se não existir saldo em Prejuízos Acumulados:
   - Enviar o lucro integralmente para **Lucros Acumulados** (regra padrão da seção 18)

### Se o resultado do período for **Prejuízo**:

1. Verificar se existe saldo na conta **Lucros Acumulados**
2. Se existir:
   - Utilizar o prejuízo para abater o saldo de lucros acumulados
   - Se **prejuízo > saldo de Lucros Acumulados**:
     - Zerar a conta de Lucros Acumulados
     - Enviar o saldo restante (prejuízo − lucro acumulado) para **Prejuízos Acumulados**
   - Se **prejuízo ≤ saldo de Lucros Acumulados**:
     - Apenas reduzir o saldo de Lucros Acumulados pelo valor do prejuízo
     - Não gerar lançamento para Prejuízos Acumulados
3. Se não existir saldo em Lucros Acumulados:
   - Enviar o prejuízo integralmente para **Prejuízos Acumulados** (regra padrão da seção 18)

### Exemplo

| Apuração | Resultado do Período | Compensação aplicada | Lançamentos efetivados |
|----------|---------------------|---------------------|------------------------|
| 1ª | R$ 1.000 Prejuízo | Nenhuma (Lucros Acumulados = 0) | Débito R$ 1.000 → Prejuízos Acumulados |
| 2ª | R$ 5.000 Lucro | Abate R$ 1.000 de Prejuízos Acumulados | Crédito R$ 1.000 → zera Prejuízos Acumulados; Crédito R$ 4.000 → Lucros Acumulados |

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

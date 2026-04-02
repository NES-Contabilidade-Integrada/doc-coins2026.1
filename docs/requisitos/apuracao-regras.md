# Apuração de Resultado

## 1. Objetivo

A tela de **Apuração** deve apresentar ao usuário uma **prévia completa** do que será executado na apuração do resultado do período, antes da confirmação.

A prévia deve permitir visualizar:
- valores considerados;
- contas envolvidas;
- lançamentos contábeis de encerramento;
- resultado final (lucro ou prejuízo);
- conta de destino.

---

## 2. Filtro de Data da Apuração

### 2.1 Campo
- **Data da Apuração**

### 2.2 Regras

#### Primeira apuração
- Considerar **todos os lançamentos** com data **≤ Data da Apuração**

#### Demais apurações
- Considerar lançamentos:
  - **posteriores à última apuração**
  - e com data **≤ Data da Apuração**

#### Sem valores
- Exibir mensagem: **"Não há valores a serem apurados"**
- Não exibir lançamentos
- Impedir execução da apuração

---

## 3. Estrutura da Prévia

A tela deve conter as seções:

1. Resumo do Resultado  
2. Contas de Resultado  
3. Lançamentos de Encerramento  
4. Resultado Final  

---

## 4. Resumo do Resultado

### Campos

- Total de Receitas  
- Total de Custos e Despesas  
- Resultado do Período  
- Indicador: **Lucro** ou **Prejuízo**

### Origem dos dados

- Receitas → grupo **CONTAS DE RESULTADO - RECEITAS**
- Custos/Despesas → grupo **CONTAS DE RESULTADO - CUSTOS E DESPESAS**

### Regra do resultado
Resultado = Receitas - Custos e Despesas


### Classificação

- **Lucro** → saldo credor  
- **Prejuízo** → saldo devedor  

---

## 5. Contas de Resultado

### Contas exibidas

- Todas as contas dos grupos:
  - CONTAS DE RESULTADO - RECEITAS
  - CONTAS DE RESULTADO - CUSTOS E DESPESAS

### Campos

- Código  
- Descrição  
- Tipo  
- Saldo Atual  
- D/C  

### Tipo

- Receita  
- Custo e Despesa  

---

## 6. Lançamentos de Encerramento

Exibe a prévia dos lançamentos que serão gerados.

---

## 7. Encerramento das Receitas

### Campos

- Conta  
- Código  
- Débito  
- Crédito  

### Regras

#### Receita com saldo credor
- Débito → Contas de Receita  
- Crédito → Apuração do Resultado  

#### Receita com saldo devedor
- Crédito → Contas de Receita  
- Débito → Apuração do Resultado  

---

## 8. Encerramento de Custos e Despesas

### Campos

- Conta  
- Código  
- Débito  
- Crédito  

### Regras

#### Saldo devedor (caso normal)
- Crédito → Custos e Despesas  
- Débito → Apuração do Resultado  

#### Saldo credor (exceção)
- Débito → Custos e Despesas  
- Crédito → Apuração do Resultado  

### Sem valores
- Exibir: **"Não há valores a serem apurados nas contas de Custos e Despesas"**

---

## 9. Confronto da Apuração

### Campos

- Descrição  
- Valor  
- D/C  

### Linhas

- Total de Custos e Despesas  
- Total de Receitas  
- Resultado  

### Regra

- Resultado = confronto entre receitas e custos/despesas

### Indicador

- C → Lucro  
- D → Prejuízo  

---

## 10. Transferência do Resultado

### Campos

- Conta  
- Código  
- Débito  
- Crédito  

### Regras

#### Lucro (saldo credor)
- Débito → Apuração do Resultado  
- Crédito → Lucros Acumulados  

#### Prejuízo (saldo devedor)
- Crédito → Apuração do Resultado  
- Débito → Prejuízos Acumulados  

---

## 11. Resultado Final

### Campos

- Tipo de Resultado  
- Valor  
- Conta Destino  

### Conta destino

- Lucro → **Lucros Acumulados**  
- Prejuízo → **Prejuízos Acumulados**  

---

## 12. Realizar Apuração

### Ação
- Botão: **Realizar Apuração**

### Regra

- Deve executar exatamente os lançamentos exibidos na prévia

---

## 13. Histórico de Apurações

### Conteúdo

- Lista de apurações realizadas

### Campos

- Data  
- Tipo (Lucro/Prejuízo)  
- Valor  
- Conta Destino  
- Ação  

### Ação disponível

- **Desfazer**

---

## 14. Regras de Desfazer

### Regras

- Deve ser feito **individualmente**
- Só pode desfazer a **última apuração**
- Não pode desfazer anteriores sem desfazer as posteriores

---

## Regras de Negócio

### RN01
Considerar apenas lançamentos dentro do intervalo da apuração

### RN02
Utilizar contas dos grupos:
- RESULTADO - RECEITAS
- RESULTADO - CUSTOS E DESPESAS

### RN03
A prévia deve refletir exatamente os lançamentos finais

### RN04
Sistema deve identificar corretamente lucro ou prejuízo

### RN05
Saldo da conta Apuração deve ser transferido integralmente

### RN06
Desfazer apuração respeita ordem cronológica inversa

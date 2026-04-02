# Apuração de Resultado

## 1. Objetivo da tela

A tela de **Apuração** deve apresentar ao usuário uma **prévia completa** do que será efetivamente executado no momento da apuração do resultado do período, antes da confirmação da ação.

A prévia deve permitir que o usuário visualize:
- os valores considerados na apuração;
- as contas envolvidas;
- os lançamentos contábeis de encerramento que serão gerados;
- o resultado final do período, indicando se houve **lucro** ou **prejuízo**;
- a conta de destino do resultado.

---

## 2. Filtro de data da apuração

### 2.1 Campo

A tela deve possuir o campo:

- **Data da Apuração**

### 2.2 Regra de consideração dos lançamentos

A data informada definirá quais lançamentos contábeis serão considerados na apuração, com base na **data do lançamento**.

### 2.3 Primeira apuração

Se ainda não existir nenhuma apuração anterior, o sistema deve considerar:

- todos os lançamentos do sistema com data **menor ou igual à Data da Apuração**.

### 2.4 Demais apurações

Se já existir apuração anterior, o sistema deve considerar apenas os lançamentos:

- posteriores à última apuração realizada; e  
- com data **menor ou igual à Data da Apuração**.

### 2.5 Ausência de valores

Se não existirem lançamentos elegíveis para apuração no intervalo calculado, a tela deve:

- informar que **não há valores a serem apurados**;
- não exibir lançamentos de encerramento;
- impedir ou tratar adequadamente a execução da apuração.

---

## 3. Estrutura da prévia da apuração

A prévia da apuração deve conter as seguintes seções:

1. Resumo do Resultado  
2. Contas de Resultado  
3. Lançamentos de Encerramento  
4. Resultado Final  

---

## 4. Resumo do resultado

A seção **Resumo do Resultado** deve exibir, no mínimo, os seguintes campos:

- Total de Receitas  
- Total de Custos e Despesas  
- Resultado do Período  
- Indicador do resultado: **Lucro** ou **Prejuízo**

### 4.1 Origem dos valores

Os totais devem ser obtidos a partir da soma dos saldos das contas de resultado do plano de contas:

- **Receitas** → contas do grupo **CONTAS DE RESULTADO - RECEITAS**
- **Custos e Despesas** → contas do grupo **CONTAS DE RESULTADO - CUSTOS E DESPESAS**

### 4.2 Regra do resultado
Resultado do Período = Total de Receitas - Total de Custos e Despesas

### 4.3 Classificação do resultado

- **Lucro** → saldo credor  
- **Prejuízo** → saldo devedor  

---

## 5. Contas de resultado

A seção **Contas de Resultado** deve listar todas as contas que participaram da apuração.

### 5.1 Contas exibidas

Devem ser exibidas todas as contas pertencentes aos grupos de primeiro nível:

- CONTAS DE RESULTADO - RECEITAS  
- CONTAS DE RESULTADO - CUSTOS E DESPESAS  

### 5.2 Campos da listagem

Para cada conta, devem ser exibidos:

- Código  
- Descrição da Conta  
- Tipo  
- Saldo Atual  
- D/C (Devedor ou Credor)  

### 5.3 Regras do campo Tipo

- Receita → contas do grupo de receitas  
- Custo e Despesa → contas do grupo de custos e despesas  

### 5.4 Regra do saldo

O **Saldo Atual** deve corresponder ao saldo da conta dentro do período considerado pela apuração.

---

## 6. Lançamentos de encerramento

A seção **Lançamentos de Encerramento** deve demonstrar, em formato de prévia, os lançamentos contábeis que serão gerados caso o usuário confirme a apuração.

---

## 7. Encerramento das Receitas

A subseção **1. Encerramento das Receitas** deve demonstrar o lançamento necessário para zerar as contas de receita e transferir sua contrapartida para a conta **Apuração do Resultado**.

### 7.1 Campos exibidos

- Conta  
- Código  
- Débito  
- Crédito  

### 7.2 Regras de encerramento

#### a) Quando o total das receitas for credor

- Débito → Contas de Receita  
- Crédito → Apuração do Resultado  

#### b) Quando o total das receitas for devedor

- Crédito → Contas de Receita  
- Débito → Apuração do Resultado  

### 7.3 Exibição da prévia

A prévia deve demonstrar:

- uma linha consolidada para **Contas de Receita**;
- uma linha para **Apuração do Resultado**;
- os respectivos valores de débito e crédito.

---

## 8. Encerramento de Custos e Despesas

A subseção **2. Encerramento de Custos e Despesas** deve demonstrar o lançamento necessário para zerar as contas de custo e despesa e transferir sua contrapartida para a conta **Apuração do Resultado**.

### 8.1 Campos exibidos

- Conta  
- Código  
- Débito  
- Crédito  

### 8.2 Regras de encerramento

#### a) Quando o total for devedor (caso normal)

- Crédito → Custos e Despesas  
- Débito → Apuração do Resultado  

#### b) Quando o total for credor (exceção)

- Débito → Custos e Despesas  
- Crédito → Apuração do Resultado  

### 8.3 Exibição da prévia

A prévia deve demonstrar:

- uma linha consolidada para **Contas de Custos e Despesas**;
- uma linha para **Apuração do Resultado**;
- os respectivos valores de débito e crédito.

### 8.4 Ausência de valores

Se não houver valores:

- Exibir mensagem:  
  **"Não há valores a serem apurados nas contas de custos e despesas"**

---

## 9. Confronto da Apuração do Resultado

A subseção **3. Confronto da Apuração do Resultado** deve demonstrar a composição do resultado apurado.

### 9.1 Campos exibidos

- Descrição  
- Valor  
- D/C  

### 9.2 Linhas obrigatórias

- Total de Custos e Despesas  
- Total de Receitas  
- Resultado  

### 9.3 Regra do cálculo

O resultado deve corresponder ao confronto entre:

- valores das **Receitas**;  
- valores de **Custos e Despesas**.

### 9.4 Regra do indicador

- **C (Credor)** → Lucro  
- **D (Devedor)** → Prejuízo  

---

## 10. Transferência do resultado

A subseção **4. Transferência do Resultado** deve demonstrar a transferência do saldo final da conta **Apuração do Resultado**.

### 10.1 Campos exibidos

- Conta  
- Código  
- Débito  
- Crédito  

### 10.2 Regra para lucro

- Débito → Apuração do Resultado  
- Crédito → Lucros Acumulados  

### 10.3 Regra para prejuízo

- Crédito → Apuração do Resultado  
- Débito → Prejuízos Acumulados  

---

## 11. Resultado final

A seção **Resultado Final** deve exibir:

- Tipo de Resultado (Lucro do Período ou Prejuízo do Período)  
- Valor  
- Conta Destino  

### 11.1 Conta destino

- Lucro → **Lucros Acumulados**  
- Prejuízo → **Prejuízos Acumulados**  

---

## 12. Ação de realizar apuração

### 12.1 Ação

Botão: **Realizar Apuração**

### 12.2 Comportamento

Ao confirmar, o sistema deve:

- efetivar exatamente os lançamentos exibidos na prévia.

### 12.3 Integridade

- Os valores e lançamentos devem ser idênticos à prévia.

---

## 13. Histórico de apurações

### 13.1 Conteúdo

Listagem de apurações realizadas.

### 13.2 Campos

- Data  
- Tipo (Lucro ou Prejuízo)  
- Valor  
- Conta Destino  
- Ação  

### 13.3 Ação

- **Desfazer**

---

## 14. Regras para desfazer apuração

### 14.1 Desfazer individualmente

Cada apuração deve ser desfeita individualmente.

### 14.2 Ordem obrigatória

Só pode desfazer a **última apuração realizada**.

### 14.3 Bloqueio

Não é permitido desfazer apurações anteriores sem desfazer as posteriores.

---

## Regras de Negócio

### RN01
Considerar apenas lançamentos dentro do intervalo da apuração.

### RN02
Utilizar contas dos grupos:
- RESULTADO - RECEITAS  
- RESULTADO - CUSTOS E DESPESAS  

### RN03
A prévia deve refletir exatamente os lançamentos finais.

### RN04
O sistema deve identificar corretamente lucro ou prejuízo.

### RN05
O saldo da conta Apuração deve ser transferido integralmente.

### RN06
Desfazer apuração respeita ordem cronológica inversa.

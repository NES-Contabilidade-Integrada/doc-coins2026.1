# Regra da Funcionalidade: Balanço Patrimonial

## 1. Objetivo da funcionalidade

A funcionalidade de **Balanço Patrimonial** tem como objetivo apresentar a posição patrimonial da empresa em um determinado período, considerando os lançamentos realizados nas contas de **Ativo**, **Passivo** e **Patrimônio Líquido**.

O Balanço Patrimonial demonstra, de forma estruturada, **o que a empresa possui** e **de onde vieram os recursos utilizados para formar esse patrimônio**.

De forma simplificada:

- **Ativo:** representa tudo aquilo que a empresa possui ou tem direito a receber.
- **Passivo:** representa as obrigações da empresa com terceiros.
- **Patrimônio Líquido:** representa os recursos próprios da empresa.

A lógica contábil esperada é:

```text
Ativo = Passivo + Patrimônio Líquido
```

Quando essa igualdade é atendida, o balanço é considerado **fechado**.

Caso exista diferença entre os valores, o balanço fica com status **aberto**, indicando que pode haver algum lançamento incorreto, incompleto ou inconsistência nos saldos.

---

## 2. Filtros da tela

A tela deve possuir os seguintes filtros:

| Campo | Obrigatório | Descrição |
|---|---|---|
| Período Inicial | Sim | Data inicial considerada para apuração do balanço. |
| Período Final | Sim | Data final considerada para apuração do balanço. |

Os filtros de período são obrigatórios, pois o balanço deve considerar apenas os lançamentos realizados dentro do intervalo informado.

Por padrão, os campos devem vir preenchidos com o **primeiro e o último dia do ano atual**.

Exemplo:

| Campo | Valor padrão |
|---|---|
| Período Inicial | 01/01/2025 |
| Período Final | 31/12/2025 |

---

## 3. Base de cálculo do balanço

O Balanço Patrimonial deve considerar todos os lançamentos realizados no período informado que estejam vinculados às contas dos seguintes grupos:

- **Ativo**
- **Passivo**
- **Patrimônio Líquido**

A funcionalidade deve calcular o saldo das contas com base nos lançamentos contábeis existentes no período filtrado.

Depois disso, os saldos devem ser organizados conforme a estrutura do plano de contas.

---

## 4. Resumo do Balanço

Após a aplicação do filtro, a tela deve apresentar um resumo com os principais valores apurados.

Os campos exibidos no resumo são:

| Campo | Descrição |
|---|---|
| Total do Ativo | Soma total dos saldos das contas pertencentes ao Ativo. |
| Total do Passivo | Soma total dos saldos das contas pertencentes ao Passivo. |
| Patrimônio Líquido | Soma total dos saldos das contas pertencentes ao Patrimônio Líquido. |
| Status | Indica se o balanço está aberto ou fechado. |

O status pode ser:

| Status | Descrição |
|---|---|
| Fechado | Quando o Total do Ativo é igual à soma do Passivo com o Patrimônio Líquido. |
| Aberto | Quando existe diferença entre o Total do Ativo e a soma do Passivo com o Patrimônio Líquido. |

---

## 5. Natureza contábil dos grupos

Cada grupo possui uma natureza contábil esperada.

| Grupo | Natureza esperada |
|---|---|
| Ativo | Devedora |
| Passivo | Credora |
| Patrimônio Líquido | Credora |

Isso significa que:

- O **Ativo** normalmente deve apresentar saldo devedor.
- O **Passivo** normalmente deve apresentar saldo credor.
- O **Patrimônio Líquido** normalmente deve apresentar saldo credor.

---

## 6. Regra de sinalização dos valores sem D/C

Em alguns pontos da tela, os valores são exibidos de forma consolidada, sem a coluna **D/C**.

Nesses casos, o sistema deve utilizar um sinal negativo quando o saldo estiver contrário à natureza contábil esperada do grupo.

Essa sinalização não significa, necessariamente, que o valor é negativo no sentido financeiro.

O sinal negativo indica que o saldo está **contra a natureza contábil esperada**.

### Regra geral

| Grupo | Condição | Exibição |
|---|---|---|
| Ativo | Saldo devedor | Valor sem sinal |
| Ativo | Saldo credor | Valor com sinal negativo |
| Passivo | Saldo credor | Valor sem sinal |
| Passivo | Saldo devedor | Valor com sinal negativo |
| Patrimônio Líquido | Saldo credor | Valor sem sinal |
| Patrimônio Líquido | Saldo devedor | Valor com sinal negativo |

Exemplo:

```text
Ativo com saldo devedor:
R$ 500.000,00

Ativo com saldo credor:
-R$ 500.000,00

Passivo com saldo credor:
R$ 300.000,00

Passivo com saldo devedor:
-R$ 300.000,00

Patrimônio Líquido com saldo credor:
R$ 200.000,00

Patrimônio Líquido com saldo devedor:
-R$ 200.000,00
```

---

## 7. Locais onde a regra de sinalização deve ser aplicada

A regra de sinalização deve ser aplicada em todos os locais da tela onde o valor for exibido sem a coluna **D/C**.

Isso inclui:

- Resumo do Balanço;
- Total exibido no cabeçalho dos grupos;
- Total do Ativo;
- Total do Passivo;
- Total do Patrimônio Líquido;
- Conferência do Balanço;
- Valores consolidados exibidos no relatório exportado, quando não houver D/C.

Exemplos de totais que devem seguir essa regra:

| Total / Grupo | Natureza esperada | Quando exibir com sinal negativo |
|---|---|---|
| Ativo | Devedora | Quando o saldo for credor |
| Ativo Circulante | Devedora | Quando o saldo for credor |
| Ativo Não Circulante | Devedora | Quando o saldo for credor |
| Passivo | Credora | Quando o saldo for devedor |
| Passivo Circulante | Credora | Quando o saldo for devedor |
| Passivo Não Circulante | Credora | Quando o saldo for devedor |
| Patrimônio Líquido | Credora | Quando o saldo for devedor |
| Contas do Patrimônio Líquido | Credora | Quando o saldo for devedor |

Exemplo:

```text
Ativo Circulante com saldo devedor:
R$ 300.000,00

Ativo Circulante com saldo credor:
-R$ 300.000,00

Passivo Circulante com saldo credor:
R$ 200.000,00

Passivo Circulante com saldo devedor:
-R$ 200.000,00
```

Portanto, sempre que o valor exibido for um total ou valor consolidado e não houver exibição da coluna **D/C**, o sistema deve utilizar o sinal negativo para indicar que o saldo está contra a natureza esperada.

Nas contas analíticas, como a coluna **D/C** é exibida individualmente, o usuário consegue identificar diretamente se o saldo é devedor ou credor pela própria coluna.

---

## 8. Exibição das contas na tela

A tela deve exibir os valores separados pelos grandes grupos contábeis:

- **Ativo**
- **Passivo**
- **Patrimônio Líquido**

Dentro de cada grupo principal, devem ser exibidos os agrupamentos de **segundo nível** do plano de contas.

Exemplo de estrutura:

| Código | Classificação | Conta | Nível |
|---|---|---|---|
| 1 | 1 | Ativo | 1º nível |
| 2 | 1.1 | Ativo Circulante | 2º nível |
| 42 | 1.2 | Ativo Não Circulante | 2º nível |

Na tela, os grupos exibidos dentro de cada primeiro nível devem corresponder ao **segundo nível do plano de contas**.

Exemplo dentro do **Ativo**:

- **Ativo Circulante**
- **Ativo Não Circulante**

Exemplo dentro do **Passivo**:

- **Passivo Circulante**
- **Passivo Não Circulante**

Exemplo dentro do **Patrimônio Líquido**:

- **Contas do Patrimônio Líquido**

Cada grupo deve apresentar suas contas analíticas e seus respectivos saldos.

---

## 9. Campos exibidos nas tabelas da tela

Cada tabela de contas deve exibir os seguintes campos:

| Campo | Descrição |
|---|---|
| Código | Código da conta conforme o plano de contas. |
| Conta | Nome da conta contábil. |
| Saldo Atual | Saldo da conta dentro do período selecionado. |
| D/C | Natureza do saldo da conta, sendo **D** para Débito e **C** para Crédito. |

Exemplo:

| Código | Conta | Saldo Atual | D/C |
|---|---|---:|:---:|
| 5 | Caixa Geral | R$ 150.000,00 | D |
| 6 | Fundo Fixo de Caixa | R$ 150.000,00 | D |

A coluna **D/C** deve ser exibida nas linhas das contas analíticas.

Nos totais e agrupamentos, como a coluna **D/C** não é exibida, deve ser aplicada a regra de sinalização conforme a natureza esperada do grupo.

---

## 10. Totalização dos grupos

Cada grupo de segundo nível deve exibir o seu total.

Exemplo:

```text
Ativo Circulante — R$ 300.000,00
```

Esse valor representa a soma dos saldos das contas analíticas pertencentes ao grupo.

Também devem ser exibidos os totais dos grupos principais:

- **Total do Ativo**
- **Total do Passivo**
- **Total do Patrimônio Líquido**

Esses totais representam a soma dos saldos de todas as contas pertencentes a cada grupo principal.

Como esses totais não exibem a coluna **D/C**, eles devem seguir a regra de sinalização:

```text
Ativo:
    Natureza esperada = Devedora
    Se o saldo final for credor, exibir com sinal negativo.

Passivo:
    Natureza esperada = Credora
    Se o saldo final for devedor, exibir com sinal negativo.

Patrimônio Líquido:
    Natureza esperada = Credora
    Se o saldo final for devedor, exibir com sinal negativo.
```

---

## 11. Expansão e recolhimento dos grupos

A tela pode permitir a expansão e o recolhimento dos grupos exibidos.

Quando o grupo estiver expandido, devem ser exibidas as contas analíticas pertencentes a ele.

Quando o grupo estiver recolhido, deve permanecer visível apenas o nome do grupo e seu respectivo total.

Exemplo:

```text
Ativo Circulante — R$ 300.000,00
```

Ao expandir o grupo, devem aparecer as contas:

```text
Código | Conta               | Saldo Atual     | D/C
5      | Caixa Geral          | R$ 150.000,00   | D
6      | Fundo Fixo de Caixa  | R$ 150.000,00   | D
```

O total do grupo deve continuar respeitando a regra de sinalização quando estiver sem a coluna **D/C**.

---

## 12. Conferência do Balanço

Após a exibição dos grupos e contas, a tela deve apresentar a seção de **Conferência do Balanço**.

Essa seção tem como objetivo validar se o balanço está fechado ou aberto.

Devem ser exibidos os seguintes campos:

| Campo | Descrição |
|---|---|
| Ativo Total | Valor total apurado para as contas do Ativo. |
| Passivo + PL | Soma do Total do Passivo com o Total do Patrimônio Líquido. |
| Diferença | Diferença entre o Ativo Total e o Passivo + PL. |
| Status | Indica se o balanço está fechado ou aberto. |

A regra de cálculo é:

```text
Diferença = Ativo Total - (Passivo + Patrimônio Líquido)
```

Quando a diferença for igual a **R$ 0,00**, o status será:

```text
Fechado
```

Esse é o cenário esperado.

Quando a diferença for diferente de **R$ 0,00**, o status será:

```text
Aberto
```

Esse é um cenário não esperado e indica que pode existir alguma inconsistência nos lançamentos ou saldos das contas.

---

## 13. Regra do status do balanço

A validação final do balanço deve seguir a seguinte regra:

```text
Se Ativo Total = Passivo + Patrimônio Líquido:
    Status = Fechado

Senão:
    Status = Aberto
```

Ou, considerando a diferença:

```text
Se Diferença = R$ 0,00:
    Status = Fechado

Senão:
    Status = Aberto
```

---

## 14. Exportação do Balanço

A tela deve possuir a opção **Exportar Balanço**, responsável por gerar o relatório do Balanço Patrimonial em formato de documento.

No relatório exportado, a visualização é diferente da tela.

Enquanto a tela apresenta os grupos principalmente até o **segundo nível**, o relatório exportado deve apresentar uma estrutura mais detalhada, incluindo também os grupos de **terceiro nível**.

O relatório deve conter:

| Informação | Descrição |
|---|---|
| Cabeçalho institucional | Informações da instituição, sistema e identificação visual. |
| Nome do sistema | Exemplo: `COIN'S - Contabilidade Integrada`. |
| Título do relatório | Exemplo: `Balanço Patrimonial`. |
| Empresa | Nome da empresa selecionada. |
| CNPJ | CNPJ da empresa. |
| Período | Intervalo utilizado para geração do balanço. |
| Data e hora de geração | Data e hora em que o documento foi gerado. |

---

## 15. Estrutura do relatório exportado

No relatório exportado, a estrutura deve exibir os grupos até o **terceiro nível** do plano de contas.

Exemplo:

| Código | Classificação | Conta |
|---|---|---|
| 1 | 1 | Ativo |
| 2 | 1.1 | Ativo Circulante |
| 3 | 1.1.1 | Disponível |
| 13 | 1.1.2 | Clientes |
| 17 | 1.1.3 | Outros Créditos |
| 25 | 1.1.4 | Aplicações Financeiras |
| 31 | 1.1.5 | Estoque |
| 38 | 1.1.6 | Despesas Pagas Antecipadamente |

Dentro dos grupos de terceiro nível, devem ser exibidas as contas analíticas e seus respectivos saldos.

Exemplo:

```text
Ativo
  Ativo Circulante
    Disponível
      Caixa Geral                  R$ 150.000,00
      Fundo Fixo de Caixa          R$ 150.000,00

    Total do Ativo Circulante      R$ 300.000,00
```

O mesmo comportamento deve ser aplicado para:

- **Ativo**
- **Passivo**
- **Patrimônio Líquido**

---

## 16. Totais exibidos no relatório exportado

O relatório exportado deve apresentar os totais de cada grupo.

Exemplos:

| Total | Descrição |
|---|---|
| Total do AC | Total do Ativo Circulante |
| Total do ANC | Total do Ativo Não Circulante |
| Total do PC | Total do Passivo Circulante |
| Total do PNC | Total do Passivo Não Circulante |
| Total do PL | Total do Patrimônio Líquido |
| Total do Ativo | Soma total das contas do Ativo |
| Total do Passivo + PL | Soma total do Passivo com o Patrimônio Líquido |

Quando esses totais forem exibidos sem a indicação **D/C**, também devem seguir a regra de sinalização conforme a natureza esperada do grupo.

---

## 17. Regra principal da funcionalidade

A funcionalidade deve executar o seguinte fluxo:

```text
1. Receber o período inicial e final informado pelo usuário.

2. Validar se os dois campos foram preenchidos.

3. Buscar os lançamentos contábeis realizados dentro do período informado.

4. Considerar apenas os lançamentos vinculados às contas de:
   - Ativo
   - Passivo
   - Patrimônio Líquido

5. Calcular o saldo atual das contas analíticas.

6. Identificar a natureza do saldo de cada conta:
   - D para Débito
   - C para Crédito

7. Agrupar as contas conforme o plano de contas.

8. Na tela, exibir os grupos até o segundo nível.

9. No relatório exportado, exibir os grupos até o terceiro nível.

10. Calcular:
    - Total do Ativo
    - Total do Passivo
    - Total do Patrimônio Líquido
    - Passivo + Patrimônio Líquido
    - Diferença
    - Status do Balanço

11. Aplicar a regra de sinalização em todos os valores consolidados sem D/C.

12. Definir o status:
    - Fechado, se a diferença for R$ 0,00
    - Aberto, se a diferença for diferente de R$ 0,00
```

---

## 18. Resumo da regra de sinalização

```text
Ativo:
    Natureza esperada = Devedora
    Se o saldo for devedor:
        Exibir valor sem sinal
    Se o saldo for credor:
        Exibir valor com sinal negativo

Passivo:
    Natureza esperada = Credora
    Se o saldo for credor:
        Exibir valor sem sinal
    Se o saldo for devedor:
        Exibir valor com sinal negativo

Patrimônio Líquido:
    Natureza esperada = Credora
    Se o saldo for credor:
        Exibir valor sem sinal
    Se o saldo for devedor:
        Exibir valor com sinal negativo
```

Essa regra deve ser aplicada sempre que o valor for apresentado sem a coluna **D/C**.

---

## 19. Explicação resumida

A tela de **Balanço Patrimonial** permite consultar a situação patrimonial da empresa em um determinado período. Para isso, o usuário informa uma data inicial e uma data final, que são campos obrigatórios.

Com base nesse período, o sistema considera todos os lançamentos realizados nas contas de **Ativo**, **Passivo** e **Patrimônio Líquido**.

A tela apresenta um resumo com o **Total do Ativo**, **Total do Passivo**, **Patrimônio Líquido** e o **status do balanço**.

Como os campos do resumo e os totais dos grupos não exibem a coluna **D/C**, o sistema utiliza um sinal negativo quando o saldo está contrário à natureza contábil esperada do grupo.

Assim:

- O **Ativo**, que possui natureza devedora, será exibido com sinal negativo caso apresente saldo credor.
- O **Passivo**, que possui natureza credora, será exibido com sinal negativo caso apresente saldo devedor.
- O **Patrimônio Líquido**, que possui natureza credora, será exibido com sinal negativo caso apresente saldo devedor.

Logo abaixo, as contas são exibidas separadamente por grupos, mostrando o **código da conta**, o **nome da conta**, o **saldo atual** e a **natureza do saldo**, indicada por **D** para débito ou **C** para crédito.

Ao final, a tela realiza a conferência do balanço, comparando o **Total do Ativo** com a soma do **Passivo** e **Patrimônio Líquido**.

Caso a diferença seja igual a **R$ 0,00**, o balanço é considerado **fechado**.

Caso exista diferença, o balanço fica **aberto**, indicando que pode haver alguma inconsistência nos lançamentos.

Na exportação, o relatório apresenta as informações em um formato mais contábil e detalhado, incluindo os grupos até o **terceiro nível** do plano de contas, as contas analíticas, seus saldos e os totais de cada grupo.

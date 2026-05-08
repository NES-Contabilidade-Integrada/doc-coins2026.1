---
name: padrão-especificacao-requisitos
description: "Padrão da Especificação de Requisitos de Software (ERS) do COINS"
applyTo:
  - "docs/requisitos/especificacao-de-requisitos-de-software.md"
  - "docs/requisitos/**"
---

# Padrão de Especificação de Requisitos de Software (COINS)

Este documento define as práticas e padrões para escrever requisitos funcionais e não-funcionais no projeto COINS, garantindo clareza, precisão e facilidade de implementação.

## Princípios Fundamentais

### 1. **Requisitos Sem Descrição Visual**
❌ **ERRADO**: "O sistema deve apresentar uma subseção denominada 'Resultado Final'"
✅ **CORRETO**: "O sistema deve calcular e armazenar o resultado final do exercício"

- Defina **O QUÊ** o sistema faz, nunca **COMO** a UI o exibe
- Evite termos de design: "seção", "subseção", "campo", "coluna", "ícone", "destaque visual", "tabela"
- UI é responsabilidade do design/prototipagem, não dos requisitos

### 2. **Regras de Negócio Precisas e Técnicas**
- Especifique validações com valores exatos (limites, formatos, ranges)
- Use unidades claras (R$, DD/MM/AAAA, caracteres, páginas)
- Defina comportamentos sem ambiguidade

**EXEMPLO BOM:**
> O campo valor é obrigatório, deve ser informado em Reais (R$), possuir duas casas decimais e respeitar um valor mínimo de R$ 0,01 e máximo de R$ 99.999.999,99.

**EXEMPLO RUIM:**
> O sistema deve exibir o campo de valor de forma clara e formatada.

### 3. **Separação Clara: Descrição, Critérios de Aceite e Exceções**

#### **Descrição do Requisito**
- Explique o **objetivo funcional** (por que existe)
- Descreva o fluxo geral ou comportamento esperado
- Referencie conceitos do glossário quando necessário
- Nunca inclua como a interface será estruturada
- **NÃO inclua especificações técnicas detalhadas** (formatos, validações, limites) — isso vai nos Critérios de Aceite

**EXEMPLO:**
> O sistema deve permitir que o usuário visualize o Plano de Contas Padrão a qualquer momento sem perda de dados ou do progresso atual no sistema. Por ser o plano de contas da empresa estática, a exibição deve apresentar todos os campos essenciais: Código, Classificação e Descrição da Conta, seguindo o formato estabelecido no documento oficial. 

#### **Critérios de Aceite (CA)**
- Listam as **condições verificáveis** para que o requisito seja considerado concluído
- Devem ser **testáveis e específicos**
- Podem referenciar dados da base (formatos, links para documentos oficiais)
- Incluem validações, limites, restrições e comportamentos esperados

**EXEMPLO ESTRUTURADO:**
```
■ O Plano de Contas Padrão deve seguir exatamente os dados do documento oficial em [link]
■ O sistema deve exibir a indentação correta para diferenciar níveis hierárquicos (grupos, sintéticas, analíticas)
■ O usuário não deve ser capaz de incluir, alterar ou remover contas
■ O sistema deve permitir filtragem independente por: Código, Classificação, Descrição
■ A busca por Descrição deve ser insensível a maiúsculas/minúsculas com correspondências parciais
■ Caso nenhum resultado seja encontrado, exibir mensagem informativa
■ Remoção de todos os filtros deve restaurar a exibição completa
```

#### **Exceções dos Critérios de Aceite**
- Definem **casos especiais, erros e limites** não cobertos pelas CA normais
- Referenciadas como `[CA-N]` ou `[CA-N.M]` dentro da descrição ou CA
- Focam em **comportamento em caso de erro** ou **condições de borda**

**EXEMPLO:**
```
[CA-3] Caso o usuário informe uma conta inexistente ou sintética, 
       o sistema deve bloquear o lançamento e exibir mensagem de erro.

[CA-10] Caso a soma total de crédito e débito não sejam iguais, 
        o lançamento contábil deve ser bloqueado e uma mensagem de erro exibida.
```

---

## Estrutura Padrão de um Requisito Funcional

### Formato em Tabela (Atual - ERS)

Este é o formato oficial do documento ERS. Os critérios de aceite usam o prefixo `CA-N.` e as exceções usam `EX- N.` (com espaço antes do número), referenciando o CA relacionado entre colchetes.

O projeto usa MkDocs Material com `md_in_html` habilitado, portanto **use HTML para replicar o estilo visual do Drive** (fundo azul no cabeçalho). Markdown puro não suporta cores de fundo em células de tabela.

#### Template HTML (padrão visual do Drive)

As cores oficiais são:
> **⚠️ Terminologia:** use sempre **Módulo** (ex: "Módulo 2"). O termo "Épico" foi descontinuado.

- **`#2E74B5`** — azul escuro para a linha do cabeçalho (RF-XX / Módulo)
- **`#BDD7EE`** — azul claro para as linhas "Critérios de Aceite:" e "Exceções dos Critérios de Aceite:"

```html
<table style="width:100%">
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">RF-XX Nome do Requisito Funcional</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo N</th>
</tr>
</thead>
<tbody>
<tr>
  <td colspan="2">Descrição do requisito.</td>
</tr>
<tr>
  <td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td>
</tr>
<tr>
  <td colspan="2"><strong>CA-1.</strong> Critério específico e verificável.</td>
</tr>
<tr>
  <td colspan="2"><strong>CA-2.</strong> Critério específico e verificável.</td>
</tr>
<tr>
  <td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td>
</tr>
<tr>
  <td colspan="2"><strong>EX- 2.</strong> [CA-2] Descrição da exceção/caso especial.</td>
</tr>
</tbody>
</table>
```

#### Fallback Markdown (sem cores)

Use apenas quando não for possível usar HTML:

```
| Nome do Requisito Funcional | Módulo X |
|-----|:---:|
| [Descrição breve e objetiva do requisito] |  |
| **Critérios de Aceite:** |  |
| CA-1. [Critério específico e verificável] |  |
| CA-2. [Critério específico e verificável] |  |
| **Exceções dos Critérios de Aceite:** |  |
| EX- 2. [CA-N] [Descrição da exceção/caso especial] |  |
```

**Regras de numeração:**
- Critérios de aceite: `CA-1.`, `CA-2.`, `CA-3.` … (sequencial, com ponto final)
- Exceções: `EX- N.` onde N é o número do CA a que a exceção se refere (com espaço entre `EX-` e o número), seguido do código `[CA-N]` entre colchetes

> **⚠️ Atenção ao copiar do Drive:** O Google Drive exporta o conteúdo sem os prefixos `CA-1.`, `CA-2.`, `EX- 2.` etc. Ao importar ou colar conteúdo do Drive, é obrigatório reinserir esses labels manualmente conforme o padrão acima.

### Formato Hierárquico com Contexto de Seção (Recomendado para Documentos Nativos)

**Estrutura Completa:**
```markdown
#### [Nome da Seção - ex: Livro Diário]

[Descrição introdutória da seção explicando o contexto geral]

##### [Nome do Requisito Funcional]

**Módulo:** [Número e nome do Módulo]

[Descrição do requisito]

**Critérios de Aceite:**
- CA-1. Critério 1
- CA-2. Critério 2
- CA-3. Critério 3

**Exceções dos Critérios de Aceite:**
- EX- 2. [CA-2] Exceção referente ao CA-2
- EX- 3. [CA-3] Exceção referente ao CA-3
```

**EXEMPLO COMPLETO:**
```markdown
#### Livro Diário

Esta subseção descreve as funcionalidades vinculadas ao Livro Diário, 
que registra de forma cronológica todos os lançamentos contábeis 
realizados pela empresa. O foco é garantir a integridade dos registros 
e permitir sua visualização, edição, exclusão e filtragem conforme 
critérios definidos pelo usuário.

##### Gerenciar Lançamento Contábil

**Módulo:** Módulo 2

O sistema deve permitir que o usuário realize lançamentos contábeis 
para uma empresa previamente cadastrada, informando data do lançamento, 
código da conta de débito e/ou crédito, valor e histórico. O nome das 
contas deve ser exibido automaticamente pelo sistema. O usuário deve 
poder editar e excluir lançamentos previamente cadastrados, desde que 
todas as regras sejam respeitadas.

**Critérios de Aceite:**
- CA-1. Data do lançamento: obrigatória, formato DD/MM/AAAA, intervalo 01/01/ano-atual a 31/01/2050
- CA-2. Códigos de débito e crédito: obrigatórios, devem ser contas analíticas do Plano de Contas Padrão
- CA-3. Nome da conta: exibido automaticamente, nunca editável manualmente
- CA-4. Máximo 6 contas de débito e 6 contas de crédito por lançamento
- CA-5. Campo Valor: obrigatório, R$, 2 casas decimais, entre R$ 0,01 e R$ 99.999.999,99
- CA-6. Campo Descrição (histórico): opcional, máximo 200 caracteres
- CA-7. Usuário pode editar qualquer campo após criar o lançamento
- CA-8. Usuário pode deletar lançamentos existentes
- CA-9. Sistema suporta mínimo 1.000 lançamentos por empresa
- CA-10. Validação: Soma(débitos) = Soma(créditos), senão bloquear

**Exceções dos Critérios de Aceite:**
- EX- 3. [CA-3] Conta inexistente ou sintética → bloquear lançamento e exibir erro
- EX- 5. [CA-5] Valor fora do range → lançar exceção
- EX- 6. [CA-6] Descrição > 200 caracteres → lançar exceção
- EX- 10. [CA-10] Soma débito ≠ soma crédito → bloquear e exibir erro
```

---

## Formato em Tabela vs. Hierárquico: Quando Usar Cada Um

### Formato em Tabela (Atual na ERS)
**Vantagem:** Compacto, bom para listas de requisitos
**Desvantagem:** Difícil de ler em docs grandes, contexto de seção fica disperso

**Use quando:**
- Requisitos precisam manter estrutura rígida (ERS oficial)
- Documento é exportado/importado frequentemente
- Consultaria via tabela é necessária

### Formato Hierárquico com Contexto
**Vantagem:** Mais legível, agrupa requisitos por seção, contexto claro, melhor para navegação
**Desvantagem:** Requer mais espaço, menos compacto

**Use quando:**
- Documentação nativa em Markdown
- Equipe precisa entender contexto da seção facilmente
- Documentos será navegado por pessoas (não gerado automaticamente)
- Requisitos relacionados precisam ser agrupados semanticamente

**RECOMENDAÇÃO:** Use hierárquico para documentos de trabalho e planejamento (COINS), tabelas para artefatos finais/oficiais.

---

Este é o **ponto crítico** para evitar desvios do padrão. Entenda exatamente o que vai em cada seção:

### O que vai na DESCRIÇÃO

✅ **DEVE conter:**
- Objetivo e contexto da funcionalidade
- Fluxo geral em linguagem natural
- Referências a conceitos/documentos
- Decisões de negócio/requisitos do usuário

❌ **NÃO deve conter:**
- Especificações de campos (nomes, tipos, formatos)
- Validações técnicas (limites, ranges, padrões)
- Detalhes de cálculos ou regras de negócio
- Descrição de componentes UI

**EXEMPLO CORRETO:**
```
O sistema deve permitir que o usuário realize lançamentos contábeis, 
informando data, contas de débito/crédito e valor. O nome das contas 
deve ser exibido automaticamente pelo sistema. O usuário deve poder 
editar e excluir lançamentos previamente cadastrados.
```

**EXEMPLO ERRADO:**
```
O sistema deve permitir que o usuário preencha um formulário com os campos:
- Data (formato DD/MM/AAAA, entre 01/01 e 31/01/2050)
- Código da Conta Débito (4 dígitos, analitica, obrigatório)
- Código da Conta Crédito (4 dígitos, analitica, obrigatório)
- Valor (R$, 2 casas, mín R$ 0,01, máx R$ 99.999.999,99)
- Descrição (até 200 caracteres, opcional)
```

### O que vai nos CRITÉRIOS DE ACEITE

✅ **DEVE conter:**
- **Cada campo do requisito especificado**: nome, tipo, formato, limites
- **Validações técnicas**: ranges, valores permitidos, restrições
- **Regras de negócio precisas**: cálculos, condições, comportamentos
- **Casos de sucesso**: o que acontece quando tudo funciona
- **Dados de referência**: links a documentos, valores exatos

❌ **NÃO deve conter:**
- Descrição de como a UI será "exposto" ou "apresentado"
- Termos visuais (seção, tabela, campo visível, destacado)
- Fluxo narrativo (use pontos diretos)
- **Texto literal de mensagens de erro ou sucesso** — apenas indicar que o sistema deve exibir uma mensagem
- **Detalhes de implementação técnica** (camadas de arquitetura, processamento em memória, "camada de serviço/UI")

**EXEMPLO CORRETO (mensagem):**
```
■ Caso não haja contas com saldo no grupo, o sistema deve exibir mensagem informando a ausência de valores
■ O sistema deve exibir mensagem de confirmação após o sucesso da operação
```

**EXEMPLO ERRADO (mensagem):**
```
■ Caso não haja contas com saldo, exibir: "Não há valores a serem apurados em [nome do grupo]."
■ O sistema deve exibir mensagem de confirmação após sucesso: "Apuração realizada com sucesso."
```

**EXEMPLO CORRETO (detalhe técnico):**
```
■ O sistema deve permitir que o usuário confira os lançamentos antes de confirmá-los
```

**EXEMPLO ERRADO (detalhe técnico):**
```
■ Os lançamentos devem ser processados apenas em memória (camada de serviço/UI) para fins de conferência
```

> **Nota:** Especificar que o sistema carrega dados **automaticamente, sem necessidade de ação do usuário**, é válido e deve ser mantido. O que se evita é descrever *como* isso ocorre internamente (ex: "via cache", "em memória").

**EXEMPLO CORRETO:**
```
■ Campo Data: obrigatório, formato DD/MM/AAAA, intervalo 01/01/ano-atual a 31/01/2050
■ Campo Código Débito: obrigatório, deve ser conta analítica do Plano de Contas
■ Campo Código Crédito: obrigatório, deve ser conta analítica do Plano de Contas
■ Campo Valor: obrigatório, R$, 2 casas decimais, entre R$ 0,01 e R$ 99.999.999,99
■ Campo Descrição: opcional, máximo 200 caracteres
■ Lançamento máximo 6 débitos + 6 créditos
■ Soma(débitos) deve ser igual a Soma(créditos), senão bloquear
■ Usuário pode editar qualquer campo após criar o lançamento
■ Usuário pode deletar lançamentos existentes
```

---

## Checklist de Qualidade

Antes de finalizar um requisito, verifique:

### Descrição
- [ ] Descreve **o que** o sistema faz (verbo no infinitivo: permitir, registrar, exibir, calcular)
- [ ] Explica o **objetivo** ou **contexto** da funcionalidade
- [ ] Não menciona componentes UI (seção, tabela, campo, ícone, etc.)
- [ ] Referencia conceitos do glossário ou documentos oficiais se necessário
- [ ] Comprimento adequado (1-3 parágrafos)
- [ ] Está vinculado à seção correta (Pré-contexto disponível)

### Critérios de Aceite
- [ ] Cada critério começa com o prefixo **`CA-N.`** (ex: `CA-1.`, `CA-2.`) — nunca omitir ao copiar do Drive
- [ ] Cada critério é **individual e verificável**
- [ ] Inclui **valores específicos** (formatos, limites, ranges, unidades)
- [ ] Evita palavras vagas: "claro", "apropriado", "bom", "intuitivo"
- [ ] Especifica **formatos de dados** (DD/MM/AAAA, R$, caracteres, etc.)
- [ ] Define **limites numéricos** se aplicável (mínimo/máximo, quantidade de registros)
- [ ] Inclui **regras de validação** e **comportamentos esperados**
- [ ] Referencia outros requisitos quando há dependência (ex: `[RF-02]`)
- [ ] **Não especifica o texto literal de mensagens** — apenas indica que o sistema deve exibir uma mensagem (de erro, aviso ou confirmação)
- [ ] **Não menciona detalhes de implementação técnica** (processamento em memória, camadas de arquitetura, etc.)

### Exceções
- [ ] Cada exceção começa com **`EX- N.`** (espaço entre `EX-` e o número) — nunca omitir ao copiar do Drive
- [ ] O número N de `EX- N.` corresponde ao **número do CA referenciado** entre colchetes (`[CA-N]`)
- [ ] Define **casos de erro** ou **situações de borda**
- [ ] Especifica **comportamento esperado** em caso de erro
- [ ] Não é redundante com os CA normais

### Geral
- [ ] Linguagem técnica e precisa
- [ ] Sem descrição de UI/Design
- [ ] Sem ambiguidade ou termos genéricos
- [ ] Alinhado com o Plano de Contas e conceitos do COINS
- [ ] Linkado ao Módulo correto

---

## Exemplos de Boas Práticas

### ✅ EXEMPLO 1: Gerenciar Lançamento Contábil (RF-05)

**Descrição:**
> O sistema deve permitir que o usuário realize lançamentos contábeis para uma empresa previamente cadastrada, informando os seguintes campos: data do lançamento, código da conta de débito e/ou código da conta de crédito, valor e histórico (descrição). O nome das contas associadas aos códigos informados deve ser exibido automaticamente pelo sistema, não devendo ser informado manualmente pelo usuário. Além disso, o usuário deve poder editar e excluir lançamentos previamente cadastrados, desde que todas as regras estabelecidas sejam respeitadas.

**Critérios de Aceite:**
- CA-1. A data do lançamento é obrigatória, deve ser especificada manualmente e estar no formato **DD/MM/AAAA** dentro do intervalo **01/01/ano-atual** a **31/01/2050**
- CA-2. O usuário deve informar manualmente os códigos das contas de débito e crédito (campos obrigatórios), que devem obrigatoriamente seguir a estrutura definida no Plano de Contas Padrão
- CA-3. O sistema deve exibir automaticamente o nome da conta correspondente aos códigos de débito e crédito informados pelo usuário
- CA-4. O campo de nome da conta não deve ser editável nem preenchido manualmente em nenhuma tela de cadastro ou edição de lançamento contábil
- CA-5. Sistema aceita apenas códigos de **contas analíticas**; caso informado código de conta sintética ou inexistente, bloquear o lançamento e lançar mensagem de exceção
- CA-6. O vínculo entre código e nome da conta deve seguir os dados do Plano de Contas Padrão (documento oficial)
- CA-7. O lançamento pode conter, no máximo, **6 contas de débito e 6 contas de crédito**; caso o limite seja excedido, impedir a operação e exibir mensagem de erro
- CA-8. Campo valor obrigatório em **R$**, **2 casas decimais**, **R$ 0,01 a R$ 99.999.999,99**; caso o valor esteja fora deste intervalo, lançar mensagem de exceção
- CA-9. Campo histórico (descrição) opcional, máximo **200 caracteres**; caso o limite seja excedido, lançar mensagem de exceção
- CA-10. Usuário pode editar qualquer campo do lançamento contábil que ele cadastrou anteriormente (data, códigos, valor, histórico)
- CA-11. Usuário pode excluir lançamentos existentes
- CA-12. Sistema suporta mínimo **1.000 lançamentos por empresa**
- CA-13. Sistema valida que **soma(débitos) = soma(créditos)**; caso não sejam iguais, bloquear e exibir mensagem de erro

**Exceções dos Critérios de Aceite:**
- EX- 5. [CA-5] Caso o usuário informe uma conta inexistente ou sintética, o sistema deve bloquear o lançamento e exibir mensagem de erro
- EX- 8. [CA-8] Caso o valor informado seja inferior ao mínimo permitido ou superior ao máximo aceito, o sistema deve lançar uma mensagem de exceção
- EX- 9. [CA-9] Caso o histórico (descrição) ultrapasse o número máximo de caracteres permitido, o sistema deve lançar uma mensagem de exceção
- EX- 13. [CA-13] Caso a soma total de crédito e débito não sejam iguais, o lançamento contábil deve ser bloqueado e uma mensagem de erro deve ser exibida

---

### ❌ EXEMPLO 2: O QUE EVITAR (Seção Apuração)

**PROBLEMA 1 - Mistura UI com Regra:**
> ❌ "O sistema deve apresentar uma subseção denominada 'Resultado Final', consolidando as informações conclusivas"

**CORRETO:**
> ✅ "O sistema deve calcular e armazenar o resultado final (lucro ou prejuízo) consolidando receitas, custos e despesas"

**PROBLEMA 2 - Critério muito genérico:**
> ❌ "A seção deve exibir os campos: Tipo de Resultado, Valor e Conta Destino"

**CORRETO:**
> ✅ Campo "Tipo de Resultado" deve conter valores **"Lucro"** ou **"Prejuízo"** conforme cálculo de (Total Receitas - Total Custos/Despesas)
> ✅ Campo "Valor" deve estar em formato **R$ com 2 casas decimais**, mínimo **R$ 0,00**, máximo **R$ 999.999.999,99**
> ✅ Campo "Conta Destino" deve referenciar **"Lucros Acumulados"** se lucro ou **"Prejuízos Acumulados"** se prejuízo, conforme Plano de Contas

**PROBLEMA 3 - Ca sem contexto técnico:**
> ❌ "O sistema deve listar obrigatoriamente todas as contas... de forma detalhada"

**CORRETO:**
> ✅ Sistema deve listar **todas as contas analíticas** com **saldo ≠ 0** dos grupos **"CONTAS DE RESULTADO - RECEITAS"** e **"CONTAS DE RESULTADO - CUSTOS E DESPESAS"**
> ✅ Cada linha deve conter: **Código (4 dígitos), Descrição (máx 100 caracteres), Tipo (Receita/Despesa), Saldo Atual (R$ com 2 casas), D/C (D ou C)**

---

## Referências

- [Fundamento da Estrutura dos Requisitos](src-link)
- [Glossário de Termos COINS](src-link)
- Módulos do Sistema (seção 4 da ERS)
- Plano de Contas Padrão (documento oficial)

---

## Hierarquia de Headings e Sumário no Documento ERS

### Estrutura de Headings

O documento ERS usa a seguinte hierarquia (com `toc_depth: 3` no MkDocs, apenas `##` e `###` aparecem no TOC lateral):

| Nível | Tipo | Exemplo |
|-------|------|---------|
| `##` | Seções principais | `## Requisitos de Software` |
| `###` | Subseções de 1º nível | `### Requisitos Funcionais`, `### Menu`, `### Empresas` |
| `####` | Subseções de 2º nível e **headings individuais de RF** | `#### Plano de Contas`, `#### RF-04 Exibir Plano de Contas Padrão {#anchor}` |

**Regras:**
- `## Requisitos Funcionais` e `## Requisitos Não-Funcionais` devem ser `###` (são filhos de `## Requisitos de Software`)
- Cada RF **obrigatoriamente** deve ter um heading `####` imediatamente antes de sua tabela HTML
- O heading do RF cria a âncora usada no sumário e nos links internos
- RNF sub-seções (Compatibilidade, Portabilidade, etc.) devem ser `####`

### Heading Obrigatório Antes de Cada Tabela de RF

Antes de toda tabela de requisito funcional, adicione:

```markdown
#### RF-XX Nome do Requisito Funcional {#anchor-do-sumario}

<table style="width:100%">
...
```

O `{#anchor}` é o ID que o MkDocs usa para o link. Use o mesmo anchor que está no sumário, em kebab-case minúsculo, sem acentos.

**EXEMPLO:**
```markdown
#### RF-05 Gerenciar Lançamento Contábil {#gerenciar-lancamento-contabil}

<table style="width:100%">
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Gerenciar Lançamento Contábil</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 2</th>
</tr>
</thead>
...
</table>
```

### Formato do Sumário

O sumário deve ser uma lista Markdown aninhada (não links planos linha-por-linha). Use 4 espaços por nível de indentação:

```markdown
**Sumário**

- [1. Introdução](#introdução)
- [6. Requisitos de Software](#requisitos-de-software)
    - [6.1. Requisitos Funcionais](#requisitos-funcionais)
        - [6.1.1. Menu](#menu)
            - [RF-01 Exibir Menu Principal](#exibir-menu-principal)
        - [6.1.2. Empresas](#empresas)
            - [6.1.2.1. Estrutura da Empresa](#estrutura-da-empresa)
                - [RF-02 Exibir Empresa Estática](#exibir-empresa-estática)
```

**Nunca** use o formato exportado do Google Drive (links planos com número de página no texto do link).

---

## Quando Usar Esta Skill

- Redigindo novos requisitos funcionais (RF)
- Revisando/modificando estrutura de requisitos existentes
- Corrigindo desvios do padrão (especialmente seção Apuração e DRE)
- Criando templates para novos módulos
- Orientando equipe sobre boas práticas de especificação
- **Preferir formato hierárquico com contexto de seção** para novos requisitos em Markdown

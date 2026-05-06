---
name: boas-praticas-markdown
description: "Guia de boas práticas de Markdown para documentação clara, legível e visualmente agradável"
applyTo:
  - "docs/**/*.md"
  - "README.md"
---

# Boas Práticas de Markdown para Documentação

Este guia estabelece padrões de formatação Markdown para garantir consistência, legibilidade e apresentação visual agradável em toda a documentação COINS.


## 1. Estrutura de Títulos

### Hierarquia Clara
Use a hierarquia de títulos de forma **semântica e consistente**:

```markdown
# Título Principal (H1) - Uma vez por documento
## Seção Principal (H2)
### Subseção (H3)
#### Detalhes (H4)
```

✅ **CORRETO:**
```markdown
# Especificação de Requisitos de Software

## Requisitos Funcionais

### Menu
#### RF-01 Exibir Menu Principal
```

❌ **ERRADO:**
```markdown
# Especificação de Requisitos de Software
# Requisitos Funcionais (não repetir H1)
# Menu (hierarquia desorganizada)
### RF-01 (pulou seções)
```

### Regras
- Máximo **um H1 por documento** (título principal)
- Cada nível de hierarquia deve ter **pelo menos 1 seção**
- Não pule níveis (ex: H1 → H3 é errado)
- Use H2 para seções principais
- Use H3 para subseções
- Use H4+ para detalhes e especificações

---

## 2. Formatação de Texto Corporal

### Regras de Ouro

| Elemento | Formato | Quando Usar | Exemplo |
|----------|---------|-------------|---------|
| **Negrito** | `**texto**` | Termos importantes, ênfase | O campo **data** é obrigatório |
| *Itálico* | `*texto*` | Definições, contexto, termos estrangeiros | Esta é uma *prévia* do resultado |
| ~~Riscado~~ | `~~texto~~` | Indicar exclusão/depreciação | ~~Funcionalidade removida~~ |
| `Código` | `` `código` `` | Valores, nomes técnicos, IDs | Digite `DD/MM/AAAA` no formato |
| Observação | `> Texto` | Contexto importante, aviso | > **Nota:** Este é um campo crítico |

### Espaçamento de Texto

✅ **CORRETO - Parágrafo espaçado:**
```markdown
Esta é a primeira linha do parágrafo. Ela contém informação importante
sobre como o sistema funciona.

Este é um novo parágrafo, separado pela linha em branco acima. 
Melhora muito a legibilidade.

E aqui temos um terceiro parágrafo com mais contexto.
```

❌ **ERRADO - Blocos compactos:**
```markdown
Esta é a primeira linha do parágrafo. Ela contém informação importante
sobre como o sistema funciona.
Este é um novo parágrafo, mas sem espaço acima.
E aqui temos um terceiro parágrafo sem separação também.
```

**Regra:** Sempre deixe **uma linha em branco** entre parágrafos.

---

## 3. Listas

### Listas com Ponto (Unordered)

✅ **CORRETO - Claro e organizado:**
```markdown
O sistema deve oferecer as seguintes funcionalidades:

- Registrar lançamentos contábeis
- Consultar Livro Diário
- Gerar Balancete de Verificação
- Exportar relatórios em PDF
```

❌ **ERRADO - Sem contexto ou compacto:**
```markdown
Funcionalidades: Registrar lançamentos contábeis, Consultar Livro Diário, Gerar Balancete de Verificação, Exportar relatórios em PDF
```

### Listas Numeradas (Ordered)

✅ **CORRETO - Para sequências:**
```markdown
Siga os passos abaixo para criar um lançamento:

1. Acesse a empresa desejada
2. Navegue até a aba Livro Diário
3. Clique em "Novo Lançamento"
4. Preencha os campos obrigatórios
5. Clique em "Salvar"
```

❌ **ERRADO - Sem contexto:**
```markdown
1) Acesse a empresa
2) Aba Livro Diário
3) Novo
4) Preencha
5) Salvar
```

### Listas Aninhadas

```markdown
Critérios de Aceite:
- Data do Lançamento
  - Formato: DD/MM/AAAA
  - Intervalo: 01/01/ano-atual a 31/01/2050
  - Obrigatório: Sim
  
- Contas Contábeis
  - Débito: contas analíticas, obrigatório
  - Crédito: contas analíticas, obrigatório
  - Máximo: 6 débitos + 6 créditos
```

---

## 4. Tabelas

### Estrutura Básica

✅ **CORRETO - Bem formatado:**
```markdown
| Campo | Tipo | Obrigatório | Intervalo |
|-------|------|:----------:|-----------|
| Data | Texto | Sim | DD/MM/AAAA |
| Valor | Numérico | Sim | R$ 0,01 a R$ 99.999.999,99 |
| Descrição | Texto | Não | Máximo 200 caracteres |
```

**Alinhamento:**
- Usar `|:---|` para alinhar **à esquerda**
- Usar `|:---:|` para **centralizar**
- Usar `|---:|` para alinhar **à direita**

### Tabelas com Múltiplas Linhas

Para tabelas complexas, use quebra de linha com `<br>`:

```markdown
| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.0 | 25/08/2025 | Adiciona base dos requisitos funcionais | Fernanda Pessoa |
| 2.0 | 22/10/2025 | Atualiza estrutura;<br/>Retirada de critérios de responsividade | Jerfferson Júnior |
| 3.0 | 23/10/2025 | Adição de Requisitos referentes ao Balancete | Fernanda Pessoa |
```

### Tabelas Centralizadas

Markdown puro não centraliza tabelas, mas você pode usar HTML quando necessário:

```html
<div style="text-align: center;">

| Campo | Valor |
|-------|-------|
| Total Receitas | R$ 50.000,00 |
| Total Despesas | R$ 30.000,00 |
| Resultado | R$ 20.000,00 |

</div>
```

### Tabelas com Estilo Visual (HTML)

Markdown puro **não suporta cores de fundo** em células de tabela. O projeto usa MkDocs Material com `md_in_html` habilitado, então é possível usar HTML com `style` inline para replicar o visual do Google Drive.

**Quando usar:** tabelas de requisitos funcionais (ERS) que precisam do fundo azul padrão do documento oficial.

Cores do padrão COINS:
- **`#2E74B5`** — azul escuro para cabeçalhos principais
- **`#BDD7EE`** — azul claro para linhas de seção intermediárias

```html
<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Título da Tabela</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Coluna</th>
</tr>
</thead>
<tbody>
<tr>
  <td colspan="2">Conteúdo normal.</td>
</tr>
<tr>
  <td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Seção Intermediária:</strong></td>
</tr>
<tr>
  <td colspan="2">Conteúdo da seção.</td>
</tr>
</tbody>
</table>
```

> **Nota:** Para tabelas simples sem necessidade de cor, prefira Markdown padrão — é mais fácil de manter.

---

## 5. Blocos de Código

### Código Inline (Uma linha)

✅ **CORRETO:**
```markdown
Digite o valor `99.999,99` para representar a quantidade máxima.
```

### Blocos de Código (Múltiplas linhas)

✅ **CORRETO - Com linguagem especificada:**
```markdown
\`\`\`json
{
  "data": "25/10/2025",
  "valor": 1500.00,
  "descricao": "Lançamento de teste"
}
\`\`\`
```

✅ **CORRETO - Markdown:**
```markdown
\`\`\`markdown
# Título
## Subtítulo
- Item 1
- Item 2
\`\`\`
```

❌ **ERRADO - Sem linguagem:**
```
```
código sem linguagem
```
```

### Citações (Blockquotes)

✅ **CORRETO:**
```markdown
> **Nota Importante:** Este requisito é crítico para a integridade
> dos dados financeiros. Não pode ser modificado sem aprovação.

> A data deve sempre estar no formato DD/MM/AAAA conforme padrão
> interno do COINS.
```

---

## 6. Links e Referências

### Links Internos (Markdown)

✅ **CORRETO:**
```markdown
Consulte a [Especificação de Requisitos](docs/requisitos/especificacao-de-requisitos-de-software.md) para mais detalhes.

Veja também o [Glossário de Termos](docs/requisitos/glossario-de-termos.md).
```

❌ **ERRADO:**
```markdown
Consulte a especificação em docs/requisitos/especificacao-de-requisitos-de-software.md

Veja também o Glossário em docs/requisitos/glossario-de-termos.md
```

### Links Externos (Google Drive, etc)

```markdown
Os dados oficiais estão em [Plano de Contas Padrão](https://docs.google.com/spreadsheets/d/1eYd4BTtSIW6IggKeMR8KJp0oBfOmKuRALwSfzIBAEEw/edit?usp=drive_link).

Consulte também o [Glossário no Drive](https://docs.google.com/document/d/1fWNvAuHWdnDFCu3-luM2oZ-49I2bVVsvHIz6awT9p3g/edit?usp=sharing).
```

---

## 7. Ênfase e Destaques

### Usando Negrito e Itálico

✅ **CORRETO - Ênfase clara:**
```markdown
O campo **data** é ***absolutamente obrigatório*** para qualquer lançamento.

O valor deve estar entre **R$ 0,01** e **R$ 99.999.999,99**.

Este é um requisito *crítico* que afeta toda a integridade do sistema.
```

### Ícones e Símbolos (Quando Apropriado)

```markdown
✅ Este procedimento foi validado
❌ Esta funcionalidade não é suportada
⚠️ Cuidado com este passo
📝 Nota implementação
🔄 Ação reversível
```

---

## 8. Seções Especiais

### Nota de Atenção
```markdown
> **⚠️ ATENÇÃO:** Esta operação não pode ser desfeita. 
> Confirme antes de prosseguir.
```

### Dica/Sugestão
```markdown
> **💡 Dica:** Você pode usar filtros combinados para encontrar 
> lançamentos mais rapidamente.
```

### Informação Importante
```markdown
> **ℹ️ Informação:** O sistema valida automaticamente a data 
> do lançamento ao exibir.
```

---

## 9. Exemplo Completo: Documento Bem Formatado

```markdown
# Gerenciamento de Lançamentos Contábeis

## Visão Geral

O sistema COINS permite que usuários registrem lançamentos contábeis 
de forma rápida e segura. Esta seção descreve os procedimentos e 
especificações técnicas.

## Criar um Lançamento

### Procedimento Passo a Passo

Siga os passos abaixo para criar um novo lançamento:

1. Acesse a **empresa desejada** no menu lateral
2. Clique na aba **Livro Diário**
3. Clique em **Novo Lançamento**
4. Preencha os campos obrigatórios (veja tabela abaixo)
5. Clique em **Salvar**

### Campos Obrigatórios

| Campo | Formato | Limite | Observação |
|-------|---------|--------|------------|
| Data | DD/MM/AAAA | 01/01 até 31/01/2050 | Sempre obrigatório |
| Débito | Código conta | Contas analíticas | Máx 6 contas |
| Crédito | Código conta | Contas analíticas | Máx 6 contas |
| Valor | R$ | 0,01 a 99.999.999,99 | 2 casas decimais |
| Descrição | Texto | 200 caracteres | Opcional |

### Validações

O sistema realiza as seguintes validações **automaticamente**:

- ✅ Verifica se a conta existe no Plano de Contas Padrão
- ✅ Valida se a conta é analítica (não sintética)
- ✅ Confirma que Débito = Crédito
- ✅ Formata o valor em Reais com 2 casas decimais

> **Nota:** Se qualquer validação falhar, o lançamento será bloqueado
> e uma mensagem de erro será exibida.

## Editar e Deletar

O usuário pode **editar** ou **deletar** lançamentos já criados, 
desde que as mesmas validações sejam respeitadas.

---

Consulte o [Glossário de Termos](../glossario-de-termos.md) para 
definições de conceitos técnicos.
```

---

## 10. Checklist de Qualidade - Markdown

Antes de finalizar um documento, verifique:

### Estrutura
- [ ] **Um único H1** (título principal) por documento
- [ ] Hierarquia de títulos é **lógica e sem pulos** (H1 → H2 → H3)
- [ ] Títulos usam **maiúscula apenas na primeira palavra** (ex: `### Subseção de requisitos`)
- [ ] Máximo **4 níveis de hierarquia** (H1 a H4)

### Formatação de Texto
- [ ] Parágrafos são **separados por linha em branco**
- [ ] Negrito `**texto**` usado para **ênfase importante**
- [ ] *Itálico* `*texto*` usado para contexto e definições
- [ ] Código `` `texto` `` usado para **valores, IDs, formatos**
- [ ] Sem parágrafos **maiores que 3-4 frases**

### Listas
- [ ] Listas têm **introdução em parágrafo anterior**
- [ ] Itens são **breves e diretos** (máx 1-2 frases cada)
- [ ] Listas numeradas têm **propósito sequencial claro**
- [ ] Listas com ponto são **homogêneas** (mesmo tipo de informação)

### Tabelas
- [ ] Headers estão **em negrito ou destacados**
- [ ] Alinhamento é **apropriado** (esquerda para texto, centro para status, direita para números)
- [ ] Sem tabelas **muito largas** (máx 6-8 colunas visíveis)
- [ ] Tabelas contêm **contexto/introdução acima delas**

### Links
- [ ] Links têm **texto descritivo** (não URLs expostas)
- [ ] Links internos usam **caminhos relativos**
- [ ] Links externos funcionam e são **verificados**
- [ ] Sem links para **recursos temporários** (Google Drive compartilhado)

### Visibilidade Geral
- [ ] Documento tem **bom contraste visual** entre seções
- [ ] Elementos importantes estão **em negrito ou citação**
- [ ] Código está em **blocos com linguagem especificada**
- [ ] Nenhuma linha fica **maior que 100 caracteres** (exceto URLs/código)
- [ ] Documento segue **tom profissional e consistente**

---

## 11. Exportação Google Drive para Markdown

Se estiver exportando documentos do Google Drive para Markdown, siga estas regras **pós-exportação**:

### Problemas Comuns e Soluções

| Problema | Causa | Solução |
|----------|-------|---------|
| Títulos perdidos em mudança de seções | Formatação do Drive não mapeia bem | Reorganizar com `##`, `###` etc |
| Espaçamento inconsistente | Drive vs Markdown usam padrões diferentes | Adicionar linhas em branco entre parágrafos |
| Links quebrados | URLs do Drive perdidas | Usar `[Texto](caminho/arquivo.md)` |
| Tabelas desalinhadas | Markdown não herda espaço do Drive | Reformatar com `\|` e padronizar |
| Negrito/itálico perdido | Formatação não exportada corretamente | Reaplicar manualmente com `**` e `*` |
| Listas aninhadas desorganizadas | Drive não exporta hierarquia bem | Usar indentação com 2 espaços |
| **Prefixos `CA-N.` e `EX- N.` ausentes** | Drive não preserva labels de itens numerados | Reinserir manualmente conforme padrão ERS |

### Problema Específico: Labels de Requisitos Perdidos

O Google Drive **não preserva os prefixos** `CA-1.`, `CA-2.`, `EX- 2.` etc. ao exportar ou copiar conteúdo para Markdown. O texto do critério é copiado, mas o label identificador é removido.

**O que acontece ao copiar do Drive:**

❌ **Resultado ao colar:**
```markdown
**Critérios de Aceite:**
- A data do lançamento é obrigatória, deve estar no formato DD/MM/AAAA
- O usuário deve informar manualmente os códigos das contas
- O sistema deve exibir automaticamente o nome da conta

**Exceções dos Critérios de Aceite:**
- [CA-5] Caso o usuário informe uma conta inexistente...
- [CA-8] Caso o valor informado seja inferior ao mínimo...
```

✅ **Como deve ficar após correção:**
```markdown
**Critérios de Aceite:**
- CA-1. A data do lançamento é obrigatória, deve estar no formato DD/MM/AAAA
- CA-2. O usuário deve informar manualmente os códigos das contas
- CA-3. O sistema deve exibir automaticamente o nome da conta

**Exceções dos Critérios de Aceite:**
- EX- 5. [CA-5] Caso o usuário informe uma conta inexistente...
- EX- 8. [CA-8] Caso o valor informado seja inferior ao mínimo...
```

**Regras de restauração:**
- Critérios: prefixo `CA-N.` (N sequencial a partir de 1, com ponto final)
- Exceções: prefixo `EX- N.` (N igual ao número do CA referenciado, com espaço entre `EX-` e o número)
- A numeração das exceções **não é sequencial** — segue o número do CA a que se refere

### Checklist Pós-Exportação

1. [ ] Revisar **todos os títulos** e reorganizar em hierarquia lógica
2. [ ] Adicionar **linhas em branco** entre parágrafos
3. [ ] Converter todos os **links em markdown**
4. [ ] Reformatar **tabelas** com pipes `|`
5. [ ] Reaplicar **negrito** em termos importantes
6. [ ] Verificar **indentação de listas**
7. [ ] Remover **caracteres estranhos** ou símbolos do Drive
8. [ ] Testar todas as **URLs/links**
9. [ ] Reinserir prefixos **`CA-N.`** em todos os critérios de aceite
10. [ ] Reinserir prefixos **`EX- N.`** em todas as exceções, com N igual ao CA referenciado

---

## Quando Usar Esta Skill

- Criando novos documentos Markdown
- Exportando/revisionando docs do Google Drive
- Revisando e padronizando documentação existente
- Orientando equipe sobre padrões de documentação
- Garantindo **consistência visual** entre documentos
- Melhorando **legibilidade** de documentação técnica

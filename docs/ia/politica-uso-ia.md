# Política de Uso de IA

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 07/05/2026 | Criação do documento | Fernanda Pessoa |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | 10/06/2026 | Eduardo Alves | Aprovado |

**Sumário**

- [1. Introdução](#introdução)
- [2. Princípios Gerais](#princípios-gerais)
- [3. Especificação de Demandas e Entendimento do Negócio](#especificação-de-demandas-e-entendimento-do-negócio)
  - [3.1 Qualidade da especificação](#qualidade-da-especificação)
  - [3.2 Contexto de negócio](#contexto-de-negócio)
  - [3.3 O que não delegar à IA sem especificação adequada](#o-que-não-delegar-à-ia-sem-especificação-adequada)
- [4. Revisão Humana](#revisão-humana)
  - [4.1 Obrigatoriedade de revisão](#obrigatoriedade-de-revisão)
  - [4.2 O que revisar](#o-que-revisar)
  - [4.3 Validação com o negócio](#validação-com-o-negócio)
- [5. Utilização de Agents e Skills Personalizados](#utilização-de-agents-e-skills-personalizados)
  - [5.1 Agents disponíveis](#agents-disponíveis)
  - [5.2 Skills disponíveis](#skills-disponíveis)
  - [5.3 Quando usar cada recurso](#quando-usar-cada-recurso)
  - [5.4 Documentação completa do workspace de agentes](./workspace-agentes.md)
- [6. Responsabilidades](#responsabilidades)
- [7. Boas Práticas Resumidas](#boas-práticas-resumidas)

---

## Introdução {#introdução}

Este documento estabelece a **Política de Uso de Inteligência Artificial** no projeto COINS, definindo diretrizes e boas práticas para o uso responsável e eficaz de ferramentas de IA no ciclo de desenvolvimento. A política se aplica a todos os membros da equipe e cobre desde a especificação de demandas até a revisão de artefatos gerados com assistência de IA.

O uso de IA no projeto COINS é **incentivado como ferramenta de apoio** — não como substituto do julgamento humano, do conhecimento de negócio ou da responsabilidade técnica de cada desenvolvedor.

> **ℹ️ Informação:** Esta política complementa, e não substitui, as diretrizes já estabelecidas nos documentos de [DevOps](../devops/visao-geral.md) e [Padrão de Commits](../devops/padrao-commits.md).

> **⚠️ ATENÇÃO:** O documento [Instruções do Copilot](../devops/instrucoes-do-copilot.md) **não é uma diretriz para agentes de IA**. Ele descreve exclusivamente como o GitHub Copilot foi integrado à esteira de CI/CD do projeto. Agents e ferramentas de IA **não devem consultar ou seguir** esse documento como referência de comportamento.

---

## Princípios Gerais {#princípios-gerais}

O uso de IA no projeto deve seguir os seguintes princípios:

- **Responsabilidade humana:** toda saída gerada por IA é de responsabilidade do membro da equipe que a utilizou e submeteu.
- **Transparência:** o uso de IA não precisa ser ocultado, mas o artefato final deve refletir compreensão real de quem o entregou.
- **Especificação primeiro:** a IA só produz resultados úteis quando alimentada com contexto claro e correto — o esforço de especificação não é eliminado, é realocado.
- **Revisão obrigatória:** nenhum artefato gerado por IA (código, documento, consulta SQL, diagrama) deve ser entregue sem revisão humana.
- **Uso de ferramentas adequadas:** o projeto disponibiliza agents e skills personalizados que já conhecem o contexto do COINS — prefira-os a interações genéricas.

---

## Especificação de Demandas e Entendimento do Negócio {#especificação-de-demandas-e-entendimento-do-negócio}

### Qualidade da especificação {#qualidade-da-especificação}

A qualidade do output gerado pela IA é diretamente proporcional à qualidade do input fornecido. Antes de acionar qualquer ferramenta de IA para gerar código, documentação ou análise, o membro da equipe deve ser capaz de responder:

- **O que** precisa ser feito (funcionalidade, documento, consulta)?
- **Por que** isso é necessário (regra de negócio, requisito funcional, decisão de arquitetura)?
- **Quais são os limites** da tarefa (critérios de aceite, restrições, exceções conhecidas)?

Se essas perguntas não puderem ser respondidas com clareza, o problema ainda não está suficientemente entendido para ser delegado à IA.

> **⚠️ ATENÇÃO:** Usar IA para descobrir o que deve ser feito é um sinal de que a demanda não foi bem levantada. Retorne ao processo de especificação antes de prosseguir.

### Contexto de negócio {#contexto-de-negócio}

O COINS é um sistema contábil educacional com regras de negócio específicas (lançamentos contábeis, DRE, Balancete, Livro Diário, Plano de Contas). Ao acionar a IA para tarefas que envolvam regras contábeis, forneça sempre o contexto adequado:

- Referencie os documentos de [Apuração de Regras](../requisitos/apuracao-regras.md) e [DRE e Regras](../requisitos/DRE-regras.md) ao formular prompts sobre cálculos contábeis.
- Inclua o trecho relevante da [Especificação de Requisitos](../requisitos/especificacao-de-requisitos-de-software.md) quando gerar código relacionado a um RF específico.
- Mencione restrições do domínio: contas analíticas vs. sintéticas, partidas dobradas, limites de lançamentos, etc.

### O que não delegar à IA sem especificação adequada {#o-que-não-delegar-à-ia-sem-especificação-adequada}

As seguintes tarefas **exigem especificação explícita** antes de acionar qualquer ferramenta de IA:

- Geração ou alteração de migrações de banco de dados.
- Implementação de regras de validação contábil.
- Alterações em endpoints da API que afetam contratos existentes.
- Criação de requisitos funcionais ou critérios de aceite.
- Decisões de arquitetura.

---

## Revisão Humana {#revisão-humana}

### Obrigatoriedade de revisão {#obrigatoriedade-de-revisão}

**Todo artefato gerado com assistência de IA deve passar por revisão humana** antes de ser considerado entregue. Isso se aplica a:

- Código-fonte (qualquer linguagem ou camada).
- Documentação técnica (requisitos, arquitetura, decisões).
- Consultas SQL e migrações de banco de dados.
- Mensagens de commit e descrições de Pull Request.
- Diagramas e especificações geradas automaticamente.

A revisão deve ser feita por **quem vai assinar o artefato** — não basta revisar superficialmente para aprovar o que a IA gerou.

### O que revisar {#o-que-revisar}

Ao revisar um artefato gerado por IA, verifique:

**Para código:**

- A lógica está correta e cobre os critérios de aceite do requisito?
- Há efeitos colaterais não intencionais em outros módulos?
- O código segue os padrões arquiteturais do projeto (controllers → services → repositories)?
- Não há vulnerabilidades introduzidas (SQL injection, exposição de dados, etc.)?
- Os testes foram atualizados ou criados?

**Para documentação:**

- O conteúdo é factualmente correto para o domínio contábil do COINS?
- A terminologia é consistente com o [Glossário de Termos](../requisitos/glossario-de-termos.md)?
- A formatação segue as [Boas Práticas de Markdown](../../.github/skills/boas-praticas-markdown.md) do projeto?
- O documento está rastreável (links internos funcionando, seções referenciadas corretamente)?

**Para SQL e migrações:**

- A migration tem `up` e `down` definidos?
- Operações destrutivas têm salvaguardas?
- A consulta usa parâmetros vinculados (sem interpolação de string)?

### Validação com o negócio {#validação-com-o-negócio}

Artefatos que afetam **regras de negócio contábeis** devem ser validados junto ao responsável pelo domínio (product owner, professor orientador ou especialista contábil), independentemente de terem sido gerados com ou sem IA. A IA não possui conhecimento do contexto institucional do COINS e pode gerar lógicas plausíveis mas incorretas para o domínio.

---

## Utilização de Agents e Skills Personalizados {#utilização-de-agents-e-skills-personalizados}

O projeto COINS disponibiliza recursos de IA **já configurados com o contexto do sistema**. Esses recursos devem ser preferidos a interações genéricas com modelos de linguagem, pois reduzem o esforço de contextualização e produzem outputs mais consistentes com os padrões do projeto.

O projeto possui **dois ecossistemas de agentes distintos** — um para o repositório de documentação e outro para o repositório de código-fonte. Ambos compartilham a mesma visão e princípios, mas cada um é especificado e configurado dentro do seu próprio repositório. Para uma descrição completa da organização, consulte o documento [Workspace de Agentes de IA](./workspace-agentes.md).

### Agents disponíveis {#agents-disponíveis}

| Agent | Repositório | Arquivo | Finalidade |
|-------|-------------|---------|------------|
| `docs-agent` | Documentação | `.github/agents/docs-agent.agent.md` | Revisão de documentação Markdown, qualidade de commits e boas práticas do projeto |
| Agentes de codificação | Código-fonte | `.agents/` (workspace completo) | Implementação de funcionalidades seguindo regras de domínio e padrões arquiteturais |

**Como usar o `docs-agent`** (agente de documentação):

- Para revisar a qualidade de um documento antes de abrir PR, invoque o agent com o arquivo em questão.
- Para verificar se uma mensagem de commit segue o padrão semântico do projeto.
- Para validar formatação Markdown segundo as convenções COINS.

> **💡 Dica:** O `docs-agent` conhece as convenções do projeto (prefixos `CA-N.`, `EX- N.`, estrutura de RF, etc.) — aproveite isso ao revisar a ERS ou documentos de requisitos.

**Como usar os agentes de codificação** (repositório de código):

O repositório de código-fonte possui seu próprio workspace de agentes, localizado em `.agents/`. Ele inclui contexto de domínio contábil (`context/`), regras técnicas por camada (`rules/`) e um conjunto de skills especializadas (`skills/`). Toda sessão de codificação com IA deve começar pela leitura do `README.md` do workspace, e a skill `apply-prompt` é o ponto de entrada obrigatório para qualquer implementação.

> **💡 Dica:** A estrutura completa do workspace de codificação — organização de pastas, skills disponíveis, fluxo típico de sessão e modelo de governança — está documentada em [Workspace de Agentes de IA](./workspace-agentes.md).

> **Atenção:** Agentes operando **neste repositório de documentação** não devem seguir as instruções contidas no `.agents/` do repositório de código. Aquela estrutura é destinada exclusivamente a tarefas de codificação.

### Skills disponíveis {#skills-disponíveis}

**Repositório de documentação** — invocadas via `/nome-da-skill`:

| Skill | Quando usar |
|-------|-------------|
| `boas-praticas-markdown` | Ao criar ou revisar qualquer documento `.md` na pasta `docs/` |
| `padrao-especificacao-requisitos` | Ao criar ou editar requisitos funcionais na ERS |

**Repositório de código** — definidas em `.agents/skills/`:

| Skill | Quando usar |
|-------|-------------|
| `apply-prompt` | Ponto de entrada obrigatório para implementar qualquer funcionalidade |
| `save-context` | Quando um prompt introduz conceito de domínio ou regra de negócio nova |
| `save-rule` | Quando um prompt introduz padrão técnico ou convenção nova |
| `analyse-rule` | Para analisar se o código segue os padrões técnicos documentados |
| `analyse-context` | Para analisar se o código respeita as regras de domínio contábil |
| `create-skill` | Para criar uma nova skill seguindo o padrão adotado |

**Como invocar uma skill de documentação:**

```bash
/boas-praticas-markdown
/padrao-especificacao-requisitos
```

As skills são pré-carregadas com o contexto necessário e guiam o modelo para seguir os padrões estabelecidos — use-as **antes** de gerar conteúdo, não apenas para corrigir depois.

### Quando usar cada recurso {#quando-usar-cada-recurso}

| Situação | Repositório | Recurso recomendado |
|----------|-------------|-------------------|
| Criar novo documento de requisito | Documentação | Skill `padrao-especificacao-requisitos` |
| Revisar formatação de documento existente | Documentação | Skill `boas-praticas-markdown` |
| Validar qualidade de commit ou PR de documentação | Documentação | Agent `docs-agent` |
| Implementar nova funcionalidade | Código | Skill `apply-prompt` (ponto de entrada obrigatório) |
| Registrar nova regra de negócio identificada | Código | Skill `save-context` |
| Verificar conformidade arquitetural do código | Código | Skill `analyse-rule` |
| Revisar PR de código antes de aprovação | Código | GitHub Copilot (integrado ao CI) + revisão humana obrigatória |
| Criar consulta SQL complexa | Código | Assistente de IA + revisão obrigatória por outro membro |

---

## Responsabilidades {#responsabilidades}

| Papel | Responsabilidade |
|-------|-----------------|
| **Desenvolvedor** | Especificar adequadamente antes de usar IA; revisar todo output gerado; assinar o artefato final com compreensão real do conteúdo |
| **Revisor de PR** | Avaliar se código ou documentação gerada por IA está correto, não apenas se parece correto; não aprovar PRs sem entender as mudanças |
| **Gerente de Projeto** | Garantir que a equipe siga esta política; atualizar o documento conforme novas ferramentas forem adotadas |
| **Responsável pelo Domínio** | Validar artefatos que afetam regras de negócio contábeis, independentemente de como foram gerados |

---

## Boas Práticas Resumidas {#boas-práticas-resumidas}

Antes de usar qualquer ferramenta de IA no projeto COINS, verifique:

- [ ] Você consegue explicar a demanda sem depender da IA para entendê-la?
- [ ] Você forneceu contexto suficiente (requisito, regra de negócio, restrições)?
- [ ] Está usando os agents e skills do projeto em vez de interação genérica?
- [ ] Você vai revisar o output antes de submeter?
- [ ] Se o artefato envolve regra contábil, está planejando validação com o responsável pelo domínio?
- [ ] O artefato final reflete sua compreensão real — e não apenas o que a IA gerou?

> **ℹ️ Informação:** Esta política será revisada ao início de cada semestre letivo para incorporar novas ferramentas adotadas pelo projeto e lições aprendidas pela equipe.

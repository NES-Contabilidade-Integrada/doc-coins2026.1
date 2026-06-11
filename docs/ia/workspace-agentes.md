# Workspace de Agentes de IA

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 08/06/2026 | Criação do documento — descreve a organização dos agentes de IA nos dois repositórios do projeto | Lohan Toledo Tosta |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | 10/06/2026 | Eduardo Alves | Aprovado |

**Sumário**

- [1. Introdução](#introdução)
- [2. Visão e Princípios Compartilhados](#visão-e-princípios-compartilhados)
- [3. Ecossistema de Documentação](#ecossistema-de-documentação)
  - [3.1 Agent: docs-agent](#agent-docs-agent)
  - [3.2 Skills do repositório de documentação](#skills-do-repositório-de-documentação)
- [4. Ecossistema de Codificação](#ecossistema-de-codificação)
  - [4.1 Estrutura do workspace `.agents/`](#estrutura-do-workspace-agents)
  - [4.2 Porta de entrada: README.md](#porta-de-entrada-readmemd)
  - [4.3 Contexto de domínio: `context/`](#contexto-de-domínio-context)
  - [4.4 Regras técnicas: `rules/`](#regras-técnicas-rules)
  - [4.5 Skills do repositório de código](#skills-do-repositório-de-código)
  - [4.6 Zona de trabalho: `input/`](#zona-de-trabalho-input)
- [5. Modelo de Governança](#modelo-de-governança)
- [6. Mapa de Decisão](#mapa-de-decisão)

---

## Introdução {#introdução}

O projeto COINS é dividido em dois repositórios distintos: o **repositório de documentação** (onde este documento reside) e o **repositório de código-fonte** (Electron/Vue/Express/SQLite). Cada repositório possui seu próprio ecossistema de agentes de IA, configurado para as tarefas que lhe são pertinentes.

```
┌──────────────────────────────────────────────────────────────────┐
│                        Projeto COINS                            │
│                                                                  │
│   ┌─────────────────────────┐   ┌─────────────────────────────┐  │
│   │  Repositório de docs    │   │  Repositório de código      │  │
│   │  doc-coins2026.1        │   │  coins (Electron/Vue/etc.)  │  │
│   │                         │   │                             │  │
│   │  Agentes de             │   │  Agentes de                 │  │
│   │  DOCUMENTAÇÃO           │   │  CODIFICAÇÃO                │  │
│   │  .github/agents/        │   │  .agents/                   │  │
│   └─────────────────────────┘   └─────────────────────────────┘  │
│                                                                  │
│          ╔══════════════════════════════════╗                    │
│          ║  Visão e princípios compartilhados ║                  │
│          ╚══════════════════════════════════╝                    │
└──────────────────────────────────────────────────────────────────┘
```

Os dois ecossistemas são **independentes na estrutura**, mas **compartilham a mesma visão e os mesmos princípios**. Esta separação é intencional: cada repositório especifica os agentes que atuam sobre ele, evitando que instruções de codificação contaminem o contexto de documentação e vice-versa.

> **Importante:** Os arquivos de configuração de agentes do repositório de código (`coins/.agents/`) **não devem ser seguidos por agentes operando neste repositório de documentação**. Eles são lidos aqui apenas para fins de documentação e entendimento.

---

## Visão e Princípios Compartilhados {#visão-e-princípios-compartilhados}

Ambos os ecossistemas operam sob os mesmos cinco princípios fundamentais:

| Princípio | Descrição |
| :--- | :--- |
| **Especificação primeiro** | Agentes não implementam o que não está especificado. A demanda precisa existir antes da ação. |
| **Supervisão humana obrigatória** | Todo artefato gerado por IA — código ou documento — exige revisão e aprovação humana antes de ser considerado entregue. |
| **Domínio é lei** | Regras do domínio contábil têm precedência sobre conveniência técnica ou estilística. |
| **Contexto persistente** | O workspace de cada repositório existe para suprir a falta de memória entre sessões dos agentes de IA. |
| **Glossário como fonte da verdade** | Termos de domínio têm definições canônicas documentadas. Agentes usam os termos definidos — nunca criam sinônimos. |

---

## Ecossistema de Documentação {#ecossistema-de-documentação}

O ecossistema de documentação vive no repositório `doc-coins2026.1`, na pasta `.github/agents/`, e é composto por um agent e duas skills.

### Agent: `docs-agent` {#agent-docs-agent}

| Atributo | Valor |
| :--- | :--- |
| **Arquivo** | `.github/agents/docs-agent.agent.md` |
| **Repositório** | `doc-coins2026.1` (documentação) |
| **Escopo de atuação** | Documentação Markdown, commits semânticos, boas práticas do projeto |

O `docs-agent` é um agente configurado com o contexto completo do projeto COINS voltado para tarefas de documentação. Ele conhece:

- As convenções de formatação Markdown compatíveis com MkDocs.
- O padrão de commits semânticos do projeto (`type(scope): descrição`).
- A estrutura esperada de documentos (histórico de versões, sumário com âncoras, seções obrigatórias).
- Os prefixos e nomenclaturas específicos dos documentos do COINS (ex: `CA-N.`, `EX- N.` na ERS, `RF`, `RNF`).
- As boas práticas de rastreabilidade (links internos, referências entre documentos).

**Quando usar o `docs-agent`:**

- Ao revisar a qualidade de um documento antes de abrir um Pull Request.
- Para verificar se uma mensagem de commit segue o padrão semântico do projeto.
- Para validar formatação e estrutura Markdown segundo as convenções COINS.
- Ao criar um documento novo e querer validar se segue o template esperado.

### Skills do repositório de documentação {#skills-do-repositório-de-documentação}

As skills do ecossistema de documentação são invocadas diretamente no Claude Code via `/nome-da-skill`.

| Skill | Invocação | Quando usar |
| :--- | :---: | :--- |
| `boas-praticas-markdown` | `/boas-praticas-markdown` | Ao criar ou revisar qualquer documento `.md` na pasta `docs/` |
| `padrao-especificacao-requisitos` | `/padrao-especificacao-requisitos` | Ao criar ou editar requisitos funcionais na ERS |

> **Dica:** Use as skills **antes** de gerar conteúdo, não apenas para corrigir depois. Elas são pré-carregadas com o contexto necessário e guiam o modelo para seguir os padrões estabelecidos.

---

## Ecossistema de Codificação {#ecossistema-de-codificação}

O ecossistema de codificação vive no repositório de código-fonte, na pasta `.agents/`. Ele é substancialmente mais complexo, pois precisa carregar contexto de domínio contábil, padrões técnicos por camada e um conjunto de skills especializadas.

### Estrutura do workspace `.agents/` {#estrutura-do-workspace-agents}

```
.agents/
├── README.md                        ← porta de entrada cognitiva (ler primeiro)
├── context/                         ← domínio contábil e regras de negócio
│   ├── accounting-domain.md         ← modelo mental do domínio contábil
│   └── exceptions/
│       └── project-exceptions.md   ← violações de padrão registradas com justificativa
├── rules/                           ← padrões técnicos por camada
│   ├── backend.md
│   ├── frontend.md
│   ├── database.md
│   └── testing.md
├── skills/                          ← skills de agentes disponíveis no projeto
│   ├── README.md                    ← índice e tabela de quando usar cada skill
│   ├── apply-prompt.md
│   ├── save-context.md
│   ├── save-rule.md
│   ├── create-skill.md
│   ├── analyse-rule.md
│   └── analyse-context.md
└── input/                           ← zona de trabalho temporária para análise
    ├── arquitetura/
    ├── banco-de-dados/
    └── ai-agent/
```

O workspace funciona como a **memória operacional e arquitetural do projeto** no repositório de código. Como agentes de IA não têm memória entre conversas, o `.agents/` fornece a fonte de verdade que pode ser lida no início de qualquer sessão para restaurar o contexto necessário.

### Porta de entrada: `README.md` {#porta-de-entrada-readmemd}

O `README.md` é o primeiro arquivo que qualquer agente de codificação deve ler. Ele contém, em formato conciso:

- Descrição do que é o COINS e sua arquitetura
- Stack tecnológico resumido (Electron, Vue 3, Express, SQLite3/Knex)
- Estrutura de camadas do backend (`main/`) e frontend (`renderer/`)
- Modelo de dados resumido (tabelas principais e restrições críticas)
- Módulos funcionais (EP01–EP04)
- Conceitos contábeis obrigatórios (partidas dobradas, tipos de conta, etc.)
- Convenções de código e commit
- Regras de comportamento do agente
- O que **nunca** fazer sem especificação explícita

### Contexto de domínio: `context/` {#contexto-de-domínio-context}

| Arquivo | Conteúdo |
| :--- | :--- |
| `accounting-domain.md` | Referência completa do modelo mental contábil: partidas dobradas, tipos de conta, hierarquia do Plano de Contas, lançamentos, apuração, DRE, Balanço Patrimonial, glossário obrigatório |
| `exceptions/project-exceptions.md` | Registro de decisões que violam intencionalmente padrões documentados, cada uma com justificativa e ciência humana explícita |

O `accounting-domain.md` é lido obrigatoriamente antes de qualquer tarefa que envolva regras de negócio contábeis. O arquivo de exceções é o único lugar onde violações de padrão podem residir — nenhum agente adiciona exceções sem aprovação humana.

### Regras técnicas: `rules/` {#regras-técnicas-rules}

| Arquivo | O que documenta |
| :--- | :--- |
| `backend.md` | 8 camadas do processo `main`, fluxo obrigatório `Controller → Service → Repository → Database`, convenções de código, regras de migrations e seeds, padrões de co-localização e testabilidade |
| `frontend.md` | 11 diretórios do processo `renderer`, distinção `schemas/` vs `types/`, comunicação com backend apenas via Services, regras de exibição por módulo (Balanço, DRE, Apuração) |
| `database.md` | Schema completo das 9 tabelas com colunas/tipos/restrições, valores seed, regras de imutabilidade de migrations, controle de idempotência |
| `testing.md` | Pirâmide de testes (5 tipos), ferramentas (Vitest unitários, Playwright E2E), estratégia de execução por branch, padrões de escrita e isolamento |

### Skills do repositório de código {#skills-do-repositório-de-código}

As skills são **protocolos de trabalho reutilizáveis** — definem como um agente deve executar um tipo específico de tarefa, com sequência de passos verificável e critério de encerramento. Quando uma situação se encaixar em uma skill, a skill deve ser usada; o agente não reinventa o fluxo.

| Skill | Arquivo | Quando usar |
| :--- | :---: | :--- |
| `apply-prompt` | `skills/apply-prompt.md` | Recebeu um prompt para implementar algo — é o **ponto de entrada obrigatório** para qualquer tarefa de código |
| `save-context` | `skills/save-context.md` | O prompt introduz conceito de domínio ou regra de negócio nova que precisa ser registrada |
| `save-rule` | `skills/save-rule.md` | O prompt introduz padrão técnico ou convenção nova que precisa ser registrada |
| `create-skill` | `skills/create-skill.md` | Precisa criar uma nova skill seguindo o padrão adotado |
| `analyse-rule` | `skills/analyse-rule.md` | Precisa analisar padrões técnicos (arquitetura, camadas, convenções) — gera `<escopo>-refac.md` |
| `analyse-context` | `skills/analyse-context.md` | Precisa analisar requisitos de domínio (regras de negócio, fórmulas, fluxos) — gera `<escopo>-context-refac.md` |

**Fluxo típico de uma sessão de codificação:**

```
1. Ler README.md          ← sempre primeiro
2. Ler rules/ relevantes  ← para o escopo da tarefa
3. Ler context/ se necessário ← para domínio contábil

       tarefa de código?
       /              \
     sim               não (análise)
      │                     │
 apply-prompt         analyse-rule ou
      │               analyse-context
 introduz algo novo?
 /           \
sim           não
 │              │
save-context   implementar
save-rule
 │
 └─► implementar
```

**Relações entre skills:**

- `apply-prompt` aciona `save-context` (quando há domínio novo) e `save-rule` (quando há padrão técnico novo)
- `apply-prompt` registra em `project-exceptions.md` quando há violação de padrão aprovada pelo usuário
- `analyse-rule` atualiza `rules/<escopo>.md` com padrões novos encontrados
- `analyse-context` atualiza `context/<escopo>.md` com contexto novo encontrado
- Todas as skills que **escrevem arquivos** exigem confirmação humana antes da escrita

### Zona de trabalho: `input/` {#zona-de-trabalho-input}

O diretório `input/` é uma zona de trabalho temporária — recebe documentos externos trazidos para análise pelo agente durante uma sessão. Não contém regras ou contexto vivo: é apenas um espaço para comparação e análise. Arquivos aqui não são fonte de verdade.

---

## Modelo de Governança {#modelo-de-governança}

Ambos os ecossistemas compartilham as mesmas fronteiras de autonomia:

### O que agentes podem fazer autonomamente

- Ler qualquer arquivo do workspace para obter contexto.
- Aplicar skills para criar artefatos de análise.
- Sugerir adições à documentação de regras ou contexto via skills correspondentes.
- Executar tarefas que seguem os padrões documentados.

### O que exige aprovação humana antes de executar

| Ação | Ecossistema | Motivo |
| :--- | :---: | :--- |
| Criar ou alterar migrations de banco | Codificação | Impacto irreversível no schema |
| Modificar regras de validação contábil | Codificação | Risco de inconsistência financeira |
| Alterar contratos de API | Codificação | Quebra de compatibilidade frontend/backend |
| Registrar exceções em `project-exceptions.md` | Codificação | Sempre precedida de ciência explícita |
| Criar requisitos funcionais | Ambos | Responsabilidade exclusiva do time humano |
| Tomar decisões de arquitetura | Ambos | Devem ser comunicadas e registradas |
| Entregar qualquer artefato gerado por IA | Ambos | Revisão humana obrigatória antes de merge/PR |

---

## Mapa de Decisão {#mapa-de-decisão}

| Situação | Repositório | Recurso recomendado |
| :--- | :---: | :--- |
| Criar novo documento de requisito | Documentação | Skill `padrao-especificacao-requisitos` |
| Revisar formatação de documento existente | Documentação | Skill `boas-praticas-markdown` |
| Validar qualidade de commit ou PR de documentação | Documentação | Agent `docs-agent` |
| Implementar nova funcionalidade no código | Código | Skill `apply-prompt` (ponto de entrada obrigatório) |
| Registrar nova regra de negócio contábil descoberta | Código | Skill `save-context` |
| Registrar novo padrão técnico descoberto | Código | Skill `save-rule` |
| Verificar se código segue padrões documentados | Código | Skill `analyse-rule` |
| Verificar se código respeita regras de domínio | Código | Skill `analyse-context` |
| Criar nova skill para o projeto de código | Código | Skill `create-skill` |
| Gerar código com IA (sem skill específica) | Código | Claude Code + contexto do PR + revisão obrigatória |
| Revisar PR de código antes de aprovação | Código | GitHub Copilot (CI) + revisão humana obrigatória |

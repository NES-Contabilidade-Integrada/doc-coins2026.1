# Relatório de Encerramento de Projeto

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 01/06/2026 | Versão inicial do documento | Fernanda Pessoa |
| 1.1 | 06/06/2026 | Preenchimento da seção 3.2 com comparativo planejado vs. executado por sprint | Fernanda Pessoa |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.1 | 10/06/2026 | Eduardo Alves | Aprovado |
| 1.1 | 10/06/2026 | Elise Lissa | Aprovado |

---

## 1. Configuração do Produto Entregue

### Módulos da Aplicação

| Módulo | Descrição | Semestre |
| ------ | --------- | :------: |
| **Plano de Contas** | Consulta ao plano de contas padrão com estrutura hierárquica de contas sintéticas e analíticas. | 2025/2 |
| **Livro Diário** | Gerenciamento completo de lançamentos contábeis — criação, edição, exclusão e listagem cronológica. Inclui a opção de limpar todos os dados da empresa. | 2025/2 |
| **Livro Razão** | Agrupamento dos lançamentos por conta, permitindo acompanhar a movimentação individual de cada conta ao longo do período. | 2025/2 |
| **Balancete de Verificação** | Confronto dos saldos devedores e credores de todas as contas com filtros por período, exibição do balancete completo e resumo consolidado dos totais. | 2025/2 |
| **Apuração do Resultado do Exercício** | Encerramento das contas de receitas e despesas com prévia completa antes da execução. Inclui histórico de apurações e possibilidade de desfazer a última apuração. | 2026/1 |
| **Demonstração do Resultado do Exercício (DRE)** | Relatório estruturado com Receita Bruta, Deduções, Receita Líquida, Lucro Bruto, Despesas Operacionais, LAJIR, Resultado Financeiro e Lucro Líquido. Permite filtrar por período e exportar o relatório. | 2026/1 |
| **Balanço Patrimonial** | Demonstrativo da posição financeira com Ativo, Passivo e Patrimônio Líquido agrupados hierarquicamente. Exibe resumo, conferência de equilíbrio e permite exportar o relatório. | 2026/1 |

### Demais Artefatos

| Artefato | Tipo |
| -------- | ---- |
| Protótipos de Interface (alta fidelidade) | Design — Figma |
| Esteira de CI com testes automatizados | DevOps — GitHub Actions |
| Esteira de CI gerando o executável instalável (ícone único, sem necessidade de extração de zip) | DevOps — GitHub Actions |
| Documentação do Projeto | Documentação — MkDocs |
| Manual de Uso do Sistema | Documentação — MkDocs |
| Teste de Usabilidade (planejamento, execução e relatório) | IHC — MkDocs |
| Fluxograma da Jornada do Usuário | Modelagem |
| Vídeo de Apresentação do Sistema | Apresentação |
| Repositório GitHub (frontend/backend) | Código-fonte |

### 1.1. Melhorias e Correções Estruturais

Além das novas funcionalidades, em 2026/1 foram realizadas melhorias estruturais e correções de bugs identificados no semestre anterior:

| Melhoria | Descrição |
| -------- | --------- |
| Executável como ícone único | O instalador passou a gerar um único arquivo executável com ícone próprio, eliminando a necessidade de extração de zip. |
| Testes automatizados E2E | Implementação de testes end-to-end com Playwright cobrindo as funcionalidades críticas do sistema. |
| Compatibilidade com versões anteriores | Correção de incompatibilidade de banco de dados que impedia o sistema de funcionar com dados gerados por versões anteriores. |
| Correções de bugs | Bugs identificados em 2025/2 foram levantados e corrigidos na Sprint 0 de 2026/1. |

### 1.2. Preparação do Ambiente de Produção

O COIN'S é distribuído como um **executável instalável** — o usuário final não precisa configurar nenhum ambiente. O instalador está disponível na página de [Releases do repositório](https://github.com/NES-Contabilidade-Integrada/coins2026.1/releases/latest).

Para quem precisa **gerar o executável**, o processo completo está documentado em: [Geração do Executável](https://nes-contabilidade-integrada.github.io/doc-coins2026.1/devops/geracao-executavel/)

Para **configurar o ambiente de desenvolvimento** — instalação de dependências, execução em modo desenvolvimento e geração do build — o passo a passo está no README do repositório de código:

[https://github.com/NES-Contabilidade-Integrada/coins2026.1](https://github.com/NES-Contabilidade-Integrada/coins2026.1)

---

## 2. Análise de Escopo de Produto

A tabela a seguir apresenta todos os itens planejados no escopo final do projeto e seu status.

| Item de escopo | Status | Categoria do Escopo |
| -------------- | :----: | :-----------------: |
| Apuração do Resultado do Exercício | Implementado | Funcionalidades de Consolidação |
| Demonstração do Resultado do Exercício (DRE) | Implementado | Funcionalidades de Consolidação |
| Balanço Patrimonial | Implementado | Funcionalidades de Consolidação |
| Exportação de Relatórios Contábeis | Implementado | Funcionalidades de Consolidação |

_Tabela 1 - Status de implementação dos itens do escopo._

O MVP do projeto, junto às funcionalidades planejadas, foram definidos no Plano do Projeto.  
Link do Plano do Projeto: [https://nes-contabilidade-integrada.github.io/doc-coins2026.1/gerencia-projeto/plano-do-projeto/](https://nes-contabilidade-integrada.github.io/doc-coins2026.1/gerencia-projeto/plano-do-projeto/)

---

## 3. Comparação entre Plano e Execução

Nesta seção é feita uma análise comparativa entre o planejamento original e a execução real do projeto. A avaliação considera três métricas principais: escopo, prazo e custo/esforço.

| Métrica | Resultado |
| ------- | :-------: |
| Percentual de escopo implementado | `<valor>` |
| Percentual de entregas planejadas por Sprint | `<valor>` |

_Tabela 2 - Comparação entre planejado e real._

### 3.1. Percentual de Escopo Implementado

Essa métrica compara o total de funcionalidades planejadas no Plano do Projeto com o total de funcionalidades efetivamente implementadas ao final do semestre.

`<Descrever o resultado e os fatores que influenciaram positiva ou negativamente o cumprimento do escopo.>`

### 3.2. Percentual de Entregas Planejadas por Sprint

Essa métrica avalia a aderência do time ao planejamento estabelecido para cada Sprint, considerando o que estava previsto versus o que foi efetivamente entregue dentro do ciclo.

| Sprint | Planejado | Executado |
| ------ | --------- | --------- |
| Sprint 0 | Descoberta e levantamento de requisitos | Descoberta, levantamento de requisitos, correção de bugs e melhorias estruturais |
| Sprint 1 | Correção de bugs e melhorias estruturais | Apuração do Resultado do Exercício |
| Sprint 2 | Apuração do Resultado do Exercício | Demonstração do Resultado do Exercício (DRE) + Exportação de Relatórios (DRE) |
| Sprint 3 | Demonstração do Resultado do Exercício (DRE) | Balanço Patrimonial + Exportação de Relatórios (Balanço Patrimonial) |

_Tabela 3 - Comparativo entre entrega planejada e executada por sprint._

A principal variação ocorreu na Sprint 0: o time optou por absorver as correções de bugs e melhorias estruturais — originalmente previstas para a Sprint 1 — ainda naquele ciclo, antecipando a estabilização da base de código. Essa decisão deslocou todas as entregas subsequentes em uma sprint: a Apuração passou para a Sprint 1, a DRE (com exportação) para a Sprint 2, e o Balanço Patrimonial (com exportação) foi entregue na Sprint 3. O escopo total do semestre foi cumprido integralmente, sem supressão de funcionalidades.

A planilha detalhada com o comparativo planejado vs. entregue está disponível no board do projeto: [GitHub Projects](https://github.com/orgs/NES-Contabilidade-Integrada/projects/9/views/1)

---

## 4. Parecer de Encerramento

Diante do exposto nas seções anteriores do presente relatório, o projeto atual foi considerado finalizado, tendo o produto entregue sido considerado **aceito** pelo(a) patrocinador(a) do projeto.

O feedback final e oficial pode ser consultado no seguinte link: [Avaliação Formal dos Proponentes](https://drive.google.com/drive/folders/1sgNv1QG4VcDq36tNcK7JW_XTM-UiIJDt?usp=drive_link)

---

## 5. Outras Observações

### 5.1. Recomendações para Equipes Futuras

#### 5.1.1. Aderir à Priorização Definida no Plano do Projeto

O Plano do Projeto apresenta a sequência planejada de funcionalidades que devem compor a evolução natural do sistema. Recomenda-se que equipes futuras utilizem esse material como referência primária para continuidade do desenvolvimento.

#### 5.1.2. Incorporar os Resultados do Teste de Usabilidade na Evolução do Sistema

O teste de usabilidade realizado fornece insights relevantes sobre clareza da interface, fluxo de navegação e percepção dos usuários. É recomendável que futuras decisões de interface e arquitetura considerem essas evidências para aprimorar a experiência de uso e apoiar melhor os objetivos pedagógicos do sistema.

Link para o relatório de usabilidade: [Relatório de Teste de Usabilidade](../ihc/relatorio-teste-usabilidade.md)

#### 5.1.3. Adotar uma Política de Revisão via Pull Requests e Abandonar o Histórico de Versão Individual

Durante este ciclo, a equipe migrou os documentos do Google Drive para o MkDocs no meio do projeto, em um período em que a revisão dos artefatos era feita de forma direta, sem o uso de Pull Requests — uma vez que o volume de documentos a migrar inviabilizava a adoção imediata desse fluxo. Dado o volume elevado de documentos a migrar em curto espaço de tempo, optou-se por manter o histórico de versão e revisão em cada documento individualmente — prática herdada do Drive — para preservar a rastreabilidade formal enquanto a transição era concluída.

Com a migração completa, essa prática deixa de ser necessária. O Git já oferece controle de versão completo e auditável por natureza: cada commit registra o que mudou, quem alterou e quando, e os Pull Requests adicionam uma camada de revisão estruturada antes que qualquer alteração seja incorporada ao repositório. Manter tabelas de histórico nos próprios documentos, nesse contexto, gera redundância e aumenta o custo de manutenção sem agregar rastreabilidade real.

Recomenda-se, portanto, que a equipe futura:

- Estabeleça uma política clara de revisão via Pull Requests, definindo critérios de aprovação, responsáveis por revisar e fluxo de merge;
- Remova as tabelas de histórico de versão e revisão dos documentos individuais no MkDocs, delegando integralmente esse controle ao Git.

#### 5.1.4. Utilizar os Agents e Skills Personalizados do Projeto

O projeto COINS possui dois ecossistemas de agentes de IA distintos, um por repositório, que devem ser priorizados em relação a interações genéricas com modelos de linguagem.

**Repositório de documentação (`doc-coins2026.1`):** os agents e skills estão em `.github/agents/` e `.github/skills/`. Eles encapsulam convenções específicas do projeto — padrão de especificação de requisitos, boas práticas de Markdown, estrutura de commits semânticos — e devem ser usados sempre que a equipe for criar ou revisar documentação.

**Repositório de código-fonte (`coins`):** o workspace de agentes vive em `.agents/` e é substancialmente mais complexo. Inclui contexto de domínio contábil (`context/`), regras técnicas por camada (`rules/`) e um conjunto de skills de codificação (`skills/`). Toda sessão de codificação com IA deve começar pela leitura do `README.md` do workspace, e a skill `apply-prompt` é o ponto de entrada obrigatório para qualquer implementação.

A documentação completa de ambos os ecossistemas, incluindo quando usar cada recurso, está em [Workspace de Agentes de IA](../ia/workspace-agentes.md).

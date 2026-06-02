# Relatório de Encerramento de Projeto

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 01/06/2026 | Versão inicial do documento | Fernanda Pessoa |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | | | Pendente |

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

O passo a passo completo para instalação do ambiente, incluindo dependências, variáveis e execução da versão final, encontra-se no link abaixo:

Guia de Instalação: `<inserir link>`

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
Link do Plano do Projeto: `<inserir link>`

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

`<Descrever o resultado e os principais fatores que causaram variações no decorrer das sprints.>`

A planilha detalhada com o comparativo planejado vs. entregue encontra-se disponível no link a seguir: `<inserir link>`.

---

## 4. Parecer de Encerramento

Diante do exposto nas seções anteriores do presente relatório, o projeto atual foi considerado finalizado, tendo o produto entregue sido considerado `<aceito ou rejeitado>` pelo(a) patrocinador(a) do projeto.

O feedback final e oficial pode ser consultado no seguinte link: `<inserir link>`

---

## 5. Outras Observações

### 5.1. Recomendações para Equipes Futuras

#### 5.1.1. Aderir à Priorização Definida no Plano do Projeto

O Plano do Projeto apresenta a sequência planejada de funcionalidades que devem compor a evolução natural do sistema. Recomenda-se que equipes futuras utilizem esse material como referência primária para continuidade do desenvolvimento.

#### 5.1.2. Incorporar os Resultados do Teste de Usabilidade na Evolução do Sistema

O teste de usabilidade realizado fornece insights relevantes sobre clareza da interface, fluxo de navegação e percepção dos usuários. É recomendável que futuras decisões de interface e arquitetura considerem essas evidências para aprimorar a experiência de uso e apoiar melhor os objetivos pedagógicos do sistema.

Link para o relatório de usabilidade: [Relatório de Teste de Usabilidade](../ihc/relatorio-teste-usabilidade.md)

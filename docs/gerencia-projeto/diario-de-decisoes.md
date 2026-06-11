# Diário de Decisões 2026.1

**Histórico de Edição**

| Versão | Descrição | Autor | Data |
| ----- | :---: | ----- | ----- |
| 1.0  | Nomenclatura Módulo | Elise Lissa Hasegawa | 10 de mar. de 2026 |
| 2.0 | Gerência de Configuração | Amanda Gois | 10 de mar. de 2026 |
| 3.0 | Método de Descoberta | Elise Lissa Hasegawa | 10 de mar. de 2026 |
| 4.0 | NotebookLLM, Planning Poker, Mkdocs, Executável automático, Migração do BD, Testes, Agents e Skills | Elise Lissa Hasegawa | 2 de jun. de 2026 |

**Histórico de Revisão**

| Versão | Autor | Data |
| :---: | ----- | ----- |
| 4.0 | Amanda Gois | 3 de jun. de 2026 |

**Sumário**

[Nomenclatura Módulo](#nomenclatura-módulo)

[Modelo de Descoberta](#modelo-de-descoberta)

[Gerência de Configuração](#gerência-de-configuração)

[NotebookLLM](#notebookllm)

[Planning Poker](#planning-poker)

[Migração da documentação para o mkdocs](#migração-da-documentação-para-o-mkdocs)

[Geração automática do executável via GitHub Actions](#geração-automática-do-executável-via-github-actions)

[Reestruturação e Migração do Banco de Dados (v2.0)](#reestruturação-e-migração-do-banco-de-dados-\(v2.0\))

[Testes de Qualidade \- Page Object Model (POM)](#testes-de-qualidade---page-object-model-\(pom\))

[Utilização de Agents e Skills](#utilização-de-agents-e-skills)

---

### Nomenclatura Módulo {#nomenclatura-módulo}

O documento de Encerramento de Projeto do ciclo anterior continha uma sugestão para reavaliar a terminologia utilizada para agrupamento de funcionalidades.

O termo **"épico"** foi empregado como forma de agrupar conjuntos de funcionalidades, porém, no contexto de metodologias ágeis, "épico" pressupõe a existência de histórias de usuário derivadas, o que não foi adotado nesta iniciativa. Isso gerava imprecisão conceitual na comunicação da equipe e na documentação do projeto.

A equipe adotou o termo **"Módulo"** para agrupamento de funcionalidades, em substituição ao termo "épico", garantindo maior precisão conceitual alinhada ao modelo de desenvolvimento utilizado.

Link: [Encerramento de Projeto](https://docs.google.com/document/d/11KY8ArqVIogDCkI6RawZNqcKAulH6ye9AHBqHHUv7ig/edit?usp=sharing)

### Modelo de Descoberta {#modelo-de-descoberta}

Após uma apresentação para o grupo de possíveis modelos para utilizar no projeto, e realizar um trade-off, foi decidido usar o método de Entrevistas para levantamento de requisitos. As outras técnicas e métodos considerados, suas vantagens e desvantagens podem ser visualizados no board da plataforma Miro.
A adoção do método de Entrevistas, traz como consequências: a coleta de requisitos mais direcionada e aprofundada com os stakeholders e maior clareza sobre as necessidades reais dos usuários e do proponente.

Link: [https://miro.com/app/board/uXjVG0HEXeY=/?share\_link\_id=578964212735](https://miro.com/app/board/uXjVG0HEXeY=/?share_link_id=578964212735)

### Gerência de Configuração {#gerência-de-configuração}

Após revisão dos documentos que constavam informações relevantes para Gerência de Configuração, foi anotado possíveis mudanças que o DevOps gostaria de fazer, para discussão da melhor decisão para a equipe, como Modelo de Ramificação, modelo de commits, versionamento e fluxo de trabalho no GitHub.  
Foi decidido continuar com o modelo já utilizado no projeto anteriormente, porém com algumas adições:

1. Versionamento da **release-candidate** e **main** bem definidas  
2. Fluxo com homologação do QA na branch **release-candidate**

### **NotebookLLM** {#notebookllm}

A equipe adotou a ferramenta Notebook LLM como parte da estratégia de gestão e consulta da documentação do projeto. Essa solução permite centralizar todos os documentos existentes em um único ambiente, dessa forma é possível realizar perguntas diretamente à documentação. Com isso, o acervo documental é transformado em uma base de conhecimento interativa, onde os membros da equipe podem obter respostas rápidas e contextualizadas sem precisar navegar manualmente por diversos arquivos. A utilização do Notebook LLM representa um avanço significativo, pois combina a praticidade de reunir informações em um só lugar com o poder dos modelos de linguagem, que conseguem interpretar e relacionar conteúdos de forma inteligente.  
Link: [https://notebooklm.google.com/notebook/6410b26e-a338-4221-bcfa-2c59349ddcf8](https://notebooklm.google.com/notebook/6410b26e-a338-4221-bcfa-2c59349ddcf8)

### **Planning Poker** {#planning-poker}

O Planning Poker foi utilizado como técnica de estimativa para definir o tempo de execução em dias de trabalho de cada tarefa registrada no board do GitHub. Essa prática traz maior precisão e colaboração ao processo de planejamento, já que cada membro da equipe contribui com sua percepção sobre o esforço necessário, reduzindo vieses individuais e promovendo consenso coletivo. A utilização do Planning Poker, por meio da plataforma [planningpokeronline.com](http://planningpokeronline.com), permite que as estimativas sejam realizadas de forma estruturada e transparente, garantindo que as tarefas sejam avaliadas de acordo com sua complexidade e impacto dentro do projeto. Além disso, essa decisão fortalece a integração entre o processo de desenvolvimento e a gestão de tarefas no GitHub, criando um fluxo contínuo entre planejamento, execução e acompanhamento. Com isso, é possível alinhar expectativas, melhorar a previsibilidade das entregas e aumentar a eficiência da equipe, mantendo a documentação das estimativas registrada diretamente no board para consulta futura e rastreabilidade.

### **Migração da documentação para o mkdocs** {#migração-da-documentação-para-o-mkdocs}

A equipe decidiu realizar a migração de todos os documentos e links para ambientes integrados do projeto para o mkdocs, uma ferramenta que oferece uma visualização mais clara, rápida e organizada da documentação. Essa mudança foi motivada pela necessidade de tornar o acesso às informações mais intuitivo e visual, o mkdocs gera páginas navegáveis e bem estruturadas, que facilitam tanto a consulta por membros da equipe quanto a manutenção contínua dos conteúdos.  
Por utilizar Markdown como linguagem base, o mkdocs tem vantagens como compatibilidade, garatindo maior interoperabilidade com diferentes plataformas e ferramentas. E considerando o avanço das tecnologias de agentes inteligentes, o uso de Markdown permite que sistemas de IA interpretem e processem a documentação com maior eficiência.  
Essa decisão fortalece a organização do projeto, garantindo que o conhecimento produzido seja acessível, sustentável e preparado para evoluir junto com as novas tecnologias que apoiam o desenvolvimento e a gestão de projetos.

Este novo registro para o **Diário de Decisões** formaliza a mudança estratégica na gestão do banco de dados do sistema COIN’S, motivada pela necessidade de resolver instabilidades técnicas e garantir a integridade dos dados contábeis entre diferentes ambientes de desenvolvimento.

### **Geração automática do executável via GitHub Actions** {#geração-automática-do-executável-via-github-actions}

Foi implementada a execução automática dos processos de integração e testes utilizando GitHub Actions, garantindo maior confiabilidade e agilidade no ciclo de desenvolvimento. Essa escolha permite que cada alteração enviada ao repositório seja validada de forma contínua, sem necessidade de intervenção manual, assegurando que o código esteja sempre em conformidade com os padrões de qualidade definidos. A automação via Actions possibilita configurar pipelines que englobam desde a compilação e geração de artefatos até a execução dos testes de unidade e de interface, integrando-se diretamente com a estratégia de modularização já estabelecida no projeto. Além disso, a utilização de workflows inteligentes permite aplicar a lógica de “affected”, executando apenas os testes relacionados às partes do sistema impactadas por mudanças recentes, o que reduz significativamente o tempo de execução e otimiza os recursos de processamento. Essa decisão fortalece a governança técnica do projeto, promovendo maior eficiência, rastreabilidade e confiança nos resultados, ao mesmo tempo em que prepara o ambiente para evoluções futuras de automação e integração contínua.

### **Reestruturação e Migração do Banco de Dados (v2.0)** {#reestruturação-e-migração-do-banco-de-dados-(v2.0)}

#### **1\. Contexto e Problema** {#1.-contexto-e-problema}

Após auditoria técnica no código e nos documentos arquiteturais, foram identificados *code smells* críticos nas migrations originais. O fluxo de atualização era não-determinístico e baseado em estados externos, o que impedia a reconstrução confiável do banco de dados a partir do zero e gerava riscos de inconsistência entre ambientes de desenvolvimento (como as branches `main` e `develop`). Além disso, a carga inicial de dados não possuía versionamento, executando-se repetidamente a cada inicialização da aplicação sem rastreabilidade.

#### **2\. Decisão Técnica: Estratégia de Baseline e Detecção de Estado** {#2.-decisão-técnica:-estratégia-de-baseline-e-detecção-de-estado}

Para sanar estas falhas, foi decidido adotar uma nova arquitetura de persistência baseada em três pilares:

* **Criação de uma Baseline (Migration 0):** Representa a estrutura atual e estável do banco, substituindo as migrations antigas que apresentavam comportamento condicional.  
* **Detecção Automática de Estado:** O sistema agora identifica se o banco de dados é **inexistente**, **legado** (versão anterior à baseline) ou **estável**.  
  * Bancos **legados** serão automaticamente apagados e reiniciados para garantir que todos os desenvolvedores e usuários utilizem o mesmo esquema.  
* **Versionamento de Carga Inicial (Data Migrations):** Implementação de controle de execução para inserções de dados, garantindo que a carga inicial e as atualizações de dataset ocorram de forma linear e segura.

#### **3\. Reconciliação do Esquema (Branch develop)** {#3.-reconciliação-do-esquema-(branch-develop)}

A migração consolidou o esquema de dados na versão 2.0, alinhando a documentação às implementações reais encontradas na branch `develop`. As principais mudanças implementadas incluem:

* **Padronização de Nomenclatura:** Tabelas e campos foram renomeados para o inglês para manter a consistência técnica (ex: `apuracoes` tornou-se `apuration` e `data_apuracao` tornou-se `apuration_date`).  
* **Expansão de Funcionalidades Contábeis:**  
  * Adoção de **8 tipos de contas padrão** (incluindo ARE, Lucros e Prejuízos Acumulados) via tabela `account_types`.  
  * Criação da tabela `actors` para distinguir lançamentos manuais de usuários de lançamentos automáticos do **Sistema de Apuração**.  
  * Suporte a **Resultados Nulos** na apuração (tipo 3\) e flexibilização da conta de destino como *nullable*.  
* **Infraestrutura para DRE:** Adição das tabelas `dre_groups` e `dre_group_account_roots` para permitir a classificação dinâmica de contas para a Demonstração do Resultado do Exercício.

#### **4\. Consequências e Próximos Passos** {#4.-consequências-e-próximos-passos}

* **Estabilidade:** A reconstrução do banco a partir do zero agora é determinística e linear.  
* **Integridade:** A camada de aplicação passa a reforçar obrigatoriedades que eram flexíveis no banco, como a descrição (`description`) de lançamentos contábeis.  
* **Governança:** Todas as novas alterações no esquema devem seguir obrigatoriamente o fluxo de migrations versionadas, sem intervenções manuais no arquivo de banco de dados SQLite.

### **Testes de Qualidade \- Page Object Model (POM)** {#testes-de-qualidade---page-object-model-(pom)}

A estratégia de Page Object Model (POM) foi utilizada para estruturar os testes de qualidade do projeto, alinhando-os à arquitetura já bem definida entre os módulos. Essa abordagem permite organizar os testes de interface de forma modular, garantindo maior clareza, reutilização de código e manutenção simplificada. Cada módulo do sistema passa a ter seus próprios objetos de página, refletindo diretamente a separação lógica já existente na arquitetura, o que facilita a evolução dos testes conforme novas funcionalidades são adicionadas ou modificadas. Além disso, a utilização do POM possibilita aplicar a estratégia de “affected”, que executa apenas os testes relacionados às partes do sistema impactadas por alterações recentes. Com isso, é possível reduzir significativamente o tempo de execução dos testes nas actions, sem comprometer a cobertura e a confiabilidade dos resultados. Essa decisão fortalece a qualidade contínua do projeto, assegurando que os testes acompanhem a evolução do sistema de forma eficiente, escalável e integrada às práticas modernas de desenvolvimento.

### **Utilização de Agents e Skills** {#utilização-de-agents-e-skills}

A equipe decidiu incorporar o uso de agents e skills como parte da estratégia de evolução da inteligência artificial aplicada ao projeto, com o objetivo de aumentar a qualidade e a eficiência na utilização da IA. Os agents permitem que tarefas complexas sejam divididas em unidades menores e mais especializadas, cada uma responsável por executar ações específicas de forma autônoma e coordenada. Já as skills funcionam como capacidades adicionais que podem ser carregadas e utilizadas conforme a necessidade, ampliando o repertório de soluções disponíveis e tornando o sistema mais adaptável.

Essa combinação possibilita que a IA seja utilizada de maneira mais inteligente e direcionada, trazendo ganhos significativos na análise de dados, na automação de processos e na interação com a documentação e artefatos do projeto. Além disso, a adoção dessa abordagem garante maior escalabilidade e flexibilidade, permitindo que o projeto acompanhe o avanço contínuo das tecnologias de IA e se beneficie de práticas modernas de desenvolvimento orientadas à qualidade.
# Especificação de Arquitetura de Software

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 11/11/2025 | Adicionando Primeira versão do documento  | Pedro Nicoletti Sotoma |
| 2.0 | 01/06/2026 | Atualização com base no working directory (branch develop): novos módulos de domínio (Apuração, DRE, Balanço Patrimonial), reorganização da pasta de testes E2E para `playwright/`, decomposição da camada de banco de dados, ajuste de CORS | Lohan Toledo Tosta |

**Histórico de Revisões** 

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | 25/11/2025 | Fernanda Pessoa | Aprovada |
| 2.0 | — | — | Pendente de revisão |

**Sumário**

[1\. Introdução	2](#introdução)

[2\. Escopo	2](#escopo)

[2.1. Restrições do sistema	2](#restrições-do-sistema)

[Framework e Plataforma	2](#framework-e-plataforma)

[Frontend	3](#frontend)

[Backend	3](#backend)

[Banco de Dados	3](#banco-de-dados)

[Padrão Arquitetural	3](#padrão-arquitetural)

[3\. Representação arquitetural	4](#representação-arquitetural)

[3.1. Nível 1 – Diagrama de Contexto	4](#nível-1-–-diagrama-de-contexto)

[3.2. Nível 2 – Diagrama de Container	4](#nível-2-–-diagrama-de-container)

[3.3. Nível 3 – Diagrama de Componentes	5](#nível-3-–-diagrama-de-componentes)

[3.4. Nível 4 – Código	5](#nível-4-–-código)

[3.5. Diagramas suplementares – Diagrama de Implantação	6](#diagramas-suplementares-–-diagrama-de-implantação)

[4\. Infraestrutura de CI/CD	7](#infraestrutura-de-cicd)

## Introdução 
Este documento tem como objetivo descrever a arquitetura do Sistema COIN'S, seguindo o modelo de visualização arquitetural de software C4<sup>1</sup>. 

O C4 é o padrão ideal para representar a arquitetura porque equilibra clareza, consistência e praticidade. Ele comunica o que importa em cada nível de detalhe, é simples de manter, se integra às ferramentas modernas de desenvolvimento e fortalece a governança técnica da organização.

Mesmo em um contexto de software desktop monolítico e offline, com escopo inicial pequeno, o uso do modelo C4 faz sentido por promover clareza estrutural desde o início do projeto, facilitando a evolução futura da aplicação — seja para modularização, integração online ou expansão arquitetural. Além disso, o C4 permite documentar decisões arquiteturais de forma leve e acessível, garantindo que o conhecimento do sistema não se perca com o tempo e possa ser facilmente comunicado a novos desenvolvedores ou stakeholders.

## Escopo 
Este documento auxilia os envolvidos no projeto a compreender os aspectos arquiteturais do sistema que são necessários para desenvolver uma solução que atenda as necessidades do proponente. Além de auxiliar equipes futuras no entendimento do projeto.

### Restrições do sistema 
As principais restrições e decisões arquiteturais do **Sistema COIN'S** são as seguintes:

### Framework e Plataforma
**Electron \+ Electron Forge**: A escolha do *Electron* foi feita para permitir o desenvolvimento de uma aplicação **desktop multiplataforma**, mantendo o mesmo código base em Windows, Linux e macOS.  
O *Electron Forge* foi adotado para facilitar o empacotamento, distribuição e atualização do aplicativo, garantindo consistência no ciclo de build e distribuição offline.

### Frontend: Vue 3 com TypeScript
Escolhido por sua **produtividade**, **reatividade nativa** e **integração simples com Electron**. O uso de TypeScript aumenta a confiabilidade do código e facilita a manutenção e refatoração futura.

### Backend: Express.js com TypeScript
Utilizado como camada de backend local dentro do mesmo processo do Electron, responsável por expor endpoints REST internos e centralizar a lógica de negócio.  
Essa escolha mantém a **separação lógica entre frontend e backend**, ainda que no mesmo container, o que facilita futura migração para um modelo cliente-servidor se o sistema vier a evoluir para ambiente online.

> **Nota (v2.0):** O middleware de CORS foi alterado para aceitar qualquer origem (`*`), sem restrição por ambiente. Essa decisão foi motivada pela necessidade de suportar os testes E2E com Playwright, que sobem a aplicação em modo headless e precisam fazer requisições ao servidor Express local independente do contexto de execução.

### Banco de Dados: SQLite3
O banco de dados local foi escolhido por ser **leve, embarcado e adequado ao uso offline**. Ele não requer servidor dedicado, reduzindo complexidade e facilitando a instalação.

* **Knex.js**: Biblioteca de query builder que provê **abstração de acesso ao banco**, portabilidade e migrações estruturadas, além de facilitar a manutenção do esquema de dados.

### Padrão Arquitetural
O sistema é formado por uma arquitetura monolítica modularizada em camadas. Essa decisão foi tomada considerando o contexto de um software offline desktop, visando a facilidade de integração entre banco/backend/frontend. O diretório `main` fica responsável por encapsular a lógica e as camadas do backend enquanto o diretório `renderer` fica responsável pelo frontend.

Para uma definição mais técnica da responsabilidade de cada camada, visualizar o documento de [Visão de Implementação](./visao-de-implementacao.md).

> **Arquivo editável disponível no repositório:** O arquivo `Diagrama_C4_COINS.drawio` está na raiz do repositório e pode ser aberto e editado diretamente no [draw.io](https://app.diagrams.net/) para atualizar qualquer diagrama C4.

## Representação arquitetural 
O modelo C4 considera as estruturas estáticas de um sistema de software em termos de containers (aplicativos, armazenamentos de dados, microservices, etc.), componentes e código. Também considera as pessoas que usam os sistemas de software que construímos.

### Nível 1 – Diagrama de Contexto 
O diagrama de contexto do sistema mostra o **Sistema COIN'S** e como ele se encaixa no mundo em termos das pessoas que o utilizam e dos outros sistemas de software com os quais ele interage.

**Ver diagrama:** [Diagrama C4 – Contexto](./diagramas-c4.md#diagrama-c4---contexto)

O diagrama evidencia:

* O **usuário principal**, que interage diretamente com o aplicativo desktop.  
* A ausência de dependências externas (sistema **offline**).  
* O escopo restrito ao ambiente local da máquina do usuário.

### Nível 2 – Diagrama de Container
O diagrama de container detalha a estrutura interna do sistema, evidenciando os **principais containers** que o compõem:

* **Frontend (Vue \+ Electron Renderer)**: responsável pela interface gráfica e interação com o usuário.  
* **Backend Local (Express \+ TypeScript)**: lida com as regras de negócio e comunicação com o banco de dados.  
* **Banco de Dados (SQLite3)**: armazena dados localmente.  
* **Camada de Acesso a Dados (Knex)**: abstrai as operações SQL e garante consistência.

**Ver diagrama:** [Diagrama C4 – Container](./diagramas-c4.md#diagrama-c4---container)

### Nível 3 – Diagrama de Componentes 
O diagrama de componentes amplia o container principal (aplicação desktop) e mostra os **componentes internos** que compõem a aplicação.

Entre os principais componentes:

* **Camada de UI (Vue Components)**: telas e componentes visuais.  
* **Camada de Serviços (Services Layer)**: coordena comunicação entre UI e backend.  
* **Camada de API Interna (Express Controllers)**: expõe endpoints locais.  
* **Camada de Persistência (Repositories e Models)**: implementa acesso ao banco via Knex.


> **Nota (v2.0 — Testes E2E):**
>
> A pasta de testes E2E foi renomeada de `e2e/` para `playwright/`, mantendo a mesma estrutura interna. A categoria `regression/` foi renomeada para `acceptance/`. Foram adicionados page objects para os novos módulos (`Apuracao.ts`, `Dre.ts`) e novos spec files de ponta a ponta (`apuracao-workflow.spec.ts`, `dre-workflow.spec.ts`).

**Ver diagrama:** [Diagrama C4 – Componentes](./diagramas-c4.md#diagrama-c4---componentes)

### Nível 4 – Código 
Neste nível, podem ser representados diagramas de classes ou entidades para os componentes mais importantes.

No caso do Sistema COIN'S, recomenda-se a elaboração de um Diagrama de Entidade-Relacionamento (DER) com base no schema do banco SQLite3, destacando tabelas, colunas e relacionamentos. 

**Ver diagrama:** [Diagrama ERD – Documentação do Modelo de Dados](../banco-de-dados/documentacao-modelo-dados.md#der-diagrama-entidade-relacionamento)

![Modelo físico relacional do banco de dados](../banco-de-dados/assets/Diagrama%20ERD.png)

### Diagramas suplementares – Diagrama de Implantação 
Por se tratar de um sistema monolítico offline, não é necessário um diagrama de implantação detalhado.  
O sistema é distribuído como um executável único via Electron Forge, contendo em si:

* A camada de frontend (Vue \+ Electron Renderer);  
* A camada de backend (Express embarcado);  
* O banco de dados SQLite3 (armazenado localmente no diretório da aplicação).

Toda a execução ocorre **no ambiente local do usuário**, sem dependência de servidores externos ou infraestrutura de rede.

> **Nota (v2.0):** No ambiente de CI, a aplicação é empacotada como um executável real antes da execução dos testes E2E. O Playwright inicia o binário gerado pelo Electron Forge e interage com ele via automação de interface gráfica. Isso garante que os testes validam o artefato de distribuição final, não apenas o ambiente de desenvolvimento.

## Infraestrutura de CI/CD

> **Seção adicionada na v2.0**

O projeto passou a contar com pipelines de integração e entrega contínua (CI/CD) hospedadas no **GitHub Actions**, divididas em quatro workflows:

| Workflow | Arquivo | Responsabilidade |
| :--- | :--- | :--- |
| CI (Unitários) | `ci.yml` | Executa os testes unitários do backend a cada push/PR |
| CI (E2E) | `ci-e2e.yml` | Compila a aplicação Electron e executa os testes Playwright |
| Build Windows | `build-windows.yml` | Gera o instalador `.exe` para distribuição |
| Release | `release.yml` | Publica a release no GitHub com o artefato gerado |

Essa infraestrutura introduz uma camada de controle de qualidade automatizada ao projeto. A pirâmide de testes do sistema é:

1. **Testes Unitários** (`main/tests/`) — validam lógica de negócio isolada, executados via Vitest.
2. **Testes de Integração E2E** (`playwright/specs/integration/`) — validam respostas da API REST do backend Express.
3. **Testes Funcionais E2E** (`playwright/specs/functional/`) — validam fluxos de UI por módulo via Playwright.
4. **Testes E2E ponta-a-ponta** (`playwright/specs/e2e/`) — validam fluxos contábeis completos (ex: criação de lançamento → apuração → DRE).
5. **Testes de Aceitação** (`playwright/specs/acceptance/`) — validam regras de negócio e integridade de dados (ex: validações do plano de contas, lançamentos).

[^1]: 
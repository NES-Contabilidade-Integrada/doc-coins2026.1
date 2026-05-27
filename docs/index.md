# COIN'S — Contabilidade Integrada

COIN'S é um aplicativo desktop educacional desenvolvido na UFMS pelo **Núcleo de Práticas de Engenharia de Software**, com início no segundo semestre de 2025.

O sistema foi criado para preencher uma lacuna no curso de Ciências Contábeis: os softwares contábeis profissionais só são introduzidos nos semestres avançados, deixando os alunos dos primeiros períodos sem contato prático com os processos fundamentais da profissão. O COIN'S simula um ambiente contábil real — do registro de lançamentos à geração de demonstrativos financeiros — em uma interface acessível e voltada ao aprendizado.

---

## Vídeo de apresentação

<div style="text-align:center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/FLl8JhWhBFk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

---

## Funcionalidades

| Módulo | Descrição |
|--------|-----------|
| **Plano de Contas** | Consulta ao plano de contas padrão com estrutura hierárquica de contas sintéticas e analíticas. |
| **Livro Diário** | Registro e consulta cronológica de todos os lançamentos contábeis realizados em uma empresa. |
| **Livro Razão** | Agrupamento dos lançamentos por conta, permitindo acompanhar a movimentação individual de cada conta ao longo do período. |
| **Balancete de Verificação** | Confronto dos saldos devedores e credores de todas as contas, verificando o equilíbrio contábil dos lançamentos. |
| **Apuração do Resultado do Exercício** | Encerramento das contas de receitas e despesas, apurando o lucro ou prejuízo do período. |
| **Demonstração do Resultado do Exercício** | Apresentação estruturada de receitas, deduções, despesas e o resultado líquido do período. |
| **Balanço Patrimonial** | Demonstrativo da posição financeira da empresa, evidenciando ativo, passivo e patrimônio líquido ao final do exercício. |

---

## Disciplinas abrangidas

O sistema abrange conteúdos de diversas disciplinas do curso de **Ciências Contábeis da ESAN/UFMS**:

<div class="grid cards" markdown>

- Contabilidade I
- Contabilidade II
- Contabilidade III
- Contabilidade de Custos
- Análise de Custos
- Contabilidade Societária I
- Contabilidade Societária II
- Contabilidade Aplicada ao Setor Público
- Contabilidade Tributária
- Contabilidade do Terceiro Setor e Sustentabilidade
- Contabilidade Tributária Empresarial
- Contabilidade Aplicada ao Agronegócio
- Contabilidade Avançada
- Auditoria Contábil
- Análise de Demonstrações Contábeis
- Laboratório de Prática Contábil I
- Laboratório de Prática Contábil II

</div>

---

## Stack

<div class="grid cards" markdown>

-   <img src="https://img.shields.io/badge/Electron-2B2E3A?style=for-the-badge&logo=electron&logoColor=9FEAF9" alt="Electron"/>

    Framework para criação de aplicativos desktop multiplataforma com tecnologias web.

-   <img src="https://img.shields.io/badge/Vue_3-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D" alt="Vue 3"/>

    Framework JavaScript progressivo para construção da interface do usuário.

-   <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript"/>

    Superset do JavaScript com tipagem estática, garantindo maior segurança e manutenibilidade do código.

-   <img src="https://img.shields.io/badge/Vuetify-1867C0?style=for-the-badge&logo=vuetify&logoColor=white" alt="Vuetify"/>

    Biblioteca de componentes de interface baseada no Material Design para Vue 3.

-   <img src="https://img.shields.io/badge/Express.js-404D59?style=for-the-badge&logo=express&logoColor=white" alt="Express.js"/>

    Framework minimalista para Node.js, utilizado na camada de API interna da aplicação.

-   <img src="https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite"/>

    Banco de dados relacional embarcado, sem necessidade de servidor externo.

-   <img src="https://img.shields.io/badge/Knex.js-E16426?style=for-the-badge&logo=knexdotjs&logoColor=white" alt="Knex.js"/>

    Query builder SQL para Node.js, facilitando migrações e consultas ao banco de dados.

</div>

---

## Download

As versões executáveis estão disponíveis na página de [Releases do repositório](https://github.com/NES-Contabilidade-Integrada/coins2026.1/releases) para quem possui acesso ao repositório.

---

## Artefatos por área

A documentação reúne os principais entregáveis do projeto, organizados por área de responsabilidade:

- **[Arquitetura](arquitetura/especificacao-arquitetural.md)**: visão de alto nível, especificação arquitetural, diagramas e decisões estruturais.
- **[Requisitos](requisitos/especificacao-de-requisitos-de-software.md)**: requisitos de produto e software, regras de negócio para apuração de DRE e Balanço Patrimonial.
- **[Banco de Dados](banco-de-dados/documentacao-modelo-dados.md)**: modelo de dados, dicionário e documentação do modelo lógico.
- **[IHC](ihc/identidade-visual.md)**: identidade visual, diretrizes de design e padrões de interface.
- **[Interface e Experiência](gerencia-projeto/plano-do-projeto.md#projeto-de-interface-e-interação)**: protótipos, visão de implementação e critérios de usabilidade.
- **[Qualidade e Testes](qualidade-testes/plano-de-testes.md)**: plano de testes, critérios de aceitação e estratégias de validação.
- **[Gerência de Projeto](gerencia-projeto/plano-do-projeto.md)**: planejamento, políticas de configuração, modelo de ramificação e relatórios de progresso.
- **[DevOps](devops/visao-geral.md)**: infraestrutura proposta, fluxo de trabalho e práticas de integração contínua.
- **[Decisões](decisoes/decisoes.md)**: registro de decisões técnicas e de projeto que sustentam a solução.

---

## Ambientes Compartilhados

<div class="centered-table" markdown>

| Ferramenta | Link |
|------------|------|
| 🎨 Figma | [Protótipo COIN'S](https://www.figma.com/design/Z3hfLoenhr73I3u5BRU5lP/COIN-S---Contabilidade-Integrada?node-id=40000778-20259&t=jaqeTyfCvmRHlX9C-1) |
| 📁 Google Drive | [Pasta do Projeto](https://drive.google.com/drive/folders/1dSzfMOYWT6Y_vLQtLixwUQxB1kRvvvQ1) |
| 📋 GitHub Projects | [Board do Projeto](https://github.com/orgs/NES-Contabilidade-Integrada/projects/9/views/1) |
| 🗺️ Miro | — |
| 📓 NotebookLM | — |

</div>

---

## Equipe

<div class="centered-table" markdown>

=== "2026/1"

    Este sistema foi desenvolvido pela seguinte equipe:

    | Nome | E-mail |
    |------|--------|
    | Amanda Gois de Balcaçar | amandagois@gmail.com |
    | Elise Lissa Hasegawa | eliselissa05@gmail.com |
    | Fernanda de Paula Pessoa | fernaandapessoa@outlook.com |
    | Lohan Toledo Tosta | lohan.ltt@gmail.com |
    | Vinicius Carneiro de Aguiar | viniciuscarneiro60@gmail.com |

    **Orientação:** Professora Vanessa Borges  
    **Proposto por:** Robert Armando Espejo e Jean Pleutim  
    **Técnico:** Loester Kiyoshi Teruya

=== "2025/2"

    Este sistema foi desenvolvido pela seguinte equipe:

    | Nome | E-mail |
    |------|--------|
    | Fernanda de Paula Pessoa | fernaandapessoa@outlook.com |
    | Gustavo Pinheiro Fujinohara | gustavoh.fujinoharah@gmail.com |
    | Jerfferson Jorge Felizardo Júnior | jerffersonjorgefj@gmail.com |
    | Pedro Nicoletti Sotoma | pedrosotoma@gmail.com |
    | Wagner Rodrigues Silva | engsoftwagner242@gmail.com |

    **Orientação:** Professora Maria Istela Cagnin Machado  
    **Proposto por:** Robert Armando Espejo e Jean Pleutim  
    **Técnico:** Lucas Borth

    [:material-download: Certificado de Registro do Software](assets/certificado-registro-software-2025-2.pdf)

</div>

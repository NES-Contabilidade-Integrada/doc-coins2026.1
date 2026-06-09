# Infraestrutura

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 09/06/2026 | Criação do documento com Pipeline CI, E2E e Release Automático | Amanda Gois |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |
| 1.0 | 09/06/2026 | Vinicius Carneiro | Aprovado |

---

=== "Pipeline CI"

    A pipeline de CI possui os seguintes objetivos:

    - Executar **testes automatizados** do backend.
    - Verificar **cobertura mínima de testes**.
    - Fornecer **feedback automático em Pull Requests**.
    - Impedir integração de código que **não atenda aos critérios de qualidade**.

    **A pipeline é acionada nas seguintes situações:**

    **1. Pull Requests**

    Executada quando um Pull Request é aberto ou atualizado para as branches:

    ```
    main
    develop
    release-candidate
    Subtask/**
    ```

    A execução ocorre apenas quando há alterações nos seguintes arquivos ou diretórios:

    ```
    my-app/main/**
    my-app/package.json
    my-app/package-lock.json
    my-app/jest.config.js
    .github/workflows/ci.yml
    ```

    **2. Push**

    Executada automaticamente quando ocorre push direto nas branches:

    ```
    main
    develop
    release-candidate
    Subtask/**
    ```

=== "Pipeline E2E"

    A pipeline de testes E2E executa a suite Playwright contra o aplicativo Electron empacotado.

    **Acionada nas seguintes situações:**

    Pull Requests abertos ou atualizados e push direto nas branches:

    ```
    main
    develop
    release-candidate
    Subtask/**
    ```

    A execução ocorre apenas quando há alterações nos seguintes caminhos:

    ```
    my-app/playwright/**
    my-app/renderer/**
    my-app/main/**
    .github/workflows/ci-e2e.yml
    ```

    **Etapas executadas:**

    1. Checkout com `fetch-depth: 0` (necessário para análise de diff)
    2. Configuração do Node.js 20 e `npm ci`
    3. Instalação do Playwright e Chromium (`npx playwright install --with-deps chromium`)
    4. Configuração do display virtual Xvfb (1920×1080) e permissões do `chrome-sandbox` para Electron
    5. Build da aplicação (`npx electron-forge package`)
    6. Reset do banco de dados (`npm run reset:db`)
    7. Determinação da estratégia de execução (ver abaixo)
    8. Execução dos testes conforme estratégia
    9. Upload de artefatos `.playwright-results/` (retenção: 7 dias)
    10. Comentário automático no PR com resultado e link para download dos artefatos

    **Estratégia de execução:**

    | Branch | Estratégia | Suites executadas |
    | :--- | :--- | :--- |
    | `main` / `release-candidate` | Completa | `functional`, `integration`, `regression`, `e2e` |
    | Feature / Subtask | Seletiva (path-based) | Apenas módulos afetados + `regression` |

    Na estratégia seletiva, mudanças em `playwright/pages/`, `playwright/utils/` ou `playwright/fixtures/` disparam a suite completa por impactarem todos os módulos.

=== "Release Automático"

    O workflow de release é acionado automaticamente ao merge de uma PR nas branches principais e gera o executável Windows com versionamento semântico automático.

    **Acionado quando:**

    Pull Request é **mergeada** (não apenas aberta) nas branches:

    ```
    main
    release-candidate
    ```

    Também pode ser disparado manualmente via `workflow_dispatch` (build manual — ver abaixo).

    **Etapas executadas:**

    1. Checkout com `fetch-depth: 0`
    2. Cálculo da próxima versão via conventional commits:
        - `feat!` / `BREAKING CHANGE` → incrementa **MAJOR**
        - `feat` → incrementa **MINOR**
        - `fix` / outros → incrementa **PATCH**
    3. Geração de changelog com IA (GPT-4o-mini via GitHub Models) resumindo os commits em português
    4. Atualização da versão no `package.json`
    5. Instalação de dependências (`npm ci`)
    6. Build do executável Windows (`npm run make`)
    7. Criação da GitHub Release com o artefato `.exe`

    **Versionamento por branch:**

    | Branch | Tipo de tag | Exemplo | Marcação |
    | :--- | :--- | :--- | :--- |
    | `main` | Estável | `v1.2.0` | Latest |
    | `release-candidate` | Pre-release | `v1.2.0-rc.1` | Pre-release |

    **Build manual:**

    O workflow `build-windows.yml` permite gerar um executável manualmente via `workflow_dispatch`, informando a tag desejada (ex: `v1.2.3`). Útil para reprocessar uma release ou gerar uma versão fora do ciclo automático.

=== "Revisão do Copilot"

    O GitHub Copilot foi integrado ao processo de desenvolvimento do sistema COIN'S com o objetivo de aprimorar a qualidade do código e aumentar a eficiência das revisões técnicas. A ferramenta atua como um mecanismo complementar de análise automatizada, auxiliando na identificação de problemas e na manutenção dos padrões estabelecidos neste documento.

    ## Instruções do Copilot

    - [Instruções](https://docs.google.com/document/d/1Wp_bDh5UTZ9743nyTy1MNr-uIZD0SD_iqtQQkKMoLZ8/edit?usp=sharing)

    ## Funcionalidades e Aplicações

    O Copilot desempenha as seguintes funções no ciclo de desenvolvimento:

    - **Análise de Código em Tempo Real**: Identifica erros de sintaxe, más práticas e potenciais bugs durante a escrita do código.
    - **Conformidade com Padrões**: Auxilia na aplicação das convenções de nomenclatura e estruturação definidas (camelCase, PascalCase, SCREAMING_SNAKE_CASE).
    - **Detecção de Vulnerabilidades**: Identifica possíveis falhas de segurança e práticas inseguras no código.
    - **Sugestões de Refatoração**: Propõe melhorias de legibilidade, performance e manutenibilidade do código.
    - **Suporte à Documentação**: Sugere aprimoramentos em comentários e documentação quando aplicável.

    ## Integração no Fluxo de Trabalho

    A ferramenta Copilot está disponível nas seguintes etapas do processo de desenvolvimento:

    - **Fase de Desenvolvimento**: Oferece sugestões e autocomplete durante a codificação.
    - **Pull Request**: Atua como recurso adicional de verificação antes da revisão formal.

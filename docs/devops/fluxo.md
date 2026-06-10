# Fluxo de Trabalho

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 02/06/2026 | Criação do documento | Amanda Gois |
| 1.1 | 09/06/2026 | Remove template de PR duplicado do fluxo.md | Amanda Gois |
| 1.2 | 09/06/2026 | Atualiza fluxo para Subtask e release-candidate fixo | Amanda Gois |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |
| 1.1 | 09/06/2026 | Vinicius Carneiro | Aprovado |

---

## Introdução

O processo de desenvolvimento no COIN'S é projetado para garantir a qualidade do código e a estabilidade das entregas através de um ciclo bem definido de ramificação e revisão.

---

## Fluxo

=== "Ciclo de Desenvolvimento"

    ### 1. Início da Feature
    Uma nova funcionalidade começa com a criação de uma branch `feature/` a partir de `develop`:

    ```bash
    git checkout develop
    git pull origin develop
    git checkout -b feature/<nome-da-funcionalidade>
    ```

    ### 2. Criação das Subtasks
    Quando a feature envolve múltiplos desenvolvedores (ex: frontend + backend da mesma tela), cria-se uma branch `Subtask/` por tarefa a partir da `feature/`:

    ```bash
    git checkout feature/<nome-da-funcionalidade>
    git checkout -b Subtask/<nome-da-tarefa>
    ```

    **Exemplos:**

    ```
    Subtask/dre-filtros-backend
    Subtask/dre-tabela-frontend
    ```

    ### 3. Implementação e Sincronia
    Durante o desenvolvimento, mantenha sua branch atualizada para evitar conflitos:
    ```bash
    git fetch origin
    git rebase origin/feature/<nome-da-funcionalidade>
    ```

    ### 4. Abertura de Pull Request (PR)
    - `Subtask/` → PR para a `feature/` correspondente.
    - `feature/` → PR para `develop` após todas as subtasks mergeadas.
    *   Preencha o **Template de PR** obrigatório.
    *   Solicite a revisão de pelo menos um colega.

    ### 5. Ciclo de Release
    Ao final da sprint, com as funcionalidades integradas na `develop`, abre-se um PR de `develop` para a branch fixa **`release-candidate`**.

    O merge na `release-candidate` dispara automaticamente o workflow de Release, gerando um executável de pré-release (ex: `v1.1.0-rc.1`) para o QA validar.

    Se todos os testes (Jest + Playwright) passarem e o QA aprovar, abre-se o PR final de `release-candidate` para `main`, gerando o executável oficial de produção com tag estável (ex: `v1.1.0`).


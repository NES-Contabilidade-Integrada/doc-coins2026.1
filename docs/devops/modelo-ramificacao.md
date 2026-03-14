# Modelo de Ramificação

O modelo de ramificação utilizado no projeto COINS é o **GitFlow**. Este modelo organiza o desenvolvimento em torno de duas branches principais com ciclos de vida infinitos e várias branches de suporte para facilitar o desenvolvimento paralelo e a entrega contínua.

```mermaid
gitGraph
    %% 1. Estado Inicial
    commit id: "Inicial" tag: "v1.0.0"

    %% 2. Base de desenvolvimento
    branch develop
    checkout develop
    commit id: "Ajuste develop"

    %% 3. Feature com Subtasks A e B
    branch feature
    checkout feature
    commit id: "Feature Start"

    branch subtaskA
    checkout subtaskA
    commit id: "Tarefa A"

    checkout feature
    branch subtaskB
    checkout subtaskB
    commit id: "Tarefa B"

    %% Finalizando Subtasks na Feature
    checkout feature
    merge subtaskA
    merge subtaskB
    commit id: "Feature Done"

    %% 4. Finalizando a Feature na Develop
    checkout develop
    merge feature

    %% 5. Hotfix (Direto da Main)
    checkout main
    branch hotfix
    checkout hotfix
    commit id: "Fix Urgente"

    %% 6. Finalizando Hotfix (Main e Develop)
    checkout main
    merge hotfix tag: "v1.0.1"
    checkout develop
    merge hotfix

    %% 7. Release Branch
    checkout develop
    branch "release-1.1.0"
    checkout "release-1.1.0"
    commit id: "Finalizando Release"

    %% 8. Finalizando Release (Main e Develop)
    checkout main
    merge "release-1.1.0" tag: "v1.1.0"
```

## Branches Principais

### 1. main

- **Propósito**: Contém o código de produção, sempre estável e pronto para a versão final.
- **Processo**: Recebe _merges_ apenas de branches de `release` ou, em emergências, de `hotfix`. Nunca se deve desenvolver ou commitar diretamente nesta branch.

### 2. develop

- **Propósito**: Integração de todas as funcionalidades prontas para o próximo ciclo de entrega. É a branch principal de trabalho da equipe.
- **Processo**: Recebe _merges_ contínuos das branches de `feature` concluídas. É onde os testes integrados são realizados.

## Branches de Suporte

### feature/

- **Propósito**: Desenvolvimento isolado de novas funcionalidades ou grandes alterações.
- **Processo**: Criada a partir da `develop`. Após concluída, testada e revisada, é integrada (via _Pull Request_) de volta na `develop`.
- **Nomenclatura**: `feature/nome-da-funcionalidade` ou `feature/ID-da-issue`.

### release/

- **Propósito**: Preparação de uma nova versão para produção. Ambiente dedicado para testes finais e homologação.
- **Processo**: Criada a partir da `develop` quando as funcionalidades planejadas estão prontas. Após a validação, é mergeada na `main` (com tag de versão) e devolvida para a `develop` caso existam correções feitas durante o período de release.

### hotfix/

- **Propósito**: Correções urgentes no ambiente de produção (bugs críticos).
- **Processo**: Criada diretamente a partir da `main`. Após a correção, é integrada na `main` (nova tag) e também na `develop`.

### subtask/

- **Propósito**: Utilizada para dividir uma `feature` muito grande em partes menores ou para tarefas internas pontuais.
- **Processo**: Geralmente criada a partir de uma branch `feature` ou da `develop`. Deve ser mergeada de volta na sua branch de origem após a conclusão.

---

> **Nota**: Todo merge para as branches `develop` e `main` deve ser realizado via **Pull Request** com revisão por pares.

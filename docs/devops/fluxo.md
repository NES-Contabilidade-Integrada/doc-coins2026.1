# Fluxo de Trabalho

O processo de desenvolvimento no COINS é projetado para garantir a qualidade do código e a estabilidade das entregas através de um ciclo bem definido de ramificação e revisão.

=== "Ciclo de Desenvolvimento"

    ### 1. Início da Tarefa
    Toda nova implementação de um Módulo deve começar a partir da branch `develop`. Use a convenção de nomenclatura para manter o repositório organizado:

    ```bash
    git checkout develop
    git pull origin develop
    git checkout -b <tipo>/<descrição-curta>
    ```

    **Tipos comuns:**
    *   `feat/`: Novas funcionalidades.
    *   `fix/`: Correção de bugs.
    *   `docs/`: Documentação.

    #### Criação da Branch Subtask a partir da Feature
    A partir da branch Feature criada para implementação de um Módulo, deve-se criar uma branch Subtask para implementação de cada tarefa separada.

    ```bash
    git checkout feat/<nome-da-feature>
    git checkout -b feat/<nome-da-tarefa>
    ```

    ### 2. Implementação e Sincronia
    Durante o desenvolvimento, mantenha sua branch atualizada com a `develop` para evitar conflitos grandes no final:
    ```bash
    git fetch origin
    git rebase origin/develop
    ```

    ### 3. Abertura de Pull Request (PR)
    Ao finalizar a tarefa, envie sua branch para o GitHub e abra um PR para a branch `develop`.
    *   Preencha o **Template de PR** obrigatório.
    *   Solicite a revisão de pelo menos um colega.

    ### 4. Ciclo de Release
    Ao final de cada sprint, após a validação das funcionalidades na `develop`, criamos uma **branch de release**.
    *   Testes finais de QA/Homologação.
    *   Merge final na `main` com geração de tag.

=== "Template de Pull Request"

    Este é o padrão que deve ser seguido em todas as submissões de código.

    ```markdown
    ## 📌 Descrição
    - O que foi alterado?
    - Por que foi alterado?
    - Contexto adicional, se necessário.

    ---

    ## 📝 Tipo de Mudança
    - [ ] 🐛 Bugfix
    - [ ] ✨ Feature
    - [ ] 🔧 Refactor
    - [ ] 🧹 Chore
    - [ ] 📖 Documentação
    - [ ] 🚀 Performance

    ---

    ## 🔗 Issue Relacionada
    - Closes #

    ---

    ## ✅ Checklist de Qualidade
    - [ ] Código compila sem erros ⚡
    - [ ] Testes adicionados ou atualizados 🧪
    - [ ] Documentação atualizada 📚
    - [ ] Segue padrões de código/lint 🛠️

    ---

    ## 📷 Evidências
    (Prints, logs ou GIFs aqui)

    ---

    ## ⚙️ Ambientes de Teste
    - [ ] Dev
    - [ ] Staging
    - [ ] Produção
    ```

# Jornada do Usuário

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 01/06/2026 | Criação do documento | Fernanda Pessoa |
| 1.1 | 01/06/2026 | Atualiza diagrama com fluxo detalhado e tratamento de balanço não fechado | Fernanda Pessoa |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |

---

## Introdução

Este documento descreve a jornada típica de um estudante de Ciências Contábeis ao utilizar o sistema, cobrindo desde o acesso inicial até a geração dos demonstrativos contábeis finais. O mapa de jornada serve como referência de IHC para garantir que os fluxos de interação estejam alinhados com a progressão natural das tarefas contábeis.

---

## Mapa de Jornada

O diagrama abaixo representa o fluxo principal de uso do sistema, desde o registro de lançamentos até a exportação dos relatórios:

```mermaid
%%{init: {"flowchart": {"rankSpacing": 50, "nodeSpacing": 30}, "themeVariables": {"clusterBkg": "#f5f5f5", "clusterBorder": "#bbbbbb"}}}%%
flowchart TD
    classDef usuario   fill:#fff2cc,stroke:#d6b656,color:#000
    classDef sistema   fill:#dae8fc,stroke:#6c8ebf,color:#000
    classDef condicao  fill:#ffe6cc,stroke:#d79b00,color:#000
    classDef inicioFim fill:#d5e8d4,stroke:#82b366,color:#000

    subgraph Legenda
        direction LR
        LU[Usuário]:::usuario
        LS[Sistema]:::sistema
        LC{Condição}:::condicao
        LI([Início / Fim]):::inicioFim
    end

    A([Início]):::inicioFim --> B

    subgraph S1["Lançamento Contábil"]
        direction TB
        B["Usuário acessa o COIN'S"]:::usuario --> C
        C[Visualiza o Plano de Contas]:::usuario --> D
        D[Consulta as contas disponíveis para lançamento]:::usuario --> E
        E[Cria um lançamento contábil]:::usuario --> F
        F[Informa data, histórico, conta de débito, conta de crédito e valor]:::usuario --> G
        G{Débito e crédito estão equilibrados?}:::condicao
        G -- Não --> H[Sistema exibe aviso de divergência]:::sistema --> F
        G -- Sim --> I[Sistema salva o lançamento]:::sistema --> J
        J[Lançamento aparece no Livro Diário]:::sistema
    end

    J --> K
    subgraph S2["Consultas e Conferências"]
        direction TB
        K[Usuário consulta o Livro Razão]:::usuario --> L
        L[Sistema apresenta a movimentação por conta]:::sistema --> M
        M[Usuário consulta o Balancete de Verificação]:::usuario --> N
        N[Sistema apresenta débitos, créditos e saldos das contas]:::sistema
    end

    N --> O
    subgraph S3["Apuração do Resultado"]
        direction TB
        O[Usuário acessa a Apuração do Resultado]:::usuario --> P
        P[Sistema exibe o resumo da apuração]:::sistema --> Q
        Q[Sistema lista as contas de resultado consideradas]:::sistema --> R
        R[Sistema mostra os lançamentos automáticos que serão realizados]:::sistema --> S
        S{Usuário confirma a apuração?}:::condicao
        S -- Não --> T[Apuração não é realizada]:::sistema
        S -- Sim --> U[Sistema realiza a apuração]:::sistema --> V
        V[Sistema gera automaticamente os lançamentos de encerramento]:::sistema --> W
        W[Lançamentos da apuração aparecem no Livro Diário]:::sistema
    end
    T -. retorna .-> O

    W --> X
    subgraph S4["Histórico e Desfazer"]
        direction TB
        X[Usuário consulta o Histórico de Apurações]:::usuario --> Y
        Y{Deseja desfazer a apuração?}:::condicao
        Y -- Sim --> Z[Usuário verifica os lançamentos da apuração no Livro Diário]:::usuario
        Z --> ZA[Sistema desfaz a apuração]:::sistema --> ZB
        ZB[Lançamentos de apuração deixam de refletir nos relatórios]:::sistema
        Y -- Não --> AA[Usuário valida as contas de resultado]:::usuario --> AB
        AB[Livro Razão ou Balancete mostram contas de resultado zeradas]:::sistema
    end
    ZB -. retorna .-> O

    AB --> AC
    subgraph S5["Demonstrativos e Exportação"]
        direction TB
        AC[Usuário acessa a DRE]:::usuario --> AD
        AD[Sistema apresenta o resultado do período e a composição das contas]:::sistema --> AE
        AE[Usuário acessa o Balanço Patrimonial]:::usuario --> AF
        AF[Sistema apresenta Ativo, Passivo e Patrimônio Líquido]:::sistema --> AG
        AG{Ativo = Passivo + Patrimônio Líquido?}:::condicao
        AG -- Sim --> AL[Sistema indica balanço fechado]:::sistema --> AM
        AM[Usuário exporta relatórios em PDF ou CSV]:::usuario
        AG -- Não --> AH[Sistema indica que o balanço não está fechado]:::sistema --> AI
        AI[Usuário identifica lançamento inconsistente]:::usuario --> AJ
        AJ[Usuário corrige o lançamento no Livro Diário]:::usuario --> AK
        AK[Usuário refaz a conferência no Livro Razão ou Balancete]:::usuario
    end
    AK -. retorna .-> O

    AM --> AN([Fim]):::inicioFim
```

---

## Etapas da Jornada

| Etapa | Descrição |
| :--- | :--- |
| **Plano de Contas** | Ponto de partida — o usuário consulta as contas disponíveis para identificar quais utilizar nos lançamentos. |
| **Livro Diário** | Registro dos lançamentos contábeis com validação do equilíbrio entre débito e crédito antes de salvar. |
| **Livro Razão** | Conferência da movimentação individualizada por conta após os lançamentos. |
| **Balancete de Verificação** | Confronto dos saldos devedores e credores de todas as contas como checagem intermediária. |
| **Apuração do Resultado** | Encerramento das contas de resultado com prévia completa, execução e possibilidade de desfazer. |
| **DRE** | Visualização estruturada do resultado do exercício após a apuração. |
| **Balanço Patrimonial** | Verificação do equilíbrio entre Ativo, Passivo e Patrimônio Líquido. Se o balanço não fechar, o usuário retorna ao Livro Diário para corrigir o lançamento inconsistente. |
| **Exportação** | Geração dos relatórios finais em PDF ou CSV, disponível após o balanço estar fechado. |

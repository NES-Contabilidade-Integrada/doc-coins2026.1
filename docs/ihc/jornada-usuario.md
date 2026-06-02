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
flowchart TD
    A([Início]) --> B["Usuário acessa o COIN'S"]

    B --> C[Visualiza o Plano de Contas]
    C --> D[Consulta as contas disponíveis para lançamento]

    D --> E[Cria um lançamento contábil]
    E --> F[Informa data, histórico, conta de débito, conta de crédito e valor]

    F --> G{Débito e crédito estão equilibrados?}

    G -- Não --> H[Sistema exibe aviso de divergência]
    H --> F

    G -- Sim --> I[Sistema salva o lançamento]
    I --> J[Lançamento aparece no Livro Diário]

    J --> K[Usuário consulta o Livro Razão]
    K --> L[Sistema apresenta a movimentação por conta]

    L --> M[Usuário consulta o Balancete de Verificação]
    M --> N[Sistema apresenta débitos, créditos e saldos das contas]

    N --> O[Usuário acessa a Apuração do Resultado]

    O --> P[Sistema exibe o resumo da apuração]
    P --> Q[Sistema lista as contas de resultado consideradas]
    Q --> R[Sistema mostra os lançamentos automáticos que serão realizados]

    R --> S{Usuário confirma a apuração?}

    S -- Não --> T[Apuração não é realizada]
    T --> O

    S -- Sim --> U[Sistema realiza a apuração]
    U --> V[Sistema gera automaticamente os lançamentos de encerramento]
    V --> W[Lançamentos da apuração aparecem no Livro Diário]

    W --> X[Usuário consulta o Histórico de Apurações]
    X --> Y{Deseja desfazer a apuração?}

    Y -- Sim --> Z[Usuário verifica os lançamentos da apuração no Livro Diário]
    Z --> ZA[Sistema desfaz a apuração]
    ZA --> ZB[Lançamentos de apuração deixam de refletir nos relatórios]
    ZB --> O

    Y -- Não --> AA[Usuário valida as contas de resultado]
    AA --> AB[Livro Razão ou Balancete mostram contas de resultado zeradas]

    AB --> AC[Usuário acessa a DRE]
    AC --> AD[Sistema apresenta o resultado do período e a composição das contas]

    AD --> AE[Usuário acessa o Balanço Patrimonial]
    AE --> AF[Sistema apresenta Ativo, Passivo e Patrimônio Líquido]

    AF --> AG{Ativo = Passivo + Patrimônio Líquido?}

    AG -- Não --> AH[Sistema indica que o balanço não está fechado]
    AH --> AI[Usuário identifica lançamento inconsistente]
    AI --> AJ[Usuário corrige o lançamento no Livro Diário]
    AJ --> AK[Usuário refaz a conferência no Livro Razão ou Balancete]
    AK --> O

    AG -- Sim --> AL[Sistema indica balanço fechado]

    AL --> AM[Usuário exporta relatórios em PDF ou CSV]
    AM --> AN([Fim])
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

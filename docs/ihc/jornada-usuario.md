# Jornada do Usuário

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 01/06/2026 | Criação do documento | Fernanda Pessoa |

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
    A([Início]) --> B[Usuário acessa o sistema]

    B --> C[Visualizar Plano de Contas]
    C --> D[Consultar contas disponíveis]

    D --> E[Adicionar lançamento contábil]
    E --> F{Débito e crédito estão equilibrados?}

    F -- Não --> G[Exibir aviso de divergência]
    G --> E

    F -- Sim --> H[Salvar lançamento]
    H --> I[Registrar no Livro Diário]

    I --> J[Visualizar Livro Razão]
    J --> K[Conferir movimentação por conta]

    K --> L[Visualizar Balancete de Verificação]
    L --> M[Conferir saldos devedores e credores]

    M --> N[Acessar Apuração do Resultado]
    N --> O[Visualizar resumo da apuração]
    O --> P[Conferir contas de resultado]
    P --> Q[Conferir lançamentos automáticos previstos]

    Q --> R{Usuário confirma a apuração?}

    R -- Não --> S[Manter lançamentos sem apurar]
    S --> N

    R -- Sim --> T[Realizar apuração]
    T --> U[Gerar lançamentos automáticos em segundo plano]
    U --> V[Registrar lançamentos de apuração no Livro Diário]

    V --> W[Consultar Histórico de Apurações]
    W --> X{Deseja desfazer apuração?}

    X -- Sim --> Y[Desfazer apuração]
    Y --> N

    X -- Não --> Z[Validar contas de resultado zeradas]
    Z --> AA[Conferir Livro Razão ou Balancete]

    AA --> AB[Acessar DRE]
    AB --> AC[Visualizar resultado e composição das contas]

    AC --> AD[Acessar Balanço Patrimonial]
    AD --> AE[Conferir Ativo = Passivo + Patrimônio Líquido]

    AE --> AF[Exportar relatórios em PDF/CSV]
    AF --> AG([Fim])
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
| **Balanço Patrimonial** | Verificação do equilíbrio entre Ativo, Passivo e Patrimônio Líquido. |
| **Exportação** | Geração dos relatórios finais em PDF ou CSV. |

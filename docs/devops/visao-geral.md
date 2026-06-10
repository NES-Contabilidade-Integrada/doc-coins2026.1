# Visão Geral

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 02/06/2026 | Criação do documento | Amanda Gois |
| 1.1 | 02/06/2026 | Adiciona visão geral dos documentos de DevOps | Fernanda Pessoa |
| 1.2 | 09/06/2026 | Remove DoD e versionamento separados; atualiza links para pipeline.md | Amanda Gois |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |
| 1.1 | 09/06/2026 | Vinicius Carneiro | Aprovado |

---

## Introdução

Esta seção reúne as práticas, padrões e ferramentas que orientam o ciclo de desenvolvimento do projeto COIN'S. Os documentos aqui descritos cobrem desde a organização do repositório e o fluxo de trabalho da equipe até a automação de build e entrega do executável final. O objetivo é garantir rastreabilidade, qualidade e consistência ao longo de todo o processo de desenvolvimento.

---

## Documentos

| Documento | Descrição |
| :--- | :--- |
| [Diretrizes de Gerência de Configuração](diretrizes-gerencia-configuracao.md) | Documento completo com todas as normas e padrões de configuração do projeto: ramificação, commits, convenções de código, versionamento, DoD, CI/CD e revisão do Copilot. |
| [Modelo de Ramificação](modelo-ramificacao.md) | Descreve o GitFlow adotado no projeto, detalhando o propósito e o fluxo de cada tipo de branch (main, develop, feature, release, hotfix, subtask). |
| [Fluxo de Trabalho](fluxo.md) | Descreve o ciclo de desenvolvimento da equipe, desde a criação de branches até a abertura de Pull Requests e o ciclo de release. |
| [Pipeline](pipeline.md) | Documenta o pipeline de integração contínua (Jest e Playwright), o release automático com versionamento semântico por branch, e a integração do GitHub Copilot. |
| [Pull Request Template](pull-request-template.md) | Template padrão a ser preenchido em todas as submissões de código via Pull Request. |
| [Geração do Executável](geracao-executavel.md) | Explica como gerar o executável do projeto (manualmente e via CI/CD) e detalha os problemas conhecidos de configuração do ambiente Electron. |

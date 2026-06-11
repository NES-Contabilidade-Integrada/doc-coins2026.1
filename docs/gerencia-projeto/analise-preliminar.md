# Análise Preliminar de Projeto

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 02/06/2026 | Criação do documento | Fernanda Pessoa |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | :---: |
| 1.0 | 10/06/2026 | Eduardo Alves | Aprovado |

---

## Introdução

Este documento registra a análise geral do sistema **COIN'S** (Contabilidade Integrada), desenvolvido no Núcleo de Práticas em Engenharia de Software no 1º semestre de 2026, para o Professor Robert Espejo e o aluno Jean Pleutim, do curso de Ciências Contábeis da UFMS.

A análise foi realizada pela equipe de 2026.1 sobre todos os artefatos entregues pela equipe anterior (2025.2): protótipos, documentação, diagramas, código-fonte e executável da aplicação. O resultado apresentado neste documento reúne os defeitos encontrados, as melhorias implementadas e o estado geral do sistema no início do ciclo atual.

---

## Tecnologias Aplicadas para o Desenvolvimento

O sistema COIN'S é uma aplicação **desktop multiplataforma** (Windows, Linux e macOS), desenvolvida com a seguinte pilha tecnológica, escolhida pela equipe de 2025.2 e mantida em 2026.1:

| Camada | Tecnologia | Justificativa |
| :--- | :--- | :--- |
| **Plataforma** | Electron + Electron Forge | Permite desenvolvimento desktop multiplataforma a partir de tecnologias web, com empacotamento e distribuição simplificados. |
| **Frontend** | Vue 3 + Vite + TypeScript | Alta produtividade, reatividade nativa e integração simples com o Electron. O TypeScript aumenta a confiabilidade e facilita a manutenção. |
| **Backend** | Express.js + TypeScript | Camada de backend local dentro do processo Electron, responsável pelos endpoints REST internos e centralização da lógica de negócio. |
| **Banco de Dados** | SQLite3 (better-sqlite3) | Leve, embarcado e adequado ao uso offline. Não requer servidor dedicado. |
| **Query Builder** | Knex.js | Abstração de acesso ao banco, migrations estruturadas e portabilidade. |
| **Testes** | Jest (unitários) + Playwright (E2E) | Cobertura de testes unitários no backend e testes end-to-end das funcionalidades críticas do sistema. |
| **CI/CD** | GitHub Actions | Automação de build, execução de testes e geração do executável a cada merge na branch de release. |

---

## Defeitos Encontrados

Esta seção lista os defeitos identificados na análise dos artefatos entregues em 2025.2, organizados por módulo do sistema.

### 3.1 Módulo 1 — Plano de Contas

- Contas sem filhos exibiam ícone de expansão, dando a falsa impressão de que eram expansíveis.
- A busca no Plano de Contas não exibia contas cujos grupos estavam fechados (recolhidos), sem nenhuma indicação visual ao usuário — aparentando ausência de dados no sistema.
- Não era exibido um popup informando que a conta selecionada era do tipo analítica ao tentar registrar um lançamento em conta sintética.

### 3.2 Módulo 2 — Livro Diário

- As validações de entrada dos campos do formulário de lançamentos eram incorretas ou ausentes, permitindo dados inconsistentes.
- Valores com separadores de milhar (`.`) e separadores decimais (`,`) não eram tratados corretamente, causando erro 500 no backend ao tentar salvar o lançamento.
- O botão "Adicionar lançamento" desaparecia em telas com resolução reduzida devido a problemas de responsividade.

### 3.3 Módulo 3 — Livro Razão

- O filtro de contas do Livro Razão havia desaparecido da interface.
- Não havia mensagem de feedback quando o resultado de um filtro aplicado era vazio.
- Os filtros não validavam datas inválidas inseridas pelo usuário.
- Os dados preenchidos nos filtros eram perdidos ao sair da tela e retornar.

### 3.4 Módulo 4 — Balancete de Verificação

- Os dados exibidos no resumo do Balancete não eram calculados corretamente.

### 3.5 Problemas Gerais

- O campo "D/C" (Débito/Crédito) era exibido incorretamente em todo o sistema quando o valor associado era R$ 0,00.
- Novas versões do executável eram incompatíveis com bases de dados geradas por versões anteriores, impedindo usuários com dados preexistentes de abrir o sistema.

---

## Melhorias Implementadas

Além da correção dos defeitos, foram implementadas melhorias identificadas durante a análise, que ampliam a usabilidade e a qualidade do sistema.

### 4.1 Módulo 1 — Plano de Contas

- Adicionado toggle para expandir e recolher grupos do Plano de Contas, facilitando a navegação em planos extensos.

### 4.2 Módulo 2 — Livro Diário

- Adicionado autocomplete por nome de conta no campo de lançamento, agilizando o preenchimento.
- Após registrar um lançamento, o sistema passa a redirecionar automaticamente para o Livro Diário.

### 4.3 Módulo 3 — Livro Razão

- Os valores totais do Livro Razão passaram a ser agrupados por dia, em vez de exibir cada lançamento em linha separada.

### 4.4 Melhorias de Infraestrutura e DevOps

- O executável, que anteriormente era distribuído como uma pasta compactada em `.zip` exigindo navegação por 5 subpastas até encontrar o arquivo executável (sem nome identificável), foi substituído por um único instalador com o ícone e o nome do COIN'S.
- A geração do executável foi automatizada via GitHub Actions a cada push na branch `main`, eliminando a necessidade de build manual.

### 4.5 Melhorias de Interface

- Adicionado suporte a zoom na aplicação.
- Adicionada a logo da UFMS na barra lateral do sistema.
- O nome "Fornecedor" foi substituído por "Núcleo de Prática de Engenharia de Software — UFMS" nos locais pertinentes.

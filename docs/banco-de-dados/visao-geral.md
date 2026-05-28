# Visão Geral — Banco de Dados

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 28/05/2026 | Versão inicial do documento | Fernanda Pessoa |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | :---: |

## Sumário

1. [Introdução](#introdução)
2. [Tecnologias](#tecnologias)
3. [Estrutura do Modelo](#estrutura-do-modelo)
4. [Documentação](#documentação)

---

## Introdução

O banco de dados do sistema foi projetado para suportar o ciclo contábil completo — do cadastro de empresas e plano de contas ao registro de lançamentos e geração de demonstrativos. A modelagem prioriza integridade referencial e simplicidade operacional, dado que o sistema roda localmente sem necessidade de servidor externo.

---

## Tecnologias

| Tecnologia | Papel |
|---|---|
| **SQLite** | Banco de dados relacional embarcado, armazenado como arquivo local junto ao executável. Não requer instalação ou configuração de servidor. |
| **Knex.js** | Query builder e gerenciador de migrações. Controla a evolução do esquema ao longo das versões do sistema. |

---

## Estrutura do Modelo

O modelo é composto por **sete tabelas de negócio**:

| Tabela | Descrição |
|---|---|
| `account_types` | Tipos de conta contábil (ex: Ativo, Passivo). |
| `actors` | Atores responsáveis pelos lançamentos. |
| `chart_of_account` | Plano de Contas com hierarquia de contas sintéticas e analíticas. |
| `company` | Empresas cadastradas no sistema. |
| `apuracoes` | Apurações contábeis vinculadas a contas de destino. |
| `journal_entry` | Lançamentos contábeis realizados por cada empresa. |
| `journal_entry_line` | Partidas de cada lançamento, com valores de débito e crédito. |

O DER foi modelado na ferramenta [dbdiagram.io](https://dbdiagram.io), que gera o diagrama visual a partir do código DBML.

---

## Documentação

- **[Documentação do Modelo de Dados](documentacao-modelo-dados.md)** — DER, código DBML e script SQL de criação das tabelas.
- **[Dicionário de Dados](dicionario-dados.md)** — descrição detalhada de cada campo, tipo, chave e relacionamento entre as tabelas.

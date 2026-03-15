---
toc_depth: 2
---

# Diário de Decisões (RDs)

Este documento centraliza todos os registros de decisões de processo do projeto COINS.

## Sumário

| ID | Título | Data |
|----|--------|------|
| [RD 001](#rd-001--adições-nas-diretrizes-de-gerência-de-configuração) | Adições nas Diretrizes de Gerência de Configuração | 2026-03-14 |
| [RD 002](#rd-002--reavaliação-da-terminologia-de-agrupamento-de-funcionalidades) | Reavaliação da Terminologia de Agrupamento de Funcionalidades | 2026-03-14 |
| [RD 003](#rd-003--modelo-de-descoberta) | Modelo de Descoberta | 2026-03-14 |

> Para registrar uma nova decisão, consulte o [Template de RD](rd-template.md).

---

## RD 001 — Adições nas Diretrizes de Gerência de Configuração

- **Data:** 2026-03-09
- **Decisores:** Equipe de DevOps

#### Contexto

Após revisão dos documentos que constavam informações relevantes para Gerência de Configuração, foram anotadas possíveis mudanças que a pessoa responsável gostaria de fazer.
A equipe se reuniu para discussão da melhor decisão, abrangendo **Modelo de Ramificação**, **Modelo de Commits**, **Versionamento** e **Fluxo de Trabalho** no GitHub.

#### Decisão

Foi decidido continuar com o modelo já utilizado no projeto anteriormente, pois se encaixa na forma de trabalho prevista pela equipe. Porém, foi identificada a falta de algumas informações e, para uma estrutura clara e bem definida, as informações faltantes foram adicionadas:

1. **Definição do Versionamento** — Foram adicionadas instruções sobre a criação de **Tags** das versões das branches **Releases** e **Main**.
2. **Fluxo com Homologação do QA** — Foi definido que o QA realizará as homologações das features novas dentro da branch **develop**.

#### Consequências

- Processo de versionamento mais claro e rastreável com uso de tags.
- Homologações centralizadas na branch `develop`, deixando a branch `release` estável para homologação com proponete.

---

## RD 002 — Reavaliação da Terminologia de Agrupamento de Funcionalidades

- **Data:** 2026-03-10
- **Decisores:** Equipe COINS 2026.1

#### Contexto

O documento de Encerramento de Projeto do ciclo anterior continha uma sugestão para reavaliar a terminologia utilizada para agrupamento de funcionalidades.

O termo **"épico"** foi empregado como forma de agrupar conjuntos de funcionalidades, porém, no contexto de metodologias ágeis, "épico" pressupõe a existência de histórias de usuário derivadas, o que não foi adotado nesta iniciativa. Isso gerava imprecisão conceitual na comunicação da equipe e na documentação do projeto.

#### Decisão

Adotamos o termo **"Módulo"** para agrupamento de funcionalidades, em substituição ao termo "épico", garantindo maior precisão conceitual alinhada ao modelo de desenvolvimento utilizado.

#### Consequências

- Terminologia mais precisa e coerente com a forma de trabalho da equipe.
- Maior clareza para equipes futuras ao interpretar a documentação e o backlog do projeto.

---

## RD 003 — Modelo de Descoberta

- **Data:** 2026-03-10
- **Decisores:** Equipe COINS 2026.1

#### Contexto

Após uma apresentação para o grupo sobre possíveis modelos para levantamento de requisitos, foram avaliadas diversas técnicas e métodos. As opções consideradas, juntamente com suas vantagens e desvantagens, podem ser visualizadas no [board do Miro](https://miro.com/app/board/uXjVG0HEXeY=/?share_link_id=578964212735).

#### Decisão

Foi decidido adotar o método de **Entrevistas** para o levantamento de requisitos do projeto.

#### Consequências

- Coleta de requisitos mais direcionada e aprofundada com os stakeholders.
- Maior clareza sobre as necessidades reais dos usuários e do proponente.

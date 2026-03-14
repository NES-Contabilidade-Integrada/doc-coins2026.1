# Definição de Pronto (DoD)

A **Definição de Pronto (DoD)** é um conjunto de critérios de qualidade e padrões obrigatórios que toda funcionalidade ou alteração deve satisfazer para ser considerada completa e aceitável. Este checklist assegura a estabilidade, a rastreabilidade e o cumprimento das diretrizes de código e desenvolvimento estabelecidas neste documento, antes que o item de trabalho possa ser integrado ou entregue.

#### **Código** {#código}

- Código commitado e seguindo o padrão semântico definido, no repositório oficial.
- O nome da branch está seguindo a semântica estabelecida.
- Lint/format executado pelo autor antes do push.

#### **Integração e Build** {#integração-e-build}

- Pull Request aberto com descrição clara e referência ao ticket.
- Build do CI passa (compilação / lint).

#### **Testes** {#testes}

- Testes unitários relacionados à função estão implementados e funcionando.
- Cobertura mínima definida atendida (ex.: cobertura global ≥ 80% ou testes críticos cobertos).

#### **Revisão e Aprovação** {#revisão-e-aprovação}

- Revisão por pelo menos 1 revisor técnico aprovado.
- Comentário no PR do revisor. Através de um simples comentário de aprovado ou até um feedback técnico.

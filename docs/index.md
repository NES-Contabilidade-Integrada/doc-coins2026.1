# COINS — Contabilidade Integrada Simplificada

Bem-vindo ao COINS! Este sistema foi idealizado pelo Núcleo de Práticas de Engenharia de Software e teve início no segundo semestre de 2025.

O COINS é um aplicativo desktop pensado para estudantes dos primeiros períodos de Ciências Contábeis, oferecendo um ambiente seguro e intuitivo para praticar lançamentos, compreender relatórios e consolidar os fundamentos contábeis.

Assista ao vídeo de apresentação para conhecer o sistema em ação:

<iframe width="560" height="315" src="https://www.youtube.com/embed/FLl8JhWhBFk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---

## Navegação Rápida

- [Início](index.md)
- [Arquitetura](arquitetura/especificacao-arquitetural.md)
- [Requisitos](requisitos/apuracao-regras.md)
- [Banco de Dados](banco-de-dados/documentacao-modelo-dados.md)
- [Qualidade e Testes](qualidade-testes/plano-de-testes.md)
- [Gerência de Projeto](gerencia-projeto/plano-do-projeto.md)
- [DevOps](devops/visao-geral.md)
- [Decisões](decisoes/decisoes.md)

---

## Objetivo

O COINS é um sistema educacional que permite a execução de atividades contábeis em um ambiente controlado. O foco está em:

* apoiar o aprendizado prático de registros contábeis;
* permitir a análise de resultados financeiros por meio de relatórios;
* oferecer uma base para avaliações acadêmicas e revisão de processos.

---

## Escopo desta documentação

Este repositório reúne os principais artefatos do projeto, incluindo:

* arquitetura e decisões de projeto;
* requisitos de produto e requisitos de software;
* modelagem de dados e dicionário de dados;
* interface e experiência do usuário;
* estratégia de qualidade e testes;
* governança de projeto e práticas de DevOps.

---

## Navegação

Use o menu lateral para acessar cada área do projeto:

* **Arquitetura**: visão geral, diagramas e decisões arquiteturais.
* **Requisitos**: visão do produto, requisitos funcionais e não funcionais, e documentação de regras.
* **Banco de Dados**: modelo conceitual, modelo lógico, documentação do modelo e dicionário de dados.
* **IHC**: personas, jornada do usuário e protótipos.
* **Qualidade e Testes**: estratégia, plano, casos de teste e cobertura.
* **Gerência de Projeto**: planejamento, cronograma, riscos e templates de documentos.
* **DevOps**: infraestrutura, fluxo de trabalho, versionamento e integração contínua.
* **Decisões**: registros de decisão e templates de requisitos.

---

## Como usar esta documentação

No diretório raiz do projeto, execute:

```bash
python -m mkdocs serve
```

Em seguida, acesse:

```
http://127.0.0.1:8000
```

---

## Público-alvo

Esta documentação é destinada a:

* estudantes de Ciências Contábeis;
* professores e tutores do curso;
* desenvolvedores e analistas que mantêm o sistema;
* avaliadores de qualidade e gestores acadêmicos.

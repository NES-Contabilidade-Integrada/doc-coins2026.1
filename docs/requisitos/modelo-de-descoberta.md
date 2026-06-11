# Modelo de Descoberta

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 01/06/2026 | Versão inicial do documento | Fernanda Pessoa |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | 10/06/2026 | Elise Lissa | Aprovado |

---

## Introdução

Este documento descreve o processo de descoberta adotado ao longo dos dois semestres de desenvolvimento do COIN'S, registrando como foram levantados, refinados e validados os requisitos e protótipos do sistema junto aos proponentes.

---

## 2025/2

### Material Fornecido pelos Proponentes

Os proponentes Jean e Robert disponibilizaram uma série de vídeos gravados explicando os fundamentos da contabilidade e apresentando o **sistema Domínio** — um software contábil comercial utilizado como referência para compreender os processos e a terminologia do domínio.

Os vídeos encontram-se na pasta do Google Drive: [Vídeos dos Proponentes](https://drive.google.com/drive/folders/1RXL-zfLxWOH7tg77ap86YH3jYLxnsooa?usp=sharing)

Além dos vídeos, foi fornecida uma **descrição inicial do projeto** que serviria de ponto de partida para o entendimento do escopo:

[Descrição Inicial do Projeto](https://docs.google.com/document/d/1PDsWocBT-59nTwv5HgZrhmlWRyi353ONFabtHrYlByM/edit?usp=drive_link)

!!! warning "Divergência com o produto atual"
    A descrição inicial não era compatível com o que o projeto se tornou. O escopo foi significativamente refinado ao longo do semestre à medida que a equipe aprofundou o entendimento do domínio contábil.

### Lean Inception Relâmpago

Com base no material recebido, a equipe realizou uma **Lean Inception relâmpago no Miro** para alinhar a visão do produto. O processo foi desafiador: as reuniões com os proponentes eram pontuais e raramente ocorriam mais de uma vez por semana, o que exigiu que a equipe avançasse com o entendimento disponível, validando incrementalmente conforme a disponibilidade dos proponentes permitia.

### Levantamento de Dúvidas Iniciais

Para aproveitar ao máximo os momentos de contato com os proponentes, a equipe organizou um **estacionamento de dúvidas** — um documento consolidando as questões técnicas e de domínio que precisavam ser esclarecidas:

[Estacionamento de Dúvidas Iniciais](https://docs.google.com/document/d/1AII2B2pea72-O5sLwjqgXaycgA4SzcmkkgyBT9MptVY/edit?usp=drive_link)

### Plano de Contas de Referência

Os proponentes forneceram um **plano de contas em Excel** como base estrutural para o desenvolvimento do módulo de Plano de Contas do sistema:

[Plano de Contas (Excel)](https://docs.google.com/spreadsheets/d/1eYd4BTtSIW6IggKeMR8KJp0oBfOmKuRALwSfzIBAEEw/edit?usp=drive_link)

### Prototipação

Com o domínio parcialmente mapeado, a equipe iniciou a prototipação no Figma, seguindo as etapas abaixo:

**1. Identidade Visual**

Definição da paleta de cores e dos elementos visuais do COIN'S:

[Paleta de Cores no Figma](https://www.figma.com/design/Z3hfLoenhr73I3u5BRU5lP/COIN-S---Contabilidade-Integrada?node-id=5-225&t=LffhAJRG1CydnNoW-1)

**2. Protótipo de Baixa Fidelidade**

Protótipo inicial das telas, validado com o proponente:

[Protótipo de Baixa Fidelidade](https://www.figma.com/design/Z3hfLoenhr73I3u5BRU5lP/COIN-S---Contabilidade-Integrada?node-id=29-811&t=LffhAJRG1CydnNoW-1)

**3. Protótipo de Alta Fidelidade**

A partir da validação do protótipo de baixa fidelidade, foi desenvolvido o protótipo de alta fidelidade, que passou a ser a referência principal para o desenvolvimento. O protótipo de baixa fidelidade deixou de ser utilizado a partir desta etapa:

[Protótipo de Alta Fidelidade](https://www.figma.com/design/Z3hfLoenhr73I3u5BRU5lP/COIN-S---Contabilidade-Integrada?node-id=199-2979&t=LffhAJRG1CydnNoW-1)

---

## 2026/1

### Modelo de Descoberta Adotado

Com um volume significativo de insumos já consolidados do semestre anterior — incluindo mapeamento de funcionalidades futuras, bugs conhecidos e feedback dos proponentes —, a equipe realizou um **tradeoff entre modelos de descoberta no Miro** e optou pelo modelo de **Entrevista**.

A escolha se justificou pela flexibilidade que esse modelo oferece para aproveitar o material já existente e pela natureza das interações com os proponentes, que não seguem uma cadência fixa.

### Mapeamento Inicial

Com base nos insumos do semestre anterior, a equipe mapeou:

- **Bugs conhecidos** — problemas identificados durante o desenvolvimento de 2025/2
- **Novas funcionalidades** — features previstas no Plano do Projeto e ainda não implementadas
- **Melhorias apontadas pelo proponente** — organizadas em uma **matriz de prioridade**

A partir desse mapeamento, metade da Sprint 0 foi dedicada ao início da correção de bugs e das melhorias priorizadas.

### Protótipo de Alta Fidelidade

Em 2026/1 foi utilizado apenas o protótipo de alta fidelidade, herdado do semestre anterior, como referência para as telas já existentes:

[Protótipo de Alta Fidelidade](https://www.figma.com/design/Z3hfLoenhr73I3u5BRU5lP/COIN-S---Contabilidade-Integrada?node-id=199-2979&t=LffhAJRG1CydnNoW-1)

### Prototipação com Figma Make

Para as novas telas — cujo conteúdo nem a equipe nem os proponentes tinham clareza inicial —, a equipe utilizou o **Figma Make** com licença de estudante para gerar protótipos rapidamente e validar com o proponente.

!!! note "Limitação do Figma Make"
    O Figma Make não consegue reproduzir fielmente a identidade visual do COIN'S. Por isso, após cada ciclo de validação, era necessário migrar e adaptar manualmente o protótipo gerado para o Figma oficial do projeto, aplicando os elementos visuais corretos.

Os protótipos do Figma Make serviam como ponto de partida para as conversas com o proponente: a partir das telas geradas e das explicações recebidas, a equipe conseguia compreender o que era necessário implementar, escrever as regras de negócio e refinar os requisitos correspondentes.

# Especificação de Identidade Visual do Software

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 29/10 | Versão inicial do documento | Fernanda Pessoa |
| 1.1 | 30/10 | Adição das colunas relacionadas ao uso do Vue, Paleta de Cores e Elementos do AVA | Jerfferson Jorge, Wagner Rodrigues |
| 1.2 | 10/11 | Complemento da seção de Elementos do AVA relacionando as figuras 2 e 3 | Jerfferson Jorge |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | :---: |
| 1.0 | 30/10 | Jerfferson Jorge | Aprovada |
| 1.2 | 12/11 | Fernanda Pessoa | Aprovada |

## Sumário

1. [Introdução](#introdução)
2. [Uso de Vue](#uso-de-vue)
3. [Paleta de Cores](#paleta-de-cores)
4. [Elementos do AVA UFMS](#elementos-do-ava-ufms)
5. [Conclusão](#conclusão)

---

## Introdução

O COIN'S — Contabilidade Integrada é um software desktop desenvolvido em 2025 na UFMS, no âmbito do Núcleo de Práticas de Engenharia de Software. Na ausência de um guia institucional específico para aplicações desktop, este documento define a identidade visual do COIN'S, com foco em usabilidade, consistência e alinhamento à identidade da UFMS.

Este material estabelece princípios, variáveis de cor e diretrizes de uso de elementos visuais relacionados à universidade, garantindo uma experiência coerente em todas as telas do sistema.

**Link do Figma:** [COIN'S — Contabilidade Integrada](https://www.figma.com/design/R9pTpBIlEFSBCrvvl2P7ZF/COIN-S---Contabilidade-Integrada?node-id=0-1&p=f&t=DPDaP80JG8v52gBV-0)

---

## Uso de Vue

Inicialmente, optamos por utilizar uma biblioteca para a criação de design e de componentes do sistema, de modo a focar o trabalho na estilização e adaptação para uma identidade própria. Essa biblioteca seria o MUI — *Material Design*. 

Entretanto, diante das decisões arquiteturais e de desenvolvimento, optamos por trocar a biblioteca pelo Vuetify, um framework de componentes para Vue.js, já que o MUI é utilizado apenas com React. Essa escolha também está relacionada com a estruturação da stack da UFMS, que utiliza [Vue.js](https://vuejs.org/) como linguagem de programação.

---

## Paleta de Cores

A paleta de cores utilizada foi baseada na cor institucional (#0088B7). A partir dela, utilizamos uma [ferramenta geradora de temas](https://www.colors.tools/color-theme/?currentColor=0088B7&currentColorMixed=ee4b0a&currentSteps=20&currentHarmony=180&currentHarmonyDominance=50,50,50,50) para facilitar a criação da identidade visual, a qual foi utilizada como base para geração da paleta completa (primary).

Como diferencial, adaptamos alguns dos elementos para variantes da cor primária institucional (que no nosso caso, é o primary 500). Entretanto, todos os tons de azul encontrados atualmente no nosso sistema são derivados dessa cor.

**Referência:** [Manual de Identidade Visual UFMS](https://www.ufms.br/wp-content/uploads/2021/08/Manual-de-Identidade-Visual-UFMS.pdf) — Página 16

---

## Elementos do AVA UFMS

Vários componentes foram utilizados com base no sistema do AVA UFMS, como:

- O fator de elevação relacionado à separação de componentes
- Cores na borda de cada componente

Abaixo há um comparativo entre o sistema COIN'S e o AVA UFMS, destacando o fundo que reforça a ideia de relevo e a área superior das seções (borda de cada componente). Estes são alguns dos exemplos de elementos gráficos cujo design foi inspirado nos sistemas da UFMS.

Além disso, em conjunto esses elementos reforçam uma estrutura separativa, funcionando como um quebra-cabeça de componentes, sendo mais uma ideia que o sistema COIN'S busca refletir, embasada nos sistemas da UFMS.

---

## Conclusão

Esta especificação padroniza a identidade visual do COIN'S, garantindo coerência com a marca UFMS e promovendo uma experiência acessível e consistente. 

A referência à identidade institucional é indireta: as decisões de layout, contraste e componentes foram orientadas para aprimorar a usabilidade de tarefas contábeis (lançamentos, conferências, filtros e leitura de relatórios), sem reproduzir literalmente o AVA/portal ou outros sistemas da UFMS. 

Ainda assim, a essência da universidade permanece — refletida na paleta, na tipografia e nos princípios de simplicidade e clareza.

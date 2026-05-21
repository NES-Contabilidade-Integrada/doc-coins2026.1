# ADR-COINS

**Registro de Decisões Arquiteturais**

**Histórico de versões**

| Versão | Data | Descrição | Autor |
| :---- | :---- | :---- | :---- |
| 1.0.0 | 19/08/2025 | Adicionando estrutura inicial da ADR sobre a plataforma que será utilizada no sistema | Pedro Nicoletti Sotoma |
| 1.1.0 | 19/08/2025 | Adicionando ADR para escolha de tecnologia principal do sistema | Pedro Nicoletti Sotoma |
| 1.1.1 | 20/08/2025 | Centralizando documentos de ADRs em um único documento, ao invés de 1 para cada | Pedro Nicoletti Sotoma  |
| 1.2.0 | 20/08/2025 | Adicionando ADR para escolha de linguagem de desenvolvimento para o backend | Pedro Nicoletti Sotoma |
| 1.3.0 | 20/08/2025 | Adicionando ADR para escolha de framework de desenvolvimento frontend | Pedro Nicoletti Sotoma |
| 1.4.0 | 20/08/2025 | Adicionando ADR para escolha de banco de dados do sistema | Pedro Nicoletti Sotoma |
| 1.4.1 | 21/08/2025 | Adicionando histórico de revisões das ADRs | Pedro Nicoletti Sotoma |
| 1.5.0 | 27/08/2025 | Adicionando ADR para ferramenta de build | Gustavo Fujinohara |
| 1.5.1 | 11/11/2025 | Ajustando sumário do documento | Pedro Nicoletti Sotoma |
| 1.6.0 | 28/11/2025 | Adicionando ADR para uso do Copilot | Wagner Rodrigues |

**Histórico de revisões**

| Versão | Data | Revisor | Observação |
| :---- | :---- | :---- | :---- |
| 1.0.0 | 20/08/2025 | Wagner | Aprovada |
| 1.1.0 | 20/08/2025 | Wagner | Aprovada |
| 1.2.0 | 28/08/2025 | Gustavo Fujinohara | Aprovada |
| 1.3.0 | 28/08/2025 | Gustavo Fujinohara | Aprovada |
| 1.4.0 | 28/08/2025 | Wagner | Aprovada |
| 1.4.1 | 28/08/2025 | Gustavo Fujinohara | Aprovada |
| 1.5.0 | 28/08/2025 | Wagner | Aprovada |
| 1.5.1 | 28/11/2025 | Wagner | Aprovada |
| 1.6.0 | 28/11/2025 | Pedro Nicoletti Sotoma | Aprovada |

**Sumário**

**[ADR-001 Plataforma do Sistema	3](#adr-001-plataforma-do-sistema)**

[**ADR-002 Tecnologia para desenvolvimento do sistema	5**](#adr-002-tecnologia-para-desenvolvimento-do-sistema)

[**ADR-003 Linguagem para o desenvolvimento back-end	7**](#adr-003-linguagem-para-o-desenvolvimento-back-end)

[**ADR-004 Framework para o desenvolvimento front-end	9**](#adr-004-framework-para-o-desenvolvimento-front-end)

[**ADR-005 Banco de Dados para Armazenamento Local	11**](#adr-005-banco-de-dados-para-armazenamento-local)

[**ADR-006 Ferramenta de build e distribuição do aplicativo	13**](#adr-006-ferramenta-de-build-e-distribuição-do-aplicativo)

[**ADR-007 Uso do GitHub Copilot nas Revisões de Código do Sistema COINS	15**](#adr-007-uso-do-github-copilot-nas-revisões-de-código-do-sistema-coins)

## **ADR-001 Plataforma do Sistema** {#adr-001-plataforma-do-sistema}

**Descrição:** A equipe da disciplina de PDS2 (Práticas de Desenvolvimento de Software 2\) está desenvolvendo um novo sistema para alunos cursando os semestres iniciais do curso de Ciências Contábeis.

**Contexto:**

- O sistema precisa ser executado nos laboratórios de ensino da ESAN, garantindo fácil instalação, manutenção simples e compatibilidade com o ambiente de hardware disponível. Além disso, os alunos deverão ter acesso a uma solução funcional sem a necessidade de infraestrutura complexa de rede ou servidores externos.

**Decisão:**

- Optamos por desenvolver um sistema desktop.

**Justificativa:**

- **Simplicidade:** O desenvolvimento de um sistema desktop é mais simples por adotar uma arquitetura monolítica que centraliza toda a lógica necessária para o funcionamento.  
- **Implantação:** A distribuição do sistema nos laboratórios é facilitada, já que basta disponibilizar um executável instalado em cada máquina, sem necessidade de servidores adicionais.  
- **Independência de Rede:** O sistema pode funcionar mesmo sem conexão à internet, reduzindo riscos de indisponibilidade por falhas de rede.  
- **Aderência ao Contexto:** Considerando que o uso é restrito aos laboratórios, a solução desktop atende de forma adequada ao escopo e aos recursos disponíveis.

**Consequências:**

- **Positivas**  
  - Facilita o desenvolvimento inicial do sistema.  
  - Implantação simples e rápida.  
  - Não depende de infraestrutura de rede.  
- **Negativos**  
  - O executável pode demandar mais recursos do hardware da máquina, dependendo da complexidade futura.  
  - Arquitetura monolítica pode dificultar escalabilidade e manutenção em longo prazo.  
  - Atualizações exigem reinstalação em todas as máquinas.

**Alternativas Consideradas:**

- **Sistema mobile:**   
  - **Prós:** Portabilidade e possibilidade de acesso fora do laboratório.  
  - **Contras:** Desenvolvimento mais complexo, necessidade de publicação em lojas de aplicativos e limitação de uso em laboratórios (nem todos os alunos têm dispositivos compatíveis).  
  - **Motivo da Rejeição:** O uso pretendido é em laboratórios de ensino, e exigir dispositivos móveis criaria barreiras de acesso e complexidade desnecessária.


- **Sistema Web:**   
  - **Prós:** Facilidade de atualização (aplicação centralizada em servidor), acessível em diferentes dispositivos, escalável e multiplataforma.  
  - **Contras:** Necessidade de infraestrutura de rede estável e servidor dedicado, aumento da complexidade de implantação e custos de manutenção.  
  - **Motivo da Rejeição:** Nos laboratórios da ESAN não há garantia de infraestrutura robusta de rede e servidor, o que poderia comprometer a disponibilidade do sistema.

## **ADR-002 Tecnologia para desenvolvimento do sistema**  {#adr-002-tecnologia-para-desenvolvimento-do-sistema}

**Descrição:** A equipe da disciplina de PDS2 (Práticas de Desenvolvimento de Software 2\) se reuniu para decidir qual tecnologia seria mais adequada para implementação do sistema.

**Contexto:**

- O Sistema COINS necessita de uma tecnologia para implementação de um sistema desktop robusto que possa ser utilizado nos laboratórios da ESAN.

**Decisão:**

- Optamos por utilizar o Electron.

**Justificativa:**

- **Simplicidade e conhecimento da equipe:** O Electron tem como base JavaScript, tecnologia já conhecida pela maioria da equipe e com amplo apoio da comunidade.

- **Distribuição:** O Electron pode ser compilado em qualquer sistema operacional desktop (Windows, Linux, MacOS) e gera um executável adequado para cada contexto.

- **Ecossistema:** Permite integração com bibliotecas web modernas (React, Vue, Angular, etc.) e acesso a APIs do sistema operacional.

- **Manutenção e evolução:** A grande comunidade garante atualizações frequentes, tutoriais e suporte para novas demandas.

**Consequências:**

- **Positivas**  
  - Desenvolvimento multiplataforma com uma única base de código.

  - Rapidez no desenvolvimento inicial, aproveitando conhecimentos já adquiridos da equipe em tecnologias web.

  - Grande ecossistema de pacotes e bibliotecas disponíveis.

  - Facilita o design de interfaces ricas e responsivas.


- **Negativos**  
  - Alto consumo de memória e recursos comparado a aplicações nativas.

  - Maior tamanho final do executável.

  - Dependência do Node.js e Chromium embutidos.

  - Possíveis problemas de desempenho em máquinas com recursos limitados.

**Alternativas Consideradas:**

- **JavaFx**  
  - **Prós:** Conhecimento da equipe  
  - **Contras:** Layout pouco amigável para o cliente, tecnologia demasiadamente rígida e robusta.  
  - **Motivo da Rejeição:** Experiência do usuário confusa para os alunos do primeiro semestre de Ciências Contábeis.


- **Tauri**  
  - **Prós:** Executável otimizado, compatibilidade com todos sistemas operacionais.  
  - **Contras:** Equipe sem nenhum background com Rust.    
  - **Motivo da Rejeição:** Curva de aprendizagem muito elevada.

**Referências:**

- [https://www.electronjs.org/docs/latest](https://www.electronjs.org/docs/latest)   
- [https://openjfx.io/javadoc/24/javafx.graphics/javafx/scene/doc-files/cssref.html](https://openjfx.io/javadoc/24/javafx.graphics/javafx/scene/doc-files/cssref.html)   
- [https://v1.tauri.app](https://v1.tauri.app) 

## 

## **ADR-003 Linguagem para o desenvolvimento back-end** {#adr-003-linguagem-para-o-desenvolvimento-back-end}

**Descrição:** A equipe da disciplina de PDS2 (Práticas de Desenvolvimento de Software 2\) se reuniu para decidir qual seria a linguagem utilizada para desenvolver o backend do sistema

**Contexto:**

- O Sistema COINS necessita de uma linguagem robusta e compatível com Electron para o desenvolvimento do backend. O Electron tem como base um ambiente Node.js, necessitando de uma linguagem que ofereça segurança, robustez para manipulação de dados financeiros e integração nativa com o ecossistema do próprio Electron. A escolha impactará diretamente a manutenibilidade, a confiabilidade dos dados e a produtividade do desenvolvimento.

**Decisão:**

- Optamos por utilizar TypeScript.

**Justificativa:**

- **Integração com o Ecossistema Node.js/Electron:** O Electron é construído sobre Node.js. TypeScript é um superconjunto (superset) do JavaScript e transpila para JavaScript puro, garantindo 100% de compatibilidade com o runtime do Node.js e com todas as APIs do Electron. Isso permite acesso direto e irrestrito a um vasto ecossistema de pacotes via NPM, manipulação de arquivos e outras funcionalidades essenciais para o backend.

- **Robustez e Segurança de Tipos:** O contexto de uma aplicação de contabilidade exige alta precisão e confiabilidade na manipulação de dados (valores monetários, transações, datas). O sistema de tipos estáticos do TypeScript mitiga uma classe inteira de erros em tempo de execução, como TypeError e undefined is not a function, que são comuns em JavaScript. Isso garante que as estruturas de dados sejam consistentes e que as operações financeiras sejam mais seguras e previsíveis, reduzindo a necessidade de validações manuais excessiva no código.

**Consequências:**

- **Positivas**

  - **Integração Simplificada:** O uso da mesma "família" de linguagens (TypeScript/JavaScript) simplifica a troca de dados e a configuração do ambiente de desenvolvimento.

  - **Redução de Bugs em Produção:** A verificação de tipos em tempo de compilação captura erros antes mesmo da execução do software, aumentando a qualidade e a confiabilidade do sistema.


- **Negativos**  
  - **Complexidade no Build:** É necessária uma etapa de transpilação (de TypeScript para JavaScript) no processo de build da aplicação. Isso adiciona uma leve complexidade ao setup inicial do projeto, que pode ser facilmente gerenciada com ferramentas como **tsc** (TypeScript Compiler) ou **esbuild**.

**Alternativas Consideradas:**

- **Javascript**  
  - **Prós:** Linguagem mais prática e facilitada.  
  - **Contras:** Sem tipagem, abrindo brechas para problemas com o contexto de contas e casting.  
  - **Motivo da Rejeição:** Necessidade de maior robustez no contexto de contabilidade.  
- **Java Spring Boot**   
  - **Prós:** Robusto, fortemente tipado e confiável.  
  - **Contras:** Alta complexidade e over engineering para o contexto.    
  - **Motivo da Rejeição:** Curva de aprendizagem muito elevada, desenvolvimento muito lento e massante para o contexto.

## **ADR-004 Framework para o desenvolvimento front-end** {#adr-004-framework-para-o-desenvolvimento-front-end}

**Descrição:** A equipe da disciplina de PDS2 (Práticas de Desenvolvimento de Software 2\) se reuniu para decidir qual seria o framework JavaScript utilizado para desenvolver a interface de usuário (frontend) do sistema.

**Contexto:**

- O Sistema COINS necessita de um framework capaz de criar interfaces reativas, suportar componentes modulares e funcionar bem dentro do ecossistema Electron.

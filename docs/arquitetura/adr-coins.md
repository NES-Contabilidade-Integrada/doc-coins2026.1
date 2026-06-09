# Registro de Decisões Arquiteturais

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
| 2.0.0 | 02/06/2026 | Adicionando ADR-008: Infraestrutura de CI/CD com GitHub Actions | Lohan Toledo Tosta |
| 2.1.0 | 02/06/2026 | Adicionando ADR-009: Testes E2E com Playwright contra executável compilado | Lohan Toledo Tosta |
| 2.2.0 | 02/06/2026 | Adicionando ADR-010: Expansão do domínio contábil — Apuração, DRE e Balanço Patrimonial | Lohan Toledo Tosta |

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

[**ADR-008 Infraestrutura de CI/CD com GitHub Actions**](#adr-008-infraestrutura-de-cicd-com-github-actions)

[**ADR-009 Testes E2E com Playwright contra Executável Compilado**](#adr-009-testes-e2e-com-playwright-contra-executável-compilado)

[**ADR-010 Expansão do Domínio Contábil — Apuração, DRE e Balanço Patrimonial**](#adr-010-expansão-do-domínio-contábil--apuração-dre-e-balanço-patrimonial)

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

- O Sistema COIN'S necessita de uma tecnologia para implementação de um sistema desktop robusto que possa ser utilizado nos laboratórios da ESAN.

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

- O Sistema COIN'S necessita de uma linguagem robusta e compatível com Electron para o desenvolvimento do backend. O Electron tem como base um ambiente Node.js, necessitando de uma linguagem que ofereça segurança, robustez para manipulação de dados financeiros e integração nativa com o ecossistema do próprio Electron. A escolha impactará diretamente a manutenibilidade, a confiabilidade dos dados e a produtividade do desenvolvimento.

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

- O Sistema COIN'S necessita de um framework capaz de criar interfaces reativas, suportar componentes modulares e funcionar bem dentro do ecossistema Electron.

---

## **ADR-008 Infraestrutura de CI/CD com GitHub Actions** {#adr-008-infraestrutura-de-cicd-com-github-actions}

**Descrição:** Com a maturidade do projeto e a adição de novos módulos de domínio, a equipe identificou a necessidade de automatizar validação de qualidade e geração de artefatos de distribuição.

**Contexto:**

- O projeto passou a contar com testes unitários (Vitest) e testes E2E (Playwright), mas sua execução era manual e suscetível a omissões.
- A geração do instalador `.exe` e a publicação de releases eram realizadas localmente, sem rastreabilidade.
- O repositório já estava hospedado no GitHub, tornando o GitHub Actions a opção de menor atrito para integração contínua.

**Decisão:**

- Adotar GitHub Actions como plataforma de CI/CD, com quatro workflows dedicados: `ci.yml`, `ci-e2e.yml`, `build-windows.yml` e `release.yml`.

**Justificativa:**

- **Integração nativa com o repositório:** O GitHub Actions é acionado diretamente por eventos do repositório (push, pull request, tags), sem configuração de webhooks externos.
- **Runners Windows disponíveis:** O Electron Forge exige um ambiente Windows para gerar o instalador `.exe`. O GitHub Actions oferece `windows-latest` como runner gerenciado, eliminando dependência de máquina local.
- **Separação de responsabilidades por workflow:** Dividir em quatro workflows (unitários, E2E, build, release) permite falha rápida e reexecução seletiva, sem necessidade de reexecutar toda a pipeline.
- **Sem custo adicional:** Para repositórios públicos, o GitHub Actions é gratuito.

**Consequências:**

- **Positivas**
  - Todo push e pull request tem qualidade verificada automaticamente antes do merge.
  - A geração do `.exe` e a publicação da release passam a ser rastreáveis e reproduzíveis.
  - Erros introduzidos por novos commits são detectados no contexto da branch, não apenas após o merge.
- **Negativas**
  - O workflow `ci-e2e.yml` tem tempo de execução elevado (compilação completa do Electron + execução do Playwright), aumentando o tempo de feedback no PR.
  - Dependência de disponibilidade dos runners gerenciados do GitHub.

**Alternativas Consideradas:**

- **Execução manual local:**
  - **Prós:** Sem custo, sem configuração.
  - **Contras:** Suscetível a omissões; sem rastreabilidade no histórico do repositório.
  - **Motivo da Rejeição:** Incompatível com o crescimento do projeto e com a cobertura de testes que passou a existir.

---

## **ADR-009 Testes E2E com Playwright contra Executável Compilado** {#adr-009-testes-e2e-com-playwright-contra-executável-compilado}

**Descrição:** O projeto precisava de uma estratégia de testes que validasse o comportamento real da aplicação desktop do ponto de vista do usuário final, incluindo a interface gráfica e a integração entre frontend, backend e banco de dados.

**Contexto:**

- Os testes unitários (Vitest) validam lógica isolada de cada service, mas não cobrem fluxos contábeis completos nem interações de UI.
- A aplicação é distribuída como executável gerado pelo Electron Forge. Testar apenas o ambiente de desenvolvimento não garante que o artefato de distribuição funciona corretamente.
- Era necessário cobrir os novos módulos (Apuração, DRE, Balanço Patrimonial) com testes de fluxo completo.

**Decisão:**

- Adotar **Playwright** como framework de testes E2E, com os testes executando contra o **executável compilado** gerado pelo Electron Forge — não contra o modo de desenvolvimento.
- Organizar os testes na pasta `playwright/` com quatro categorias: `functional/`, `integration/`, `e2e/` e `acceptance/`.

**Justificativa:**

- **Validação do artefato real:** Testar o binário compilado garante que o que é distribuído aos usuários é o mesmo que passou pela suíte de testes, eliminando divergências entre ambiente de dev e de produção.
- **Suporte a Electron:** O Playwright tem suporte oficial a aplicações Electron, permitindo lançar e interagir com o processo principal e o renderer de forma integrada.
- **Cobertura em múltiplos níveis:** A separação em `functional` (UI por módulo), `integration` (API REST), `e2e` (fluxos ponta a ponta) e `acceptance` (regras de negócio) permite identificar rapidamente em qual nível um defeito se manifesta.
- **Page Object Model (POM):** A adoção do POM na camada `playwright/pages/` desacopla os seletores de UI dos casos de teste, reduzindo custo de manutenção quando componentes mudam.

**Consequências:**

- **Positivas**
  - Defeitos que surgem apenas no executável compilado (ex: caminhos de recursos, permissões de arquivo) são detectados antes da release.
  - Novos módulos são cobertos com testes de fluxo completo, incluindo cenários contábeis reais.
- **Negativas**
  - O tempo de execução da suíte E2E é elevado, pois exige compilação completa da aplicação antes dos testes.
  - O middleware de CORS do Express precisou ser alterado para aceitar qualquer origem (`*`), pois o Playwright em modo headless faz requisições ao servidor local sem origem definida. Essa mudança é uma consequência direta desta decisão.

**Alternativas Consideradas:**

- **Testar em modo de desenvolvimento (sem compilar):**
  - **Prós:** Execução mais rápida; sem necessidade de Electron Forge no CI.
  - **Contras:** Não valida o artefato que será distribuído; pode mascarar problemas de empacotamento.
  - **Motivo da Rejeição:** O objetivo principal é garantir a qualidade do produto entregue ao usuário final.

---

## **ADR-010 Expansão do Domínio Contábil — Apuração, DRE e Balanço Patrimonial** {#adr-010-expansão-do-domínio-contábil--apuração-dre-e-balanço-patrimonial}

**Descrição:** O sistema COIN'S na v1.x cobria apenas os módulos de Plano de Contas e Lançamentos Contábeis. Para completar o ciclo contábil básico exigido pelo contexto pedagógico, foram adicionados três novos módulos de domínio.

**Contexto:**

- O fluxo contábil completo requer: registrar lançamentos → apurar o resultado → gerar DRE → gerar Balanço Patrimonial. Sem os três últimos módulos, o sistema não atendia ao objetivo pedagógico da disciplina de Ciências Contábeis.
- Cada novo módulo precisava ser representado em todas as camadas da arquitetura (migrations, entities, repositories, services, controllers, frontend pages e components), respeitando o padrão arquitetural já estabelecido.
- As migrations existentes precisavam ser reorganizadas para suportar o schema incremental dos novos módulos sem quebrar instalações existentes.

**Decisão:**

- Adicionar os módulos **Apuração**, **DRE (Demonstração do Resultado do Exercício)** e **Balanço Patrimonial** ao sistema, com representação completa em todas as camadas.
- Consolidar as 4 migrations originais em uma **migration de baseline** (`20260331195800_baseline.ts`) e adicionar migrations incrementais para cada evolução do schema.
- Para DRE e Balanço Patrimonial, **não criar repositories dedicados** — os services operam diretamente com queries, dado que esses módulos são essencialmente consultas de agregação sem estado próprio.

**Justificativa:**

- **Completude do ciclo contábil:** Os três módulos formam a sequência natural do fluxo pedagógico: apuração de resultado → demonstração → balanço.
- **Baseline de migrations:** Consolidar as migrations originais em uma única baseline simplifica a inicialização de novos ambientes e torna o histórico de schema incremental legível.
- **Ausência de repository para DRE e Balanço Patrimonial:** Esses módulos não têm entidades próprias com CRUD completo — são cálculos derivados de dados existentes. Um repository seria uma abstração sem benefício real.
- **Exportação CSV no Balanço Patrimonial:** A necessidade de exportação foi tratada como um service separado (`BalanceSheetStatementCsvService`), mantendo a responsabilidade única do service principal.

**Consequências:**

- **Positivas**
  - O sistema passa a cobrir o ciclo contábil completo, tornando-se funcionalmente completo para o contexto pedagógico.
  - A organização por módulo de domínio em todas as camadas (`Apuracao/`, `Demonstracao/`, `BalancoPatrimonial/`) mantém a coesão e facilita navegação no código.
- **Negativas**
  - O crescimento do número de camadas e arquivos aumenta o custo de onboarding de novos membros na equipe.
  - A ausência de repository em DRE e Balanço Patrimonial cria uma inconsistência de padrão em relação aos demais módulos, exigindo que futuros mantenedores entendam o motivo da diferença.

**Alternativas Consideradas:**

- **Manter repositories para todos os módulos por consistência:**
  - **Prós:** Padrão uniforme em todo o backend.
  - **Contras:** Repositories vazios ou com um único método de consulta agregada seriam apenas boilerplate sem valor real.
  - **Motivo da Rejeição:** Complexidade sem benefício no contexto atual.

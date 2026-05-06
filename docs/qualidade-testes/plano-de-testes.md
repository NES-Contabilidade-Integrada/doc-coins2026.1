# Plano de Teste E2E

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 25/03 | Criando plano Inicial com análise da situação atual | Amanda Caroline de Gois Balcaçar |
| 1.1 | 15/04 | Atualizando Conteúdo sobre o Plano | Amanda Caroline de Gois Balcaçar |
|  |  |  |  |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | 19/08 | Fulano de Tal | Aprovada |
| 1.1 | 19/08 | Fulano de Tal | Reprovada |
| 1.1.1 | 20/08 | Fulano de Tal | Resolver pendências |

**Sumário**

[1\. Introdução	2](#introdução)

[**2\. Análise da Situação Atual dos Testes	2**](#análise-da-situação-atual-dos-testes)

[3\. Objetivos dos Testes	2](#objetivos-dos-testes)

[4\. Escopo	2](#escopo)

[**5\. Tipo de Testes	2**](#tipo-de-testes)

[**6\. Estratégia de Execução	3**](#estratégia-de-execução)

[**7\. Ferramentas	4**](#ferramentas)

[🛠️ Ferramentas e Tecnologias	4](#heading=h.2jk3943i28xr)

[**8\. Organização dos Casos de Teste	5**](#organização-dos-casos-de-teste)

1. # Introdução {#introdução}
Este documento define a estratégia de validação do COIN'S. O objetivo é garantir que a lógica financeira e os fluxos de interface Electron/React funcionem conforme o esperado, utilizando uma abordagem de pirâmide de testes para assegurar a qualidade e confiabilidade dos dados.

2. # Análise da Situação Atual dos Testes {#análise-da-situação-atual-dos-testes}
Atualmente, a cobertura de testes do sistema é composta exclusivamente por testes unitários desenvolvidos com o Jest. Estes testes validam funções isoladas, cálculos e componentes do React. Identificou-se uma lacuna na validação de fluxos completos de usuário e na integração real entre o frontend (Renderer) e o backend (Main/Electron).

3. # Objetivos dos Testes {#objetivos-dos-testes}
* Validar a corretude das regras de negócio contábeis em fluxos reais.  
* Assegurar a integridade da persistência de dados no banco de dados através da interface.  
* Evitar regressões em funcionalidades críticas a cada novo deploy.

4. # Escopo {#escopo}
**Dentro do Escopo:**

* Validação de interface e navegação entre módulos (Plano de Contas, Razão, Balancete).  
* Integridade da gravação e leitura de dados no banco local.  
* Testes funcionais por módulo e testes de regressão crítica.

**Fora do Escopo (Não Prioritários):**

* Performance e Carga: Por ser um app local, o foco é a eficiência do código e não a concorrência de acessos simultâneos.  
* Rede e Latência: O executável opera majoritariamente offline ou com chamadas locais, tornando testes de latência de rede irrelevantes para este MVP.

5. # Tipo de Testes {#tipo-de-testes}
Para os testes de interface, adotamos uma separação em quatro níveis:

1. **Funcional:** Valida componentes isolados da interface (ex: o botão de salvar habilita/desabilita corretamente?).  
2. **Integração:** Valida se a interface consegue ler e gravar dados no banco local com sucesso.  
3. **Regressão:** Testes de segurança que rodam em cada alteração para garantir que funções críticas (como o cálculo do Balancete) não quebraram.  
4. **E2E:** Fluxos de negócio completos, como "Criar uma empresa e realizar o primeiro lançamento".

6. # Estratégia de Execução {#estratégia-de-execução}
A estratégia de execução é determinada automaticamente pelo sistema com base na branch em que o código está sendo enviado. Isso garante que alterações pequenas recebam feedback rápido, enquanto merges críticos passem por uma validação exaustiva.

**a. Execução Seletiva (strategy: affected)**  
Esta modalidade é ativada em branches de desenvolvimento, como Subtask/\* ou develop. O objetivo é validar apenas o que foi alterado, reduzindo o tempo de CI

1. **Detecção de Mudanças:** O script select-tests.sh executa um git diff main...HEAD para identificar quais arquivos foram modificados.  
2. **Módulos Afetados:** Se um arquivo no módulo General Journal for alterado, o CI rodará apenas os testes funcionais e de integração específicos desse módulo.  
3. **Regressão Obrigatória:** Independentemente do que foi alterado, os Testes de Regressão (validações contábeis críticas) são executados sempre, garantindo que as regras de negócio base permaneçam intactas.  
4. **Exceção de Arquivos Globais:** Se houver mudanças em arquivos "genéricos" (como Page Objects base, fixtures ou o próprio playwright.config.ts), o sistema ignora a seletividade e executa todos os testes para evitar quebras em cascata.

**b. Execução Completa (strategy: all)**  
Esta modalidade é obrigatória em branches de entrega, como main ou release-candidate.

1. **Confiança Máxima:** Todos os testes unitários (Jest), funcionais, integração, regressão e fluxos E2E completos são executados.  
2. **Pipeline de Release:** Somente após o sucesso total desta suíte é que o workflow de build (geração do executável .exe) é liberado para distribuição.

Para permitir que um aplicativo desktop (Electron) rode em servidores Linux do GitHub sem monitor, a arquitetura utiliza as seguintes ferramentas:

* **Display Virtual (Xvfb):** Como os servidores de CI não possuem tela física, o CI configura um display virtual para que o navegador (Playwright) possa renderizar a interface do COIN'S e interagir com ela.  
* **Isolamento de Ambiente:** Cada execução limpa o banco de dados e utiliza Fixtures (dados de teste controlados) para garantir que um teste não influencie o resultado do outro.  
* **Captura de Evidências:** Em caso de falha no CI, o sistema realiza automaticamente o upload de screenshots, vídeos e traces para a pasta *artifacts/*, permitindo que o desenvolvedor visualize exatamente onde o erro ocorreu na interface

7. # Ferramentas {#ferramentas}
Nesta seção, detalhamos o conjunto de ferramentas selecionado para garantir a qualidade do ciclo de vida do software, desde a lógica de negócio até a interface final.

| Jest | Teste Unitários e de Lógica |
| :---- | :---- |
| Playwright | Automação de Interface e E2E |
| GitHub Actions | Orquestração de CI |
| Xvfb | Emulador de display para servidores Linux. |

8. # Organização dos Casos de Teste {#organização-dos-casos-de-teste}
A arquitetura de testes do COIN'S utiliza uma estrutura Multicamadas, organizada por Tipo e Módulo. Essa abordagem permite que o sistema cresça sem perder a rastreabilidade e a facilidade de manutenção.

**1\. Distribuição por Tipo de Teste**  
A suíte atual conta com 19 arquivos de especificação distribuídos estrategicamente para cobrir desde interações simples até fluxos complexos:

| Tipo | Arquivo | Localização |
| :---- | :---- | :---- |
| Funcional | 14 | specs/functional/ |
| Integração | 13 | specs/integration/ |
| Regressão | 1 | specs/regression/ |
| E2E | 1 | specs/e2e/ |

**2\. Estrutura por Módulo**  
Para facilitar o desenvolvimento, os testes são agrupados pelos módulos de negócio do sistema:

* **Módulo Financeiro (Balance Sheet & Ledger):** 8 testes focados em cálculos, filtros e exibição de dados.  
* **Módulo Operacional (General Journal):** 6 testes cobrindo CRUD, validações de lançamentos e integração.  
* **Gestão (Company & Accounts):** 2 testes para configuração inicial e cadastro.  
* **Interface (Menu):** 1 teste para garantir a navegação global.  
* **Workflow (Accounting Workflow):** 1 teste de fluxo ponta a ponta (E2E).

**3\. Estrutura de Suporte (Arquitetura Técnica)**  
A organização técnica segue o padrão DRY (Don't Repeat Yourself), utilizando objetos reutilizáveis:

* **Page Objects (e2e/pages/):** 7 classes que centralizam os seletores da interface (Ex: JournalPage, CompanyPage), permitindo atualizações rápidas na UI sem quebrar múltiplos testes.  
* **Fixtures (e2e/utils/app.fixture.ts):** Scripts responsáveis pelo setup (preparação) e teardown (limpeza) do banco de dados local antes e depois de cada execução.  
* **Utils (e2e/utils/globalFunctions.ts):** Central de funções globais e auxiliares compartilhadas por toda a suíte de testes.
**Documento de Visão de Implementação**

**Histórico de Versões** 

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 28/10 | Adiciona versão inicial do documento de Visão de Implementação | Pedro Nicoletti Sotoma |
| 1.1 | 11/11 | Ajustando links do Sumário | Pedro Nicoletti Sotoma |

**Histórico de Revisões** 

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.1 | 25/11/2025 | Fernanda Pessoa | Aprovada |

**Sumário**

[1\. Introdução	1](#introdução)

[2\. Arquitetura Geral do Sistema	2](#arquitetura-geral-do-sistema)

[2.1 Arquitetura do Backend	2](#2.1-arquitetura-do-backend)

[2.2 Arquitetura do frontend	3](#2.2-arquitetura-do-frontend)

[3\. Conclusão	3](#conclusão)

1. # Introdução {#introdução}
Esse documento tem por objetivo especificar a estrutura organizacional do código-fonte do software COIN’S, desenvolvido na disciplina de Núcleo de Práticas de Engenharia de Software 2025/2.

Ele serve como um guia para a equipe de desenvolvimento, detalhando a responsabilidade de cada camada e diretório principal. O objetivo é facilitar a manutenção e a implementação de novas funcionalidades, garantindo que a estrutura do código seja preservada.

As decisões arquiteturais de alto nível estão registradas no Documento de Registro de Decisões (ADRs), e a visão geral dos componentes pode ser vista nos diagramas C4 do projeto. Este documento foca exclusivamente na Visão de Implementação.

2. # Arquitetura Geral do Sistema {#arquitetura-geral-do-sistema}
O sistema em geral é constituído por uma arquitetura monolítica modular baseada em camadas. Essa decisão foi tomada por conta do contexto de que a solução desenvolvida seria um sistema desktop offline, facilitando a integração frontend/backend/banco de dados local.  
Essa arquitetura consiste basicamente em agrupar todo o sistema em um único repositório, separando os componentes em camadas de acordo com suas responsabilidades.   
Mais adiante será detalhado como separamos nossas camadas tanto para o frontend quanto para o backend.

### 2.1 Arquitetura do Backend {#2.1-arquitetura-do-backend}
Para o backend(diretório “main”), separamos nosso código em 8 camadas principais:

* **Database:** Essa camada fica responsável por configurar o banco de dados local.  
* **Migrations:** Alinhada à database, essa camada tem como objetivo gerar as tabelas do banco de dados em conformidade com o modelo de dados do código.  
* **Seed:** Ainda sobre o banco de dados, essa camada é responsável por popular o banco com dados que devem ser instanciados assim que o sistema é gerado, ex: Plano de Contas padrão.  
* **Entities:** Essa camada é responsável por representar as tabelas do banco de dados no código.  
* **Repositories:** Essa camada é responsável por acessar e realizar operações no banco de dados  
* **Services:** Essa camada é responsável por gerenciar as regras de negócio da aplicação.  
* **Controllers:** Essa camada é responsável por disponibilizar rotas de acesso aos dados do backend para o frontend.  
* **Tests:** Essa camada basicamente engloba os testes unitários da aplicação.


### 2.2 Arquitetura do frontend {#2.2-arquitetura-do-frontend}
Para o frontend(diretório “renderer”), separamos nosso código em 4 camadas principais:

* **Components:** Essa camada fica responsável por armazenar os componentes principais e as páginas do sistema.  
* **Pages:** Essa camada fica responsável por renderizar as páginas da aplicação.  
* **Router:** Essa camada é responsável por gerenciar as rotas da aplicação.  
* **Services:** Essa camada estabelece a comunicação com o backend para retorno dos endpoints.  
* **Schemas:** Essa camada é responsável por definir as estruturas de dados que serão utilizadas nos componentes.

3. # Conclusão {#conclusão}
A arquitetura definida pelo time entrega uma estrutura robusta e organizada para o escopo do projeto, garantindo clareza no desenvolvimento e manutenção do software.  

# **Especificação de Arquitetura de Software**

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 11/11/2025 | Adicionando Primeira versão do documento  | Pedro Nicoletti Sotoma |

**Histórico de Revisões** 

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | 25/11/2025 | Fernanda Pessoa | Aprovada |

**Sumário**

[1\. Introdução	2](#introdução)

[2\. Escopo	2](#escopo)

[2.1. Restrições do sistema	2](#restrições-do-sistema)

[Framework e Plataforma	2](#framework-e-plataforma)

[Frontend	3](#frontend)

[Backend	3](#backend)

[Banco de Dados	3](#banco-de-dados)

[Padrão Arquitetural	3](#padrão-arquitetural)

[3\. Representação arquitetural	4](#representação-arquitetural)

[3.1. Nível 1 – Diagrama de Contexto	4](#nível-1-–-diagrama-de-contexto)

[3.2. Nível 2 – Diagrama de Container	4](#nível-2-–-diagrama-de-container)

[3.3. Nível 3 – Diagrama de Componentes	5](#nível-3-–-diagrama-de-componentes)

[3.4. Nível 4 – Código	5](#nível-4-–-código)

[3.5. Diagramas suplementares – Diagrama de Implantação	6](#diagramas-suplementares-–-diagrama-de-implantação)

1. ## **Introdução** {#introdução}

Este documento tem como objetivo descrever a arquitetura do Sistema COIN’S, seguindo o modelo de visualização arquitetural de software C4[^1]. 

O C4 é o padrão ideal para representar a arquitetura porque equilibra clareza, consistência e praticidade. Ele comunica o que importa em cada nível de detalhe, é simples de manter, se integra às ferramentas modernas de desenvolvimento e fortalece a governança técnica da organização.

Mesmo em um contexto de software desktop monolítico e offline, com escopo inicial pequeno, o uso do modelo C4 faz sentido por promover clareza estrutural desde o início do projeto, facilitando a evolução futura da aplicação — seja para modularização, integração online ou expansão arquitetural. Além disso, o C4 permite documentar decisões arquiteturais de forma leve e acessível, garantindo que o conhecimento do sistema não se perca com o tempo e possa ser facilmente comunicado a novos desenvolvedores ou stakeholders.

2. ## **Escopo** {#escopo}

Este documento auxilia os envolvidos no projeto a compreender os aspectos arquiteturais do sistema que são  necessários para desenvolver uma solução que atenda as necessidades do proponente. Além de auxiliar equipes futuras no entendimento do projeto.

1. ### **Restrições do sistema** {#restrições-do-sistema}

As principais restrições e decisões arquiteturais do **Sistema COIN’S** são as seguintes:

### **Framework e Plataforma** {#framework-e-plataforma}

* **Electron \+ Electron Forge**: A escolha do *Electron* foi feita para permitir o desenvolvimento de uma aplicação **desktop multiplataforma**, mantendo o mesmo código base em Windows, Linux e macOS.  
   O *Electron Forge* foi adotado para facilitar o empacotamento, distribuição e atualização do aplicativo, garantindo consistência no ciclo de build e distribuição offline.

### **Frontend** {#frontend}

* **Vue 3 com TypeScript**: Escolhido por sua **produtividade**, **reatividade nativa** e **integração simples com Electron**. O uso de TypeScript aumenta a confiabilidade do código e facilita a manutenção e refatoração futura.

### **Backend** {#backend}

* **Express.js com TypeScript**: Utilizado como camada de backend local dentro do mesmo processo do Electron, responsável por expor endpoints REST internos e centralizar a lógica de negócio.  
   Essa escolha mantém a **separação lógica entre frontend e backend**, ainda que no mesmo container, o que facilita futura migração para um modelo cliente-servidor se o sistema vier a evoluir para ambiente online.

### **Banco de Dados** {#banco-de-dados}

* **SQLite3**: O banco de dados local foi escolhido por ser **leve, embarcado e adequado ao uso offline**. Ele não requer servidor dedicado, reduzindo complexidade e facilitando a instalação.

* **Knex.js**: Biblioteca de query builder que provê **abstração de acesso ao banco**, portabilidade e migrações estruturadas, além de facilitar a manutenção do esquema de dados.

### **Padrão Arquitetural** {#padrão-arquitetural}

O sistema é formado por uma arquitetura monolítica modularizada em camadas. Essa decisão foi tomada considerando o contexto de um software offline desktop, visando a facilidade de integração entre banco/backend/frontend. O diretório “main” fica responsável por encapsular a lógica e as camadas do backend enquanto o diretório “renderer” fica responsável pelo frontend.

Para uma definição mais técnica da responsabilidade de cada camada, visualizar o documento de Visão de Implementação: [https://docs.google.com/document/d/1O2Qf1cnLYiqCjFxQCzfQZ4MwuyMp6zRecco6XBTN5NA/edit?tab=t.0](https://docs.google.com/document/d/1O2Qf1cnLYiqCjFxQCzfQZ4MwuyMp6zRecco6XBTN5NA/edit?tab=t.0) 

3. ## **Representação arquitetural** {#representação-arquitetural}

O modelo C4 considera as estruturas estáticas de um sistema de software em termos de containers (aplicativos, armazenamentos de dados, microservices, etc.), componentes e código. Também considera as pessoas que usam os sistemas de software que construímos.

1. ### **Nível 1 – Diagrama de Contexto** {#nível-1-–-diagrama-de-contexto}

O diagrama de contexto do sistema mostra o **Sistema COIN’S** e como ele se encaixa no mundo em termos das pessoas que o utilizam e dos outros sistemas de software com os quais ele interage.

**Link do diagrama (alta resolução / online):**  
 [https://app.diagrams.net/\#G1c1DKeRUihqU2T4k0uf1OzZv9n-dHTEJc\#%7B"pageId"%3A"zNMGI6wU0Mi8Qe2H5Q59"%7D](https://app.diagrams.net/#G1c1DKeRUihqU2T4k0uf1OzZv9n-dHTEJc#%7B"pageId"%3A"zNMGI6wU0Mi8Qe2H5Q59"%7D) 

O diagrama evidencia:

* O **usuário principal**, que interage diretamente com o aplicativo desktop.  
* A ausência de dependências externas (sistema **offline**).  
* O escopo restrito ao ambiente local da máquina do usuário.


  2. ### **Nível 2 – Diagrama de Container** {#nível-2-–-diagrama-de-container}

O diagrama de container detalha a estrutura interna do sistema, evidenciando os **principais containers** que o compõem:

* **Frontend (Vue \+ Electron Renderer)**: responsável pela interface gráfica e interação com o usuário.  
* **Backend Local (Express \+ TypeScript)**: lida com as regras de negócio e comunicação com o banco de dados.  
* **Banco de Dados (SQLite3)**: armazena dados localmente.  
* **Camada de Acesso a Dados (Knex)**: abstrai as operações SQL e garante consistência.

**Link do diagrama (alta resolução / online):**  
 [https://app.diagrams.net/\#G1c1DKeRUihqU2T4k0uf1OzZv9n-dHTEJc\#%7B"pageId"%3A"7UhaJ9ljh7ebol46HkWr"%7D](https://app.diagrams.net/#G1c1DKeRUihqU2T4k0uf1OzZv9n-dHTEJc#%7B"pageId"%3A"7UhaJ9ljh7ebol46HkWr"%7D) 

3. ### **Nível 3 – Diagrama de Componentes** {#nível-3-–-diagrama-de-componentes}

O diagrama de componentes amplia o container principal (aplicação desktop) e mostra os **componentes internos** que compõem a aplicação.

Entre os principais componentes:

* **Camada de UI (Vue Components)**: telas e componentes visuais.  
* **Camada de Serviços (Services Layer)**: coordena comunicação entre UI e backend.  
* **Camada de API Interna (Express Controllers)**: expõe endpoints locais.  
* **Camada de Persistência (Repositories e Models)**: implementa acesso ao banco via Knex.

**Link do diagrama (alta resolução / online):**  
 [https://app.diagrams.net/\#G1c1DKeRUihqU2T4k0uf1OzZv9n-dHTEJc\#%7B"pageId"%3A"2XVK7RYDKxdhMDquu4st"%7D](https://app.diagrams.net/#G1c1DKeRUihqU2T4k0uf1OzZv9n-dHTEJc#%7B"pageId"%3A"2XVK7RYDKxdhMDquu4st"%7D) 

4. ### **Nível 4 – Código** {#nível-4-–-código}

Neste nível, podem ser representados diagramas de classes ou entidades para os componentes mais importantes.

No caso do Sistema COIN’S, recomenda-se a elaboração de um Diagrama de Entidade-Relacionamento (DER) com base no schema do banco SQLite3, destacando tabelas, colunas e relacionamentos. 

**Link para documentação do DER:** [https://docs.google.com/document/d/1NIrxoi\_JZqYGeUrJK2uUcePTO2prriPYV1HKR5y8Hxo/edit?tab=t.0](https://docs.google.com/document/d/1NIrxoi_JZqYGeUrJK2uUcePTO2prriPYV1HKR5y8Hxo/edit?tab=t.0)  

5. ### **Diagramas suplementares – Diagrama de Implantação** {#diagramas-suplementares-–-diagrama-de-implantação}

Por se tratar de um sistema monolítico offline, não é necessário um diagrama de implantação detalhado.  
 O sistema é distribuído como um executável único via Electron Forge, contendo em si:

* A camada de frontend (Vue \+ Electron Renderer);  
* A camada de backend (Express embarcado);  
* O banco de dados SQLite3 (armazenado localmente no diretório da aplicação).

Toda a execução ocorre **no ambiente local do usuário**, sem dependência de servidores externos ou infraestrutura de rede.

[^1]: 
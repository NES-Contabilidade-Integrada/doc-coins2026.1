# Plano do Projeto

**Histórico de Edição**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 23/03/2026 |  | Elise Lissa Hasegawa |
| 1.1 | 22/04/2026 |  | Elise Lissa Hasegawa |
| 3.0 |  |  |  |
| 3.1 |  |  |  |

**Histórico de Revisão**

| Versão | Data | Autor | Observação |
| :---: | :---: | :---: | ----- |
|  |  |  | Aprovada |

**Sumário**

[1\. Introdução	3](#introdução)

[2\. Proponentes	3](#proponentes)

[3\. Escopo do Projeto	3](#escopo-do-projeto)

[2.1 Funcionalidades do MVP (Versão Inicial)	3](#2.1-funcionalidades-do-mvp-\(versão-inicial---2025.2\))

[2.2 Funcionalidades Complementares (Pós-MVP)	4](#2.2-funcionalidades-de-expansão-\(2026.1\))

[2.3 Incrementos Planejados	5](#2.3-incrementos-planejados)

[4\. Equipe e Infraestrutura	6](#equipe-e-infraestrutura)

[5\. Cronograma do Projeto	7](#cronograma-do-projeto)

[6\. Riscos	8](#riscos)

[7\. Planejamento de Gerência de Dados	8](#planejamento-de-gerência-de-dados)

[8\. Planejamento do Acompanhamento do Projeto	8](#planejamento-do-acompanhamento-do-projeto)

[9\. Planejamento da Comunicação	9](#planejamento-da-comunicação)

[10\. Ferramentas e Tecnologias de Desenvolvimento	9](#ferramentas-e-tecnologias-de-desenvolvimento)

[11\. Projeto de Interface e Interação	10](#projeto-de-interface-e-interação)

[12\. Arquitetura de Software	11](#arquitetura-de-software)

[13\. Validação, Verificação & Teste	11](#validação,-verificação-&-teste)

[14\. Análise de Viabilidade e Comprometimento	12](#análise-de-viabilidade-e-comprometimento)

## Introdução {#introdução}
Este documento apresenta o Plano de Projeto para o desenvolvimento do Sistema COIN'S (Contabilidade Integrada). O sistema tem como objetivo oferecer uma plataforma prática e didática para que os alunos dos primeiros semestres do curso de Ciências Contábeis da UFMS tenham um contato inicial com as práticas contábeis.  
Atualmente, os softwares contábeis avançados são utilizados apenas nos últimos semestres do curso. O COIN'S busca preencher essa lacuna, proporcionando aos alunos uma experiência introdutória que facilita a compreensão dos conceitos básicos e serve como motivação para o aprendizado contínuo.

## Proponentes {#proponentes}
Os proponentes são os responsáveis por solicitar, validar e acompanhar o desenvolvimento do Sistema COIN'S ao longo do semestre, atuando como representantes do curso de Ciências Contábeis e garantindo alinhamento acadêmico-pedagógico do projeto.

| Nome | Telefone | E-mail |
| :---- | :---- | :---- |
| Professor Robert Espejo | \+55 67 8137-9154 | robert.espejo@ufms.br |
| Aluno Jean Pleutim | \+55 67 9208-3908 | jean\_pleutim@ufms.br |

## Escopo do Projeto {#escopo-do-projeto}
O escopo do Sistema COIN'S define as funcionalidades que serão desenvolvidas ao longo do projeto, seguindo um plano incremental baseado na priorização definida durante a entrevista com o proponente. O desenvolvimento será dividido em etapas, dando continuidade à implementação do sistema que iniciou em 2025\.

### 2.1 Funcionalidades do MVP (Versão Inicial - 2025.2)

As funcionalidades essenciais que compõem o MVP são:

* **Exibição do Plano de Contas Padrão:** Disponibilizar um plano de contas pré-definido para consulta pelos usuários.  
* **Gerenciamento de Lançamentos Contábeis:** Permitir o cadastro, edição, exclusão e consulta dos lançamentos contábeis seguindo o Plano de Contas Padrão.  
* **Visualização de Lançamentos no Livro Diário:** Exibir, de forma organizada, todos os lançamentos registrados no sistema.

| Épico | Funcionalidade | Link de Acesso | Status |
| :---- | :---- | :---- | :---- |
| Épico 1 \- Plano de Contas | Exibição do Plano de Contas Padrão | [https://github.com/NES-Contabilidade-Integrada/coins/issues/11](https://github.com/NES-Contabilidade-Integrada/coins/issues/11)  | Implementado Anteriormente |
| Épico 2 \- Empresa | Gerenciamento de Lançamentos Contábeis | [https://github.com/NES-Contabilidade-Integrada/coins/issues/12](https://github.com/NES-Contabilidade-Integrada/coins/issues/12)  | Implementado Anteriormente |
| Épico 2 \- Empresa | Visualização de Lançamentos no Livro Diário | [https://github.com/NES-Contabilidade-Integrada/coins/issues/12](https://github.com/NES-Contabilidade-Integrada/coins/issues/12)  | Implementado Anteriormente |


### 2.2 Funcionalidades de Expansão (2026.1)

As funcionalidades complementares agregam valor ao sistema e serão desenvolvidas após a entrega do MVP:

* **Transferência Automática para o Livro Razão:** Realizar a movimentação dos lançamentos do Livro Diário para o Livro Razão.  
* **Geração do Balancete de Verificação:** Permitir a conferência dos saldos contábeis por meio da exibição do balancete detalhado em tela.  
* **Apuração do Resultado do Exercício:** Calcular automaticamente o resultado do exercício com base nos dados registrados e apresentar o resultado final na interface do sistema.  
* **Geração da Demonstração do Resultado do Exercício (DRE)**: Criar automaticamente o demonstrativo de resultados com base nos lançamentos contábeis e exibi-lo de forma estruturada em tela.  
* **Geração do Balanço Patrimonial**: Elaborar o balanço patrimonial de forma automatizada a partir dos dados registrados e apresentá-lo visualmente na interface.  
* **Exportação de Relatórios Contábeis**: Permitir a exportação dos demonstrativos e relatórios para formatos compatíveis (ex.: PDF, XLSX).


| Épico | Funcionalidade | Link de Acesso | Status |
| :---- | :---- | :---- | :---- |
| Épico 3 \- Livro Razão | Transferência para o Livro Razão | [https://github.com/NES-Contabilidade-Integrada/coins/issues/87](https://github.com/NES-Contabilidade-Integrada/coins/issues/87)  | Implementado Anteriormente |
| Épico 4 \- Balancete de Verificação | Geração do Balancete de Verificação | [https://github.com/NES-Contabilidade-Integrada/coins/issues/38](https://github.com/NES-Contabilidade-Integrada/coins/issues/38)  | Implementado Anteriormente |
| Não existente | Apuração do Resultado do Exercício | Não existente | Implementado na Sprint 1 |
| Não existente | Geração da Demonstração do Resultado do Exercício (DRE) | Não existente | A ser implementado |
| Não existente | Geração do Balanço Patrimonial | Não existente | A ser implementado |
| Não existente | Exportação de Relatórios Contábeis | Não existente | Próximas versões |

### 2.3 Incrementos Planejados

Os incrementos planejados consistem em funcionalidades adicionais previstas para versões futuras, visando ampliar a flexibilidade e a interatividade do sistema:

* **Gerenciamento Personalizado de Contas:** Permitir a inclusão, edição e exclusão de novas contas no plano contábil de acordo com a necessidade do usuário, sem alterar as contas estáticas do plano.  
* **Importação e Exportação de Dados Empresariais:** Facilitar a integração de dados com outros sistemas por meio da importação e exportação de informações das empresas.  
* **Gerenciamento de Empresas:** Cadastrar, atualizar, listar e excluir dados de empresas no sistema.

| Épico | Funcionalidade | Link de Acesso | Status |
| :---- | :---- | :---- | :---- |
| Não existente | Gerenciamento Personalizado de Contas | Não existente | Próximas versões |
| Não existente | Importação e Exportação de Dados Empresariais | Não existente | Próximas versões |
| Não existente | Gerenciamento de Empresas | Não existente | Próximas versões |

## Equipe e Infraestrutura {#equipe-e-infraestrutura}
   

| Papel | Responsável Primário | Responsável Secundário | Contato |
| :---: | :---: | :---: | :---: |
| Gerente de Projetos | Fernanda Pessoa | \- | [fernanda\_pessoa@ufms.br](mailto:fernanda_pessoa@ufms.br),  |
| Analista de Requisitos | Fernanda Pessoa,  Elise Lissa Hasegawa |  | [fernanda\_pessoa@ufms.br](mailto:fernanda_pessoa@ufms.br),  [hasegawa\_lissa@ufms.br](mailto:hasegawa_lissa@ufms.br) |
| Analista de Qualidade/Tester | Amanda Gois,  Elise Lissa Hasegawa | Eduardo Alves | [amanda.gois@ufms.br](mailto:amanda.gois@ufms.br),  [hasegawa\_lissa@ufms.br](mailto:hasegawa_lissa@ufms.br), [eduardo.h.alves@ufms.br](mailto:eduardo.h.alves@ufms.br)  |
| IHC | Amanda Gois,  Elise Lissa Hasegawa | Fernanda Pessoa | [amanda.gois@ufms.br](mailto:amanda.gois@ufms.br),  [hasegawa\_lissa@ufms.br](mailto:hasegawa_lissa@ufms.br), [fernanda\_pessoa@ufms.br](mailto:fernanda_pessoa@ufms.br) |
| Arquiteto de Software | Lohan Toledo | Vinicius Carneiro | [lohan.toledo@ufms.br](mailto:lohan.toledo@ufms.br), [vinicius.aguiar@ufms.br](mailto:vinicius.aguiar@ufms.br) |
| Desenvolvedor Back-End | Vinicius Carneiro |  | [vinicius.aguiar@ufms.br](mailto:vinicius.aguiar@ufms.br) |
| Desenvolvedor Front-End |  | Amanda Gois | [amanda.gois@ufms.br](mailto:amanda.gois@ufms.br)  |
| Desenvolvedor Full-Stack | Eduardo Alves, Lohan Toledo |  | [eduardo.h.alves@ufms.br](mailto:eduardo.h.alves@ufms.br), [lohan.toledo@ufms.br](mailto:lohan.toledo@ufms.br) |
| DevOps | Amanda Gois | Vinicius Carneiro | [amanda.gois@ufms.br](mailto:amanda.gois@ufms.br), [vinicius.aguiar@ufms.br](mailto:vinicius.aguiar@ufms.br) |
| Banco de Dados | Lohan Toledo, Vinicius Carneiro |  | [lohan.toledo@ufms.br](mailto:lohan.toledo@ufms.br), [vinicius.aguiar@ufms.br](mailto:vinicius.aguiar@ufms.br) |

## Cronograma do Projeto {#cronograma-do-projeto}
   

| Sprint | Período | Funcionalidade | Feature |
| :---- | :---- | :---- | :---- |
| Sprint 0 | 02 a 26/03 | Levantamento de requisitos e resolução de bugs. |   |
| Sprint 1 | 30/03 a 16/04 | Apuração do Resultado do Exercício |  |
| Sprint 2 | 22/04 a 11/05 | Geração da Demonstração do Resultado do Exercício (DRE) |  |
| Sprint 3 | 12/05 a 01/06 | Geração do Balanço Patrimonial  |  |

 


## Riscos {#riscos}
   Por se tratar de um sistema educacional orientado a aprendizado, não foram identificados riscos críticos relacionados a impacto financeiro, regulatório ou corporativo. Os principais riscos são associados à expectativa dos proponentes, continuidade acadêmica e disponibilidade da equipe.  
   

## Planejamento de Gerência de Dados {#planejamento-de-gerência-de-dados}
     
   Os artefatos e código do projeto estão armazenados em:  
     
* Repositório GitHub: [https://github.com/NES-Contabilidade-Integrada/coins2026.1](https://github.com/NES-Contabilidade-Integrada/coins2026.1)  
* Board de tarefas (Projects): dentro do repositório  
* Repositório de documentos (Google Drive): [https://drive.google.com/drive/folders/1dSzfMOYWT6Y\_vLQtLixwUQxB1kRvvvQ1](https://drive.google.com/drive/folders/1dSzfMOYWT6Y_vLQtLixwUQxB1kRvvvQ1)   
* Documentação com MKdocs: [https://nes-contabilidade-integrada.github.io/doc-coins2026.1/](https://nes-contabilidade-integrada.github.io/doc-coins2026.1/)  
  


## Planejamento do Acompanhamento do Projeto {#planejamento-do-acompanhamento-do-projeto}
   

* Dailies seguindo o Scrum  
* Reunião semanal de acompanhamento com a orientadora Vanessa Borges.  
* Sprint Planning ao início de cada sprint e método planning poker para estimar tempo  
* Sprint Review com proponentes e orientadora para apresentação das atividades desenvolvidas  
* Retrospectiva ao final de cada Sprint via Miro: [https://miro.com/app/board/uXjVGicFlCo=/](https://miro.com/app/board/uXjVGicFlCo=/)  
    
  Critérios para replanejamento:  
* Atrasos superiores a 20% do esforço previsto.  
* Mudanças significativas no escopo.  
* Impedimentos técnicos que prejudiquem os marcos do projeto.  
  


## Planejamento da Comunicação {#planejamento-da-comunicação}
     
   Nesta seção é descrito o plano de comunicação do projeto, conforme as definições da Tabela 6\. Para cada comunicação relevante, o responsável por realizá-la, assim como seu meio e momento de realização são definidos.  
   

| Comunicação | Responsável | Canal de Comunicação | Momento da Comunicação |
| :---- | :---- | :---- | :---- |
| Revisão de PR | Devs | Discord | Momento da abertura |
| Atualização de entregas | Gerente de Projetos | Google Meet | Ao final de cada Sprint |
| Alinhamento de informações/dúvidas com proponentes | Gerente de Projetos (participação de demais membros permitida) | WhatsApp (grupo dos proponentes) | Conforme necessidade |
| Reunião semanal | Equipe \+ Orientadora | Presencial / Meet | Quinta-feira |
| Comunicação de impedimentos | Qualquer membro | WhatsApp do time | Imediato |
| Registro de tarefas | Equipe | GitHub Projects | Contínuo |

   

   

## Ferramentas e Tecnologias de Desenvolvimento {#ferramentas-e-tecnologias-de-desenvolvimento}
| Categoria | Ferramenta | Justificativa |
| :---- | :---- | :---- |
| Controle de Versão | GitHub | Utilizado para versionamento do código, colaboração entre a equipe e integração com GitHub Projects. |
| Gerenciamento de Tarefas | GitHub Projects | Organização do fluxo de trabalho, acompanhamento das sprints e priorização das entregas. |
| Prototipação | Figma | Permite criar protótipos de interface, validar fluxos e coletar feedback do cliente. |
| Linguagem Backend | TypeScript | Oferece tipagem estática, maior segurança no desenvolvimento e padronização do código do backend. |
| Linguagem FrontEnd | TypeScript | Mantém consistência tecnológica entre front e back, e melhora manutenção do código do Vue. |
| Framework Desktop | Electron | Utilizado para construir aplicações desktop multiplataforma usando tecnologias web. |
| Framework FrontEnd | Vue | Facilita a construção de interfaces reativas e escaláveis, além de possuir curva de aprendizado suave para prototipagem rápida. |
| Framework BackEnd | Express | Framework minimalista e eficiente para criar APIs REST de forma rápida e modular. |
| Banco de Dados | SQLite  | Banco local simples, leve e adequado ao propósito educacional do sistema |
| Sprint Retrospective | Miro | Utilizado para conduzir retrospectivas visuais e colaborativas, facilitando discussões da equipe. |

### 9.1 Preparação do Ambiente de Desenvolvimento

    O COIN’S é um aplicativo desktop, executado localmente. Para executar o sistema, basta seguir o passo a passo descrito no arquivo README.md do repositório oficial: 

    [https://github.com/NES-Contabilidade-Integrada/coins/blob/main/README.md](https://github.com/NES-Contabilidade-Integrada/coins/blob/main/README.md) 

    

    Link da geração do executável:

    [https://docs.google.com/document/d/1b\_eht1n-qZuhE2UQDKL7gDRMEorrpAL0xdJHC\_dhaDc/edit?usp=drive\_link](https://docs.google.com/document/d/1b_eht1n-qZuhE2UQDKL7gDRMEorrpAL0xdJHC_dhaDc/edit?usp=drive_link) 

    

## Projeto de Interface e Interação {#projeto-de-interface-e-interação}
    Os protótipos de interface foram desenvolvidos no Figma e validados com os proponentes ao longo das sprints. Estes protótipos serviram como base para a construção das telas do sistema. Além disso, antes de serem criados protótipos, trabalhamos com Sketchs (esboços a mão) para validar as ideias iniciais.   
      
    Sketchs disponíveis em: [https://drive.google.com/drive/folders/16aMUyvXe49CFAoiDYZO-J0BOQJ\_HPYPh?usp=sharing](https://drive.google.com/drive/folders/16aMUyvXe49CFAoiDYZO-J0BOQJ_HPYPh?usp=sharing)   
      
    Protótipos disponíveis em:  
    [https://www.figma.com/design/Z3hfLoenhr73I3u5BRU5lP/COIN-S---Contabilidade-Integrada?node-id=199-2979\&t=s9hH0eGFNNkmnlwo-1](https://www.figma.com/design/Z3hfLoenhr73I3u5BRU5lP/COIN-S---Contabilidade-Integrada?node-id=199-2979&t=s9hH0eGFNNkmnlwo-1)  
      
    O processo de prototipação e validação  segue o fluxo definido em BPMN, garantindo clareza no de validação com os proponentes.  
      
    Modelo BPMN do fluxo de interação:  
    [https://drive.google.com/drive/folders/1HkFLJtOT9pKymSfiwGUwvJVbgP38gO9e](https://drive.google.com/drive/folders/1HkFLJtOT9pKymSfiwGUwvJVbgP38gO9e)   
    

## Arquitetura de Software {#arquitetura-de-software}
    A arquitetura do Sistema COIN’S está detalhada no artefato específico dedicado à Arquitetura de Software, que descreve os componentes, camadas, interações e decisões arquiteturais adotadas.  
    Este plano de projeto apenas referencia esse documento como a fonte oficial das definições arquiteturais.  
      
    Documentação completa disponível em: [https://docs.google.com/document/d/14JxRcIGH7QDPQTHxo652JSl\_OJUCMZCo/edit?usp=drive\_link\&ouid=108261102528406926829\&rtpof=true\&sd=true](https://docs.google.com/document/d/14JxRcIGH7QDPQTHxo652JSl_OJUCMZCo/edit?usp=drive_link&ouid=108261102528406926829&rtpof=true&sd=true)   
    

## Validação, Verificação & Teste {#validação,-verificação-&-teste}
      
    A estratégia de Validação e Verificação do Sistema COIN’S foi definida para garantir que todas as funcionalidades atendam aos requisitos especificados e que o sistema opere de forma estável, coerente e alinhada ao objetivo educacional do projeto.  
    Os artefatos oficiais de teste estão distribuídos da seguinte forma:  
      
    **Plano de testes:**   
    Documento que descreve a estratégia geral de testes, tipos aplicados, critérios de entrada/saída e abordagem adotada.   
    [Plano do Projeto](https://docs.google.com/document/d/1XogaSN2T2aq22X2BNMwlFlzndOfwDwhcQEkXrJsNhKw/edit?usp=sharing)  
      
    **Matriz de rastreabilidade:**   
    Responsável por mapear requisitos funcionais aos casos de teste e às evidências de execução, garantindo rastreabilidade completa entre o escopo e as validações.   
      
    **Casos de teste:**  
    	Testes E2E com Playwright.  
    [Casos de teste - E2E](https://docs.google.com/document/d/1_fC4yM7P6VXOWBw06KzTC0eE3m--QW6s4Vxe3CA8QaQ/edit?usp=sharing)  
      
    **Issues registradas no Github:**  
    Os bugs foram registradas como Issues no GitHub, sendo visualizadas com o filtro *is:issue type:Bug*  
    [https://github.com/orgs/NES-Contabilidade-Integrada/projects/9/views/1](https://github.com/orgs/NES-Contabilidade-Integrada/projects/9/views/1)   
    

## Análise de Viabilidade e Comprometimento {#análise-de-viabilidade-e-comprometimento}
    Nesta seção é feito o registro da análise de viabilidade do projeto. A Tabela 8 apresenta cada aspecto avaliado e o resultado da análise.  
      
    

| Aspecto | É viável? | Justificativa |
| :---- | :---- | :---- |
| Técnico | Sim | A equipe está disposta a aprender as tecnologias utilizadas, caso ainda não as domine (Electron, TypeScript, Vue, Express, SQLite). Todas as ferramentas são amplamente documentadas, gratuitas e adequadas ao contexto acadêmico. O escopo planejado é factível dentro das restrições de tempo e recursos disponíveis. |
| Comercial | Sim | O produto atende a uma necessidade real da comunidade acadêmica, proporcionando aos alunos de Ciências Contábeis contato inicial com práticas contábeis. Tem potencial de uso em disciplinas iniciais e projetos de extensão. |
| Legal | Sim | O sistema não lida com dados sensíveis reais, não viola normas regulatórias e segue boas práticas de registro contábil educacional. Não há qualquer funcionalidade que infrinja leis ou regulamentações vigentes. |

    

    Com base na análise apresentada, o projeto COIN’S é considerado totalmente viável nos aspectos técnico, comercial e legal.

    Dessa forma, todos os membros do projeto consideram o plano aqui descrito aprovado.
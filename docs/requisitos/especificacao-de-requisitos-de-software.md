# Especificação de Requisitos de Software

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | ----- | :---: |
| 1.0 | 25/08/2025 | Adiciona base dos requisitos funcionais | Fernanda Pessoa |
| 1.1 | 03/09/2025 | Atualiza requisitos funcionais do RF-01 ao RF-06 | Fernanda Pessoa |
| 1.2 | 22/09/2025 | Adição do requisito de Limpar dados da Empresa  | Fernanda Pessoa |
| 1.3 | 21/10/2025 | Adição de referências aos Módulos para cada requisito | Jerfferson Júnior |
| 2.0 | 22/10/2025 | Documento em geral: atualizada a estrutura da documentação \- agora a documentação das funcionalidades está alinhada com a hierarquia das informações do sistema; Retirada de critérios de aceite relacionados à responsividade, tendo em vista que este faz parte de requisitos não funcionais de usabilidade do sistema. RF-01: reestruturação completa do RF considerando a retirada do plano de contas do menu principal; Referência as abas de funcionalidades adicionada ao CA-3. RF-03: Reformulação focada na adição do plano de contas como mais uma funcionalidade, retirada da contagem de funcionalidades no CA-1 considerando a expansão futura (agora são apenas listadas as funcionalidades existentes). | Jerfferson Júnior |
| 3.0 | 23/10/2025 | Adição de Requisitos Funcionais referentes ao Balancete | Fernanda Pessoa |
| 4.0 | 27/10 | Adição de Requisitos não funcionais | Fernanda Pessoa |
| 4.1 | 16/11 | Adição do RNF de responsividade | Fernanda Pessoa |
| 4.2 | 17/11 | Migração dos Conceitos para Glossário de Termos | Fernanda Pessoa |
| 4.3 | 25/11 | Correções de alinhamento, adição de link para Glossário de Termos | Jerfferson Júnior |
| 4.4 | 08/04 | Adição dos RFs de Apuração do Resultado do Exercício (ARE) | Elise Lissa Hasegawa  |
| 4.5 |  | Adição dos RFs da Demonstração do Resultado do Exercício (DRE) | Fernanda Pessoa  |
| 4.6 | 06/05/2026 | Refatoração completa dos RFs de Apuração (RF-012 a RF-021) com estrutura clara baseada em boas práticas;<br/>Adição completa dos RFs de DRE (RF-022 a RF-034) com requisitos granulares seguindo hierarquia de cálculo;<br/>Atualização de módulos e aplicação consistente de boas práticas de formatação Markdown | Fernanda Pessoa |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.2 | 25/09/2025 | Jerfferson Júnior | Aprovada |
| 3.0 | 30/10/2025 | Jerfferson Júnior | Aprovada |
| 4.2 | 25/11/2025 | Jerfferson Júnior | Aprovada |

**Sumário**

- [1. Introdução](#introdução)
- [2. Classes de Usuários](#classes-de-usuários)
- [3. Definição de conceitos](#definição-de-conceitos)
- [4. Módulos](#módulos)
- [5. Modelo dos Requisitos Funcionais](#modelo-dos-requisitos-funcionais)
- [6. Requisitos de Software](#requisitos-de-software)
    - [6.1. Requisitos Funcionais](#requisitos-funcionais)
        - [6.1.1. Menu](#menu)
            - [RF-01 Exibir Menu Principal](#exibir-menu-principal)
        - [6.1.2. Empresas](#empresas)
            - [6.1.2.1. Estrutura da Empresa](#estrutura-da-empresa)
                - [RF-02 Exibir Empresa Estática](#exibir-empresa-estática)
                - [RF-03 Exibir Abas de Funcionalidades da Empresa](#exibir-abas-de-funcionalidades-da-empresa)
            - [6.1.2.2. Plano de Contas](#plano-de-contas)
                - [RF-04 Exibir Plano de Contas Padrão](#exibir-plano-de-contas-padrão)
        - [6.1.3. Livro Diário](#livro-diário)
            - [RF-05 Gerenciar Lançamento Contábil](#gerenciar-lançamento-contábil)
            - [RF-06 Listar Lançamentos Contábeis no Livro Diário](#listar-lançamentos-contábeis-no-livro-diário)
            - [RF-07 Deletar dados da Empresa](#deletar-dados-da-empresa)
        - [6.1.4. Livro Razão](#livro-razão)
            - [RF-08 Exibir Livro Razão](#exibir-livro-razão)
        - [6.1.5. Balancete](#balancete)
            - [RF-09 Aplicar Filtros do Balancete](#aplicar-filtros-do-balancete)
            - [RF-010 Exibir Balancete de Verificação](#exibir-balancete-de-verificação)
            - [RF-011 Exibir Resumo do Balancete](#exibir-resumo-do-balancete)
        - [6.1.6. Apuração do Resultado](#apuração-do-resultado)
            - [RF-012 Filtrar Data da Apuração](#filtrar-data-da-apuração)
            - [RF-013 Exibir Resumo do Resultado](#exibir-resumo-do-resultado)
            - [RF-014 Exibir Contas de Resultado](#exibir-contas-de-resultado)
            - [RF-015 Exibir Lançamentos de Encerramento](#exibir-lançamentos-de-encerramento)
            - [RF-016 Exibir Confronto da Apuração](#exibir-confronto-da-apuração)
            - [RF-017 Exibir Transferência do Resultado](#exibir-transferência-do-resultado)
            - [RF-018 Exibir Resultado Final](#exibir-resultado-final)
            - [RF-019 Realizar Apuração](#realizar-apuração)
            - [RF-020 Exibir Histórico de Apurações](#exibir-histórico-de-apurações)
            - [RF-021 Desfazer Última Apuração](#desfazer-última-apuração)
        - [6.1.7. Demonstração do Resultado do Exercício](#demonstração-do-resultado-do-exercício)
            - [RF-022 Filtrar Período da DRE](#filtrar-período-da-dre)
            - [RF-023 Exibir Receita Bruta](#exibir-receita-bruta)
            - [RF-024 Exibir Deduções da Receita](#exibir-deduções-da-receita)
            - [RF-025 Calcular e Exibir Receita Líquida](#calcular-e-exibir-receita-líquida)
            - [RF-026 Exibir CMV / CPV](#exibir-cmv--cpv)
            - [RF-027 Calcular e Exibir Lucro Bruto](#calcular-e-exibir-lucro-bruto)
            - [RF-028 Exibir Despesas Operacionais](#exibir-despesas-operacionais)
            - [RF-029 Exibir Outras Receitas/Despesas Operacionais](#exibir-outras-receitas-despesas-operacionais)
            - [RF-030 Calcular e Exibir LAJIR](#calcular-e-exibir-lajir)
            - [RF-031 Exibir Resultado Financeiro](#exibir-resultado-financeiro)
            - [RF-032 Calcular e Exibir LAIR](#calcular-e-exibir-lair)
            - [RF-033 Exibir Resultado Não Operacional](#exibir-resultado-não-operacional)
            - [RF-034 Calcular Resultado Antes dos Impostos](#calcular-resultado-antes-dos-impostos)
            - [RF-035 Exibir Impostos sobre o Lucro](#exibir-impostos-sobre-o-lucro)
            - [RF-036 Calcular e Exibir Lucro Líquido](#calcular-e-exibir-lucro-líquido)
            - [RF-037 Exibir Composição das Contas da DRE](#exibir-composição-das-contas-da-dre)
    - [6.2. Requisitos Não-Funcionais](#requisitos-não-funcionais)
        - [Compatibilidade](#compatibilidade)
        - [Portabilidade](#portabilidade)
        - [Desempenho](#desempenho)
        - [Armazenamento](#armazenamento)
        - [Disponibilidade](#disponibilidade)
        - [Responsividade](#responsividade)

## Introdução {#introdução}
   

Este documento apresenta a Especificação de Requisitos de Software (ERS) do Sistema COIN’S – Contabilidade Integrada. O sistema tem como objetivo oferecer uma plataforma prática, didática e acessível para que os alunos dos primeiros semestres do curso de Ciências Contábeis da UFMS tenham um contato inicial com as atividades fundamentais do processo contábil.  
Enquanto softwares contábeis profissionais — amplamente utilizados no mercado e introduzidos apenas nos semestres avançados do curso — exigem conhecimento prévio e maior maturidade técnica, o COIN’S preenche uma lacuna essencial ao permitir que os estudantes vivenciem práticas contábeis semelhantes às do mundo real, mas em um ambiente simplificado e focado na aprendizagem.  
No COIN’S, os alunos realizam lançamentos contábeis alinhados ao Plano de Contas, registram movimentações no Livro Diário, consultam informações no Livro Razão e geram relatórios estruturados, como o Balancete de Verificação, Balancete Consolidado e Demonstração do Resultado do Exercício (DRE). Dessa forma, compreendem como os dados são registrados, organizados e transformados em informações relevantes para análise contábil, desenvolvendo desde cedo uma visão prática e aplicada da disciplina.

## Classes de Usuários {#classes-de-usuários}
   

	No Sistema COINS, foram identificadas duas classes de usuários relevantes: **Aluno** e **Professor**. Ambas utilizam o sistema com o mesmo conjunto de funcionalidades, sem distinção de permissões ou papéis nesta versão. A Tabela 1 apresenta suas responsabilidades, restrições de acesso e características típicas.

| Classe | Responsabilidades principais | Restrições de acesso | Características típicas |
| :---- | :---- | :---- | :---- |
| Aluno | Registrar lançamentos, consultar livros (Diário/Razão), gerar/exibir relatórios (Balancete, DRE, Balanço) | Não há distinções | Usuário iniciante; conhecimento técnico básico |
| Professor | Registrar lançamentos, consultar livros (Diário/Razão), gerar/exibir relatórios (Balancete, DRE, Balanço) | Não há distinções | Usa o sistema para fins didáticos/demonstração |

## Definição de conceitos {#definição-de-conceitos}
Os conceitos utilizados neste documento estão consolidados no Glossário de Termos do Sistema COIN’S (Contabilidade Integrada): [Glossario de Termos](https://docs.google.com/document/d/1fWNvAuHWdnDFCu3-luM2oZ-49I2bVVsvHIz6awT9p3g/edit?usp=sharing)  
Para evitar redundâncias e facilitar a manutenção da documentação, este documento apenas referencia o glossário como fonte única de definições.  
Os principais termos de domínio utilizados na especificação de requisitos incluem (consultar definições no Glossário de Termos):

* Apuração do Resultado do Exercício  
* Balancete de Verificação  
* Balanço Patrimonial  
* Conta Analítica  
* Conta Contábil  
* Conta Sintética  
* Demonstração do Resultado do Exercício (DRE)  
* Lançamento Contábil  
* Livro Diário  
* Livro Razão  
* Plano de Contas  
* Razão Social


## Módulos {#módulos}
A seção de Módulos apresenta uma visão macro das grandes funcionalidades do sistema e serve como base de rastreabilidade para os Requisitos Funcionais descritos posteriormente. Cada requisito está vinculado ao módulo correspondente, permitindo rastrear a relação entre funcionalidades detalhadas e seus objetivos de alto nível.

| Módulo 1 | Plano de Contas |
| :---: | :---: |
| **Módulo 2** | Empresa |
| **Módulo 3** | Livro Razão |
| **Módulo 4** | Balancete de Verificação |
| **Módulo 5** | Apuração do Resultado |
| **Módulo 6** | Demonstração do Resultado do Exercício |

## Modelo dos Requisitos Funcionais {#modelo-dos-requisitos-funcionais}
O seguinte exemplo demonstra o modelo adotado para os requisitos funcionais. O uso foi especificado no documento [Fundamento da Estrutura dos Requisitos](https://docs.google.com/document/u/0/d/1eAsVxnGFQnY8Fp2fKZukeNej2aNxZxu0_dLkIjcqvxE/edit).

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Nome do Requisito Funcional</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 1</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">Descrição do Requisito.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> Critérios de Aceite do Requisito.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>EX- 1.</strong> [CA-1] Exceções do Critério de Aceite.</td></tr>
</tbody>
</table>

Modelo de Especificação - Requisitos Funcionais.

## Requisitos de Software {#requisitos-de-software}
Esta seção descreve os requisitos que definem o comportamento e as características do sistema COIN’S (Contabilidade Integrada). Os requisitos foram organizados em duas categorias: Requisitos Funcionais, que descrevem o que o sistema deve fazer, e Requisitos Não-Funcionais, que especificam restrições e qualidades esperadas. Cada requisito funcional está associado a um Módulo, de forma a manter a rastreabilidade entre as funcionalidades e os objetivos do projeto.

### Requisitos Funcionais {#requisitos-funcionais}
Os requisitos funcionais descrevem as funcionalidades que o sistema deve oferecer para atender às necessidades dos usuários. Eles estão organizados por seções que correspondem aos principais módulos do sistema: Menu, Empresas, Plano de Contas, Livro Diário, Livro Razão, Balancete, Apuração do Resultado e Demonstração do Resultado do Exercício. Cada requisito segue o padrão definido no modelo apresentado anteriormente, contendo sua descrição, critérios de aceite e exceções associadas aos critérios especificados.

#### Menu {#menu}
Esta subseção apresenta os requisitos relacionados à navegação do sistema. O menu é o ponto central de acesso às funcionalidades, permitindo ao usuário visualizar as opções disponíveis e alternar entre diferentes seções de forma intuitiva e consistente. 

##### RF-01 Exibir Menu Principal {#exibir-menu-principal}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Menu Principal</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 1</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir um menu principal fixo que permita a navegação entre as funcionalidades principais. Esse menu deve conter a seção de Empresas, contendo subopções expansíveis. Dentro da seção Empresas, o sistema deve exibir subopções referentes às empresas cadastradas no sistema, incluindo a empresa estática previamente cadastrada.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O menu principal deve exibir a seção "Empresas".</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> A seção "Empresas" deve conter as subopções com o nome das empresas cadastradas (razão social).</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Ao selecionar uma empresa cadastrada, o sistema deve exibir a tela referente à empresa com suas informações (Nome e CNPJ), bem como as abas de funcionalidades disponíveis [<a href="#exibir-abas-de-funcionalidades-da-empresa">RF-03 – Exibir Abas de Funcionalidades da Empresa</a>].</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> O menu deve iniciar contendo uma empresa previamente cadastrada, estática, utilizada como base para realizar os lançamentos contábeis no sistema [<a href="#exibir-empresa-estática">RF-02 – Exibir Empresa Estática</a>].</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> O menu deve destacar visualmente a seção e a subopção ativa, indicando ao usuário onde ele está navegando.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> O menu deve permanecer acessível durante a navegação entre telas.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

#### Empresas {#empresas}
##### Estrutura da Empresa {#estrutura-da-empresa}
      

Esta subseção detalha os requisitos referentes à visualização de informações e acesso às funcionalidades para as empresas cadastradas no sistema. O objetivo é fornecer ao usuário uma visão informativa e padronizada das empresas utilizadas nos lançamentos contábeis, assegurando consistência e similaridade com práticas reais. Além disso, permite a navegação entre as diferentes funcionalidades oferecidas para a realização de operações contábeis em uma determinada empresa.

##### RF-02 Exibir Empresa Estática {#exibir-empresa-estática}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;"><a href="#exibir-empresa-estática">Exibir Empresa Estática</a></th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 2</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário visualize uma empresa previamente cadastrada, utilizada como base para realizar os lançamentos contábeis. Essa empresa será a primeira subopção da seção "Empresas", exibida de forma estática e sem permitir alteração de informações (Nome e CNPJ) por parte do usuário.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O nome da empresa exibida deve corresponder à empresa previamente cadastrada no sistema.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> O CNPJ exibido deve corresponder ao CNPJ da empresa previamente cadastrada.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> As informações da empresa devem ser exibidas no formato padronizado: Nome: "Nome da Empresa". CNPJ: "CNPJ: 00.000.000/0000-00".</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> O usuário não deve ser capaz de incluir, alterar ou remover as informações dessa empresa estática.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> As informações da empresa devem permanecer visíveis em todas as abas de funcionalidades da empresa.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-03 Exibir Abas de Funcionalidades da Empresa {#exibir-abas-de-funcionalidades-da-empresa}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;"><a href="#exibir-abas-de-funcionalidades-da-empresa">Exibir Abas de Funcionalidades da Empresa</a></th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 2</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir um conjunto fixo de abas ao acessar uma empresa em "Empresas", permitindo que o usuário acesse as principais funcionalidades contábeis da empresa selecionada. As abas devem representar as seguintes seções: Plano de Contas, Livro Diário, Livro Razão, Balancete de Verificação e Apuração. As abas devem estar sempre visíveis enquanto o usuário navega entre as funcionalidades, permitindo alternância sem que ocorra perda de dados ou descarte de informações que estejam em processo de preenchimento.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> As abas devem exibir as seguintes seções: Plano de Contas, Livro Diário, Livro Razão, Balancete de Verificação e Apuração.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Ao selecionar uma aba, o sistema deve exibir o conteúdo correspondente à seção escolhida.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> As informações em processo de preenchimento devem ser preservadas ao alternar entre abas.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> A aba atualmente selecionada deve ser destacada visualmente, indicando ao usuário a seção ativa.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>EX- 2.</strong> [CA-2] Caso uma aba não consiga carregar seu conteúdo, o sistema deve exibir uma mensagem de erro.</td></tr>
</tbody>
</table>

##### Plano de Contas {#plano-de-contas}
Esta subseção especifica os requisitos relacionados à exibição do Plano de Contas por cada empresa cadastrada no sistema. Sendo utilizado como base para a organização das contas de forma hierárquica e padronizada, além de fornecer informações necessárias para a realização de lançamentos contábeis e relatórios gerenciais.

##### RF-04 Exibir Plano de Contas Padrão {#exibir-plano-de-contas-padrão}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Plano de Contas Padrão</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 1</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário visualize o Plano de Contas Padrão a qualquer momento sem perda de dados ou do progresso atual no sistema. Por ser o plano de contas da empresa estática, a exibição deve apresentar todos os campos essenciais, incluindo Código, Classificação e Descrição da Conta, seguindo o formato estabelecido no documento oficial. O plano de contas deve ser exibido com hierarquia e indentação adequadas, de forma a diferenciar grupos, subdivisões, contas sintéticas (agrupadoras) e contas analíticas (utilizadas em lançamentos contábeis). Além disso, o sistema deve permitir que o usuário filtre os resultados do Plano de Contas com base em qualquer um dos campos disponíveis.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O Plano de Contas Padrão deve seguir exatamente os dados do documento oficial disponibilizado em <a href="https://docs.google.com/spreadsheets/d/1eYd4BTtSIW6IggKeMR8KJp0oBfOmKuRALwSfzIBAEEw/edit?usp=drive_link">Plano de Contas Padrão</a>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> O Plano de Contas deve ser estático e padrão para todas as empresas do sistema.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> O sistema deve exibir a indentação correta para diferenciar níveis hierárquicos, incluindo grupos, subdivisões, contas sintéticas e contas analíticas.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> O usuário não deve ser capaz de incluir, alterar ou remover contas no Plano de Contas Padrão.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> O sistema deve permitir a filtragem independente por qualquer um dos campos: Código, Classificação, Descrição da Conta.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> O sistema deve permitir a combinação de filtros, exibindo apenas as contas que satisfaçam todas as condições aplicadas simultaneamente.</td></tr>
<tr><td colspan="2"><strong>CA-7.</strong> A filtragem deve ser dinâmica, atualizando os resultados sem necessidade de recarregar a página.</td></tr>
<tr><td colspan="2"><strong>CA-8.</strong> Os filtros devem preservar a hierarquia visual das contas (grupos, sintéticas e analíticas), exibindo apenas as que correspondem ao critério.</td></tr>
<tr><td colspan="2"><strong>CA-9.</strong> A busca por Descrição da Conta deve ser insensível a maiúsculas/minúsculas e permitir correspondências parciais (ex.: "Caixa" retorna "Caixa Geral" e "Caixa Pequeno Valor").</td></tr>
<tr><td colspan="2"><strong>CA-10.</strong> Caso nenhum resultado seja encontrado, o sistema deve exibir uma mensagem informativa.</td></tr>
<tr><td colspan="2"><strong>CA-11.</strong> A remoção de todos os filtros deve restaurar a exibição completa do Plano de Contas Padrão.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

#### Livro Diário {#livro-diário}
Esta subseção descreve as funcionalidades vinculadas ao Livro Diário, que registra de forma cronológica todos os lançamentos contábeis realizados pela empresa. O foco é garantir a integridade dos registros e permitir sua visualização, edição, exclusão e filtragem conforme critérios definidos pelo usuário.

##### RF-05 Gerenciar Lançamento Contábil {#gerenciar-lançamento-contábil}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Gerenciar Lançamento Contábil</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 2</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário realize lançamentos contábeis para uma empresa previamente cadastrada, informando os seguintes campos: data do lançamento, código da conta de débito e/ou código da conta de crédito, valor e histórico (descrição). O nome das contas associadas aos códigos informados deve ser exibido automaticamente pelo sistema, não devendo ser informado manualmente pelo usuário. Além disso, o usuário deve poder editar e excluir lançamentos previamente cadastrados, desde que todas as regras estabelecidas sejam respeitadas.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> A data do lançamento é obrigatória, deve ser especificada manualmente pelo usuário e estar obrigatoriamente no formato DD/MM/AAAA e dentro do intervalo de 01/01 do ano atual à 31/01/2050.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> O usuário deve informar manualmente os códigos das contas de débito e crédito (campos obrigatórios), que devem obrigatoriamente seguir a estrutura definida no Plano de Contas Padrão.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> O sistema deve exibir automaticamente o nome da conta correspondente aos códigos de débito e crédito informados pelo usuário.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> O campo de nome da conta não deve ser editável nem preenchido manualmente em nenhuma tela de cadastro ou edição de lançamento contábil.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> Caso o usuário informe um código de conta inexistente, o campo de nome da conta deve permanecer em branco e o sistema deve exibir mensagem de erro ou alerta informando que o código é inválido.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> O vínculo entre código e nome da conta deve seguir os dados do Plano de Contas Padrão (documento oficial).</td></tr>
<tr><td colspan="2"><strong>CA-7.</strong> O sistema deve aceitar apenas códigos de contas analíticas para lançamentos contábeis. Caso seja informado um código inexistente ou correspondente a uma conta sintética, o sistema deve bloquear o lançamento e lançar uma mensagem de exceção.</td></tr>
<tr><td colspan="2"><strong>CA-8.</strong> O lançamento pode conter, no máximo, 6 contas de débito e 6 contas de crédito; caso o limite seja excedido, o sistema deve impedir a operação e exibir uma mensagem de erro.</td></tr>
<tr><td colspan="2"><strong>CA-9.</strong> O campo valor é obrigatório, deve ser informado em Reais (R$), possuir duas casas decimais e respeitar um valor mínimo de R$ 0,01 e máximo de R$ 99.999.999,99. Caso o valor esteja fora deste intervalo, o sistema deve lançar uma mensagem de exceção.</td></tr>
<tr><td colspan="2"><strong>CA-10.</strong> O campo histórico (descrição) é opcional, mas, quando preenchido, deve respeitar o limite máximo de 200 caracteres; caso o limite seja excedido, o sistema deve lançar uma mensagem de exceção.</td></tr>
<tr><td colspan="2"><strong>CA-11.</strong> O usuário deve poder editar qualquer campo do lançamento contábil que ele cadastrou anteriormente: data do lançamento, código da conta de débito, código da conta de crédito, valor e histórico (descrição). Assim como no momento do lançamento, o nome da conta não deve ser informado manualmente pelo usuário.</td></tr>
<tr><td colspan="2"><strong>CA-12.</strong> O usuário deve poder excluir um lançamento contábil existente.</td></tr>
<tr><td colspan="2"><strong>CA-13.</strong> O sistema deve suportar, no mínimo, 1.000 lançamentos contábeis por empresa.</td></tr>
<tr><td colspan="2"><strong>CA-14.</strong> O sistema deve validar que a soma total dos valores dos lançamentos das contas de débito seja igual à soma total dos valores das contas de crédito.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>EX- 7.</strong> [CA-7] Caso o usuário informe uma conta inexistente ou sintética, o sistema deve bloquear o lançamento e exibir mensagem de erro.</td></tr>
<tr><td colspan="2"><strong>EX- 9.</strong> [CA-9] Caso o valor informado seja inferior ao mínimo permitido ou superior ao máximo aceito, o sistema deve lançar uma mensagem de exceção.</td></tr>
<tr><td colspan="2"><strong>EX- 10.</strong> [CA-10] Caso o histórico (descrição) ultrapasse o número máximo de caracteres permitido, o sistema deve lançar uma mensagem de exceção.</td></tr>
<tr><td colspan="2"><strong>EX- 11.</strong> [CA-11] Não é permitido editar um lançamento que contenha contas de resultado vinculadas a uma apuração já realizada. O sistema deve bloquear a operação e exibir mensagem informando que a edição requer desfazer a apuração correspondente.</td></tr>
<tr><td colspan="2"><strong>EX- 12.</strong> [CA-12] Não é permitido excluir um lançamento que contenha contas de resultado vinculadas a uma apuração já realizada. O sistema deve bloquear a operação e exibir mensagem informando que a exclusão requer desfazer a apuração correspondente.</td></tr>
<tr><td colspan="2"><strong>EX- 14.</strong> [CA-14] Caso a soma total de crédito e débito não sejam iguais, o lançamento contábil deve ser bloqueado e uma mensagem de erro deve ser exibida.</td></tr>
</tbody>
</table>

##### RF-06 Listar Lançamentos Contábeis no Livro Diário {#listar-lançamentos-contábeis-no-livro-diário}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Listar Lançamentos Contábeis no Livro Diário</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 2</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário visualize os lançamentos contábeis na aba do Livro Diário, apresentando de forma clara, organizada e interativa todas as informações essenciais de cada movimentação registrada. A listagem deve exibir para cada lançamento: data, códigos e nomes das contas de débito e crédito, valores e histórico (descrição), caso informada. Quando um lançamento contiver mais de uma conta de débito ou crédito, o sistema deve agrupar a linha principal com uma descrição indicando Partidas Múltiplas, exibindo um ícone de expansão no lugar do número da conta.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O sistema deve exibir todos os lançamentos contábeis registrados para a empresa selecionada, respeitando os filtros aplicados.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> A data apresentada em cada lançamento deve ser a data informada pelo usuário no momento do cadastro; a ordenação deve considerar o horário real de registro no sistema.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> O sistema deve permitir que o usuário aplique filtros avançados: Número da Conta (código numérico), Nome da Conta (texto livre), Período Início e Período Fim (DD/MM/AAAA). O filtro de período deve considerar todos os períodos disponíveis na base de dados.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Quando houver partidas múltiplas, o lançamento principal deve exibir a descrição "Partidas múltiplas" e, ao expandir a linha, o sistema deve detalhar cada conta individual com código, nome, tipo (débito/crédito) e valor.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> O sistema deve permitir que o usuário ordene os lançamentos por data do lançamento, código da conta, nome da conta ou valor, sendo permitido apenas um critério de ordenação por vez. Ao selecionar um novo critério, o anterior deve ser desmarcado automaticamente.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> O sistema deve permitir que o usuário selecione a quantidade de registros exibidos por página: <strong>10, 20 ou 50 registros</strong>, mantendo sempre os filtros aplicados entre as páginas.</td></tr>
<tr><td colspan="2"><strong>CA-7.</strong> Para cada lançamento, o sistema deve exibir: data (DD/MM/AAAA), código e nome da conta de débito, código e nome da conta de crédito, descrição (histórico) ou "—" quando ausente, e valor formatado em R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-8.</strong> Caso não existam lançamentos para os filtros aplicados, o sistema deve exibir uma mensagem informativa.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>EX- 8.</strong> [CA-8] Caso o usuário selecione filtros que não resultem em lançamentos, o sistema deve exibir uma mensagem informativa.</td></tr>
</tbody>
</table>

##### RF-07 Deletar dados da Empresa {#deletar-dados-da-empresa}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Deletar dados da Empresa</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 2</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário exclua todos os lançamentos contábeis vinculados à empresa estática utilizada no sistema, mantendo intactos os dados da própria empresa, bem como o Plano de Contas Padrão associado. Essa funcionalidade tem como objetivo restaurar o ambiente da empresa para o estado inicial, removendo apenas os registros de movimentações e lançamentos realizados durante o uso do sistema.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O sistema deve excluir todos os lançamentos contábeis cadastrados no Livro Diário e no Livro Razão da empresa selecionada.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Os dados da empresa estática (nome, CNPJ e demais informações cadastrais) devem ser preservados.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> O Plano de Contas Padrão da empresa deve ser mantido sem alterações.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Após a exclusão, o sistema deve exibir uma mensagem de confirmação informando que os lançamentos foram removidos com sucesso.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> Caso o usuário tente acessar o Livro Diário, Livro Razão ou Balancete após a exclusão, o sistema deve exibir uma mensagem informativa indicando que não há lançamentos disponíveis.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> O sistema deve exigir confirmação explícita do usuário antes de realizar a exclusão.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

#### Livro Razão {#livro-razão}
Esta subseção define os requisitos referentes ao Livro Razão, responsável por apresentar as movimentações organizadas por conta contábil. Seu propósito é permitir a análise detalhada de débitos, créditos e saldos, possibilitando o acompanhamento do histórico e da evolução de cada conta.

##### RF-08 Exibir Livro Razão {#exibir-livro-razão}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Livro Razão</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 3</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário visualize o <strong>Livro Razão</strong> ao acessar a respectiva aba na interface de funcionalidades da empresa. O Livro Razão deve apresentar as movimentações organizadas por grupos de contas: <strong>Contas Patrimoniais do Ativo</strong>, <strong>Contas Patrimoniais do Passivo e Patrimônio Líquido</strong>, <strong>Contas de Resultado</strong> (Custos e Despesas; Receitas) e <strong>Contas de Encerramento</strong> (Contas de Apuração). Para cada conta sintética listada, o sistema deve exibir: Saldo Inicial, Entradas e Saídas (Débito e Crédito), Saldo Atual, Saldo Final e Indicador D/C.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O sistema deve exibir os lançamentos do Livro Razão com base nos filtros aplicados pelo usuário.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> O Livro Razão deve apresentar as contas agrupadas de acordo com suas categorias: Ativo, Passivo, Resultado e Encerramento.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Para cada conta sintética, o sistema deve exibir: saldo inicial; valores de débito e crédito; saldo atualizado após cada movimentação; saldo final calculado para o período filtrado; indicador <strong>D/C</strong> para saldo inicial e final.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> A listagem deve atualizar dinamicamente ao alterar os filtros de Nome do Grupo, Nome da Conta, Período Inicial e Período Final.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> Caso o usuário não aplique filtros, o sistema deve exibir o Livro Razão completo da empresa.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> O sistema deve ordenar as movimentações por data do lançamento em ordem crescente.</td></tr>
<tr><td colspan="2"><strong>CA-7.</strong> Ao final de cada tabela de conta, o sistema deve exibir um resumo totalizador com a soma de débitos, créditos e o saldo final.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>EX- 4.</strong> [CA-4] Caso os filtros selecionados não retornem movimentações, o sistema deve exibir uma mensagem informativa.</td></tr>
<tr><td colspan="2"><strong>EX- 5.</strong> [CA-5] Caso a base de dados não possua lançamentos para o período selecionado, o sistema não deve exibir uma tabela para essa conta.</td></tr>
<tr><td colspan="2"><strong>EX- 4b.</strong> [CA-4] Caso o usuário selecione um período inválido (Data Inicial > Data Final), o sistema deve exibir uma mensagem de erro solicitando correção dos filtros.</td></tr>
</tbody>
</table>

#### Balancete {#balancete}
   

Esta subseção descreve as funcionalidades relacionadas ao Balancete de Verificação, que tem como objetivo apresentar, de forma organizada e consolidada, os saldos das contas contábeis de uma empresa em determinado período.  
O balancete é um instrumento essencial para conferência da igualdade entre débitos e créditos, auxiliando na verificação da consistência dos lançamentos contábeis realizados no Livro Diário e refletidos no Livro Razão.  
O sistema deve permitir a aplicação de filtros de consulta, a visualização detalhada das contas analíticas com seus respectivos saldos e a exibição de um resumo consolidado por natureza contábil, possibilitando a análise do Resultado do Exercício (lucro ou prejuízo) dentro do período selecionado.

##### RF-09 Aplicar Filtros do Balancete {#aplicar-filtros-do-balancete}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Aplicar Filtros do Balancete</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 4</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário filtre as informações exibidas no Balancete de Verificação com base nos campos Nome do Grupo, Nome da Conta, Período Inicial e Período Final.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O sistema deve exibir os campos de filtro: Nome do Grupo (texto livre), Nome da Conta (texto livre), Período Inicial (DD/MM/AAAA), Período Final (DD/MM/AAAA).</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> O filtro de período deve determinar o intervalo considerado para os cálculos de Saldo Anterior, Débito, Crédito e Saldo Atual.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Caso o usuário não preencha o filtro de período, o sistema deve considerar todos os registros disponíveis no banco de dados.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> O sistema não deve permitir que o Período Final seja anterior à data do Período Inicial.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> O sistema deve permitir múltiplos filtros combinados e atualizar automaticamente a tabela conforme os parâmetros informados.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> Caso nenhum resultado seja encontrado, deve ser exibida uma mensagem informativa.</td></tr>
<tr><td colspan="2"><strong>CA-7.</strong> Os filtros devem ser aplicados integralmente tanto ao Balancete de Verificação quanto ao Resumo do Balancete, mantendo consistência entre ambas as visualizações.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-010 Exibir Balancete de Verificação {#exibir-balancete-de-verificação}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Balancete de Verificação</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 4</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir a visualização do Balancete de Verificação, exibindo apenas as contas analíticas do Plano de Contas Padrão, agrupadas por: Ativo, Passivo, Contas de Resultado – Custos e Despesas, Contas de Resultado – Receita e Contas de Apuração. Para cada conta listada, devem ser apresentados os valores consolidados de acordo com os lançamentos contábeis registrados no Livro Diário, considerando o período informado nos filtros.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O Balancete deve exibir as colunas: Código, Classificação, Descrição da Conta, Saldo Anterior (R$), Débito (R$), Crédito (R$), Saldo Atual (R$), D/C.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Devem ser exibidas exclusivamente as contas analíticas, agrupadas por: Ativo, Passivo, Contas de Resultados – Custos e Despesas, Contas de Resultado – Receita, Contas de Apuração.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> O Saldo Anterior deve representar o saldo da conta antes do Período Inicial informado.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> O Débito e o Crédito devem somar todas as movimentações no período informado.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> O campo D/C deve exibir "D" quando o saldo for devedor e "C" quando for credor.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> A tabela deve conter uma linha de TOTAL, somando apenas as colunas de Débito e Crédito do período.</td></tr>
<tr><td colspan="2"><strong>CA-7.</strong> A ordenação padrão deve ser pela coluna "Classificação", em ordem crescente.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-011 Exibir Resumo do Balancete {#exibir-resumo-do-balancete}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Resumo do Balancete</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 4</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">Após a tabela de contas analíticas, o sistema deve apresentar um resumo consolidado do balancete, agrupando as contas por natureza contábil, de modo a evidenciar a composição global dos saldos e o Resultado do Exercício. Grupos do resumo: Contas de Resultado – Receitas, Contas de Resultado – Custos e Despesas, Contas Devedoras, Contas Credoras e Resultado do Exercício.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> Cada grupo deve exibir as colunas: Saldo Anterior, Débito, Crédito, Saldo Atual, D/C.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> O agrupamento deve considerar as naturezas contábeis conforme o Plano de Contas Padrão: Contas Devedoras (Ativo, Contas de Resultado – Custos e Despesas) e Contas Credoras (Passivo, Patrimônio Líquido, Contas de Resultado – Receitas).</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> O cálculo do Resultado do Exercício deve seguir a fórmula: <strong>(Soma das Contas de Resultado – Receitas) – (Soma das Contas de Resultado – Custos e Despesas)</strong>, indicando Lucro (saldo credor) ou Prejuízo (saldo devedor).</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Caso o período não contenha movimentações nas contas de resultado, o grupo "Resultado do Exercício" deve exibir R$ 0,00 em todas as colunas.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

#### Apuração do Resultado

Esta subseção descreve as funcionalidades relacionadas à **Apuração do Resultado do Exercício (ARE)**, que tem como objetivo apresentar uma prévia completa do que será efetivamente executado no momento da apuração do resultado do período, antes da confirmação da ação.

O sistema deve permitir a definição da data de apuração, a visualização do resumo do resultado, os saldos das contas analíticas, os lançamentos de encerramento e o resultado final, indicando lucro ou prejuízo no período.

##### RF-012 Filtrar Data da Apuração {#filtrar-data-da-apuração}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Filtrar Data da Apuração</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário defina a <strong>Data da Apuração</strong>, que servirá como parâmetro para filtrar quais lançamentos contábeis do Livro Diário serão considerados no encerramento do período.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O sistema deve disponibilizar um campo obrigatório para inserção da <strong>Data da Apuração</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Ao abrir a tela, a data deve ser preenchida com o <strong>último dia do ano atual</strong> no formato <code>DD/MM/YYYY</code>.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> A apuração deve considerar todos os lançamentos com data <strong>≤ Data da Apuração</strong> que <strong>ainda não tenham sido apurados anteriormente</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Caso não existam lançamentos elegíveis, o sistema deve exibir mensagem informativa e não permitir realizar a apuração.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> Se um lançamento for criado com data anterior à última apuração, ele <strong>DEVE entrar na próxima apuração</strong> desde que ainda não tenha sido apurado.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-013 Exibir Resumo do Resultado {#exibir-resumo-do-resultado}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Resumo do Resultado</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir um <strong>resumo consolidado</strong> do resultado contábil, apresentando os totais de receitas, custos e despesas, bem como o resultado do período com indicador de <strong>lucro ou prejuízo</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O resumo deve exibir obrigatoriamente: <strong>Total de Receitas</strong>, <strong>Total de Custos e Despesas</strong>, <strong>Resultado do Período</strong> e <strong>Indicador de Resultado</strong> (Lucro ou Prejuízo).</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Os valores devem ser apresentados com sinal de acordo com a natureza padrão da conta: receitas com natureza credora exibem positivo; custos/despesas com natureza devedora exibem positivo.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Saldos invertidos (contra natureza) devem exibir valores negativos.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> A fórmula aplicada deve ser: <strong>Resultado = Receitas − Custos/Despesas</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> A classificação deve ser: credor (saldo positivo) = <strong>Lucro</strong>; devedor (saldo negativo) = <strong>Prejuízo</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-014 Exibir Contas de Resultado {#exibir-contas-de-resultado}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Contas de Resultado</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve apresentar uma <strong>listagem detalhada</strong> de todas as contas analíticas que participaram da apuração, permitindo ao usuário conferir a origem dos valores que compõem o resumo do resultado.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O sistema deve listar todas as contas analíticas com <strong>saldo ≠ 0</strong> pertencentes aos grupos: <strong>CONTAS DE RESULTADO − RECEITAS</strong> e <strong>CONTAS DE RESULTADO − CUSTOS E DESPESAS</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> A tabela de exibição deve conter as colunas: <strong>Código</strong>, <strong>Descrição da Conta</strong>, <strong>Tipo</strong>, <strong>Saldo Atual</strong> (formatado em R$) e <strong>D/C</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Se não houver contas com saldo em algum grupo, o sistema deve exibir mensagem informando a ausência de valores a apurar naquele grupo.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-015 Exibir Lançamentos de Encerramento {#exibir-lançamentos-de-encerramento}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Lançamentos de Encerramento</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve calcular e apresentar, <strong>exclusivamente em caráter de prévia</strong>, os lançamentos contábeis necessários para zerar os saldos das contas de resultado transferindo-os para a conta transitória <strong>Apuração do Resultado do Exercício (ARE)</strong>. Nesta etapa, o sistema <strong>não deve realizar nenhum lançamento real</strong> nem qualquer alteração nas tabelas do banco de dados.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> <strong>Encerramento das Receitas:</strong> se saldo credor (natureza normal): simular <strong>Débito → Receita</strong> e <strong>Crédito → ARE</strong>; se saldo devedor (natureza invertida): simular <strong>Crédito → Receita</strong> e <strong>Débito → ARE</strong>; se não houver receitas: exibir mensagem informando a ausência de valores a apurar nas contas de Receita.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> <strong>Encerramento de Custos e Despesas:</strong> se saldo devedor (natureza normal): simular <strong>Crédito → Custos/Despesas</strong> e <strong>Débito → ARE</strong>; se saldo credor (natureza invertida): simular <strong>Débito → Custos/Despesas</strong> e <strong>Crédito → ARE</strong>; se não houver custos/despesas: exibir mensagem informando a ausência de valores a apurar nas contas de Custos e Despesas.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> A prévia deve listar as linhas de conta com códigos e respectivos valores de débito e crédito simulados para cada grupo.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Nenhum dado deve ser persistido durante esta etapa; os lançamentos calculados são exibidos exclusivamente para conferência do usuário antes da confirmação.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-016 Exibir Confronto da Apuração {#exibir-confronto-da-apuração}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Confronto da Apuração</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve apresentar uma seção denominada <strong>"Confronto da Apuração do Resultado"</strong> demonstrando detalhadamente a composição do saldo final acumulado na conta transitória <strong>ARE (Apuração do Resultado do Exercício)</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> A seção deve exibir as colunas: <strong>Descrição</strong>, <strong>Valor</strong> (formatado em R$) e <strong>D/C</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Deve apresentar três linhas de consolidação: <strong>Total de Custos e Despesas</strong>, <strong>Total de Receitas</strong> e <strong>Resultado</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> A classificação deve seguir a regra: credor = <strong>Lucro (C)</strong>; devedor = <strong>Prejuízo (D)</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Caso não existam valores de receitas ou despesas, a linha de Resultado deve exibir <code>R$ 0,00</code> e o indicador D/C deve permanecer em branco.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-017 Exibir Transferência do Resultado {#exibir-transferência-do-resultado}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Transferência do Resultado</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve calcular e apresentar, <strong>exclusivamente em caráter de simulação</strong>, o lançamento contábil necessário para transferir o saldo final da conta <strong>ARE</strong> para a conta de <strong>Lucros Acumulados</strong> ou <strong>Prejuízos Acumulados</strong>, conforme o resultado.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> <strong>Se resultado = Lucro</strong> (saldo credor na ARE): simular <strong>Débito:</strong> Apuração do Resultado e <strong>Crédito:</strong> Lucros Acumulados.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> <strong>Se resultado = Prejuízo</strong> (saldo devedor na ARE): simular <strong>Crédito:</strong> Apuração do Resultado e <strong>Débito:</strong> Prejuízos Acumulados.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Este lançamento deve ser exibido apenas como prévia, sem persistência no banco de dados até que o usuário confirme a <strong>"Realizar Apuração"</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-018 Exibir Resultado Final {#exibir-resultado-final}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Resultado Final</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir uma seção de <strong>Resultado Final</strong>, consolidando as informações conclusivas da apuração para que o usuário identifique rapidamente o desfecho do exercício contábil.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> A seção deve exibir os campos: <strong>Tipo de Resultado</strong> (Lucro, Prejuízo ou Resultado Nulo), <strong>Valor</strong> (formatado em R$ com duas casas decimais) e <strong>Conta Destino</strong> (Lucros Acumulados, Prejuízos Acumulados ou nenhuma, conforme o tipo de resultado).</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Se o resultado do período for R$ 0,00, o Tipo de Resultado deve ser exibido como <strong>Resultado Nulo</strong> e o campo Conta Destino não deve indicar nenhuma conta.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-019 Realizar Apuração {#realizar-apuração}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Realizar Apuração</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário <strong>efetive a apuração do resultado</strong> através de uma ação de confirmação final. Ao confirmar, o sistema deve executar todos os cálculos e lançamentos demonstrados na prévia e <strong>zerar as contas de resultado</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O sistema deve disponibilizar o botão <strong>"Realizar Apuração"</strong>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> A operação só deve ocorrer após confirmação explícita do usuário.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Ao executar: vincular todos os lançamentos à apuração; zerar os saldos das contas de receita, custos e despesas; aplicar compensação automática e realizar a destinação final conforme CA-5 e CA-6; registrar a data, tipo de resultado e valor do período na tabela de histórico.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> O sistema deve exibir mensagem de confirmação ao usuário após a realização da apuração com sucesso.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> Se o resultado do período for R$ 0,00 (Resultado Nulo), nenhum lançamento de destinação deve ser gerado para Lucros ou Prejuízos Acumulados; o registro no histórico deve indicar Resultado Nulo.</td></tr>
<tr><td colspan="2"><strong>CA-6.</strong> Antes de enviar o resultado à conta de destino, o sistema deve aplicar compensação automática: se o resultado for lucro e houver saldo em Prejuízos Acumulados, utilizar o lucro para abater esse saldo; se o lucro for maior, zerar Prejuízos Acumulados e enviar o restante para Lucros Acumulados; se o lucro for menor ou igual, apenas reduzir Prejuízos Acumulados sem gerar lançamento para Lucros Acumulados. A lógica inversa se aplica quando o resultado for prejuízo em relação a Lucros Acumulados. O resultado exibido na tela e registrado no histórico reflete sempre o valor calculado do período, sem alteração pela compensação.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-020 Exibir Histórico de Apurações {#exibir-histórico-de-apurações}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Histórico de Apurações</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve manter um <strong>histórico completo</strong> de todas as apurações realizadas, permitindo ao usuário consultar informações sobre operações anteriores.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> A seção de histórico deve exibir as colunas: <strong>Data da Apuração</strong>, <strong>Tipo de Resultado</strong> (Lucro, Prejuízo ou Resultado Nulo), <strong>Valor</strong> (formatado em R$) e <strong>Conta Destino</strong> (Lucros Acumulados, Prejuízos Acumulados ou nenhuma quando Resultado Nulo). O valor e o tipo registrados refletem o resultado do período calculado, independentemente da compensação aplicada na destinação.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Cada registro deve ter associada uma ação <strong>"Desfazer"</strong> para reversão (ver RF-021).</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Os registros devem ser ordenados por data (mais recente primeiro).</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-021 Desfazer Última Apuração {#desfazer-última-apuração}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Desfazer Última Apuração</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 5</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário <strong>reverta apenas a apuração mais recente</strong>, restaurando o estado anterior das contas e removendo todos os registros de encerramento gerados.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> A funcionalidade "Desfazer" deve estar disponível unicamente na apuração <strong>mais recente</strong> do histórico.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Ao selecionar "Desfazer": solicitar confirmação ao usuário antes de prosseguir; remover o vínculo dos lançamentos à apuração; restaurar os saldos originais das contas; remover o registro do histórico; exibir mensagem de sucesso ao usuário.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> <strong>Restrição:</strong> não é permitido desfazer apurações fora de ordem (ex.: desfazer apuração antiga deixando a recente intacta).</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Após desfazer a apuração, os lançamentos que estavam vinculados a ela voltam a ser editáveis e excluíveis normalmente.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

#### Demonstração do Resultado do Exercício

Esta subseção descreve as funcionalidades relacionadas à **Demonstração do Resultado do Exercício (DRE)**, um relatório contábil oficial que evidencia receitas, custos, despesas e o resultado líquido de uma empresa em determinado período.

A DRE é um instrumento essencial de análise contábil que confronta receitas com despesas, apresentando de forma estruturada e hierárquica o desempenho financeiro do exercício, desde a receita bruta até o lucro (ou prejuízo) líquido.

##### RF-022 Filtrar Período da DRE {#filtrar-período-da-dre}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Filtrar Período da DRE</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário especifique o <strong>período de análise</strong> da DRE através de filtros de data, determinando quais lançamentos serão considerados no relatório.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O sistema deve disponibilizar dois campos obrigatórios: <strong>Período Inicial</strong> e <strong>Período Final</strong>, ambos no formato <code>DD/MM/YYYY</code>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Os valores padrão ao acessar a tela devem ser: <strong>Período Inicial:</strong> primeiro dia do ano atual (<code>01/01/YYYY</code>) e <strong>Período Final:</strong> último dia do ano atual (<code>31/12/YYYY</code>).</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> A DRE deve <strong>carregar automaticamente</strong> com esses valores padrão, sem necessidade de ação do usuário.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> O usuário deve poder alterar os períodos e a DRE deve ser recalculada dinamicamente.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> A DRE deve considerar <strong>apenas lançamentos apurados</strong> (reconhecimento contábil conforme regime de competência).</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-023 Exibir Receita Bruta {#exibir-receita-bruta}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Receita Bruta</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir a <strong>Receita Bruta de Vendas e Serviços</strong>, que é a soma de todas as contas analíticas pertencentes ao grupo <strong>RECEITA BRUTA DE VENDAS E SERVIÇOS</strong> dentro de <strong>CONTAS DE RESULTADO − RECEITAS</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> Exibir o valor consolidado da Receita Bruta no período selecionado.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Deve ser exibido na linha com label <strong>"(1) Receita Bruta de Vendas e Serviços"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Se não houver valores, exibir <code>R$ 0,00</code>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-024 Exibir Deduções da Receita {#exibir-deduções-da-receita}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Deduções da Receita</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir as <strong>Deduções da Receita Bruta</strong>, que é a soma de todas as contas analíticas pertencentes ao grupo <strong>DEDUÇÕES DA RECEITA BRUTA</strong> dentro de <strong>CONTAS DE RESULTADO − RECEITAS</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> Exibir o valor consolidado das deduções no período selecionado.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Deve ser exibido na linha com label <strong>"(−) Deduções da Receita Bruta"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> <strong>Fórmula da Receita Líquida:</strong> <code>Receita Líquida = Receita Bruta − Deduções</code>.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Se não houver deduções, exibir <code>R$ 0,00</code> e a Receita Líquida será igual à Receita Bruta.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-025 Calcular e Exibir Receita Líquida {#calcular-e-exibir-receita-líquida}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Calcular e Exibir Receita Líquida</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve calcular e exibir a <strong>Receita Líquida</strong>, resultante da subtração entre Receita Bruta e Deduções.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O cálculo deve seguir: <code>Receita Líquida = Receita Bruta − Deduções</code>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Exibir na linha com label <strong>"(=) Receita Líquida"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Aplicar destaque visual de subtotal na linha correspondente.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-026 Exibir CMV / CPV {#exibir-cmv--cpv}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir CMV / CPV</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir o <strong>Custo das Mercadorias/Produtos Vendidos</strong> (CMV/CPV), que é a soma de todas as contas analíticas pertencentes ao grupo <strong>CUSTOS</strong> dentro de <strong>CONTAS DE RESULTADO − CUSTOS E DESPESAS</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> Exibir o valor consolidado no período selecionado.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Deve ser exibido na linha com label <strong>"(−) CMV / CPV"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Se não houver custos, exibir <code>R$ 0,00</code>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-027 Calcular e Exibir Lucro Bruto {#calcular-e-exibir-lucro-bruto}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Calcular e Exibir Lucro Bruto</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve calcular e exibir o <strong>Lucro Bruto</strong>, resultante da subtração entre Receita Líquida e CMV/CPV.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O cálculo deve seguir: <code>Lucro Bruto = Receita Líquida − CMV/CPV</code>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Exibir na linha com label <strong>"(=) Lucro Bruto"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Aplicar destaque visual de subtotal na linha correspondente.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-028 Exibir Despesas Operacionais {#exibir-despesas-operacionais}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Despesas Operacionais</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir as <strong>Despesas Operacionais</strong>, que é a soma de contas analíticas pertencentes ao grupo <strong>DESPESAS OPERACIONAIS</strong> dentro de <strong>CONTAS DE RESULTADO − CUSTOS E DESPESAS</strong>, <strong>excluindo</strong> as contas de <strong>DESPESAS FINANCEIRAS</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> Exibir o valor consolidado no período selecionado.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Deve ser exibido na linha com label <strong>"(−) Despesas Operacionais"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Se não houver despesas operacionais, exibir <code>R$ 0,00</code>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-029 Exibir Outras Receitas/Despesas Operacionais {#exibir-outras-receitas-despesas-operacionais}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Outras Receitas/Despesas Operacionais</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir o <strong>Resultado de Outras Receitas/Despesas Operacionais</strong>, calculado pela diferença entre contas analíticas dos grupos <strong>OUTRAS RECEITAS OPERACIONAIS</strong> e <strong>OUTRAS DESPESAS OPERACIONAIS</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> <strong>Outras Receitas Operacionais:</strong> soma das contas analíticas em <strong>OUTRAS RECEITAS OPERACIONAIS</strong> (CONTAS DE RESULTADO − RECEITAS).</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> <strong>Outras Despesas Operacionais:</strong> soma das contas analíticas em <strong>OUTRAS DESPESAS OPERACIONAIS</strong> (dentro de CUSTOS E DESPESAS).</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> <strong>Cálculo:</strong> <code>Outras Operacionais = Outras Receitas Operacionais − Outras Despesas Operacionais</code>.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Se resultado positivo → apresentar como <code>(+)</code> receita; se negativo → apresentar como <code>(−)</code> despesa.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> Exibir na linha com label <strong>"(+/−) Outras Receitas/Despesas Operacionais"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-030 Calcular e Exibir LAJIR {#calcular-e-exibir-lajir}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Calcular e Exibir LAJIR</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve calcular e exibir o <strong>LAJIR</strong> (Lucro Antes dos Juros e do Imposto de Renda), representando o resultado operacional sem efeitos financeiros.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O cálculo deve seguir: <code>LAJIR = Lucro Bruto − Despesas Operacionais ± Outras Operacionais</code>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Exibir na linha com label <strong>"(=) LAJIR"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Aplicar destaque visual de subtotal na linha correspondente.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-031 Exibir Resultado Financeiro {#exibir-resultado-financeiro}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Resultado Financeiro</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir o <strong>Resultado Financeiro</strong>, calculado pela diferença entre <strong>Receitas Financeiras</strong> e <strong>Despesas Financeiras</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> <strong>Receitas Financeiras:</strong> soma das contas analíticas em <strong>RECEITAS FINANCEIRAS</strong> (CONTAS DE RESULTADO − RECEITAS).</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> <strong>Despesas Financeiras:</strong> soma das contas analíticas em <strong>DESPESAS FINANCEIRAS</strong> (CONTAS DE RESULTADO − CUSTOS E DESPESAS).</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> <strong>Cálculo:</strong> <code>Resultado Financeiro = Receitas Financeiras − Despesas Financeiras</code>.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Se resultado positivo → apresentar como <code>(+)</code> receita; se negativo → apresentar como <code>(−)</code> despesa.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> Exibir na linha com label <strong>"(+/−) Resultado Financeiro"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-032 Calcular e Exibir LAIR {#calcular-e-exibir-lair}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Calcular e Exibir LAIR</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve calcular e exibir o <strong>LAIR</strong> (Lucro Antes do Imposto de Renda), incorporando o resultado financeiro ao LAJIR.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O cálculo deve seguir: <code>LAIR = LAJIR ± Resultado Financeiro</code>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Exibir na linha com label <strong>"(=) LAIR"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Aplicar destaque visual de subtotal na linha correspondente.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-033 Exibir Resultado Não Operacional {#exibir-resultado-não-operacional}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Resultado Não Operacional</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir o <strong>Resultado Não Operacional</strong>, calculado pela diferença entre <strong>Receitas Não Operacionais</strong> e <strong>Despesas Não Operacionais</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> <strong>Receitas Não Operacionais:</strong> soma das contas analíticas em <strong>RECEITAS NÃO OPERACIONAIS</strong> (CONTAS DE RESULTADO − RECEITAS).</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> <strong>Despesas Não Operacionais:</strong> soma das contas analíticas em <strong>DESPESAS NÃO OPERACIONAIS</strong> (CONTAS DE RESULTADO − CUSTOS E DESPESAS).</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> <strong>Cálculo:</strong> <code>Resultado Não Operacional = Receitas Não Operacionais − Despesas Não Operacionais</code>.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Se resultado positivo → apresentar como <code>(+)</code>; se negativo → apresentar como <code>(−)</code>.</td></tr>
<tr><td colspan="2"><strong>CA-5.</strong> Exibir na linha com label <strong>"(+/−) Resultado Não Operacional"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-034 Calcular Resultado Antes dos Impostos {#calcular-resultado-antes-dos-impostos}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Calcular Resultado Antes dos Impostos</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve calcular e exibir o <strong>Resultado Antes dos Impostos</strong>, incorporando o resultado não operacional.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O cálculo deve seguir: <code>Resultado Antes dos Impostos = LAIR ± Resultado Não Operacional</code>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Exibir na linha com label <strong>"(=) Resultado Antes dos Impostos"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Aplicar destaque visual de subtotal na linha correspondente.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-035 Exibir Impostos sobre o Lucro {#exibir-impostos-sobre-o-lucro}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Impostos sobre o Lucro</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve exibir os <strong>Impostos sobre o Lucro</strong> (IR e CSLL), que é a soma de todas as contas analíticas pertencentes ao grupo <strong>IMPOSTOS SOBRE O LUCRO (IR/CSLL)</strong> dentro de <strong>CONTAS DE RESULTADO</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> Exibir o valor consolidado dos impostos no período selecionado.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Deve ser exibido na linha com label <strong>"(−) IR e CSLL"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Se não houver impostos registrados, exibir <code>R$ 0,00</code>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-036 Calcular e Exibir Lucro Líquido {#calcular-e-exibir-lucro-líquido}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Calcular e Exibir Lucro Líquido</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve calcular e exibir o <strong>Lucro Líquido</strong>, que é o resultado final após dedução de todos os impostos.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> O cálculo deve seguir: <code>Lucro Líquido = Resultado Antes dos Impostos − Impostos</code>.</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Exibir na linha com label <strong>"(=) Lucro Líquido do Exercício"</strong> no formato R$ com duas casas decimais.</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> Aplicar destaque visual especial na linha final.</td></tr>
<tr><td colspan="2"><strong>CA-4.</strong> Indicador: se Lucro Líquido &gt; 0 → <strong>"Lucro Líquido"</strong>; se Lucro Líquido &lt; 0 → <strong>"Prejuízo Líquido"</strong>.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

##### RF-037 Exibir Composição das Contas da DRE {#exibir-composição-das-contas-da-dre}

<table>
<thead>
<tr>
  <th style="background-color:#2E74B5; color:white;">Exibir Composição das Contas da DRE</th>
  <th style="background-color:#2E74B5; color:white; text-align:center; width:120px;">Módulo 6</th>
</tr>
</thead>
<tbody>
<tr><td colspan="2">O sistema deve permitir que o usuário explore os <strong>detalhes das contas analíticas</strong> que compõem cada linha da DRE, facilitando a análise e rastreabilidade dos valores apresentados.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"><strong>CA-1.</strong> Fornecer seções de composição para cada bloco da DRE: <strong>Receita Bruta</strong> (RECEITA BRUTA DE VENDAS E SERVIÇOS), <strong>Deduções</strong> (DEDUÇÕES DA RECEITA BRUTA), <strong>CMV/CPV</strong> (CUSTOS), <strong>Despesas Operacionais</strong> (excluindo DESPESAS FINANCEIRAS), <strong>Resultado Financeiro</strong> (RECEITAS e DESPESAS FINANCEIRAS), <strong>Resultado Não Operacional</strong> (RECEITAS e DESPESAS NÃO OPERACIONAIS) e <strong>Impostos</strong> (IMPOSTOS SOBRE O LUCRO).</td></tr>
<tr><td colspan="2"><strong>CA-2.</strong> Cada bloco deve exibir tabela com colunas: <strong>Código da Conta</strong>, <strong>Descrição</strong> e <strong>Valor</strong> (formatado em R$).</td></tr>
<tr><td colspan="2"><strong>CA-3.</strong> O valor no cabeçalho de cada bloco deve corresponder exatamente ao valor calculado na DRE.</td></tr>
<tr><td colspan="2" style="background-color:#BDD7EE; text-align:center;"><strong>Exceções dos Critérios de Aceite:</strong></td></tr>
<tr><td colspan="2"></td></tr>
</tbody>
</table>

### Requisitos Não-Funcionais {#requisitos-não-funcionais}

#### Compatibilidade
O sistema deve ser executado corretamente no sistema operacional Windows, nas versões 10 e 11.

#### Portabilidade
A instalação do software deve ser executada sem a necessidade de exigir permissões de administrador.

#### Desempenho
Após instalado, as telas principais devem responder de forma fluida.

#### Armazenamento
Os dados devem ficar salvos localmente na pasta do usuário (banco local do aplicativo).

#### Disponibilidade
O sistema deve ser capaz de operar de forma autônoma (modo offline), sem a necessidade de uma conexão com a internet ativa para a execução de suas funcionalidades.

#### Responsividade
A interface deve ser responsiva, adaptando-se a diferentes resoluções de tela, sem distorções ou sobreposição de elementos.


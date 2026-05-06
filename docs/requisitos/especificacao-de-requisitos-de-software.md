**Especificação de Requisitos de Software**

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | ----- | :---: |
| 1.0 | 25/08/2025 | Adiciona base dos requisitos funcionais | Fernanda Pessoa |
| 1.1 | 03/09/2025 | Atualiza requisitos funcionais do RF-01 ao RF-06 | Fernanda Pessoa |
| 1.2 | 22/09/2025 | Adição do requisito de Limpar dados da Empresa  | Fernanda Pessoa |
| 1.3 | 21/10/2025 | Adição de referências aos Épicos para cada requisito | Jerfferson Júnior |
| 2.0 | 22/10/2025 | Documento em geral: atualizada a estrutura da documentação \- agora a documentação das funcionalidades está alinhada com a hierarquia das informações do sistema; Retirada de critérios de aceite relacionados à responsividade, tendo em vista que este faz parte de requisitos não funcionais de usabilidade do sistema. RF-01: reestruturação completa do RF considerando a retirada do plano de contas do menu principal; Referência as abas de funcionalidades adicionada ao CA-3. RF-03: Reformulação focada na adição do plano de contas como mais uma funcionalidade, retirada da contagem de funcionalidades no CA-1 considerando a expansão futura (agora são apenas listadas as funcionalidades existentes). | Jerfferson Júnior |
| 3.0 | 23/10/2025 | Adição de Requisitos Funcionais referentes ao Balancete | Fernanda Pessoa |
| 4.0 | 27/10 | Adição de Requisitos não funcionais | Fernanda Pessoa |
| 4.1 | 16/11 | Adição do RNF de responsividade | Fernanda Pessoa |
| 4.2 | 17/11 | Migração dos Conceitos para Glossário de Termos | Fernanda Pessoa |
| 4.3 | 25/11 | Correções de alinhamento, adição de link para Glossário de Termos | Jerfferson Júnior |
| 4.4 | 08/04 | Adição dos RFs de Apuração do Resultado do Exercício (ARE) | Elise Lissa Hasegawa  |
| 4.5 |  | Adição dos RFs da Demonstração do Resultado do Exercício (DRE) |  |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.2 | 25/09/2025 | Jerfferson Júnior | Aprovada |
| 3.0 | 30/10/2025 | Jerfferson Júnior | Aprovada |
| 4.2 | 25/11/2025 | Jerfferson Júnior | Aprovada |

**Sumário**

[1\. Introdução	4](#introdução)

[2\. Classes de Usuários	4](#classes-de-usuários)

[3\. Definição de conceitos	5](#definição-de-conceitos)

[**4\. Épicos	5**](#épicos)

[**5\. Modelo dos Requisitos Funcionais	6**](#modelo-dos-requisitos-funcionais)

[**6\. Requisitos de Software	7**](#requisitos-de-software)

[**6.1. Requisitos Funcionais	7**](#requisitos-funcionais)

[6.1.1. Menu	7](#menu)

[RF-01 Exibir Menu Principal	7](#exibir-menu-principal)

[6.1.2. Empresas	8](#empresas)

[6.1.2.1. Estrutura da Empresa	8](#estrutura-da-empresa)

[RF-02 Exibir Empresa Estática	8](#exibir-empresa-estática)

[RF-03 Exibir Abas de Funcionalidades da Empresa	9](#exibir-abas-de-funcionalidades-da-empresa)

[6.1.2.2. Plano de Contas	10](#plano-de-contas)

[RF-04 Exibir Plano de Contas Padrão	10](#exibir-plano-de-contas-padrão)

[6.1.2.3. Livro Diário	12](#livro-diário)

[RF-05 Gerenciar Lançamento Contábil	12](#gerenciar-lançamento-contábil)

[RF-06 Listar Lançamentos Contábeis no Livro Diário	14](#listar-lançamentos-contábeis-no-livro-diário)

[RF-07 Deletar dados da Empresa	16](#deletar-dados-da-empresa)

[6.1.2.4. Livro Razão	17](#livro-razão)

[RF-08 Exibir Livro Razão	17](#exibir-livro-razão)

[6.1.2.5. Balancete	19](#balancete)

[RF-09 Aplicar Filtros do Balancete	19](#aplicar-filtros-do-balancete)

[RF-010 Exibir Balancete de Verificação	20](#exibir-balancete-de-verificação)

[RF-011 Exibir Resumo do Balancete	21](#exibir-resumo-do-balancete)

[**6.2. Requisitos Não-Funcionais	23**](#requisitos-não-funcionais)

[Compatibilidade:	23](#compatibilidade:)

[Portabilidade:	23](#portabilidade:)

[Desempenho:	23](#desempenho:)

[Armazenamento:	23](#armazenamento:)

[Disponibilidade:	24](#disponibilidade:)

[Responsividade:	24](#responsividade:)

# 

1. # **Introdução** {#introdução}

   

Este documento apresenta a Especificação de Requisitos de Software (ERS) do Sistema COIN’S – Contabilidade Integrada. O sistema tem como objetivo oferecer uma plataforma prática, didática e acessível para que os alunos dos primeiros semestres do curso de Ciências Contábeis da UFMS tenham um contato inicial com as atividades fundamentais do processo contábil.  
Enquanto softwares contábeis profissionais — amplamente utilizados no mercado e introduzidos apenas nos semestres avançados do curso — exigem conhecimento prévio e maior maturidade técnica, o COIN’S preenche uma lacuna essencial ao permitir que os estudantes vivenciem práticas contábeis semelhantes às do mundo real, mas em um ambiente simplificado e focado na aprendizagem.  
No COIN’S, os alunos realizam lançamentos contábeis alinhados ao Plano de Contas, registram movimentações no Livro Diário, consultam informações no Livro Razão e geram relatórios estruturados, como o Balancete de Verificação, Balancete Consolidado e Demonstração do Resultado do Exercício (DRE). Dessa forma, compreendem como os dados são registrados, organizados e transformados em informações relevantes para análise contábil, desenvolvendo desde cedo uma visão prática e aplicada da disciplina.

2. # **Classes de Usuários** {#classes-de-usuários}

   

	No Sistema COINS, foram identificadas duas classes de usuários relevantes: **Aluno** e **Professor**. Ambas utilizam o sistema com o mesmo conjunto de funcionalidades, sem distinção de permissões ou papéis nesta versão. A Tabela 1 apresenta suas responsabilidades, restrições de acesso e características típicas.

| Classe | Responsabilidades principais | Restrições de acesso | Características típicas |
| :---- | :---- | :---- | :---- |
| Aluno | Registrar lançamentos, consultar livros (Diário/Razão), gerar/exibir relatórios (Balancete, DRE, Balanço) | Não há distinções | Usuário iniciante; conhecimento técnico básico |
| Professor | Registrar lançamentos, consultar livros (Diário/Razão), gerar/exibir relatórios (Balancete, DRE, Balanço) | Não há distinções | Usa o sistema para fins didáticos/demonstração |

3. # **Definição de conceitos** {#definição-de-conceitos}

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


4. # **Épicos** {#épicos}

A seção de Épicos apresenta uma visão macro das grandes funcionalidades do sistema e serve como base de rastreabilidade para os Requisitos Funcionais descritos posteriormente. Cada requisito está vinculado ao épico correspondente, permitindo rastrear a relação entre funcionalidades detalhadas e seus objetivos de alto nível.

| Épico 1 | Plano de Contas |
| :---: | :---: |
| **Épico 2** | Empresa |
| **Épico 3** | Livro Razão |
| **Épico 4** | Balancete de Verificação |
| **Épico 5** | Apuração |

5. # **Modelo dos Requisitos Funcionais** {#modelo-dos-requisitos-funcionais}

O seguinte exemplo demonstra o modelo adotado para os requisitos funcionais. O uso foi especificado no documento [Fundamento da Estrutura dos Requisitos](https://docs.google.com/document/u/0/d/1eAsVxnGFQnY8Fp2fKZukeNej2aNxZxu0_dLkIjcqvxE/edit).

| Nome do Requisito Funcional | Épico 1 |
| ----- | :---: |
| Descrição do Requisito. |  |
| **Critérios de Aceite:** |  |
| Critérios de Aceite do Requisito. |  |
| **Exceções dos Critérios de Aceite:** |  |
| \[CA-1\] Exceções do Critério de Aceite.  |  |

Modelo de Especificação \- Requisitos Funcionais. 

# 

# 

6. # **Requisitos de Software** {#requisitos-de-software}

Esta seção descreve os requisitos que definem o comportamento e as características do sistema COIN’S (Contabilidade Integrada). Os requisitos foram organizados em duas categorias: Requisitos Funcionais, que descrevem o que o sistema deve fazer, e Requisitos Não-Funcionais, que especificam restrições e qualidades esperadas. Cada requisito funcional está associado a um Épico, de forma a manter a rastreabilidade entre as funcionalidades e os objetivos do projeto.

1. # **Requisitos Funcionais** {#requisitos-funcionais}

Os requisitos funcionais descrevem as funcionalidades que o sistema deve oferecer para atender às necessidades dos usuários. Eles estão organizados por seções que correspondem aos principais módulos do sistema: Menu, Empresas, Plano de Contas, Livro Diário, Livro Razão, Balancete e Apuração. Cada requisito segue o padrão definido no modelo apresentado anteriormente, contendo sua descrição, critérios de aceite e exceções associadas aos critérios especificados.

1. ### **Menu** {#menu}

Esta subseção apresenta os requisitos relacionados à navegação do sistema. O menu é o ponto central de acesso às funcionalidades, permitindo ao usuário visualizar as opções disponíveis e alternar entre diferentes seções de forma intuitiva e consistente. 

| Exibir Menu Principal | Épico 1 |
| ----- | :---: |
| O sistema deve exibir um menu principal fixo que permita a navegação entre as funcionalidades principais. Esse menu deve conter a seção de Empresas, contendo subopções expansíveis. Dentro da seção Empresas, o sistema deve exibir subopções referentes às empresas cadastradas no sistema, incluindo a empresa estática previamente cadastrada.  |  |
| **Critérios de Aceite:** |  |
| O menu principal deve exibir a seção “Empresas”. A seção “Empresas” deve conter as subopções com o nome das empresas cadastradas (razão social).  Ao selecionar uma empresa cadastrada, o sistema deve exibir a tela referente a empresa com suas informações (Nome e CNPJ), bem como as abas de funcionalidades disponíveis \[[RF-03 – Exibir Abas de Funcionalidades da Empresa](#exibir-abas-de-funcionalidades-da-empresa)\]. O menu deve iniciar contendo uma empresa previamente cadastrada, estática, utilizada como base para realizar os lançamentos contábeis no sistema. \[[RF-02 – Exibir Empresa Estática](#exibir-empresa-estática)\] O menu deve destacar visualmente a seção e a subopção ativa, indicando ao usuário onde ele está navegando. O menu deve permanecer acessível durante a navegação entre telas. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

2. ### **Empresas** {#empresas}

   1. #### **Estrutura da Empresa** {#estrutura-da-empresa}

      

Esta subseção detalha os requisitos referentes à visualização de informações e acesso às funcionalidades para as empresas cadastradas no sistema. O objetivo é fornecer ao usuário uma visão informativa e padronizada das empresas utilizadas nos lançamentos contábeis, assegurando consistência e similaridade com práticas reais. Além disso, permite a navegação entre as diferentes funcionalidades oferecidas para a realização de operações contábeis em uma determinada empresa.

| [Exibir Empresa Estática](#exibir-empresa-estática) | Épico 2 |
| ----- | :---: |
| O sistema deve permitir que o usuário visualize uma empresa previamente cadastrada, utilizada como base para realizar os lançamentos contábeis. Essa empresa será a primeira subopção da seção “Empresas”, exibida de forma estática e sem permitir alteração de informações (Nome e CNPJ) por parte do usuário. |  |
| **Critérios de Aceite:** |  |
| O nome da empresa exibida deve corresponder à empresa previamente cadastrada no sistema. O CNPJ exibido deve corresponder ao CPNJ da empresa previamente cadastrada. As informações da empresa devem ser exibidas no formato padronizado: Nome: “Nome da Empresa”. CNPJ: “CNPJ: 00.000.000/0000-00”. O usuário não deve ser capaz de incluir, alterar ou remover as informações dessa empresa estática. As informações da empresa devem permanecer visíveis em todas as abas de funcionalidades da empresa. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

| [Exibir Abas de Funcionalidades da Empresa](#exibir-abas-de-funcionalidades-da-empresa) | Épico 2 |
| ----- | :---: |
| O sistema deve exibir um conjunto fixo de abas ao acessar uma empresa em “Empresas”, permitindo que o usuário acesse as principais funcionalidades contábeis da empresa selecionada. As abas devem representar as seguintes seções: Plano de Contas, Livro Diário, Livro Razão, Balancete de Verificação e Apuração. As abas devem estar sempre visíveis enquanto o usuário navega entre as funcionalidades, permitindo alternância sem que ocorra perda de dados ou descarte de informações que estejam em processo de preenchimento, garantindo que o progresso do usuário seja preservado até que ele confirme ou cancele as operações. |  |
| **Critérios de Aceite:** |  |
| As abas devem exibir as seguintes seções: Plano de Contas, Livro Diário, Livro Razão, Balancete de Verificação e Apuração. Ao selecionar uma aba, o sistema deve exibir o conteúdo correspondente à seção escolhida. As informações em processo de preenchimento devem ser preservadas ao alternar entre abas. A aba atualmente selecionada deve ser destacada visualmente, indicando ao usuário a seção ativa. |  |
| **Exceções dos Critérios de Aceite:** |  |
| \[CA-2\] Caso uma aba não consiga carregar seu conteúdo, o sistema deve exibir uma mensagem de erro. |  |

2. #### **Plano de Contas** {#plano-de-contas}

Esta subseção especifica os requisitos relacionados à exibição do Plano de Contas por cada empresa cadastrada no sistema. Sendo utilizado como base para a organização das contas de forma hierárquica e padronizada, além de fornecer informações necessárias para a realização de lançamentos contábeis e relatórios gerenciais.

| Exibir Plano de Contas Padrão | Épico 1 |
| ----- | :---: |
| O sistema deve permitir que o usuário visualize o Plano de Contas Padrão a qualquer momento sem perda de dados ou do progresso atual no sistema. Por ser o plano de contas da empresa estática, a exibição deve apresentar todos os campos essenciais, incluindo Código, Classificação e Descrição da Conta, seguindo o formato estabelecido no documento oficial. O plano de contas deve ser exibido com hierarquia e indentação adequadas, de forma a diferenciar grupos, subdivisões, contas sintéticas (agrupadoras) e contas analíticas (utilizadas em lançamentos contábeis). Além disso, o sistema deve permitir que o usuário filtre os resultados do Plano de Contas com base em qualquer um dos campos disponíveis, incluindo Código, Classificação e Descrição da Conta, possibilitando localizar rapidamente informações específicas. |  |
| **Critérios de Aceite:** |  |
| O Plano de Contas Padrão deve seguir exatamente os dados do documento oficial disponibilizado em [https://docs.google.com/spreadsheets/d/1eYd4BTtSIW6IggKeMR8KJp0oBfOmKuRALwSfzIBAEEw/edit?usp=drive\_link](https://docs.google.com/spreadsheets/d/1eYd4BTtSIW6IggKeMR8KJp0oBfOmKuRALwSfzIBAEEw/edit?usp=drive_link)  O Plano de Contas deve ser estático e padrão para todas as empresas do sistema. O sistema deve exibir a indentação correta para diferenciar níveis hierárquicos, incluindo grupos, subdivisões, contas sintéticas e contas analíticas. O usuário não deve ser capaz de incluir, alterar ou remover contas no Plano de Contas Padrão. O sistema deve permitir a filtragem independente por qualquer um dos campos: Código Classificação Descrição da Conta O sistema deve permitir a combinação de filtros, exibindo apenas as contas que satisfaçam todas as condições aplicadas simultaneamente. A filtragem deve ser dinâmica, atualizando os resultados sem necessidade de recarregar a página. Os filtros devem preservar a hierarquia visual das contas (grupos, sintéticas e analíticas), exibindo apenas as que correspondem ao critério (ex.: não deve mostrar o grupo-pai de uma conta filtrada se ele não conter o que está no filtro). A busca por Descrição da Conta deve ser insensível a maiúsculas/minúsculas e permitir correspondências parciais (ex.: “Caixa” retorna “Caixa Geral” e “Caixa Pequeno Valor”). Caso nenhum resultado seja encontrado, o sistema deve exibir uma mensagem informativa. A remoção de todos os filtros deve restaurar a exibição completa do Plano de Contas Padrão. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

3. #### **Livro Diário** {#livro-diário}

Esta subseção descreve as funcionalidades vinculadas ao Livro Diário, que registra de forma cronológica todos os lançamentos contábeis realizados pela empresa. O foco é garantir a integridade dos registros e permitir sua visualização, edição, exclusão e filtragem conforme critérios definidos pelo usuário.

| Gerenciar Lançamento Contábil | Épico 2 |
| ----- | :---: |
| O sistema deve permitir que o usuário realize lançamentos contábeis para uma empresa previamente cadastrada, informando os seguintes campos: data do lançamento, código da conta de débito e/ou código da conta de crédito, valor e histórico (descrição). O nome das contas associadas aos códigos informados deve ser exibido automaticamente pelo sistema, não devendo ser informado manualmente pelo usuário.  Além disso, o usuário deve poder editar e excluir lançamentos previamente cadastrados, desde que todas as regras estabelecidas sejam respeitadas. |  |
| **Critérios de Aceite:** |  |
| A data do lançamento é obrigatória, deve ser especificada manualmente pelo usuário e estar obrigatoriamente no formato DD/MM/AAAA e dentro do intervalo de 01/01 do ano atual à 31/01/2050. O usuário deve informar manualmente os códigos das contas de débito e crédito (campos obrigatórios), que devem obrigatoriamente seguir a estrutura definida no Plano de Contas Padrão. O sistema deve exibir automaticamente o nome da conta correspondente aos códigos de débito e crédito informados pelo usuário. O campo de nome da conta não deve ser editável nem preenchido manualmente em nenhuma tela de cadastro ou edição de lançamento contábil. Caso o usuário informe um código de conta inexistente, o campo de nome da conta deve permanecer em branco e o sistema deve exibir mensagem de erro ou alerta informando que o código é inválido. O vínculo entre código e nome da conta deve seguir os dados do Plano de Contas Padrão (documento oficial). O sistema deve aceitar apenas códigos de contas analíticas para lançamentos contábeis. Caso seja informado um código inexistente ou correspondente a uma conta sintética, o sistema deve bloquear o lançamento e lançar uma mensagem de exceção. O lançamento pode conter, no máximo, 6 contas de débito e 6 contas de crédito; caso o limite seja excedido, o sistema deve impedir a operação e exibir uma mensagem de erro. O campo valor é obrigatório, deve ser informado em Reais (R$), possuir duas casas decimais e respeitar um valor mínimo de R$ 0,01 e máximo de R$ 99.999.999,99. Caso o valor esteja fora deste intervalo, o sistema deve lançar uma mensagem de exceção. O campo histórico (descrição) é opcional, mas, quando preenchido, deve respeitar o limite máximo de 200 caracteres; caso o limite seja excedido, o sistema deve lançar uma mensagem de exceção. O usuário deve poder editar qualquer campo do lançamento contábil que ele cadastrou anteriormente: data do lançamento, código da conta de débito, código da conta de crédito, valor e histórico (descrição). Assim como no momento do lançamento, o nome da conta não deve ser informado manualmente pelo usuário. O usuário deve poder excluir um lançamento contábil existente. O sistema deve suportar, no mínimo, 1.000 lançamentos contábeis por empresa. O sistema deve validar que a soma total dos valores dos lançamentos das contas de débito seja igual à soma total dos valores das contas de crédito.  |  |
| **Exceções dos Critérios de Aceite:** |  |
| \[CA-3\] Caso o usuário informe uma conta inexistente ou sintética, o sistema deve bloquear o lançamento e exibir mensagem de erro. \[CA-4\] Caso o valor informado seja inferior ao mínimo permitido ou superior ao máximo aceito, o sistema deve lançar uma mensagem de exceção. \[CA-6\] Caso o histórico (descrição) ultrapasse o número máximo de caracteres permitido, o sistema deve lançar uma mensagem de exceção. \[CA-10\] Caso a soma total de crédito e débito não sejam iguais, o lançamento contábil deve ser bloqueado e uma mensagem de erro deve ser exibida. |  |

| Listar Lançamentos Contábeis no Livro Diário | Épico 2 |
| ----- | :---: |
| O sistema deve permitir que o usuário visualize os lançamentos contábeis na aba do Livro Diário, apresentando de forma clara, organizada e interativa todas as informações essenciais de cada movimentação registrada. A listagem deve exibir para cada lançamento: data, códigos e nomes das contas de débito e crédito, valores e histórico (descrição), caso informada. Quando um lançamento contiver mais de uma conta de débito ou crédito, o sistema deve agrupar a linha principal com uma descrição indicando que o lançamento se trata de Partidas Múltiplas, exibindo um ícone de expansão no lugar do número da conta. Ao expandir a linha, o sistema deve exibir, de forma detalhada, cada conta participante do lançamento, com código, nome, tipo (débito/crédito) e valor. |  |
| **Critérios de Aceite:** |  |
| O sistema deve exibir todos os lançamentos contábeis registrados para a empresa selecionada, respeitando o filtro. A data apresentada em cada lançamento deve ser a data informada pelo usuário no momento do cadastro, mas a ordenação deve considerar o horário real de registro no sistema. \[CA-3\] O sistema deve permitir que o usuário aplique filtros avançados para visualizar os lançamentos, incluindo os seguintes campos: Número da Conta (código numérico); Nome da Conta (texto livre); Período Início e Período Fim, ambos no formato DD/MM/AAAA. O filtro de período deve considerar todos os períodos disponíveis na base de dados, sem limitações adicionais. Quando houver partidas múltiplas, o lançamento principal deve exibir a descrição “Partidas múltiplas” e, ao expandir a linha, o sistema deve detalhar cada conta individual com suas informações correspondentes. O sistema deve permitir que o usuário ordene os lançamentos por data do lançamento, código da conta, nome da conta ou valor, sendo permitido apenas um critério de ordenação por vez. Ao selecionar um critério de ordenação, qualquer outro critério previamente aplicado deve ser desmarcado automaticamente, mantendo apenas um critério ativo. O sistema deve permitir que o usuário selecione a quantidade de registros exibidos por página, com as opções **10, 20 ou 50 registros**, mantendo sempre os filtros aplicados entre as páginas. A paginação deve permitir que o usuário navegue entre todas as páginas de registros, preservando os filtros ativos. Para cada lançamento, o sistema deve exibir a data informada no formato DD/MM/AAAA, o código e o nome da conta de débito, o código e o nome da conta de crédito, a descrição (histórico) se informada — ou “—” quando ausente — e o valor formatado em Reais (R$) com duas casas decimais. Caso não existam lançamentos para os filtros aplicados, o sistema deve exibir uma mensagem informativa. |  |
| **Exceções dos Critérios de Aceite:** |  |
| \[CA-06.1\] Caso o usuário selecione filtros que não resultem em lançamentos, o sistema deve exibir uma mensagem informativa. |  |

| Deletar dados da Empresa | Épico 2 |
| ----- | :---: |
| O sistema deve permitir que o usuário exclua todos os lançamentos contábeis vinculados à empresa estática utilizada no sistema, mantendo intactos os dados da própria empresa, bem como o Plano de Contas Padrão associado. Essa funcionalidade tem como objetivo restaurar o ambiente da empresa para o estado inicial, removendo apenas os registros de movimentações e lançamentos realizados durante o uso do sistema, sem comprometer as informações estruturais e de referência. |  |
| **Critérios de Aceite:** |  |
| O sistema deve excluir todos os lançamentos contábeis cadastrados no Livro Diário e no Livro Razão da empresa selecionada. Os dados da empresa estática (nome, CNPJ e demais informações cadastrais) devem ser preservados. O Plano de Contas Padrão da empresa deve ser mantido sem alterações. Após a exclusão, o sistema deve exibir uma mensagem de confirmação informando que os lançamentos foram removidos com sucesso. Caso o usuário tente acessar o Livro Diário, Livro Razão ou Balancete após a exclusão, o sistema deve exibir uma mensagem informativa indicando que não há lançamentos disponíveis. O sistema deve exigir confirmação explícita do usuário antes de realizar a exclusão. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

4. #### **Livro Razão** {#livro-razão}

Esta subseção define os requisitos referentes ao Livro Razão, responsável por apresentar as movimentações organizadas por conta contábil. Seu propósito é permitir a análise detalhada de débitos, créditos e saldos, possibilitando o acompanhamento do histórico e da evolução de cada conta.

| Exibir Livro Razão | Épico 3 |
| ----- | :---: |
| O sistema deve permitir que o usuário visualize o **Livro Razão** ao acessar a respectiva aba na interface de funcionalidades da empresa. O Livro Razão deve apresentar as movimentações organizadas por grupos de contas, divididas nas seguintes categorias principais: **Contas Patrimoniais do Ativo Contas Patrimoniais do Passivo e Patrimônio Líquido Contas de Resultado** *(Custos e Despesas; Receitas)* **Contas de Encerramento** *(Contas de Apuração)* Para cada **conta sintética** listada, o sistema deve exibir as informações de forma clara, detalhada e interativa, permitindo a visualização das movimentações associadas. O Livro Razão deve apresentar: **Saldo Inicial** — calculado com base no período informado nos filtros. **Entradas e Saídas** — exibindo valores separados por **Débito** e **Crédito**. **Saldo Atual** — resultado do cálculo entre saldo inicial, débitos e créditos. **Saldo Final** — correspondente ao fechamento do período filtrado. **Indicador D/C** — coluna obrigatória para todos os saldos, onde: **D** \= Saldo Devedor **C** \= Saldo Credor A interface deve exibir os dados em formato tabular, organizando cada grupo de contas em seções separadas e destacando visualmente os títulos, conforme mostrado na interface do sistema. |  |
| **Critérios de Aceite:** |  |
| O sistema deve exibir os lançamentos do Livro Razão com base nos filtros aplicados pelo usuário. O Livro Razão deve apresentar as contas agrupadas de acordo com suas categorias (Ativo, Passivo, Resultado e Encerramento). Para cada conta sintética, o sistema deve exibir: Saldo inicial. Valores de débito e crédito. Saldo atualizado após cada movimentação. Saldo final calculado para o período filtrado. Indicador **D/C** corretamente preenchido para o saldo inicial e final, apenas. A listagem deve atualizar dinamicamente ao alterar os filtros de Nome do Grupo, Nome da Conta, Período Inicial e Período Final. Caso o usuário não aplique filtros, o sistema deve exibir o Livro Razão completo da empresa. O sistema deve ordenar as movimentações por data do lançamento em ordem crescente. Ao final de cada tabela de conta, o sistema deve exibir um resumo totalizador com a soma de débitos, créditos e o saldo final. |  |
| **Exceções dos Critérios de Aceite:** |  |
| **\[CA-06.1\]** Caso os filtros selecionados não retornem movimentações, o sistema deve exibir uma mensagem avisando. **\[CA-06.2\]** Caso a base de dados não possua lançamentos para o período selecionado, o sistema não deve exibir uma tabela para essa conta. **\[CA-06.3\]** Caso o usuário selecione um período inválido (por exemplo, Data Inicial \> Data Final), o sistema deve exibir uma mensagem de erro solicitando correção dos filtros. |  |

5. #### **Balancete** {#balancete}

   

Esta subseção descreve as funcionalidades relacionadas ao Balancete de Verificação, que tem como objetivo apresentar, de forma organizada e consolidada, os saldos das contas contábeis de uma empresa em determinado período.  
O balancete é um instrumento essencial para conferência da igualdade entre débitos e créditos, auxiliando na verificação da consistência dos lançamentos contábeis realizados no Livro Diário e refletidos no Livro Razão.  
O sistema deve permitir a aplicação de filtros de consulta, a visualização detalhada das contas analíticas com seus respectivos saldos e a exibição de um resumo consolidado por natureza contábil, possibilitando a análise do Resultado do Exercício (lucro ou prejuízo) dentro do período selecionado.

| Aplicar Filtros do Balancete | Épico 4 |
| ----- | :---: |
| O sistema deve permitir que o usuário filtre as informações exibidas no Balancete de Verificação com base nos campos Nome do Grupo, Nome da Conta, Período Inicial e Período Final. |  |
| **Critérios de Aceite:** |  |
| O sistema deve exibir os campos de filtro Nome do Grupo (texto livre) Nome da Conta (texto livre); Período Inicial (DD/MM/AAAA); Período Final (DD/MM/AAAA). O filtro de período deve determinar o intervalo considerado para os cálculos de Saldo Anterior, Débito, Crédito e Saldo Atual. Caso o usuário não preencha o filtro de período, o sistema deve considerar todos os registros disponíveis no banco de dados. O sistema não deve permitir que o Período Final seja anterior a data do Período Inicial. O sistema deve permitir múltiplos filtros combinados e atualizar automaticamente a tabela conforme os parâmetros informados. Caso nenhum resultado seja encontrado, deve ser exibida uma mensagem informativa. Os filtros devem ser aplicados integralmente tanto ao Balancete de Verificação quanto ao Resumo do Balancete, mantendo consistência entre ambas as visualizações. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

| Exibir Balancete de Verificação | Épico 4 |
| ----- | :---: |
| O sistema deve permitir a visualização do Balancete de Verificação, exibindo apenas as contas analíticas do Plano de Contas Padrão, agrupadas por: Ativo, Passivo, Contas de Resultado – Custos e Despesas, Contas de Resultado – Receita e Contas de Apuração. Para cada conta listada, devem ser apresentados os campos obrigatórios e os valores consolidados de acordo com os lançamentos contábeis registrados no Livro Diário, considerando o período informado nos filtros. O Saldo Anterior e o Saldo Atual devem refletir todas as movimentações compreendidas entre o início e o fim do período selecionado, garantindo a precisão dos valores exibidos. |  |
| **Critérios de Aceite:** |  |
| O Balancete deve exibir as colunas: Código Classificação Descrição da Conta Saldo Anterior (R$) Débito (R$) Crédito (R$) Saldo Atual (R$) D/C (Indicador de saldo devedor ou credor) Devem ser exibidas exclusivamente as contas analíticas, agrupadas por: Ativo Passivo Contas de Resultados \- Custos e Despesas Contas de Resultado \- Receita Contas de Apuração O Saldo Anterior deve representar o saldo da conta antes do Período Inicial informado. O Débito e o Crédito devem somar todas as movimentações no período informado. O campo D/C deve exibir “D” quando o saldo for devedor e “C” quando for credor. A tabela deve conter uma linha de TOTAL, somando apenas as colunas de Débito e Crédito do período. A ordenação padrão deve ser pela coluna “Classificação”, em ordem crescente. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

| Exibir Resumo do Balancete | Épico 4 |
| ----- | :---: |
| Após a tabela de contas analíticas, o sistema deve apresentar um resumo consolidado do balancete, agrupando as contas por natureza contábil, de modo a evidenciar a composição global dos saldos e o Resultado do Exercício. O resumo tem como finalidade facilitar a interpretação das demonstrações contábeis e permitir a verificação da posição financeira e do desempenho da empresa dentro do período selecionado. Grupos do resumo: Contas de Resultado – Receitas Contas de Resultado – Custos e Despesas Contas Devedoras Contas Credoras Resultado do Exercício |  |
| **Critérios de Aceite:** |  |
| Cada grupo deve exibir as colunas: Saldo Anterior Débito Crédito Saldo Atual D/C (indicador de natureza do saldo) O agrupamento deve considerar as naturezas contábeis conforme o Plano de Contas Padrão, da seguinte forma: Contas Devedoras: Ativo Contas de Resultado \- Custos e Despesas Contas Credoras: Passivo,  Patrimônio Líquido Contas de Resultado \- Receitas O cálculo do Resultado do Exercício deve ser obtido pela fórmula: **(Soma das Contas de Resultado – Receitas) – (Soma das Contas de Resultado – Custos e Despesas),** indicando Lucro (saldo credor) ou Prejuízo (saldo devedor) conforme o resultado final. Caso o período não contenha movimentações nas contas de resultado, o grupo “Resultado do Exercício” deve exibir R$ 0,00 em todas as colunas. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

6. #### **Apuração**

   

Esta subseção descreve as funcionalidades relacionadas à Apuração do Resultado, que tem como objetivo apresentar uma prévia completa do que será efetivamente executado no momento da apuração do resultado do período, antes da confirmação da ação.  
O sistema deve permitir a aplicação de filtros de consulta, a visualização do resumo do resultado, os saldos das contas analíticas, os lançamentos de encerramento e o resultado final, indicando lucro ou prejuízo no período.  
Ao confirmar a realização da apuração, o sistema deve realizar os devidos lançamentos para na conta de apuração e zerar as contas de resultados.

| Definir Período da Apuração | Módulo 5 |
| ----- | :---: |
| O sistema deve permitir a definição da Data da Apuração, que servirá como parâmetro para filtrar quais lançamentos contábeis do Livro Diário serão considerados no encerramento do período. |  |
| **Critérios de Aceite:** |  |
| O sistema deve disponibilizar um campo para inserção da "Data da Apuração" e realizar o cálculo dos resultados até a data selecionada. Ao abrir a tela, a data deve ser preenchida com o último dia do ano atual (31/12/YYYY). **Regra para Primeira Apuração:** Se não houver apurações anteriores, o sistema deve considerar todos os lançamentos com data menor ou igual à informada  |  |
| **Exceções dos Critérios de Aceite:** |  |
| **\[CA-01.1\]** Caso não existam lançamentos elegíveis no intervalo calculado, o sistema deve exibir uma mensagem informativa e não permitir a apuração. |  |

| Exibir Resumo do Resultado | Módulo 5 |
| ----- | :---: |
| O sistema deve permitir que o usuário visualize um resumo do resultado contendo: o total das contas de resultados e custos e despesas e o Resultado do Período com um indicador de lucro ou prejuízo. Os valores deverão ser apresentados com sinal (positivo ou negativo) de acordo com a natureza padrão, ou seja, deve considerar que Receitas possuem natureza credora e Custos/Despesas possuem natureza devedora, se o saldo estiver invertido (contra a natureza) deve mostrar valor negativo (-). Esta funcionalidade visa dar segurança ao usuário, permitindo conferir rapidamente os valores e resultado do período selecionado antes de gerar os lançamentos definitivos de encerramento. |  |
| **Critérios de Aceite:** |  |
| O resumo deve exibir obrigatoriamente os campos: Total de Receitas, Total de Custos e Despesas, Resultado do Período e Indicador de Resultado (Lucro ou Prejuízo). |  |
| **Exceções dos Critérios de Aceite:** |  |
| **\[CA-01.1\]** Caso não existam lançamentos elegíveis no intervalo calculado, o sistema deve exibir uma mensagem informativa e não permitir a apuração. |  |

| Exibir Detalhamento das Contas de Resultado | Módulo 5 |
| ----- | :---: |
| O sistema deve apresentar uma listagem detalhada de todas as contas analíticas que participaram da apuração, permitindo ao usuário conferir a origem dos valores que compõem o resumo do resultado |  |
| **Critérios de Aceite:** |  |
| O sistema deve listar obrigatoriamente todas as contas analíticas com saldo diferente de 0, pertencentes aos grupos de primeiro nível "CONTAS DE RESULTADO \- RECEITAS" e "CONTAS DE RESULTADO \- CUSTOS E DESPESAS".  A tabela de exibição deve conter os campos: Código, Descrição da Conta, Tipo, Saldo Atual e D/C (indicador de débito ou crédito). |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

| Encerramento das Receitas e Custos e Despesas |  |
| ----- | :---: |
| O sistema deve calcular e apresentar, exclusivamente em caráter de prévia, os lançamentos contábeis necessários para zerar os saldos das contas de resultado (Receitas, Custos e Despesas) e transferi-los para a conta transitória "Apuração do Resultado do Exercício (ARE)". Nesta etapa, o sistema não deve realizar nenhum lançamento real nem qualquer alteração nas tabelas do banco de dados. |  |
| **Critérios de Aceite:** |  |
| O sistema deve calcular o saldo das contas de receita e demonstrar a lógica de zeramento: Se saldo credor (natureza normal): Simular Débito na conta de Receita e Crédito na conta ARE. Se saldo devedor (natureza invertida): Simular Crédito na conta de Receita e Débito na conta ARE Ausência de Receitas: Caso não existam valores elegíveis, o sistema deve exibir a mensagem: "Não há valores a serem apurados nas contas de Receita" Simulação do Encerramento de Custos e Despesas: O sistema deve calcular o saldo das contas de custos e despesas e demonstrar a lógica de zeramento:  Se saldo devedor (natureza normal): Simular Crédito na conta de Custos/Despesas e Débito na conta ARE. Se saldo credor (natureza invertida): Simular Débito na conta de Custos/Despesas e Crédito na conta ARE Ausência de Custos/Despesas: Caso não existam valores elegíveis, o sistema deve exibir a mensagem: "Não há valores a serem apurados nas contas de Custos e Despesas" Restrição de Persistência: Os lançamentos gerados nesta funcionalidade devem ser processados apenas em memória (camada de serviço/UI) para fins de conferência. Exibição na Interface: A prévia deve listar as linhas de conta, códigos, e os respectivos valores de débito e crédito simulados para cada grupo de encerramento. |  |
| **Exceções dos Critérios de Aceite:** |  |
| **\[CA-01.1\]** Caso não existam valores a serem apurados nas contas de resultado de receitas ou custos e despesas, o sistema deve exibir uma mensagem informativa e prosseguir normalmente com a apuração. |  |

| Demonstrar Confronto da Apuração do Resultado | Módulo 5 |
| ----- | :---: |
| O sistema deve apresentar uma subseção denominada "Confronto da Apuração do Resultado", com o objetivo de demonstrar detalhadamente a composição do saldo final acumulado na conta transitória "Apuração do Resultado do Exercício (ARE)". |  |
| **Critérios de Aceite:** |  |
| A seção deve exibir obrigatoriamente as colunas: Descrição, Valor e D/C (indicador de débito ou crédito) e três linhas de consolidação: Total de Custos e Despesas, Total de Receitas e Resultado. |  |
| **Exceções dos Critérios de Aceite:** |  |
| **\[CA-01.1\]** Caso não existam valores de receitas ou despesas no período, a linha de Resultado deve exibir R$ 0,00 e o indicador D/C deve permanecer vazio |  |

| Demonstrar Confronto da Apuração do Resultado | Módulo 5 |
| ----- | :---: |
| O sistema deve calcular e apresentar, exclusivamente em caráter de simulação, o lançamento contábil necessário para transferir o saldo final da conta transitória "Apuração do Resultado do Exercício (ARE)" para a conta de Lucros Acumulados ou para a conta de Prejuízos Acumulados. |  |
| **Critérios de Aceite:** |  |
| Caso o resultado da apuração seja lucro (saldo credor na conta ARE), o sistema deve demonstrar o lançamento: Debitar a conta "Apuração do Resultado" e Creditar a conta "Lucros Acumulados". Caso o resultado da apuração seja prejuízo (saldo devedor na conta ARE), o sistema deve demonstrar o lançamento: creditar a conta "Apuração do Resultado" e debitar a conta "Prejuízos Acumulados". |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

| Exibir Resumo do Resultado Final | Módulo 5 |
| ----- | :---: |
| O sistema deve apresentar uma seção de Resultado Final, consolidando as informações conclusivas da apuração para que o usuário identifique rapidamente o desfecho do exercício contábil. |  |
| **Critérios de Aceite:** |  |
| A seção deve exibir os campos: Tipo de Resultado (Lucro ou Prejuízo do Período), Valor (formatado em R$) e Conta Destino. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

| Realizar Apuração do Resultado | Módulo 5 |
| ----- | :---: |
| O sistema deve permitir que o usuário efetive a apuração do resultado através de uma ação de confirmação final. Ao confirmar, o sistema deve efetuar todos os cálculos e lançamentos demonstrados na prévia da Apuração. |  |
| **Critérios de Aceite:** |  |
| O sistema deve disponibilizar o botão "Realizar Apuração". A operação só deve ocorrer após o clique de confirmação do usuário. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

| Desfazer Última Apuração Realizada | Módulo 5 |
| ----- | :---: |
| O sistema deve permitir que o usuário reverta a apuração do resultado mais recente, restaurando o estado das contas e removendo os registros de encerramento gerados anteriormente. |  |
| **Critérios de Aceite:** |  |
| A funcionalidade de desfazer deve estar disponível dentro da seção de "Histórico de Apurações", associada a cada registro individual de apuração concluída. O sistema deve permitir desfazer exclusivamente a última apuração realizada no sistema. O sistema deve permitir desfazer exclusivamente a última apuração realizada no sistema, exibindo uma mensagem informativa e solicitando confirmação do usuário. |  |
| **Exceções dos Critérios de Aceite:** |  |
|  |  |

7. #### **Demonstração do Resultado do Exercício**

   

Esta subseção descreve as funcionalidades relacionadas à Demonstração do Resultado do Exercício que é um relatório contábil oficial que evidencia as receitas, custos e despesas de uma empresa em um determinado período. Seu objetivo principal é confrontar esses valores para chegar ao resultado líquido do exercício, indicando se a organização obteve lucro ou prejuízo.

2. # **Requisitos Não-Funcionais** {#requisitos-não-funcionais}

   

### Compatibilidade: {#compatibilidade:}
1. O sistema deve ser executado corretamente no sistema operacional Windows, nas versões 10 e 11\.

### Portabilidade: {#portabilidade:}
2. A instalação do software deve ser executada sem a necessidade de exigir permissões de administrador.

### Desempenho: {#desempenho:}
3. Após instalado, as telas principais devem responder de forma fluida.

### Armazenamento: {#armazenamento:}
4. Os dados devem ficar salvos localmente na pasta do usuário (banco local do aplicativo).

### Disponibilidade: {#disponibilidade:}
5. O sistema deve ser capaz de operar de forma autônoma (modo offline), sem a necessidade de uma conexão com a internet ativa para a execução de suas funcionalidades.

### Responsividade: {#responsividade:}
6. A interface deve ser responsiva, adaptando-se a diferentes resoluções de tela, sem distorções ou sobreposição de elementos.


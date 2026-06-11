# Fundamento da Estrutura dos Requisitos

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
| :---: | :---: | :---: | :---: |
| 1.0 | 20/10 | Fundamento da estrutura dos requisitos | Fernanda Pessoa |

**Histórico de Revisões**

| Versão | Data | Revisor | Observação |
| :---: | :---: | :---: | ----- |
| 1.0 | 04/11 | Jerfferson Jorge | Aprovada |

**Sumário**

[1\. Introdução](#introdução)

[2\. Fundamentação da Estrutura Adotada](#fundamentação-da-estrutura-adotada)

[2.1 Clareza e comunicação entre áreas](#21-clareza-e-comunicação-entre-áreas)

[2.2 Flexibilidade e profundidade técnica](#22-flexibilidade-e-profundidade-técnica)

[3\. Organização em Épicos](#organização-em-épicos)

[3.1 Nota sobre a terminologia adotada](#31-nota-sobre-a-terminologia-adotada)

[4\. Modelo de Estrutura da Especificação dos Requisitos Funcionais](#modelo-de-estrutura-da-especificação-dos-requisitos-funcionais)

[5\. Comparativo com Outras Estruturas](#comparativo-com-outras-estruturas)

[6\. Conclusão](#conclusão)

---

## Introdução {#introdução}

O Sistema COIN'S (Contabilidade Integrada) foi desenvolvido com o objetivo de proporcionar uma plataforma didática e prática para o ensino e simulação de processos contábeis.

Durante a elaboração da sua Especificação de Requisitos de Software, foi adotada uma estrutura textual organizada por épicos e requisitos funcionais, em vez dos modelos tradicionais baseados em histórias de usuário ou casos de uso.

Essa decisão buscou garantir clareza, flexibilidade e rastreabilidade, considerando o domínio contábil altamente regrado e técnico, e a necessidade de que o documento fosse compreensível tanto por profissionais técnicos (desenvolvedores e testadores) quanto por profissionais de negócio (professores e contadores).

## Fundamentação da Estrutura Adotada {#fundamentação-da-estrutura-adotada}

### 2.1 Clareza e comunicação entre áreas {#21-clareza-e-comunicação-entre-áreas}

A estrutura adotada foi pensada para eliminar barreiras de interpretação entre o time técnico e o público de negócio.

Enquanto as histórias de usuário priorizam a perspectiva do usuário final ("Como \<usuário\>, desejo \<ação\> para \<benefício\>"), o domínio contábil exige detalhamento exato de regras, exceções e restrições lógicas — algo que não pode ser plenamente representado em formato narrativo.

A escrita textual dos requisitos, apoiada em tabelas padronizadas, torna possível explicitar:

* As condições sob as quais o lançamento contábil é válido;
* As restrições de hierarquia de contas;
* Os critérios que diferenciam contas sintéticas e analíticas;
* As regras de soma entre débitos e créditos;
* As exceções que invalidam determinadas operações.

Dessa forma, o documento se torna autoexplicativo e auditável, sem depender de interpretação subjetiva.

### 2.2 Flexibilidade e profundidade técnica {#22-flexibilidade-e-profundidade-técnica}

O domínio contábil é um dos mais rigorosos em termos de regras e validações cruzadas.

Ao contrário de sistemas administrativos genéricos, o COIN'S exige uma abordagem que permita inserir todas as regras diretamente no corpo dos requisitos, sem fragmentá-las entre diversos artefatos (casos de uso, fluxogramas ou narrativas).

O formato textual adotado permite:

* Inserir regras de cálculo e validação junto ao requisito que as origina;
* Detalhar critérios de aceite e exceções dentro de um mesmo bloco;
* Evitar redundância e divergência entre artefatos paralelos.

Além disso, o uso de uma estrutura de tabelas por requisito garante legibilidade e mantém o padrão de rastreabilidade esperado em projetos de engenharia de software.

Os critérios de aceite e suas exceções bem definidos também reforçam o processo de QA (*Quality Assurance*), pois funcionam como referência direta para o desenho e automação de testes, garantindo que cada funcionalidade implementada seja validada conforme o comportamento descrito no requisito.

## Organização em Épicos {#organização-em-épicos}

Os épicos representam agrupamentos de requisitos funcionais relacionados à mesma entrega ou funcionalidade geral, promovendo organização, rastreabilidade e controle de progresso.

Além disso, essa estrutura reflete diretamente o modelo de versionamento e desenvolvimento utilizado no projeto, no qual cada branch do repositório Git segue o padrão:

* **feat/ep02-empresas** → desenvolvimento de novas funcionalidades pertencentes ao Épico 2;
* **subtask/ep02-lancamento-interface** → implementações específicas dentro do mesmo épico.

Esse modelo permite rastreabilidade direta entre a documentação de requisitos, as branchs de desenvolvimento e as entregas de código, fortalecendo o controle de evolução do sistema e a integridade das versões.

Os épicos definidos para o projeto COIN'S são:

* **Épico-01 – Plano de Contas**

    Trata da criação, hierarquização e vinculação das contas contábeis, diferenciando contas sintéticas e analíticas, e garantindo que apenas as analíticas possam receber lançamentos.

* **Épico-02 – Empresas**

    Abrange o cadastro e a exibição das informações das empresas, além do acesso às suas respectivas funcionalidades contábeis.

* **Épico-03 – Livro Razão**

    Responsável pela exibição detalhada das movimentações por conta contábil, incluindo valores de débito, crédito e saldo acumulado.

* **Épico-04 – Balancete de Verificação**

    Consolida as informações dos livros contábeis e apresenta a verificação de igualdade entre débitos e créditos, assegurando a consistência contábil das operações registradas.

Essa organização por épicos permite alinhar entregas técnicas com entregas de negócio, além de promover rastreabilidade entre código, tarefas e requisitos em todo o ciclo de vida do projeto.

### 3.1 Nota sobre a terminologia adotada {#31-nota-sobre-a-terminologia-adotada}

No contexto do projeto COIN'S, o termo "Épico" foi mantido por convenção organizacional, porém com um significado adaptado. Diferentemente do uso tradicional em metodologias ágeis, onde um épico representa uma história de usuário de grande porte, aqui o termo é utilizado para agrupar requisitos funcionais técnicos relacionados a um mesmo módulo do sistema.

Essa adaptação foi necessária porque o projeto não utiliza histórias de usuário nem casos de uso, dado o seu domínio contábil altamente técnico, que exige descrição precisa de regras, cálculos e exceções.

Assim, cada Épico funciona como um container de funcionalidades, assegurando rastreabilidade entre documentação, código e entregas sem perder clareza ou alinhamento metodológico.

## Modelo de Estrutura da Especificação dos Requisitos Funcionais {#modelo-de-estrutura-da-especificação-dos-requisitos-funcionais}

Para padronizar a escrita dos requisitos e garantir consistência em todo o documento, foi utilizado o modelo a seguir:

<table style="width:100%">
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
<tr><td colspan="2"><strong>EX-1.</strong> [CA-1] Exceções do Critério de Aceite.</td></tr>
</tbody>
</table>

## Comparativo com Outras Estruturas {#comparativo-com-outras-estruturas}

A escolha pela estrutura de requisitos adotada no COIN'S foi feita com base em uma análise de trade-off entre os modelos tradicionais (Histórias de Usuário e Casos de Uso) e a necessidade de profundidade técnica e rastreabilidade exigida por um sistema de domínio contábil.

A tabela a seguir sintetiza os ganhos e perdas de cada abordagem, considerando clareza, flexibilidade, rastreabilidade e adequação ao contexto do projeto.

| Critério | Histórias de Usuário | Casos de Uso | Estrutura do COIN'S (adotada) |
| ----- | ----- | ----- | ----- |
| **Foco principal** | ✅ Forte foco no usuário final e valor de negócio. ❌ Pouco espaço para detalhamento técnico e validações. | ✅ Bom equilíbrio entre ator e sistema. ❌ Ainda limita regras de negócio extensas. | ✅ Centraliza regras, fluxos e exceções contábeis. ❌ Exige leitura mais técnica. |
| **Detalhamento de regras** | ❌ Superficial, voltado à experiência do usuário. | ⚙️ Moderado, adequado para fluxos simples. | ✅ Alto: detalhamento, com integração de regras e exceções em um único artefato. |
| **Adequação ao domínio contábil** | ❌ Limitada, por não comportar múltiplas condições e validações cruzadas. | ⚙️ Moderada — permite algum detalhamento, mas exige documentos complementares. | ✅ Alta: possibilita descrever regras fiscais, restrições de contas e critérios de verificação. |
| **Público-alvo** | ✅ Ideal para equipes ágeis. ❌ De difícil leitura para contadores e docentes. | ⚙️ Acessível para analistas e técnicos. | ✅ Atinge tanto público técnico quanto especialistas de negócio. |
| **Flexibilidade** | ❌ Estrutura rígida e curta. | ⚙️ Moderada: permite expansão limitada. | ✅ Ampla: comporta textos, tabelas, exemplos e exceções. |
| **Rastreabilidade de entregas** | ❌ Depende de artefatos externos (sprints, issues). | ⚙️ Parcial: rastreia interações, mas não implementações. | ✅ Implícita via épicos e padronização de branchs (feat/epXX, subtask/epXX). |

## Conclusão {#conclusão}

A estrutura dos Requisitos Funcionais do Sistema COIN'S foi planejada para atender a um domínio técnico e rigoroso, preservando clareza, rastreabilidade e alinhamento entre documentação e código.

O uso de épicos numerados e ramificações Git nomeadas de forma padronizada assegura que a rastreabilidade entre requisitos → branch → entrega seja mantida durante todo o ciclo de desenvolvimento.

Os critérios de aceite e suas exceções funcionam como ponte entre documentação, desenvolvimento e QA, permitindo que validações do sistema e testes automatizados derivem diretamente da especificação funcional.

Essa abordagem consolidou o COIN'S como um projeto com maturidade técnica e documental, capaz de comunicar regras complexas de forma objetiva, transparente e verificável — tanto para o time de tecnologia quanto para o domínio contábil.

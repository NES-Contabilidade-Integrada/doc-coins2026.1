# Roteiro de Teste de Usabilidade

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | Nov/2025 | Criação do roteiro de execução do teste de usabilidade | Amanda Caroline, Elise Lissa |
| 1.1 | 01/06/2026 | Migração para o formato de documento do repositório | Fernanda Pessoa |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |

---

## Introdução

Este documento apresenta o roteiro de execução do teste de usabilidade do sistema COIN'S (Contabilidade Integrada), baseado na Especificação de Requisitos de Software. O objetivo principal é identificar problemas de usabilidade e compreender como os usuários interagem com o sistema, avaliando aspectos como facilidade de uso, clareza das informações e eficiência na execução das tarefas. A técnica utilizada será o *Think Aloud*, que permite observar o raciocínio e as percepções dos usuários em tempo real.

---

## Think Aloud

A técnica Think Aloud, ou "Pensar em Voz Alta", consiste em solicitar que o participante verbalize seus pensamentos, dúvidas, decisões e percepções enquanto realiza tarefas no sistema. O objetivo é compreender o processo cognitivo por trás de cada ação do usuário, identificando dificuldades e pontos de confusão na interface. Durante o teste, o facilitador deve encorajar o participante a expressar o que está pensando, sem interferir ou sugerir respostas.

O observador registrará verbalizações, hesitações, expressões faciais e comportamentos inesperados. Essas informações servirão como base para identificar oportunidades de melhoria na usabilidade do sistema COIN'S.

---

## Execução do Teste

A seguir, apresenta-se o roteiro de execução proposto para a sessão de testes.

### Preparação do Ambiente

- O teste será conduzido em ambiente remoto ou presencial (disponibilizando o link da ferramenta Google Meet).
- Duração estimada: **40 a 50 minutos por participante** (incluindo preenchimento do formulário de consentimento e coleta de feedback).
- Cada sessão contará com um facilitador e um observador:
    - Facilitador: **Amanda Caroline**
    - Observador: **Elise Lissa**
- Todos os participantes devem **consentir** com a gravação de vídeo e áudio.

### Etapas do Teste

#### Configuração do Ambiente

**Local:** Presencialmente (na Sala de Reuniões I da Faculdade de Computação — FACOM) ou de forma remota (via Google Meet, com câmera e áudio habilitados).

**Duração:** 45 a 60 minutos (considerando a execução do teste e o preenchimento dos formulários).

**Equipamentos e Infraestrutura:** Presencialmente — Notebook Dell de integrante do time + dispositivo para gravação de áudio (Google Meet). Remotamente — Sala do Google Meet.

**Versão do Executável:** 1.1

#### Backstage para realização do Teste (Preparação)

- [x] Formulário de Instruções, Termo de Consentimento e Mapeamento de Perfil pronto e com link testado — via Google Forms: [https://forms.gle/XLCpNaWd3ThJHw1a6](https://forms.gle/XLCpNaWd3ThJHw1a6)
- [x] SE Remotamente: testar previamente a conexão da sala virtual. SE Presencialmente: instruções para chegar à Sala de Reuniões e preparação do notebook de execução do teste.
- [x] SE Remotamente: link do Meet criado e enviado ao participante. SE Presencialmente: aplicativo instalado e pronto para execução do teste pelo participante.
- [x] Formulário de Avaliação de Uso pronto e com link testado — via Google Forms: [https://forms.gle/oYe98FsJ6YGvdeMw9](https://forms.gle/oYe98FsJ6YGvdeMw9)
- [x] SE Remotamente: testar microfone e câmera. SE Presencialmente: testar aplicativo rodando e dispositivo de gravação de áudio.

#### Início do Teste

1. Boas-vindas, introdução e agradecimentos: apresentar os objetivos do teste e explicar a técnica Think Aloud, ensinando o participante a verbalizar pensamentos.
2. Verificar se o participante conseguiu seguir o passo a passo para instalar o aplicativo via executável.
3. Solicitar que o participante compartilhe a tela (caso seja remoto) e confirmar a gravação.
4. Cronometrar a duração total de execução do teste, incluindo o tempo de execução para cada tarefa.
5. Se o participante travar por mais de 45s: oferecer pista aberta ("Onde acha que encontraria X?").
6. Ler tarefas uma a uma, sem mostrar todas de imediato.
7. Ao final, aplicar um breve formulário de avaliação sobre a experiência do participante.

### Instrumentos de Coleta

Durante o teste, os dados serão coletados por meio dos seguintes instrumentos:

- Gravação de áudio e vídeo da sessão.
- Notas do observador sobre interações, erros e hesitações.
- Questionário do Google Forms: [https://forms.gle/oYe98FsJ6YGvdeMw9](https://forms.gle/oYe98FsJ6YGvdeMw9)

### Métricas

Durante o teste, os seguintes dados serão coletados:

- Tempo de conclusão e taxa de sucesso para cada tarefa.
- Número de ações realizadas.
- Feedback objetivo sobre a facilidade de uso e sugestões do participante.

### Roteiro Detalhado (Script)

#### Boas-Vindas

- **Apresentação:** nomes dos membros da equipe de desenvolvimento e explicação dos papéis (Observador e Facilitador).
- **Objetivo:** avaliar se o COIN'S atende às necessidades de um acadêmico dos semestres iniciais de contabilidade, identificando pontos de melhoria na usabilidade.
- **Explicar sobre a metodologia Think Aloud**, ensinando o participante a verbalizar pensamentos:

> Para nos ajudar a entender como você usa nosso produto, gostaríamos que você "pensasse em voz alta" para concluir a tarefa.
>
> Ao interagir com o produto, diga tudo o que vier à mente — e queremos dizer tudo mesmo. Não se preocupe se está certo ou errado, ou se parece relevante para a tarefa em questão!

Pilares do Think Aloud (o que é interessante que o participante exponha):

- **Verbalize seus pensamentos:** ao realizar as tarefas, tente verbalizar tudo o que estiver pensando, por exemplo: "Não sei por onde começar" ou "Acho que este botão me leva para a próxima etapa".
- **Descreva o que você vê:** se algo em particular chamar sua atenção, compartilhe. Sinta-se à vontade para dizer: "Esse botão parece estranho" ou "Esta seção é interessante, mas não tenho certeza do que faz".
- **Explique suas ações:** ao navegar pelo produto, compartilhe o raciocínio por trás de suas ações: "Estou clicando aqui porque acho que isso me levará à página de finalização".
- **Compartilhe suas frustrações:** se em algum momento você se sentir perdido ou sem saber o que fazer, não hesite em nos contar.

> Na dúvida, compartilhe tudo o que vier à mente! Entendemos que os pensamentos nem sempre serão claros ou organizados, e isso não tem problema. Nosso objetivo é entender como você experimenta o produto.

Demais instruções:

- Solicitar compartilhamento de tela (se remotamente).
- Obter consentimento do participante para gravação.
- Confirmar a ativação da gravação antes de iniciar o teste.
- Explicar que o teste será subdividido em 5 tarefas, envolvendo ou não interações entre si.
- Explicar que os dados do teste serão totalmente fictícios, assim como os dados fornecidos (Plano de Contas), sem a necessidade de buscar dados que se aproximem da realidade.

#### Tarefas

##### T1 — Exploração Inicial

**Duração máxima:** 5 minutos

1. Explore o sistema. Diga o que está vendo, o que acha que ele faz e onde você pode ir.

##### T2 — Registrar Lançamentos Contábeis

**Duração máxima:** 20 minutos

**Parte 1 — Lançamentos**

Vou te passar três lançamentos para registrar no sistema. Para cada lançamento, eu te digo as contas; você escolhe o valor e fica à vontade para navegar pelo sistema:

1. Lançamento de débito em CAIXA GERAL e crédito em VENDA DE MERCADORIAS.
2. Lançamento de débito em ALUGUÉIS DE IMÓVEIS e crédito CAIXA GERAL.
3. Lançamento de débito MATERIAL DE ESCRITÓRIO e crédito CONTAS A PAGAR.

**Parte 2 — Edição de Lançamentos**

1. Corrija o valor do primeiro lançamento — use um valor diferente do que registrou.

##### T3 — Interpretar o Balancete

**Duração máxima:** 8 minutos

1. Verifique se os lançamentos do mês atual estão equilibrados.

##### T4 — Apuração do Resultado

**Duração máxima:** 8 minutos

1. Encerre o período contábil e obtenha o resultado do exercício da empresa.
2. Verifique os saldos das contas e o resultado da empresa após a apuração.
3. Desfaça a apuração — você esqueceu de registrar um lançamento antes.

##### T5 — Visualizar e Exportar a DRE

**Duração máxima:** 8 minutos

1. Verifique qual foi o lucro líquido da empresa nesse período.
2. Exporte em PDF ou CSV.

#### Função do Observador

O que o observador deve analisar e registrar durante o teste:

**Conclusão de tarefas**

- Sucesso ou falha em cada tarefa.
- Caminho percorrido até o objetivo.

**Erros e impedimentos**

- Erro crítico (bloqueio de execução durante a tarefa).
- Erro recuperável ou cliques incorretos.

**Passos extras e atritos**

- Ações desnecessárias (rolagens, voltas, menus abertos novamente).
- Hesitações e pausas.
- Silêncio ou cursor parado por mais de 2s.

**Navegação**

- Ordem real das telas, uso de "Voltar", atalhos acionados.

**Citações do Think Aloud**

- Frases que expressem emoções ou expectativas.

**Reações não verbais**

- Expressões faciais, suspiros, risos, frustrações.

**Satisfação imediata**

- Tom de voz e comentários ao concluir cada tarefa.

**Sugestões espontâneas**

- Ideias ou melhorias mencionadas sem serem solicitadas.

---

## Referências

MAZE. *A Beginner's Guide to Usability Testing*. Disponível em: [https://maze.co/guides/usability-testing](https://maze.co/guides/usability-testing). Acesso em: 4 nov. 2025.

MAZE. *Usability Testing Tools*. Disponível em: [https://maze.co/guides/usability-testing/tools/](https://maze.co/guides/usability-testing/tools/). Acesso em: 4 nov. 2025.

MAZE. *What is Guerrilla Usability Testing? (+ How to do it)*. Disponível em: [https://maze.co/guides/usability-testing/guerrilla](https://maze.co/guides/usability-testing/guerrilla). Acesso em: 4 nov. 2025.

CONTENTSQUARE. *8 different types of usability testing methods for your website, app, or product*. Outubro 2023. Disponível em: [https://contentsquare.com/guides/usability-testing/methods](https://contentsquare.com/guides/usability-testing/methods). Acesso em: 4 nov. 2025.

DesCOMPlica, Oliba!. *Avaliação de Usabilidade — O método Think Aloud (Definição, Protocolo e Exemplo Prático)*. Disponível em: [https://youtu.be/HrS8jlHGlIM](https://youtu.be/HrS8jlHGlIM). Acesso em: 10 nov. 2025.

UX Unicórnio. *Bônus | Exemplo de Teste de Usabilidade — Unibank*. Disponível em: [https://youtu.be/iWxQ_kcbNgE](https://youtu.be/iWxQ_kcbNgE). Acesso em: 10 nov. 2025.

WEBBER, Ella. Think-aloud protocol in UX: Getting participants to verbalize feedback. Maze, 20 dez. 2024. Disponível em: [https://maze.co/collections/user-research/think-aloud-protocol](https://maze.co/collections/user-research/think-aloud-protocol). Acesso em: 18 nov. 2025.

\* Também foi utilizado como referência o teste de usabilidade aplicado ao protótipo do projeto PróVolei Planner.

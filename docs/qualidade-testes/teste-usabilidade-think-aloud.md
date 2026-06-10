# Plano de Teste de Usabilidade — Think Aloud
## Sistema COIN'S — Contabilidade Integrada

**Histórico de Versões**

| Versão | Data | Descrição | Autor |
|:---:|:---:|---|:---:|
| 1.0 | 25/05/2026 | Versão inicial | — |

---

## Sumário

1. [Objetivo](#1-objetivo)
2. [Perfil dos Participantes](#2-perfil-dos-participantes)
3. [Ambiente e Materiais](#3-ambiente-e-materiais)
4. [Procedimento da Sessão](#4-procedimento-da-sessão)
5. [Roteiro do Moderador](#5-roteiro-do-moderador)
6. [Tarefas](#6-tarefas)
7. [Guia de Observação](#7-guia-de-observação)
8. [Formulário de Registro por Sessão](#8-formulário-de-registro-por-sessão)
9. [Formulário de Percepção Pós-Sessão (SUS adaptado)](#9-formulário-de-percepção-pós-sessão-sus-adaptado)
10. [Análise e Consolidação](#10-análise-e-consolidação)
11. [Estado Inicial do Sistema](#11-estado-inicial-do-sistema)

**Tarefas (5):** T1 Exploração · T2 Lançamentos · T3 Balancete · T4 Apuração e Desfazer · T5 DRE

---

## 1. Objetivo

Identificar problemas de usabilidade no COIN'S por meio da observação direta de estudantes de Ciências Contábeis realizando tarefas contábeis reais no sistema.

**Abordagem metodológica:** Think Aloud com probing concorrente (abordagem híbrida). O participante verbaliza pensamentos continuamente durante as tarefas (Think Aloud clássico); em momentos pontuais, o moderador formula perguntas diretas durante a execução para elicitar interpretação de relatórios e resultados (probing concorrente). Essa combinação é adotada quando a verbalização espontânea é insuficiente para capturar a compreensão semântica de elementos visuais como Balancete e DRE.

**Perguntas específicas que o teste deve responder:**

- Os usuários conseguem navegar entre os módulos sem orientação?
- O formulário de lançamento contábil (códigos de conta, débito/crédito, validações) é compreendido sem treinamento?
- As mensagens de erro são claras o suficiente para o usuário corrigir o que está errado?
- O fluxo de Apuração — que exibe uma prévia antes de confirmar — é entendido como tal (prévia vs. ação real)?
- A restrição "desfazer apenas a apuração mais recente" é percebida e compreendida?
- A DRE e o Balancete comunicam visualmente o resultado (lucro/prejuízo) de forma clara?

---

## 2. Perfil dos Participantes

| Critério | Descrição |
|---|---|
| **Curso** | Ciências Contábeis — UFMS |
| **Período** | 1º ou 2º semestre (usuário-alvo primário) |
| **Experiência contábil** | Cursando ou recém-concluído Contabilidade Básica/Introdução à Contabilidade |
| **Experiência com sistemas contábeis profissionais** | Nenhuma ou mínima (objetivo do sistema é justamente ser a primeira exposição) |
| **Quantidade recomendada** | 5 participantes (suficiente para identificar ~85% dos problemas recorrentes) |
| **Exclusão** | Participantes que já usaram o COIN'S em versões anteriores |

> **Nota de recrutamento:** Priorizar alunos que nunca viram o sistema. Evitar alunos que participaram do desenvolvimento ou dos testes automatizados.

---

## 3. Ambiente e Materiais

### 3.1 Configuração física

- Computador com o COIN'S instalado e em estado inicial (ver [Seção 11](#11-estado-inicial-do-sistema))
- Mesa e cadeira confortáveis
- Moderador sentado ao lado (não à frente) do participante para não intimidar
- Observador silencioso opcional — posicionado atrás e fora do campo de visão do participante

### 3.2 Gravação

- Gravar tela + áudio com ferramenta de captura (OBS, Loom ou similar)
- Solicitar consentimento por escrito antes de iniciar
- Informar que a gravação é para análise interna e não será divulgada

### 3.3 Materiais necessários

- [ ] Termo de consentimento (1 via para o participante, 1 via para o arquivo)
- [ ] Este documento impresso (roteiro do moderador + guia de observação)
- [ ] Formulário de registro em branco (1 por sessão) — [Seção 8](#8-formulário-de-registro-por-sessão)
- [ ] Formulário SUS adaptado impresso — [Seção 9](#9-formulário-de-percepção-pós-sessão-sus-adaptado)
- [ ] Caneta para o observador anotar
- [ ] Referência de lançamentos impressa (uso exclusivo do moderador — ver Seção 3.4)

### 3.4 Referência de lançamentos — uso exclusivo do moderador (NÃO entregar ao participante)

> As orientações abaixo são transmitidas verbalmente durante a tarefa T2. O moderador lê cada lançamento em voz alta conforme o participante avança.

| Lançamento | Débito | Crédito |
|---|---|---|
| 1 | CAIXA GERAL | VENDA DE MERCADORIAS |
| 2 | ALUGUÉIS DE IMÓVEIS | CAIXA GERAL |
| 3 | MATERIAL DE ESCRITÓRIO | CONTAS A PAGAR |

> O participante escolhe livremente os valores — o importante é que débito e crédito estejam equilibrados. Consulte o Plano de Contas no sistema para encontrar os códigos.

---

### 3.5 Gabarito — uso exclusivo do moderador (NÃO entregar ao participante)

> O participante deve consultar o Plano de Contas no sistema para encontrar os códigos. Este gabarito serve apenas para o moderador acompanhar se o participante chegou às contas corretas.

| Lançamento | Débito | Crédito |
|---|---|---|
| 1 — Venda de mercadorias à vista | CAIXA GERAL — `1.1.1.01.001` | VENDA DE MERCADORIAS — `5.1.1.01.002` |
| 2 — Pagamento de aluguel | ALUGUÉIS DE IMÓVEIS — `4.2.2.02.001` | CAIXA GERAL — `1.1.1.01.001` |
| 3 — Material de escritório a prazo | MATERIAL DE ESCRITÓRIO — `4.2.2.04.006` | CONTAS A PAGAR — `2.1.5.01.001` |

**Armadilha esperada — conta sintética:**
A conta `CAIXA` (classificação `1.1.1.01`) existe no Plano de Contas mas é **sintética** (`is_analytic: false`). O participante pode tentá-la antes de encontrar `CAIXA GERAL` (`1.1.1.01.001`), que é a analítica correta. Isso é um comportamento de observação valioso — anotar se ocorreu.

**Valores:** livres — participante escolhe. Anotar os valores registrados para referência durante a edição.

---

## 4. Procedimento da Sessão

| Etapa | Duração estimada | Descrição |
|---|:---:|---|
| Recepção e consentimento | 5 min | Apresentação, termo de consentimento, objetivo geral sem revelar detalhes |
| Aquecimento | 5 min | Perguntas sobre experiência contábil e uso de sistemas |
| Instrução think aloud | 5 min | Explicar e praticar a técnica com tarefa neutra |
| Tarefas (T1 a T5) | 35–45 min | Execução com verbalização |
| Questionário pós-sessão | 5 min | Formulário SUS adaptado |
| Debriefing | 10 min | Entrevista de encerramento |
| **Total** | **~60 min** | |

---

## 5. Roteiro do Moderador

### 5.1 Abertura (ler em voz alta)

> "Olá, obrigado por participar. Hoje vamos testar um sistema chamado COIN'S, desenvolvido para estudantes de Ciências Contábeis.
>
> Quero deixar claro: **estamos testando o sistema, não você**. Não existe resposta certa ou errada. Se você encontrar dificuldade, é exatamente isso que precisamos saber — isso nos ajuda a melhorar o sistema.
>
> Vou pedir que você use o sistema em voz alta, verbalizando tudo o que estiver pensando enquanto faz as tarefas — o que está vendo, o que está tentando fazer, o que está confuso, o que está esperando que aconteça. É como se você estivesse pensando em voz alta.
>
> Eu não vou te ajudar durante as tarefas, mesmo que você travar — mas posso lembrar você de continuar verbalizando se parar. Se você desistir de uma tarefa, tudo bem, seguimos para a próxima.
>
> Alguma dúvida antes de começar?"

### 5.2 Prática de think aloud (tarefa neutra)

Antes das tarefas do sistema, peça ao participante para verbalizar enquanto abre um aplicativo qualquer do computador (calculadora, bloco de notas). Corrija gentilmente se o participante parar de verbalizar ou começar a explicar para você em vez de pensar em voz alta.

### 5.3 Durante as tarefas — intervenções permitidas

| Situação | O que dizer |
|---|---|
| Participante para de verbalizar | *"Continue pensando em voz alta."* |
| Participante pede confirmação de acerto | *"O que você acha? Continue."* |
| Participante pergunta como fazer | *"O que você tentaria fazer?"* |
| Participante desiste e fica em silêncio | *"Tudo bem, podemos passar para a próxima tarefa."* |
| Participante trava >2 minutos sem progresso | Anote, e se julgar necessário para não frustrar demais: *"Pode pular essa parte, vamos para o próximo passo."* |

**Nunca** diga "certo", "errado", "quase lá", ou qualquer avaliação do desempenho.

### 5.4 Debriefing (após questionário SUS)

Perguntas para encerramento:

1. "Qual parte do sistema você achou mais difícil? Por quê?"
2. "Teve alguma coisa que você esperava que o sistema fizesse de um jeito e ele fez diferente?"
3. "Quando o sistema exibiu mensagens de erro, ficou claro o que você deveria fazer para corrigir?"
4. "O que você mais gostou no sistema?"
5. "Se você pudesse mudar uma coisa, o que seria?"

---

## 6. Tarefas

> **Instrução para o moderador:** Leia as orientações de cada tarefa em voz alta. Não dê dicas adicionais. Inicie o cronômetro assim que terminar de ler.

---

### T1 — Exploração inicial

**Duração máxima:** 5 minutos

**O que ler ao participante:**

> *"Explore o sistema. Diga o que está vendo, o que acha que ele faz e onde você pode ir."*

---

### T2 — Registrar lançamentos contábeis

**Duração máxima:** 18 minutos

**O que ler ao participante:**

> *"Registre os três lançamentos que vou passar. Use a empresa cadastrada. Você escolhe os valores — débito e crédito devem estar equilibrados."*

Ler cada lançamento e aguardar o registro antes de passar ao próximo:

1. > *"Débito: CAIXA GERAL. Crédito: VENDA DE MERCADORIAS."*
2. > *"Débito: ALUGUÉIS DE IMÓVEIS. Crédito: CAIXA GERAL."*
3. > *"Débito: MATERIAL DE ESCRITÓRIO. Crédito: CONTAS A PAGAR."*

Após os três lançamentos registrados:

> *"Corrija o valor do primeiro lançamento — use um valor diferente do que registrou."*

---

### T3 — Gerar e interpretar o Balancete

**Duração máxima:** 8 minutos

**O que ler ao participante:**

> *"Verifique se o total de débitos e créditos dos lançamentos do mês atual estão iguais."*

Após o participante localizar o relatório:

> *"O que esse relatório está dizendo sobre o resultado da empresa?"*

---

### T4 — Apuração do Resultado e Desfazer

**O que ler ao participante:**

**Parte A — Realizar a apuração:**

> *"Encerre o período contábil e obtenha o resultado do exercício da empresa."*

**Parte B — Verificar saldos após o encerramento (ler após a confirmação):**

> *"Verifique os saldos das contas e o resultado da empresa."*

**Parte C — Desfazer (ler após a verificação dos saldos):**

> *"Você esqueceu de registrar um lançamento antes de encerrar o período. Reverta o que acabou de fazer."*

---

### T5 — Visualizar e exportar a DRE

**O que ler ao participante (após desfazer, registrar o lançamento esquecido e re-apurar):**

> *"Descubra qual foi o lucro líquido da empresa nesse período."*

Após o participante localizar o valor:

> *"Exporte esse relatório em PDF e em CSV."*

---

## 7. Guia de Observação

Use este guia em paralelo ao Formulário de Registro. Para cada tarefa, marque os comportamentos observados.

### 7.1 Conclusão de tarefas

| Código | Comportamento a observar |
|:---:|---|
| **C1** | Sucesso na tarefa sem ajuda — anotar caminho percorrido |
| **C2** | Falha na tarefa — anotar ponto de bloqueio |

### 7.2 Erros e impedimentos

| Código | Comportamento a observar |
|:---:|---|
| **E1** | Erro crítico — bloqueia execução durante a tarefa |
| **E2** | Erro recuperável — cliques incorretos, participante se corrige |

### 7.3 Passos extras e atritos

| Código | Comportamento a observar |
|:---:|---|
| **A1** | Ações desnecessárias: rolagens, voltas, menus reabertos |
| **A2** | Hesitações e pausas longas |
| **A3** | Silêncio ou cursor parado por mais de 2s |

### 7.4 Navegação

| Código | Comportamento a observar |
|:---:|---|
| **N1** | Ordem real das telas visitadas — registrar sequência |
| **N2** | Uso do botão "Voltar" (intencional vs. acidental) |
| **N3** | Atalhos acionados |

### 7.5 Citações do think-aloud

| Código | Comportamento a observar |
|:---:|---|
| **T1** | Frases que expressem emoções ou expectativas — transcrever literalmente |

### 7.6 Reações não verbais

| Código | Comportamento a observar |
|:---:|---|
| **R1** | Expressões faciais, suspiros, risos, frustrações — anotar momento e tarefa |

### 7.7 Satisfação imediata

| Código | Comportamento a observar |
|:---:|---|
| **S1** | Tom de voz e comentários ao concluir cada tarefa |

### 7.8 Sugestões espontâneas

| Código | Comportamento a observar |
|:---:|---|
| **SU1** | Ideias ou melhorias mencionadas sem serem solicitadas — transcrever literalmente |

### 7.9 Perguntas diretas ao participante

Fazer ao final de cada bloco de tarefas, antes do debriefing geral:

1. > *"A hierarquia por blocos do Plano de Contas foi útil ou confusa?"*
2. > *"Os filtros automáticos foram perceptíveis durante a busca?"*
3. > *"Consultar o Plano de Contas e adicionar um lançamento ao mesmo tempo foi fácil ou difícil?"*
4. > *"Você usaria a função de importar ou exportar dados? Para quê?"*

---

## 8. Formulário de Registro por Sessão

> Preencher um formulário por participante durante a sessão.

---

**Participante #:** ______ &nbsp;&nbsp; **Data:** __________ &nbsp;&nbsp; **Moderador:** ______________________

**Período/Semestre:** ______ &nbsp;&nbsp; **Já usou software contábil antes?** ( ) Sim ( ) Não

---

### Registro por tarefa

Para cada tarefa, registre:
- **Tempo** (início → conclusão ou abandono)
- **Resultado**: ✅ concluiu sem ajuda | ⚠️ concluiu com dificuldade | ❌ não concluiu
- **Observações**: verbalizações relevantes, comportamentos marcantes, erros cometidos

| Tarefa | Tempo (min) | Resultado | Observações |
|:---:|:---:|:---:|---|
| T1 — Exploração inicial | | | |
| T2 — Lançamentos | | | |
| T3 — Balancete | | | |
| T4 — Apuração e Desfazer | | | |
| T5 — DRE | | | |

---

### Incidentes críticos

Liste aqui qualquer momento de bloqueio prolongado, erro recorrente, verbalização de frustração ou confusão significativa:

| # | Tarefa | O que aconteceu | Possível causa |
|:---:|:---:|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |

---

### Notas gerais da sessão

_Espaço livre para observações do moderador sobre o comportamento geral do participante, padrões percebidos, ou qualquer coisa relevante não capturada acima._

```
_______________________________________________________________________________

_______________________________________________________________________________

_______________________________________________________________________________
```

---

## 9. Formulário de Percepção Pós-Sessão (SUS adaptado)

> Entregar ao participante após concluir todas as tarefas. Resposta em escala de 1 a 5:
> **1 = Discordo totalmente** | **5 = Concordo totalmente**

**Participante #:** ______ &nbsp;&nbsp; **Data:** __________

| # | Afirmação | 1 | 2 | 3 | 4 | 5 |
|:---:|---|:---:|:---:|:---:|:---:|:---:|
| 1 | Eu me sentiria confortável em usar este sistema com frequência. | | | | | |
| 2 | Achei o sistema desnecessariamente complexo. | | | | | |
| 3 | Consegui realizar as tarefas sem precisar de ajuda externa. | | | | | |
| 4 | Precisaria de muito treinamento para usar este sistema com confiança. | | | | | |
| 5 | As funções do sistema estavam bem integradas e coerentes entre si. | | | | | |
| 6 | Havia muita inconsistência no sistema (coisas que funcionavam de formas diferentes). | | | | | |
| 7 | A maioria das pessoas aprenderia a usar este sistema rapidamente. | | | | | |
| 8 | Achei o sistema difícil de usar. | | | | | |
| 9 | Me senti confiante ao usar o sistema. | | | | | |
| 10 | Precisei aprender muita coisa antes de conseguir usar o sistema. | | | | | |

> **Cálculo do SUS Score:** Itens ímpares (1,3,5,7,9): subtrair 1 de cada resposta. Itens pares (2,4,6,8,10): subtrair a resposta de 5. Somar todos os resultados e multiplicar por 2,5. Score ≥ 68 = usabilidade aceitável.

**Comentário aberto:**

> _O que você diria para um colega que fosse usar o sistema pela primeira vez?_

```
_______________________________________________________________________________

_______________________________________________________________________________
```

---

## 10. Análise e Consolidação

Após todas as sessões, consolidar os dados nesta tabela:

| Tarefa | P1 | P2 | P3 | P4 | P5 | Taxa de sucesso | Tempo médio |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| T1 — Exploração | | | | | | | |
| T2 — Lançamentos | | | | | | | |
| T3 — Balancete | | | | | | | |
| T4 — Apuração e Desfazer | | | | | | | |
| T5 — DRE | | | | | | | |

**Legenda:** ✅ = concluiu sem ajuda | ⚠️ = com dificuldade | ❌ = não concluiu

### Priorização de problemas encontrados

Para cada problema identificado, classificar:

| Problema | Tarefas afetadas | Frequência (de 5) | Severidade (1–4) | Prioridade |
|---|---|:---:|:---:|:---:|
| | | | | |

**Escala de severidade:**
- **1** — Cosmético (não impede uso)
- **2** — Menor (causa atraso, participante recupera sozinho)
- **3** — Maior (bloqueia tarefa, participante precisou de ajuda ou abandonou)
- **4** — Crítico (impede conclusão por maioria dos participantes)

---

## 11. Estado Inicial do Sistema

Para garantir consistência entre sessões, o sistema deve ser reiniciado para o estado abaixo antes de cada participante.

**Checklist de preparação:**

- [ ] Abrir o sistema
- [ ] Verificar que a empresa estática está presente (nome e CNPJ visíveis)
- [ ] Verificar que o Livro Diário está **vazio** (sem lançamentos)
- [ ] Se houver lançamentos de sessão anterior: usar a função "Deletar dados da Empresa" para limpar
- [ ] Verificar que o histórico de Apurações está **vazio**
- [ ] Fechar e reabrir o sistema para garantir estado limpo
- [ ] Iniciar gravação de tela + áudio
- [ ] Abrir o sistema na tela inicial (menu lateral exibindo "Empresas")

> **Atenção:** A função "Deletar dados da Empresa" remove apenas lançamentos — a empresa e o Plano de Contas são preservados. Isso é o comportamento esperado para a preparação.

# Instruções do Copilot

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 02/06/2026 | Criação do documento | Equipe de Desenvolvimento |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |

---

## Decisão da Equipe de Desenvolvimento

A definição do uso do GitHub Copilot nas revisões de Pull Requests foi estruturada de forma colaborativa pela equipe de desenvolvimento. Durante as discussões internas, estabeleceram-se os critérios sobre como a ferramenta deve participar do processo de revisão, considerando seu papel como apoio técnico complementar. O objetivo é permitir que o Copilot auxilie na identificação de melhorias, inconsistências e oportunidades de refatoração, atuando como reforço ao processo de análise, sem substituir a avaliação humana. Essa abordagem contribui para padronizar verificações recorrentes, fortalecer a qualidade das entregas e tornar o fluxo de revisão mais eficiente.

---

## Guia de Revisão de Pull Requests

### 1. Expectativas Centrais

- Revisar diffs de forma holística; sinalizar mudanças de lógica que afetam o fluxo de dados entre o processo principal do Electron, a API Express, a camada de banco de dados e o renderer Vue.
- Rejeitar PRs que quebrem a compilação TypeScript, linting, testes unitários Jest ou cobertura end-to-end com Playwright. Apontar testes ausentes ou desatualizados quando o comportamento muda.
- Garantir a higiene do repositório: mudanças em `package.json` devem incluir o arquivo de lock correspondente; migrações devem atualizar os artefatos SQL gerados quando aplicável; atualizações de documentação devem acompanhar as mudanças de funcionalidade.

### 2. Backend (`main/`)

- Confirmar que os controllers apenas orquestram requisições e delegam para services/repositories; regras de negócio pertencem aos services, lógica SQL/Knex nos repositories.
- Validar queries Knex quanto ao uso de parameter binding (sem interpolação de strings), uso adequado de transações em escritas multi-etapa e alinhamento com as definições de schema de entidades em `main/entities/`.
- Quando migrações (`main/migrations/`) ou seeds (`main/seed/`) mudarem, garantir que repositories/services e testes correspondentes reflitam o novo schema. Verificar se novas migrações possuem passos de down e evitam operações destrutivas sem salvaguardas.
- Para mudanças nas rotas Express em `main/server.ts` e pastas de controllers, garantir a existência de validações (ex.: campos obrigatórios, verificações de formato UUID) e que as respostas estejam em conformidade com os Swagger docs existentes.

### 3. Electron Main e Preload

- Verificar que mudanças em `main/main.ts` e `main/preload.ts` mantenham os canais IPC tipados (contratos `contextBridge.exposeInMainWorld`). Não permitir acesso direto do renderer a APIs Node além da whitelist do preload.
- Garantir que atualizações em `electron-forge`, Vite e scripts de build mantenham paridade entre as configs `.vite/` e `forge.config.ts`. Rejeitar PRs que quebrem targets de plataforma definidos nos scripts de `package.json`.

### 4. Frontend (`renderer/`)

- Verificar que componentes Vue permaneçam composition-friendly: estado em `stores/`, lógica reutilizável em `utils/` ou composables, lógica de UI apenas em components.
- Aplicar padrões de uso do Vuetify e temas consistentes; garantir que novos componentes importem tokens compartilhados (ex.: `renderer/assets/`, `renderer/plugins/vuetify.ts`).
- Para atualizações do router, confirmar que rotas carregadas por lazy-loading e guards estejam alinhados com as expectativas de autenticação/autorização.
- Garantir que tipos compartilhados em `renderer/types/` estejam sincronizados com os DTOs do backend; sinalizar tipos duplicados ou divergentes.

### 5. Testes e Gates de Qualidade

- Exigir atualizações nos testes unitários Jest (`main/tests`, `renderer/tests`) ou specs Playwright quando o comportamento mudar. Rejeitar PRs que pulem testes ou enfraqueçam asserções.
- Garantir que `main/tests/setup.ts` ou outros fixtures sejam ajustados quando os schemas do banco de dados evoluírem.
- Sinalizar atualizações ausentes no Swagger (`main/swagger.ts`) quando contratos de API mudarem.

### 6. Segurança, Performance e Operações

- Monitorar secrets ou credenciais adicionados ao repositório; insistir no uso de variáveis de ambiente e carregamento `.env` via helpers existentes.
- Sinalizar operações bloqueantes em request handlers ou componentes do renderer que possam congelar a UI. Preferir trabalho assíncrono, em lote ou em stream quando possível.
- Garantir que logging e tratamento de erros sigam os padrões existentes; sem `console.log` em caminhos de produção.
- Verificar fallback gracioso para funcionalidades específicas de plataforma (instaladores Windows, builds mac/Linux) quando scripts de build ou configs mudarem.

### 7. Documentação e Experiência do Desenvolvedor

- Exigir atualizações no README ou docs inline quando workflows, scripts ou etapas de ambiente mudarem.
- Confirmar que os docs Swagger/OpenAPI estejam precisos para novos endpoints ou mudanças de schema.
- Incentivar mensagens de commit descritivas e descrições de PR com evidências de teste e avaliação de risco.

O Copilot deve bloquear a aprovação se algum problema crítico permanecer sem resolução. Sugestões são bem-vindas, mas aprovações verdes exigem confiança de que o comportamento em runtime, a integridade dos dados e as ferramentas do desenvolvedor permanecem intactos.

---

## Agente Personalizado para Documentação e Commits

Foi criado um agente personalizado chamado `docs-agent` para auxiliar na manutenção de boas práticas de documentação e no uso de commits semânticos no projeto.

### Como Usar o Agente

- Para revisar a qualidade da documentação: invoque o agente com consultas relacionadas à documentação.
- Para verificar commits: o agente pode analisar mensagens de commit e sugerir correções para seguir o padrão semântico.

### Boas Práticas de Documentação

O agente enfatiza:

- Clareza e concisão nos documentos.
- Formatação Markdown compatível com MkDocs.
- Estrutura consistente.
- Inclusão de diagramas e exemplos relevantes.
- Manutenção de links de navegação precisos.

### Commits Semânticos

O agente reforça o uso do formato conventional commit:

- `type(scope): description`
- Tipos comuns: feat, fix, docs, style, refactor, test, chore
- Descrições em modo imperativo, curtas (até 72 caracteres).

Para mais detalhes, consulte o arquivo `.github/agents/docs-agent.agent.md`.

---

## Referências e Fundamentação

- [Documentação Oficial do GitHub Copilot](https://docs.github.com/en/copilot)

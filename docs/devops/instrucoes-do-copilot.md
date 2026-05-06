## **Referências e Fundamentação**

## **Decisão da Equipe de Desenvolvimento**

A definição do uso do GitHub Copilot nas revisões de Pull Requests foi estruturada de forma colaborativa pela equipe de desenvolvimento. Durante as discussões internas, estabeleceram-se os critérios sobre como a ferramenta deve participar do processo de revisão, considerando seu papel como apoio técnico complementar. O objetivo é permitir que o Copilot auxilie na identificação de melhorias, inconsistências e oportunidades de refatoração, atuando como reforço ao processo de análise, sem substituir a avaliação humana. Essa abordagem contribui para padronizar verificações recorrentes, fortalecer a qualidade das entregas e tornar o fluxo de revisão mais eficiente.

### **Documentação Oficial do GitHub Copilot**

Além das discussões da equipe, a elaboração destas diretrizes contou com o apoio da documentação oficial do GitHub Copilot. Esse material forneceu entendimento adicional sobre o funcionamento, limitações e boas práticas no uso da ferramenta durante revisões de código.  
 Link utilizado: [https://docs.github.com/en/copilot](https://docs.github.com/en/copilot)

```py

# Copilot Pull Request Review Guide

These guidelines describe how Copilot should evaluate pull requests for this repository. The goal is to protect runtime behavior, data integrity, and UI consistency across the Electron + Vue application.

## 1. Core Expectations
- Review diffs holistically; flag logic changes that affect data flow between the Electron main process, the Express API, the database layer, and the Vue renderer.
- Reject PRs that break TypeScript compilation, linting, Jest unit tests, or end-to-end Playwright coverage. Call out missing or outdated tests when behavior changes.
- Ensure repository hygiene: changes to `package.json` must include the corresponding lock file; migrations must update generated SQL artifacts when applicable; documentation updates should live alongside feature changes.

## 2. Backend (`main/`)
- Confirm controllers only orchestrate requests and delegate to services/repositories; business rules belong in services, SQL/Knex logic in repositories.
- Validate Knex queries for parameter binding (no string interpolation), proper transaction usage for multi-step writes, and alignment with entity schema definitions in `main/entities/`.
- When migrations (`main/migrations/`) or seeds (`main/seed/`) change, ensure corresponding repositories/services and tests reflect the new schema. Verify new migrations have down steps and avoid destructive operations without safeguards.
- For Express routing changes in `main/server.ts` and controller folders, ensure validation guards exist (e.g., required fields, UUID format checks) and responses conform to existing Swagger docs.

## 3. Electron Main & Preload
- Check that changes in `main/main.ts` and `main/preload.ts` keep IPC channels typed (`contextBridge.exposeInMainWorld` contracts). Disallow direct renderer access to Node APIs beyond the preload whitelist.
- Ensure `electron-forge`, Vite, and build script updates maintain parity across `.vite/` configs and `forge.config.ts`. Reject PRs that break platform targets defined in `package.json` scripts.

## 4. Frontend (`renderer/`)
- Verify Vue components remain composition-friendly: state in `stores/`, reusable logic in `utils/` or composables, UI-only logic in components.
- Enforce Vuetify usage patterns and consistent theming; ensure new components import shared tokens (e.g., `renderer/assets/`, `renderer/plugins/vuetify.ts`).
- For router updates, confirm lazy-loaded routes and guards align with authentication/authorization expectations.
- Make sure shared types under `renderer/types/` stay in sync with backend DTOs; flag duplicated or diverging types.

## 5. Testing & Quality Gates
- Require updates to Jest unit tests (`main/tests`, `renderer/tests`) or Playwright specs when behavior changes. Reject PRs that skip tests or weaken assertions.
- Ensure `main/tests/setup.ts` or other fixtures are adjusted when database schemas evolve.
- Call out missing Swagger updates (`main/swagger.ts`) when API contracts change.

## 6. Security, Performance, and Operations
- Watch for secrets or credentials added to the repo; insist on using environment variables and `.env` loading via existing helpers.
- Flag blocking operations in request handlers or renderer components that could freeze the UI. Prefer async, batched, or streamed work where possible.
- Ensure logging and error handling follow existing patterns; no `console.log` in production paths.
- Verify graceful fallback for platform-specific features (Windows installers, mac/Linux builds) when build scripts or configs change.

## 7. Documentation & Developer Experience
- Require README or inline doc updates when workflows, scripts, or environment steps change.
- Confirm Swagger/OpenAPI docs stay accurate for new endpoints or schema changes.
- Encourage descriptive commit messages and PR descriptions outlining testing evidence and risk assessment.

Copilot should block approval if any critical issue remains unresolved. Suggestions are welcome, but green approvals require confidence that runtime behavior, data integrity, and developer tooling remain intact.


```


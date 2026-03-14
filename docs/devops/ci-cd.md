# Infraestrutura

## **Relatório do Atual CI:**

A pipeline de CI possui os seguintes objetivos:

- Executar **testes automatizados** do backend.
- Verificar **cobertura mínima de testes**.
- Fornecer **feedback automático em Pull Requests**.
- Impedir integração de código que **não atenda aos critérios de qualidade**.

A pipeline é acionada automaticamente nas seguintes situações:

### Pull Requests

Executada quando um Pull Request é aberto ou atualizado para as branches:

```
main
develop
Subtask/**
```

A execução ocorre apenas quando há alterações nos seguintes arquivos ou diretórios:

```
my-app/main/**
my-app/package.json
my-app/package-lock.json
my-app/jest.config.js
.github/workflows/ci.yml
```

### Push

Executada automaticamente quando ocorre push direto nas branches:

```
main
develop
```

O GitHub Copilot foi integrado ao processo de desenvolvimento do sistema COINS com o objetivo de aprimorar a qualidade do código e aumentar a eficiência das revisões técnicas. A ferramenta atua como um mecanismo complementar de análise automatizada, auxiliando na identificação de problemas e na manutenção dos padrões estabelecidos neste documento.

1. **Instruções do copilot**
   1. [Instruções](https://docs.google.com/document/d/1Wp_bDh5UTZ9743nyTy1MNr-uIZD0SD_iqtQQkKMoLZ8/edit?usp=sharing)

2. ## **Funcionalidades e Aplicações** {#funcionalidades-e-aplicações}

O Copilot desempenha as seguintes funções no ciclo de desenvolvimento:

- **Análise de Código em Tempo Real**: Identifica erros de sintaxe, más práticas e potenciais bugs durante a escrita do código;
- **Conformidade com Padrões**: Auxilia na aplicação das convenções de nomenclatura e estruturação definidas (camelCase, PascalCase, SCREAMING_SNAKE_CASE);
- **Detecção de Vulnerabilidades**: Identifica possíveis falhas de segurança e práticas inseguras no código;
- **Sugestões de Refatoração**: Propõe melhorias de legibilidade, performance e manutenibilidade do código; e
- **Suporte à Documentação**: Sugere aprimoramentos em comentários e documentação quando aplicável.

3. ## **Integração no Fluxo de Trabalho** {#integração-no-fluxo-de-trabalho}

A ferramenta Copilot está disponível nas seguintes etapas do processo de desenvolvimento:

**Fase de Desenvolvimento**: Oferece sugestões e autocomplete durante a codificação

**Pull Request**: Atua como recurso adicional de verificação antes da revisão formal

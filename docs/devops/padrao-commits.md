# Padrão de Commits e Código

A adoção do Padrão de Commit Semântico não é apenas uma convenção, mas um requisito técnico que traz benefícios cruciais para a gestão de projetos e o ciclo de vida do software:

Vantagens:

- **Rastreabilidade:** Oferece **identificação instantânea** do propósito da alteração, facilitando a leitura do histórico e a revisão de código.
- **Controle de Versão:** É fundamental para o **versionamento automático** (Semantic Versioning), onde o tipo do _commit_ define qual parte da versão deve ser incrementada (ex.: feat incrementa a _minor_, fix incrementa o _patch_).
- **Qualidade:** Incentiva _commits_ mais **atômicos e focados** (um _commit_ de fix só deve corrigir, e não adicionar nova _feature_).

Estrutura:

```
<tipo>: <mensagem curta em português>
```

### Tipos permitidos:

- **feat** → nova funcionalidade
- **fix** → correção de bug
- **docs** → alterações na documentação
- **style** → ajustes de formatação (sem impacto no código)
- **refactor** → alteração de código sem mudar comportamento
- **test** → adição ou ajuste de testes
- **chore** → mudanças que não afetam o código de produção (ex.: .gitignore)
- **build** → mudanças em build ou dependências

## **Convenções de Código**

- **Variáveis, funções e métodos** → camelCase
- **Constantes** → SCREAMING_SNAKE_CASE
- **Classes** → PascalCase
- Nomes claros e em **inglês**
- Comentários em português, **apenas quando necessário** para explicar lógica complexa.

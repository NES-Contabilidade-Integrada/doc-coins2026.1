# Geração do Executável e Problemas Conhecidos

## Histórico de Versões

| Versão | Data | Descrição | Autor |
| :---: | :---: | :--- | :--- |
| 1.0 | 16/10/2025 | Adicionando versão inicial do documento | Pedro Nicoletti Sotoma |
| 2.0 | 02/06/2026 | Atualizando documento para nova versão do COIN'S | Vinicius Carneiro |

## Histórico de Revisões

| Versão | Data | Revisor | Observação |
| :---: | :---: | :--- | :--- |
| 1.0 | 25/11/2025 | Fernanda Pessoa | Aprovada |

---

## Introdução

Este guia explica como gerar o executável do nosso projeto e detalha os principais desafios de configuração que encontramos, servindo como um manual de consulta para futuras manutenções.

---

## Configuração do Ambiente de Desenvolvimento

Para executar o projeto localmente em modo desenvolvimento, siga os passos abaixo.

**1.** Clone o repositório e entre no diretório da aplicação:

```bash
cd .\my-app\
```

**2.** Instale as dependências:

```bash
npm install
```

**3.** Execute o projeto em modo desenvolvimento:

```bash
npm start
```

> Não é necessário configurar variáveis de ambiente para este projeto.

---

## Geração do Executável

A geração do executável acontece de duas maneiras:

### Geração Manual

**1.** Execute o comando:

```bash
npm run make:win
```

Essa facilidade no processo de gerar o executável acontece graças ao Electron Forge, que cuida do empacotamento e da otimização do executável, evitando um aplicativo final desnecessariamente pesado. Ao mesmo tempo, o conjunto de tecnologias e dependências utilizados pode gerar uma complexidade de configuração do projeto para que tudo funcione harmonicamente, que será o assunto do próximo tópico.

**2.** Após finalizado o processo, abra a pasta gerada, entre no diretório `Make` e navegue até o diretório `x64`.

**3.** Execute o arquivo `Setup.exe`.

!!! warning "Aviso do Windows"
    O Windows pode alertar que o arquivo é desconhecido ou "perigoso". Isso ocorre porque o executável não possui assinatura de código comercial — a execução não oferece risco algum.

**4.** Aguarde a finalização da instalação. O aplicativo estará pronto para uso.

### Geração Automática via GitHub Actions

Sempre que um Pull Request é aprovado e incorporado à branch de release, o pipeline de integração contínua executa o processo de build e empacotamento da aplicação, gerando automaticamente um novo executável.

Dessa forma, não é necessário gerar o executável manualmente para cada alteração aceita na release. O comando manual deve ser utilizado apenas em casos de teste local, validação antes do PR ou situações em que seja necessário reproduzir o processo de empacotamento fora do pipeline.

---

## Problemas Conhecidos e Complexidades Envolvidas

A integração entre TypeScript, Vue3 + Vite, Express e Knex com better-sqlite3 em um ambiente Electron introduz desafios específicos. A seguir, detalhamos os pontos de atenção nos principais arquivos de configuração.

### 3.1 Configurações do Vite

Para que o Vite funcione corretamente no ambiente do Electron, precisamos alinhar três arquivos de configuração principais.

- **vite.preload.config.ts**: este arquivo aponta para o script de preload do projeto. A configuração é simples: basta garantir que o caminho e o target do build estejam corretos. Geralmente, não exige muita manutenção.
- **vite.renderer.config.ts**: similar ao anterior, este arquivo precisa do caminho correto para o código do renderer (a parte do Vue.js). Também é um arquivo de configuração simples.
- **vite.main.config.ts**: este é o arquivo de configuração mais crítico e a principal fonte de problemas.
  - **Dependências externas (external)**: a principal tarefa aqui é declarar quais dependências são externas ao Vite. De forma simplificada, todas as dependências do backend (Node.js, Express, Knex, etc.) devem ser listadas aqui. Se uma dependência do backend não for declarada como externa, o executável irá quebrar.
  - **O problema do Knex**: bibliotecas como o Knex possuem requires dinâmicos, ou seja, elas tentam carregar outras dependências que talvez você nem use. Mesmo utilizando apenas o better-sqlite3, o Knex mantém referências a outros drivers de banco de dados. Por isso, precisamos adicionar oracledb, mysql, mysql2, entre outros, na lista de external, mesmo sem usá-los diretamente. Se forem removidos, a aplicação quebrará.
  - **Workaround para referências**: em alguns casos, como com pg-query-stream, apenas declarar como external não resolve. A solução é enganar o Vite, apontando a referência para um arquivo vazio. Isso evita erros de importação que podem impedir a execução.
  - **Dificuldade envolvendo as seeds**: um dos pontos de atenção do projeto está relacionado às seeds do banco de dados. Como a aplicação utiliza um banco SQLite local, os dados iniciais, como empresa padrão, plano de contas e estruturas contábeis necessárias para o funcionamento do sistema, precisam ser carregados corretamente no momento de criação ou recriação do banco. A principal dificuldade é garantir que essas seeds permaneçam compatíveis com as migrations e com a versão atual da aplicação. Quando há alteração na estrutura das tabelas ou nos dados esperados pelo sistema, seeds antigas ou incompletas podem causar inconsistências, erros de inicialização ou comportamentos inesperados nas telas que dependem desses dados iniciais.

### 3.2 Configurações do Forge (forge.config.ts)

O Electron Forge também precisa de atenção em seu arquivo de configuração, principalmente por causa do empacotamento com asar.

- **Empacotamento com asar**: o asar é um formato que otimiza o código da aplicação, tornando-a mais rápida. No entanto, alguns arquivos não funcionam corretamente se estiverem empacotados.
  - **Desempacotar módulos nativos (unpack)**: é fundamental garantir que arquivos de módulos nativos (.node, .dll, .dylib, .so) sejam desempacotados. A configuração deve instruir o Forge a mantê-los fora do pacote asar.
  - **Recursos extras (extraResource)**: pastas que contêm arquivos essenciais e que não devem ser alterados, como nossas pastas de migrations e seeds, precisam ser declaradas como extraResource. Isso garante que elas sejam copiadas para a versão final do aplicativo sem compressão, preservando sua integridade. Se os caminhos dessas pastas mudarem, lembre-se de atualizar também os arquivos knexfile.ts e connection.ts.
  - **Ignorar arquivos**: também é uma boa prática configurar o Forge para ignorar arquivos desnecessários no pacote final (ex: arquivos de configuração de lint, testes, etc.).

### 3.3 Gerenciamento do Banco de Dados Local

Atualmente, o banco de dados (data.db) é persistido no computador do usuário, o que permite que seu progresso seja salvo entre as sessões.

- **O desafio**: quando alteramos a estrutura das tabelas (migrations) ou os dados iniciais (seeds), o arquivo de banco de dados antigo do usuário se torna incompatível e pode causar erros na inicialização do aplicativo.
- **A solução (temporária)**: a forma mais simples de resolver isso é apagar o arquivo do banco de dados local. A aplicação irá recriá-lo do zero na próxima vez que for aberta, já com a nova estrutura.
- **Onde encontrar o arquivo do banco**:
  - **Windows**: `C:\Users\<seu-usuario>\AppData\Roaming\my-app\data.db`
  - **Linux**: `/home/<seu-usuario>/.config/my-app/data.db`
- **Próximos passos**: será alinhado com o proponente se é interessante manter essa abordagem ou apagar e remontar o banco de dados toda vez que a aplicação for iniciada. Caso a segunda opção seja escolhida, esses processos não serão necessários.

---

## Conclusão

Os problemas apresentados foram os mais complexos que enfrentamos. Mantendo a arquitetura e as configurações atuais do projeto, eles não devem ocorrer com frequência. No entanto, é fundamental ter cuidado redobrado ao adicionar novas dependências, pois elas podem exigir ajustes nos arquivos de configuração mencionados neste guia.

Ao se deparar com erros no executável que não aparecem no console, fiquem atentos a um arquivo chamado "errors" que é um .txt gerado com o erro completo no mesmo diretório do banco de dados. Ele foi criado manualmente justamente para facilitar a depuração de erros no executável, que se torna complexo sem informações no console.

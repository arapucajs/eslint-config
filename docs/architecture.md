# Arquitetura

## Objetivo e fronteira

O pacote oferece presets flat config para projetos de aplicação e pacote. Ele não inicia o ESLint, descobre o projeto, executa comandos ou contém regras próprias em arquivos separados. `index.js` monta e retorna blocos de configuração usando `typescript-eslint`.

## Montagem do preset

As funções `configPkg` e `configApp` constroem um array flat config com quatro partes compartilhadas: ignores globais, `tseslint.configs.base`, registro de plugins e regras padrão aplicadas a `INCLUDE_LIST`. Os blocos passados pelo consumidor são concatenados por último, seguindo a ordem de argumentos.

`configApp` restringe adicionalmente o bloco de regras a `APP_IGNORE_LIST`. Os padrões globais estão em `GLOBAL_IGNORE_LIST`. A semântica de objetos de configuração, merges e matching de `files`/`ignores` é a semântica do ESLint flat config.

## Plugins e regras

`PLUGINS_LIST` importa e registra Unicorn, Stylistic, Prettier e `@arapucajs/eslint-plugin`. `RULES_LIST` combina regras core, TypeScript, Unicorn, regras do recomendado Prettier e regras específicas ArapucaJS.

O plugin ArapucaJS é instalado como dependência de runtime; importado como objeto default; registrado no namespace `@arapucajs`; e suas regras são ligadas explicitamente. Os detalhes da regra residem no repositório do plugin.

## Publicação

O pacote é ESM e seu ponto de entrada publicado é `index.js`. O workflow publica o pacote conforme gatilhos de release definidos em `.github/workflows/`. A referência de automação distingue os workflows locais dos jobs compartilhados.

## Limites atuais

- Não há presets “recommended” nomeados nem export default: o consumidor chama `configPkg` ou `configApp`.
- Os scripts locais `test`, `lint`, `typecheck` e `build` são placeholders e não oferecem validação real.
- A configuração suporta os tipos de arquivo definidos em `INCLUDE_LIST`; `.tsx` não está nessa lista padrão.
- Alterar níveis, ignores e ordem dos blocos pode mudar comportamento em todos os consumidores do pacote.

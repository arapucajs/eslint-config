# Pacote e compatibilidade

## Manifesto

`package.json` declara:

- nome `@arapucajs/eslint-config` e módulo ESM;
- entrada principal `index.js`, também o único arquivo explicitamente incluído em `files`;
- peer dependencies ESLint `^10.13.0` e Prettier `^3.9.10` no estado atual deste checkout;
- dependências de runtime: `@arapucajs/eslint-plugin`, `@stylistic/eslint-plugin`, `eslint-config-prettier`, `eslint-plugin-prettier`, `eslint-plugin-unicorn` e `typescript-eslint`.

`package-lock.json` fixa resoluções para npm. Ao mudar dependências, atualize o lockfile junto com `package.json`.

## Compatibilidade do plugin ArapucaJS

O manifesto atual solicita `@arapucajs/eslint-plugin: ^1.3.0`. Essa linha inclui as regras de Inertia Link/Form e `no-backend-import-in-frontend`, além das regras lazy já existentes. O pacote plugin declara ESLint `^10.13.0` como peer dependency; mantenha os ranges de peers alinhados entre os dois pacotes. O `typescript-eslint` usado pela configuração também deve aceitar ESLint 10; a versão declarada é `^8.72.0`.

## Empacotamento

O campo `files` publica `index.js`. Os demais arquivos do repositório, incluindo fontes de configuração, workflow e documentação, não fazem parte do conteúdo publicado, exceto inclusões automáticas do npm como manifests e licença.

Não há engine `node` declarada neste `package.json`. Requisitos adicionais de Node devem ser documentados apenas quando forem declarados ou validados pelas dependências e automações.

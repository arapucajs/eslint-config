# API pública

O pacote usa ESM (`type: module`) e publica `index.js`. Os exports abaixo são definidos nesse arquivo.

## `configPkg(...configBlocksToMerge)`

Retorna um flat config composto por:

1. um bloco global com `GLOBAL_IGNORE_LIST`;
2. `tseslint.configs.base`;
3. um bloco que registra os plugins em `PLUGINS_LIST`;
4. um bloco chamado `Arapuca pkg defaults`, direcionado a `INCLUDE_LIST` e com `RULES_LIST`;
5. cada bloco recebido como argumento, na ordem fornecida.

## `configApp(...configBlocksToMerge)`

Tem a mesma estrutura, mas seu bloco de regras usa o nome `Arapuca app defaults` e a lista adicional `APP_IGNORE_LIST`. A lista adicional tem efeito no bloco de regras da aplicação; o bloco global de ignores é compartilhado com `configPkg`.

## Constantes exportadas

| Export               | Valor / finalidade                                                                                                                  |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `INCLUDE_LIST`       | `['**/*.ts', '**/*.js']`; arquivos aos quais o bloco de regras padrão se aplica                                                     |
| `GLOBAL_IGNORE_LIST` | Configuração ESLint, minificados, declarações `.d.ts`, changelog, saídas, assets de build, lockfiles npm/yarn/pnpm e `node_modules` |
| `APP_IGNORE_LIST`    | `public/assets/**`, `__snapshots__/**`, `resources/**`                                                                              |
| `PLUGINS_LIST`       | Plugins `@arapucajs`, `@unicorn`, `@stylistic` e os plugins exportados pelo preset recommended do ESLint Prettier                   |
| `RULES_LIST`         | Regras core, TypeScript, Unicorn, Prettier e ArapucaJS habilitadas pelo preset                                                      |

As constantes são valores exportados e podem ser importadas para compor blocos customizados. Para nomes e níveis detalhados, consulte [regras habilitadas](rules.md).

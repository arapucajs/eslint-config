# Plugins e regras habilitadas

`PLUGINS_LIST` registra os plugins utilizados por `RULES_LIST`. O namespace `@arapucajs` recebe o objeto default de `@arapucajs/eslint-plugin`.

## Regras ArapucaJS

| Nome                                       | Nível padrão | Comportamento resumido                                            |
| ------------------------------------------ | ------------ | ----------------------------------------------------------------- |
| `@arapucajs/prefer-lazy-controller-import` | `error`      | Recomenda import lazy em chamadas de rota reconhecidas            |
| `@arapucajs/prefer-lazy-listener-import`   | `error`      | Recomenda import lazy em listeners associados a `.on()`           |
| `@arapucajs/prefer-adonisjs-inertia-link`  | `warn`       | Recomenda o `Link` tipado de `@adonisjs/inertia`                  |
| `@arapucajs/prefer-adonisjs-inertia-form`  | `warn`       | Recomenda o `Form` tipado de `@adonisjs/inertia`                  |
| `@arapucajs/no-backend-import-in-frontend` | `error`      | Bloqueia imports não permitidos de backend em arquivos `inertia/` |

Essas regras são fornecidas pelo pacote plugin, e seus nomes/limites estão sujeitos à versão instalada. Consulte [a documentação do plugin](https://github.com/arapucajs/eslint-plugin/tree/main/docs) para os detalhes de detecção, opção `allowed`, correções e limitações. O preset desta configuração define níveis, mas não redefine a implementação das regras.

## Outras famílias

- **ESLint core:** regras de whitespace, fluxo de controle, igualdade, segurança e convenções gerais listadas em `RULES_LIST`.
- **TypeScript ESLint:** `@typescript-eslint/no-shadow` e `@typescript-eslint/naming-convention`.
- **Unicorn:** convenções de módulos, caminhos Node, nomes de arquivo e outras regras indicadas por `@unicorn/*`.
- **Prettier:** regras do preset `eslint-plugin-prettier/recommended`, com `prettier/prettier` configurada para `{ endOfLine: 'auto' }`.
- **Stylistic:** o plugin é registrado com namespace `@stylistic`; esta versão da lista mantém algumas regras ESLint core correspondentes desligadas.

As regras e opções exatas são as constantes no arquivo `index.js`; evite inferir regras habilitadas apenas pelo fato de um plugin estar registrado.

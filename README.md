# @arapucajs/eslint-config

Configuração flat compartilhada do ESLint para projetos TypeScript e JavaScript da ArapucaJS. O pacote exporta duas funções (`configPkg` e `configApp`) que combinam regras base, plugins e padrões de arquivos. Também integra as cinco regras do [@arapucajs/eslint-plugin](https://github.com/arapucajs/eslint-plugin).

[![npm-image]][npm-url] [![license-image]][license-url]

## Requisitos

As versões suportadas são definidas no `package.json`:

- ESLint `^10.13.0`
- Prettier `^3.9.10`
- Node.js compatível com essas versões e dependências

## Instalação

```sh
npm install --save-dev @arapucajs/eslint-config eslint prettier
```

O pacote instala seus plugins como dependências. ESLint e Prettier são peer dependencies e devem estar disponíveis no projeto consumidor.

## Uso

Escolha o preset conforme o tipo do projeto.

Para um pacote ou biblioteca:

```js
// eslint.config.js
import { configPkg } from '@arapucajs/eslint-config'

export default configPkg()
```

Para uma aplicação:

```js
// eslint.config.js
import { configApp } from '@arapucajs/eslint-config'

export default configApp()
```

Ambos incluem arquivos `.ts` e `.js`, registram os plugins TypeScript, Unicorn, Stylistic, Prettier e ArapucaJS, e aplicam `RULES_LIST`. `configApp` também ignora assets web, snapshots e `resources/` nos blocos de regras da aplicação.

## Estender a configuração

Passe um ou mais blocos flat config como argumentos posicionais. Eles são acrescentados depois dos blocos padrão, permitindo especializar arquivos ou substituir regras:

```js
import { configApp } from '@arapucajs/eslint-config'

export default configApp(
  {
    name: 'Custom TypeScript rules',
    files: ['src/**/*.ts'],
    rules: {
      '@arapucajs/prefer-adonisjs-inertia-link': 'error',
    },
  },
  {
    name: 'Generated files',
    ignores: ['src/generated/**'],
  }
)
```

## Regras do plugin ArapucaJS

O preset registra `@arapucajs/eslint-plugin` com o namespace `@arapucajs` e habilita:

| Regra                           | Nível padrão |
| ------------------------------- | ------------ |
| `prefer-lazy-controller-import` | error        |
| `prefer-lazy-listener-import`   | error        |
| `prefer-adonisjs-inertia-link`  | warn         |
| `prefer-adonisjs-inertia-form`  | warn         |
| `no-backend-import-in-frontend` | error        |

Consulte a [referência das regras](docs/references/rules.md) para escopo, opções, limites e correções automáticas.

## Exports

O ponto de entrada `index.js` exporta `configPkg`, `configApp`, `INCLUDE_LIST`, `GLOBAL_IGNORE_LIST`, `APP_IGNORE_LIST`, `PLUGINS_LIST` e `RULES_LIST`. Detalhes estão na [referência da API](docs/references/api.md).

## Desenvolvimento e documentação

Os scripts do pacote ainda incluem placeholders para lint, testes, typecheck e build. Veja [desenvolvimento](docs/guides/development.md) antes de usá-los como verificação. A documentação detalhada do projeto está no [índice de docs](docs/README.md).

Toda mudança em código, configuração, dependências, scripts, CI ou exemplos deve atualizar a documentação correspondente na mesma alteração.

## Licença

MIT. Consulte [LICENSE](LICENSE).

[npm-image]: https://img.shields.io/npm/v/@arapucajs/eslint-config/latest.svg?style=for-the-badge&logo=npm
[npm-url]: https://www.npmjs.com/package/@arapucajs/eslint-config
[license-image]: https://img.shields.io/github/license/arapucajs/eslint-config?style=for-the-badge
[license-url]: LICENSE

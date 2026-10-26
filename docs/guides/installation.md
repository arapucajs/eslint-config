# Instalação e configuração

## Compatibilidade

As peer dependencies declaradas em `package.json` são ESLint `^10.13.0` e Prettier `^3.9.10`. Instale o pacote e seus peers no projeto consumidor:

```sh
npm install --save-dev @arapucajs/eslint-config eslint prettier
```

As dependências de plugins, incluindo `@arapucajs/eslint-plugin` e `typescript-eslint`, são instaladas pelo pacote de configuração.

## Pacote ou biblioteca

Crie `eslint.config.js` na raiz do projeto:

```js
import { configPkg } from '@arapucajs/eslint-config'

export default configPkg()
```

## Aplicação

Para uma aplicação, use:

```js
import { configApp } from '@arapucajs/eslint-config'

export default configApp()
```

`configApp` aplica uma lista adicional de ignores para `public/assets/**`, `__snapshots__/**` e `resources/**` ao bloco que aplica as regras. `GLOBAL_IGNORE_LIST` se aplica a ambas as fábricas.

## Estender e ajustar regras

As funções aceitam qualquer quantidade de blocos flat config como argumentos posicionais. Os blocos são passados no final da lista, depois dos defaults:

```js
import { configApp } from '@arapucajs/eslint-config'

export default configApp({
  name: 'Adjust project rules',
  files: ['app/**/*.ts'],
  rules: {
    '@arapucajs/prefer-adonisjs-inertia-link': 'error',
    '@arapucajs/no-backend-import-in-frontend': ['error', { allowed: ['#shared/**'] }],
  },
})
```

Use as opções de cada regra conforme a [referência do plugin](https://github.com/arapucajs/eslint-plugin/tree/main/docs/reference/rules.md). Não é necessário registrar manualmente o plugin ArapucaJS: o preset já o inclui.

## Configuração completa

Os arquivos analisados e ignorados, além das regras, estão descritos em [API pública](../references/api.md) e [Regras habilitadas](../references/rules.md).

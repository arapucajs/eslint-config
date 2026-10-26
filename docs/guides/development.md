# Desenvolvimento e verificações

## Arquivos principais

- `index.js`: implementação ESM dos presets, plugins, ignores e regras.
- `eslint.config.js`: auto configuração deste repositório via `configPkg()`.
- `package.json`: compatibilidade, dependências, scripts e arquivos publicados.
- `package-lock.json`: árvore de dependências npm.
- `.github/workflows/`: verificações, releases e publicação.
- `docs/`: documentação do consumidor e da manutenção.

## Scripts declarados

| Comando             | Estado atual                                                       |
| ------------------- | ------------------------------------------------------------------ |
| `npm run format`    | Executa `prettier --write .`                                       |
| `npm run lint`      | Placeholder que imprime “no test specified” e termina com sucesso  |
| `npm test`          | Placeholder que imprime “no test specified” e termina com sucesso  |
| `npm run typecheck` | Placeholder que imprime “no test specified” e termina com sucesso  |
| `npm run build`     | Placeholder que imprime “no build specified” e termina com sucesso |

Os comandos placeholder não verificam código. Não interprete seu exit code zero como lint, teste, typecheck ou build concluído.

## Formatar e inspecionar mudanças

O Prettier é configurado por `@arapucajs/prettier`. Para formatar o repositório, use `npm run format`; revise o diff para garantir que apenas as alterações esperadas foram formatadas. Para a mudança em si, inspecione os exports e regras efetivos com leitura de `index.js` e valide exemplos de configuração no consumidor quando possível.

## Adicionar ou alterar uma regra padrão

Plugins são registrados em `PLUGINS_LIST` e regras são habilitadas em `RULES_LIST`. Ao integrar uma nova regra:

1. confirme a exportação do plugin e a compatibilidade peer dele;
2. registre o plugin com namespace consistente;
3. escolha nível padrão coerente com `meta.type` e impacto para projetos existentes;
4. documente a regra, nível, opções e limitações em `docs/references/rules.md`;
5. atualize README, se a API ou uso público mudou.

## Documentação e commits

Atualize documentação detalhada na mesma alteração que modifica código, dependências, scripts ou workflows. Registre páginas novas em `docs/README.md`. O commitlint estende a configuração convencional do commitlint; use Conventional Commits.

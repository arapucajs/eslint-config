# Orientações para Claude e agentes de IA

As instruções canônicas estão em [AGENTS.md](./AGENTS.md). Comece pelo [índice da documentação](./docs/README.md) e leia as páginas relevantes antes de editar arquivos.

Este repositório publica uma configuração flat de ESLint em ESM. As fábricas `configPkg` e `configApp` e as constantes públicas estão em `index.js`. A configuração instala e ativa plugins, incluindo cinco regras de `@arapucajs/eslint-plugin`; não é um CLI nem um preset oculto carregado automaticamente. Confirme todos os níveis e comportamentos em `index.js` e nas referências do plugin.

## Documentação obrigatória

Crie ou atualize documentação detalhada na mesma tarefa sempre que modificar qualquer parte do projeto: código, configuração, dependências, lockfile, scripts, CI, exemplos, README ou documentação.

- Registre cada página de `docs/` em `docs/README.md`.
- Explique o uso real, inputs, outputs, defaults, limites e manutenção para humanos e IAs.
- Atualize o README quando o contrato público mudar.
- Não transforme scripts placeholder em garantias de teste, lint, typecheck ou build.
- Confira `index.js`, `package.json`, `package-lock.json`, workflows e as regras atuais do plugin.

Preserve mudanças locais existentes e use Conventional Commits.

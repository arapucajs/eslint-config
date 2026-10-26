# Instruções para agentes — @arapucajs/eslint-config

Leia este arquivo e [docs/README.md](docs/README.md) antes de alterar o repositório. O código, `package.json`, `package-lock.json`, workflows e documentação são fontes de verdade. Confirme afirmações no estado atual desses arquivos; atualize a documentação na mesma alteração quando houver divergência.

## Escopo real

Este repositório publica `@arapucajs/eslint-config`, uma configuração ESLint flat em ESM. `index.js` exporta duas fábricas (`configPkg` e `configApp`) e constantes reutilizáveis. As fábricas compõem `tseslint.configs.base`, os plugins declarados e `RULES_LIST`, acrescentando blocos customizados recebidos como argumentos.

O preset registra `@arapucajs/eslint-plugin` e habilita cinco regras ArapucaJS. Não é um CLI e não executa lint por conta própria. Confira [docs/architecture.md](docs/architecture.md) e as referências antes de alterar contrato ou níveis de regra.

## Documentação obrigatória

É obrigatório criar ou atualizar documentação detalhada na mesma tarefa sempre que qualquer parte do projeto for criada ou modificada, incluindo configuração exportada, dependências, scripts, lockfiles, CI, README e estas instruções.

- Coloque a documentação em `docs/` e registre todas as páginas em `docs/README.md`.
- Explique comportamento, entradas, saídas, compatibilidade, limites e manutenção para humanos e agentes de IA.
- Atualize o README se instalação, exports, dependências, níveis padrão ou exemplos mudarem.
- Mantenha guias, referências, arquitetura e planejamento proporcionais ao projeto. Não documente placeholders como funcionalidades implementadas.
- Verifique exemplos contra `index.js`, `package.json`, lockfile, regras de `@arapucajs/eslint-plugin` e workflows disponíveis.

## Antes de alterar

1. Leia o índice e as páginas relevantes em `docs/`.
2. Inspecione `index.js` e a dependência atual do plugin antes de descrever regras ou mudar sua ativação.
3. Confira versões, peer dependencies, scripts e arquivos publicados no `package.json` e `package-lock.json`.
4. Confira os workflows antes de afirmar o comportamento de CI, release ou deploy.
5. Preserve mudanças locais existentes e nunca substitua alterações do usuário sem necessidade.
6. Ao mudar dependências, mantenha o lockfile npm coerente com o manifesto.

## Verificações e convenções

Os scripts `lint`, `test`, `typecheck` e `build` atualmente são placeholders no `package.json`; não os descreva como verificações reais. `format` chama Prettier. Escolha verificações concretas para a mudança e reporte o que foi executado. Use Conventional Commits conforme `commitlint.config.js`.

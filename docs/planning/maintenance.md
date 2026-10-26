# Manutenção

Esta página define verificações contínuas e pontos de atenção. Não é uma lista de funcionalidades prometidas.

## Checklist para mudanças

- Compare configuração e API com `index.js` e `package.json`.
- Atualize o lockfile quando alterar dependências.
- Ao adicionar plugin ou regra, confirme peer compatibility, registre em `PLUGINS_LIST`, habilite em `RULES_LIST` e documente seu nível.
- Atualize o README se o uso público, peer requirements, exports ou defaults mudarem.
- Atualize as referências e registre novas páginas em `docs/README.md`.
- Não reporte scripts placeholder como verificações aprovadas.
- Reveja os workflows locais e a implementação compartilhada antes de mudar CI.

## Pontos de atenção

- `INCLUDE_LIST` abrange `.ts` e `.js`, mas não `.tsx` ou `.jsx` por padrão.
- `APP_IGNORE_LIST` é anexada ao bloco que aplica as regras do preset de aplicação; seu efeito deve ser descrito em relação à estrutura flat config do ESLint.
- O plugin ArapucaJS usa a peer range ESLint 10; mudanças de compatibilidade do plugin devem ser refletidas neste pacote.
- Os scripts placeholder mascaram ausência de testes e builds locais. Ao implementar verificações reais, atualizar o README, guia de desenvolvimento e CI sem declarar resultados além dos executados.

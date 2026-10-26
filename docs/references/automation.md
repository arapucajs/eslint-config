# CI, release e publicação

## Pull requests

`.github/workflows/checks.yml` é acionado em pull requests para `main` e chama os workflows reutilizáveis de `arapucajs/.github` na ordem typecheck, lint e test. A implementação dos workflows reutilizáveis não está neste repositório. Os scripts locais `typecheck`, `lint` e `test` continuam placeholders, portanto não são equivalentes à execução confirmada desses jobs.

`.github/workflows/ci.yml` é acionado em push para `main` e valida a mensagem de commit com Commitlint. Embora o arquivo também contenha uma etapa condicional para commits de pull request, o gatilho declarado deste workflow é `push`; a validação de PR descrita pelo pipeline principal está em `checks.yml`.

## Release e deploy

`.github/workflows/release.yml` roda após a conclusão do workflow `CI` na branch `main`. Ele chama Release Please; quando uma release é criada, instala as dependências, empacota o pacote e anexa o artefato à release.

`.github/workflows/deploy.yml` é acionado quando uma release é publicada. O job publica primeiro no GitHub Packages após `npm ci` e `npm run build`; em seguida, outro job instala as dependências e publica no npm com provenance. Os jobs usam Node `20.x`. A publicação usa secrets do GitHub Actions; não registre seus valores.

`.github/workflows/labels.yml` sincroniza labels sob acionamento manual (`workflow_dispatch`), e `stale.yml` roda diariamente para tratar issues e pull requests sem atividade.

## Atualizar esta referência

Ao alterar os workflows, registre os eventos, dependências entre jobs, versões Node explicitamente configuradas, comandos locais chamados e destinos de publicação. Separe o que está definido aqui da lógica de workflows reutilizáveis remotos.

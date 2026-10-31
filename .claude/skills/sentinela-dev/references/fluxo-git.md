# Fluxo de branch, commit e PR

Regra de não commitar na `main`: SKILL.md (Regras inegociáveis). Barreira antes de push/PR: SKILL.md (Antes de qualquer saída).

## Passo a passo
1. `git switch main && git pull`
2. `git switch -c <tipo>/<area>-<assunto>` (ex.: `feat/api-eventos`, `fix/visao-agachar`).
3. Trabalhe só nos arquivos da tarefa.
4. Antes de commitar: `guarda-sensivel`; confira `git status` por arquivos que não devem entrar (imagens, vídeos, `.env`, `runs/`).
5. Commit pequeno, mensagem no imperativo em português. Só quando a pessoa pedir.
6. Push da branch (nunca da `main`) e abra PR descrevendo objetivo, critério de pronto e o que foi verificado e não verificado.
7. Outra pessoa revisa. Rode `code-review` e `simplify` no PR.
8. Merge só após aprovação e CI verde.

## Conteúdo do PR
Objetivo; arquivos/pastas; como testar; marco servido; privacidade (imagens/segredos) e resultado da `guarda-sensivel`, dizendo que ela não entende imagens nem lê binários.

## Dependências
Fixe versões (`requirements.txt`, `package-lock.json`). Mudança de modelo ou arquitetura exige pedido explícito (SKILL.md, Decisões fixas).

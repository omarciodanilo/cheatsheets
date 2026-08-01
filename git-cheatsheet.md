# Git Cheat Sheet

---

## Configuração inicial
- `git init` - Cria um novo repositório local.
- `git clone <url>` - Baixa um repositório do servidor.
- `git config --global user.name "Seu Nome"` - Define seu nome para os commits.
- `git config --global user.email "seu@email.com"` - Define seu e-mail para os commits.
- `git remote add <nome> <url>` - Conecta seu repositório local a um servidor remoto.
- `git remote -v` - Lista os servidores remotos configurados ("v" de verbose).

## Ciclo de trabalho
- `git status` - Exibe estado atual, mostrando arquivos modificados e prontos para commit.
- `git add <arquivo>` - Adiciona um arquivo específico ao staging.
- `git add .` - Adiciona todas as mudanças ao staging.
- `git diff --cached` - Revisa o que será commitado.
- `git commit -m "Mensagem clara"` - Grava alterações com descrição.
- `git add -p` - Abre o modo interativo para revisar e selecionar blocos de código (hunks) antes do commit. Principais opções:
  - `y` (yes) - Aceita o bloco atual no stage.
  - `n` (no) - Pula o bloco atual e o mantém apenas localmente.
  - `s` (split) - Divide o bloco em partes menores para maior precisão.
  - `q` (quit) - Finaliza a sessão salvando apenas o que já foi aceito.

## Gerenciamento de branches
- `git branch` - Lista branches locais.
- `git checkout -b <nome>` - Cria e muda para uma nova branch.
- `git checkout <nome>` - Alterna entre branches existentes.
- `git merge <nome>` - Une a branch escolhida à atual.
- `git branch -m <novo-nome>` - Renomeia a branch atual.
- `git remote set-head origin --auto` - Atualiza o espelhamento da branch principal (útil se o padrão mudou de master para main no servidor).

## Limpeza e sincronização
- `git fetch --all --prune` - Atualiza dados e remove referências de branches deletadas no servidor.
- `git branch -r` - Lista branches remotas.
- `git branch -r --merged master` - Lista branches remotas que já foram mescladas (seguro deletar).
- `git push origin --delete <nome>` - Deleta branch no servidor.
- `git branch -d <nome>` - Exclui uma branch local que já foi mergeada.
- `git branch -D <nome>` - Força a exclusão de uma branch local (mesmo sem merge).

## Inspeção e diferenças
- `git log --oneline` - Histórico resumido de commits.
- `git log --oneline --graph --all` - Histórico completo e visual dos commits e branches.
- `git log master..branch --oneline` - Commits exclusivos de uma branch.
- `git diff master..branch` - Compara alterações de código entre branches.
- `git diff master..branch --stat` - Resumo de arquivos alterados e volume de mudanças.

## Emergência e Recuperação
- `git checkout -- <arquivo>` - Descarta alterações locais de um arquivo.
- `git reset --hard HEAD` - Descarta todas as alterações não commitadas (USAR COM CUIDADO).
- `git commit --amend` - Adiciona arquivos esquecidos ao último commit ou altera sua mensagem.
- `git revert <hash>` - Cria um novo commit que desfaz as alterações de um commit anterior (forma segura para commits já enviados).
- `git reflog` - Histórico de movimentos do HEAD (AJUDA BASTANTE).
- `git checkout -b <nome> <hash>` - Recria uma branch a partir de um ponto do reflog.

## Resolução de conflitos
- `git merge --abort` - Aborta um merge com falha e restaura o estado anterior.
- `git status` - Durante conflitos, lista os arquivos que precisam de correção manual.
- `git status -s | grep ^UU` - Visão ainda mais limpa e direta dos arquivos que restam para corrigir.
- **Dica:** Procure pelos marcadores `<<<<<<<`, `=======`, `>>>>>>>` nos arquivos conflituosos.

## Remoto (push e pull)
- `git pull origin <branch>` - Traz novidades e mescla no seu código.
- `git pull --rebase origin <branch>` - Integra mudanças de forma linear, sem commits de merge inúteis.
- `git push origin <branch>` - Envia seus commits locais para o servidor.
- `git remote rename <antigo> <novo>` - Altera o nome de exibição do remoto (ex: de origin para upstream).
- `git remote remove <nome>` - Remove a conexão com um servidor remoto específico.
- `git remote set-url origin <nova-url>` - Altera URL da origin (ex. de link HTTPS para link SSH)

---

## Padrões de nomenclatura de branches
Usar prefixos para categorizar o trabalho e facilitar a automação:

- `chore/nome-da-tarefa` — Tarefas não relacionadas a código ou documentação.
- `docs/nome-do-arquivo` — Alterações apenas em documentação.
- `feat/nome-da-feature` — Novas funcionalidades.
- `fix/descrição-do-bug` — Correções de bugs.
- `hotfix/ajuste-urgente` — Correções críticas em produção.
- `perf/descrição-da-melhoria` — Alterações focadas exclusivamente em otimização de desempenho.
- `refactor/o-que-mudou` — Melhorias no código sem alterar comportamento, mas melhora a estrutura ou legibilidade.
- `release/versão` — Branches usadas para preparar uma nova versão de lançamento em produção (ex: release/v1.2.0).
- `support/versão` ou `patch/descrição` — Manutenção de versões antigas do software que continuam ativas.
- `test/nome-do-teste` — Criação ou ajuste de testes.

**Dica:** usar letras minúsculas, separar palavras com hífen (`-`) e evitar nomes genéricos como `ajustes` ou `testes`.

---

## Padrões de descrição de commits
Usar tipo de alteração e descrição da alteração:

### Modelo
```
<tipo>(<escopo opcional>): <descrição curta no imperativo ou infinitivo>

[corpo opcional detalhando o "o quê" e o "porquê"]

[rodapé opcional para breaking changes ou issues relacionadas]
```

### Exemplo:

```
feat(auth): adiciona autenticação via token JWT

Implementa o fluxo de login gerando um token JWT com validade de 24 horas
para proteger as rotas da API e garantir que apenas usuários autenticados
consigam acessar os recursos.`

Closes #42
```

### Tipos
- `build` (Build): alterações que afetam o sistema de build ou dependências externas (ex: npm, pip, Docker, Maven).
- `chore` (Chore): tarefas não relacionadas a código ou documentação.
- `ci` (Continuous Integration): mudanças nos arquivos de configuração de CI/CD.
- `docs` (Documentation): alterações apenas em documentação.
- `feat` (Feature): novas funcionalidade.
- `fix` (Bugfix): correções de bugs.
- `perf` (Performance): alterações focadas exclusivamente em otimização de desempenho.
- `refactor` (Refactoring): melhorias no código sem alterar comportamento, mas melhora a estrutura ou legibilidade.
- `revert` (Revert): reversão de um commit anterior.
- `style` (Styles): mudanças que não afetam a lógica do código (espaçamento, formatação, ponto e vírgula, etc.)
- `test` (Test): adição ou correção de testes automatizados.

---

## Boas práticas gerais

### 1. Organização do histórico
- **Commits atômicos:** fazer commits pequenos e focados. Cada commit deve resolver uma única tarefa ou funcionalidade.
- **Mensagens descritivas:** usar o modo imperativo (ex: "Adiciona login", "Corrige bug", "Refatora menu").

### 2. Fluxo de trabalho
- **Nunca trabalhar na Master/Main:** sempre criar uma branch separada para funcionalidades (`feat/nome-da-func`) ou correções (`fix/nome-do-bug`).
- **Sincronia constante:** antes de dar `push`, sempre fazer um `pull` para integrar mudanças recentes e resolver conflitos o quanto antes.

### 3. Higiene do repositório
- **Use o .gitignore:** Adicionar o `.gitignore` logo no início para evitar subir logs, pastas de dependências (como `node_modules` ou `venv`) ou arquivos do sistema operacional.
- **Prune automático:** configurar `git config --global fetch.prune true` para seu Git sempre "podar" branches remotas mortas.
- **Limpeza periódica:** deletar branches locais e remotas assim que o trabalho for mesclado (merge).

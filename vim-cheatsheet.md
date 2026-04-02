# Vim Cheat Sheet

---

## Geral

- `ESC` - Retorna ao Modo Comando.
- `.` - Repete o último comando de edição.

## Navegação

- `h` - Movimenta o cursor para a esquerda.
- `j` - Movimenta o cursor para baixo.
- `k` - Movimenta o cursor para cima.
- `l` - Movimenta o cursor para a direita.
- `w` - Movimenta o cursor para a palavra seguinte.
- `b` - Movimenta o cursor para a palavra anterior.
- `Ctrl + w + seta direcional` ou `Ctrl + w + h, j, k, l` - Alterna entre janelas.

## Modo de Inserção

- `i` - Insere texto na posição do cursor.
- `I` - Insere texto no início da linha.
- `o` - Insere texto na linha abaixo.
- `O` - Insere texto na linha acima.
- `a` - Insere texto um caractere à frente.
- `A` - Insere texto no final da linha.

## Salvar e sair
- `:w` - Salva o arquivo.
- `:q` - Sai do arquivo, que precisa estar salvo.
- `:qa` - Sai de todos os arquivos abertos, que precisam estar salvos.
- `:q!` - Sai do arquivo de forma forçada (se não foi salvo, progresso é perdido).
- `:wq` - Salva o arquivo e sai.
- `:x` - Salva o arquivo e sai.
- `ZZ` - Salva o arquivo e sai.
- `ZQ` - Sai do arquivo sem salvar.

## Copiar,  colar e recortar
- `yy` - Copia a linha inteira.
- `yw` - Copia uma palavra.
- `y$` - Copia do cursor até o final da linha.
- `y^` - Copia do cursor até o início da linha.
- `p` - Cola o conteúdo na linha abaixo.
- `P` - Cola o conteúdo na linha acima.
- `yNy` - Copia `N` linhas inteiras.
- `dd` - Apaga/recorta a linha inteira.
- `dNd` - Apaga/recorta `N` linhas inteiras.
- `dw` - Apaga uma palavra.
- `dG` - Apaga da posição atual até o final do arquivo.
- `dgg` - Apaga da posição atual até o início do arquivo.
- `cw` - Apaga/recorta uma palavra e entra no Modo de Inserção.
- `x` - Apaga o caractere atual (igual ao Delete).
- `X` - Apaga o caractere antes do cursor (igual ao backspace).
- `rN` - Substitui o caractere atual pelo `N`.

## Modo Visual
- `v` (visual) - Seleciona um pedaço do texto.
- `V` (visual line) - Seleciona linhas do texto.
- `Ctrl + v` (visual block) - Seleciona um bloco de texto.

## Desfazer e refazer
- `u` - Defaz ação.
- `Ctrl + r` - Refaz ação.
- `g+` - Refaz todas as ações até o estado mais novo do arquivo.

## Localizar
- `/palavra` - Busca a palavra de modo descendente.
- `?palavra` - Busca a palavra de modo ascendente.
- `n` - Continua com a busca.
- `N` - Continua com a busca no sentido inverso.
- `gg` - Move o cursor para o início da primeira linha.
- `G` - Move o cursor para o início da última linha.
- `M` - Move o cursor para o início da linha no meio da tela.
- `H` - Move o cursor para o início da linha no alto da tela.
- `L` - Move o cursor para o início da linha no fim da tela.

## Substituir
- `:40s/palavra-antiga/palavra-nova/` - Substitui na linha 40 a `palavra-antiga` pela `palavra-nova`.
- `:40,50s/palavra-antiga/palavra-nova/` - Substitui entre as linhas 40 e 50 a `palavra-antiga` pela `palavra-nova`.
- `:%s/palavra-antiga/palavra-nova/` - Substitui a `palavra-antiga` pela `palavra-nova` em todo o arquivo,  uma palavra por linha.
- `:%s/palavra-antiga/palavra-nova/g` - Substitui a `palavra-antiga` pela `palavra-nova` em todo o arquivo.

## Comandos `set` para configuração

- `:set hlsearch` - Habilita destaque para os resultados das buscas.
- `:set nohlsearch` - Desabilita destaque para os resultados das buscas.
- `:set number` ou `:set nu` - Exibe numeração de linhas.
- `:set nonumber` ou `:set nonu` - Retira numeração de linhas.
- `:set tabstop=N` - Configura tamanho do TAB para `N` espaços.
- `:set tabstop?` - Exibe configuração atual do tabstop.
- `:set expandtab` - Converte o TAB em espaços.
- `:set bg=light` ou `:set bg=dark` - Ajusta o esquema de cor dos destaques, de acordo com a cor do plano de fundo do Terminal (claro ou escuro).

## Outros comandos
- `:e ARQUIVO` - Abre outro arquivo chamado `ARQUIVO`.
- `:r ARQUIVO` - Copia o conteúdo do arquivo `ARQUIVO` para o arquivo atual.
- `:split ARQUIVO` - Divide a tela horizontalmente com o arquivo `ARQUIVO`.
- `:vsplit ARQUIVO` - Divide a tela verticalmente com o arquivo `ARQUIVO`.
- `:! COMANDO` - Executa o comando `COMANDO` no Shell e retorna para o Vim.
- `!! COMANDO` - Executa o comando `COMANDO` em segundo plano e cola sua saída dentro do arquivo.

---
title: Como mudar para o cwd do Netrw ao sair do Vim?
description: Descrevemos como é possível mudar o terminal para o current working directory do Netrw ao sair do vim
tags: 'vim, cwd, netrw, bash'
cover_image: 'https://i.imgur.com/NW2Sn5z.png'
canonical_url: null
published: true
series: vim
id: 1607706
date: '2023-09-21T22:42:12Z'
---

# Introdução

Eu gosto de estruturas minimalistas, e esse é um dos motivos pelos quais eu utilizo `Vim` como meu editor de texto. Desde a versão 5.5, o `Vim` vem de fábrica com um plugin que permite navegar no terminal através de arquivos e pastas de maneira visual e sem precisar ficar dando `cd` e `ls` toda hora. Trata-se do [Netrw](https://github.com/vim-scripts/netrw.vim).
 
Muita gente não o utiliza, sendo o [Nerdtree](https://github.com/preservim/nerdtree) seu principal substituto. Uma das desvantagens do `Netrw` é que, para que funcione de maneira aceitável, um punhado de configurações são necessárias. No entanto, seguindo a filosofia do minimalismo, não vejo nisso argumento forte o suficiente para instalar um plugin a mais.

Em momento oportuno farei uma publicação sobre minhas configurações para o `Netrw`. Hoje, no entanto, gostaria de trazer a solução de um problema que me \ ,incomodava há algum tempo.

# O Problema

Suponhamos que você abriu seu `Netrw` e começou a navegar por diretórios *dentro do `Vim`*. Rapidamente você sai de um diretório `A` e chega em um diretório distante `B`. Suponhamos, agora, que você quer executar algum comando de `Bash` (digamos `cmd_Bash`) estando no diretório `B`. Utilizando  apenas de um  ferramental builtin, tem-se algumas opções:

1. executar `:shell` no `Vim` para abrir um prompt, o qual iniciará no diretório `B`;
2. executar `:! cd path/to/B | cmd_Bash` no `Vim`.

Suponha, ainda, que você já não mais precisa do `Vim` e quer fazer coisas no terminal no entorno do diretório `B`. Nesse caso, você sairá do `Vim`. Seria muito interessante se o seu working directory do terminal estivesse sincronizado com o working directory do `Netrw`. Pois, assim, ao fechar o `Netrw` no diretório `B` seu terminal estaria já posicionado ali.

O problema é que, no entanto, tal sincronização não existe: *alterações em buffers do `Vim` só se aplicam ao `Vim`*.

# A Solução Errada

A estratégia imediata de solução ao problema seria a seguinte:

1. definir uma variável `vim_cwd` interna ao `Vim` que contém o working directory do `Netrw`;
2. atualizar tal variável quando o buffer do `Netrw` é fechado;
3. associar `vim_cwd` uma variável `bash_cwd` em `Bash`;
4. configurar o `Vim` para que, ao ser fechado, seja executado o comando `cd $bash_cwd`.

As etapas 1. e 2. são tranquilas, como segue.

## Etapa 1

No `Netrw` o símbolo `%` representa o arquivo em uso, `p` representa "tomar o full path de", ao passo que `h` representa "pegar o diretório de". Assim, pode-se obter o diretório de um arquivo aberto através de `expand('%:p:h')`. Em um buffer do `Netrw` isso se refere exatamente ao working directory. Para salvá-lo em uma variável global `vim_cwd`,  basta um 

```vim
let g:vim_cwd = expand('%:p:h').
```

## Etapa 2

No `Vim` pode-se executar comandos internos ao se fechar um buffer adicionando-os como 

```vim
autocmd BufDelete * your_command
```

Para se restringir a um dado buffer, concatena-se com um `if &ft ==# 'your_buffer' `. No nosso caso, o buffer é `netrw`, de modo que ficamos com

```vim
autocmd BufDelete * if &ft ==# 'netrw' | your_command | endif
```
Aplicando à situação particular da etapa anterior, temos:

```vim
autocmd BufDelete * if &ft ==# 'netrw' | let g:vim_cwd = expand('%:p:h') | endif
```

## Etapa 4

Assim como existe uma maneira de executar comandos internos ao `Vim` quando buffers são fechados, pode-se executá-los quando o próprio `Vim` é fechado. A sintaxe é a seguinte:

```vim
autocmd VimLeave * your_command
```

Por outro lado, pode-se executar comandos de `Bash` como comandos de `Vim` através de `execute '!your_bash_command'`. Portanto, o seguinte código executa um comando em `Bash` ao se fechar o `Vim`:

```vim
autocmd VimLeave * execute '!your_bash_command'
```

## Etapa 3

É no ato de transformar uma variável interna ao `Vim` em uma variável de `Bash` (etapa 3) que a estratégia anterior falha. Até onde vai meu conhecimento, não existe uma maneira de se fazer isso diretamente dentro do `Vim` sem se recorrer a um script de `Bash`. 

# A solução Correta

Como contornar a situação? Ao invés de transformar diretamente uma variável `vim_cwd` do `Vim` em uma variável `bash_cwd` do `Bash`, podemos fazer isso em passos:

1. escrever o valor da variável `vim_cwd` em um arquivo;
2. ler tal arquivo em uma variável de `Bash`.

Isso sim funciona, pois o `Vim` admite uma função chamada `writefile()` que permite exatamente a escrita de uma variável em um arquivo. Em nosso caso, temos:

```vim
writefile([g:vim_cwd], '/tmp/some_file').
```

Por sua vez, poderíamos obter `bash_cwd` através de

```bash
bash_cwd=$(cat /tmp/some_file)
```

Juntando tudo, a solução ao nosso problema seria, então, dada pelo seguinte código:

```vim
autocmd BufDelete * if &ft ==# 'netrw' | let g:vim_cwd = expand('%:p:h') | call writefile([g:vim_cwd], '/tmp/some_file') | endif
autocmd VimLeave * execute '!bash_cwd=$(cat /tmp/some_file) | cd $bash_cwd'
```

Temos, no entanto, mais um problema: 

* *o operador de substituição `$()` não funciona muito bem ao ser executado como um comando dentro do `Vim`!*

A alternativa é pedir que o comando `cd $(cat /tmp/some_file)` seja executado não dentro do `Vim`, mas diretamente em `Bash`. Isso pode ser feito redefinindo o comando `vim` substituindo-o por uma função `vim()`:

```bash
function vim(){
    command vim "$@"
    if [[ -f /tmp/some_file  ]]; then
        bash_cwd=$(cat /tmp/some_file)
        cd $bash_cwd
        rm /tmp/some_file
    else
        return
    fi
}
```

# Conclusão

Se você quer que ao fechar o `Vim` seu terminal esteja no último diretório acessado pelo `Netrw`, faça o seguinte:

* em seu `.vim/vimrc` adicione

```vim
autocmd BufDelete * if &ft ==# 'netrw' | let g:vim_cwd = expand('%:p:h') | call writefile([g:vim_cwd], '/tmp/some_file') | endif
```

* em seu `.bashrc` adicione

```bash
function vim(){
    command vim "$@"
    if [[ -f /tmp/some_file  ]]; then
        bash_cwd=$(cat /tmp/some_file)
        cd $bash_cwd
        rm /tmp/some_file
    else
        return
    fi
}
```
# Fim

Até mais,

Yuri.

* [yxm.me](https://yxm.me)
* [github.com/yxm-dev](https://github.com/yxm.dev)
* [codeberg.com/yxm](https://codeberg.com/yxm)

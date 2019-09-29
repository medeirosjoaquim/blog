---
title: Migrando para neovim
date: 2017-08-18
---

## Migrando para neovim - pós instalação

Bom, ninguém quer perder aquelas 800 linhas de .vimrc ;
então, a primeira coisa é editar o $HOME/.config/nvim/init.vim
para que o neovim utilize o antigo .vimrc

```
set runtimepath^=~/.vim runtimepath+=~/.vim/after
    let &packpath = &runtimepath
    source ~/.vimrc


    if !has(`nvim`)
        set ttymouse=xterm2
    endif
```

Como decidi migrar de vez, criei

```
alias vi="nvim"
alias vim="nvim"
```


---
title: build tmux from source
date: 2017-07-23
---

### Compilando TMUX e dependências- sem root

Como compilar TMUX -- SEM ROOT.
Às vezes precisamos trabalhar naquele servidor via SSH com um usuário sem "poderes" de root (como em uma hospedagem compartilhada por exemplo). Para deixar o
trabalho mais dinâmico, além dos dotfiles de praxe, TMUX é uma ferramenta
essêncial e aqui vai minha receita para compilar sem precisar ser root:

### FERRAMENTAS NECESSÁRIAS:

Além do código do próprio tmux, precisaremos da biblioteca
**libevent** (faça download da versão desejada em https://github.com/libevent/libevent/releases/  -- dê preferência
a um release stable).
O TMUX depende, também, da biblioteca **ncurses** (baixe em ftp://ftp.gnu.org/gnu/ncurses/).
E, claro, o próprio TMUX (https://github.com/tmux/tmux).

Faça uma tarball ou compacte esses arquivos de uma maneira que facilite a
transmissão por ssh (com scp) ou ftp.

#### Prepare uma pasta para receber as bibliotecas
Eu costumo criar na minha pasta $HOME uma pasta __local__ para instalar todas as
aplicações compiladas da fonte sem precisar de root. É uma boa prática que
usarei aqui.

### Começando:

Agora, com os arquivos descompactados já em nosso servidor SSH, cada qual em seu
diretório, faremos:

* Compilação da __libevent__

```
./configure --prefix=$HOME/local --disable-shared
make
make install
```
* Compilação da __ncurses__

```
./configure --prefix=$HOME/local
make
make install
```
* Compilação do __tmux__

```
./configure CFLAGS="-I$HOME/local/include -I$HOME/local/include/ncurses" LDFLAGS="-L$HOME/local/lib \
-L$HOME/local/include/ncurses -L$HOME/local/include" \
CPPFLAGS="-I$HOME/local/include -I$HOME/local/include/ncurses" \
LDFLAGS="-static -L$HOME/local/include -L$HOME/local/include/ncurses -L$HOME/local/lib"
```
** _Se tiver problemas para copiar/colar, aqui segue o comando sem cortes:_**

```
./configure CFLAGS="-I$HOME/local/include -I$HOME/local/include/ncurses" LDFLAGS="-L$HOME/local/lib -L$HOME/local/include/ncurses -L$HOME/local/include" CPPFLAGS="-I$HOME/local/include -I$HOME/local/include/ncurses" LDFLAGS="-static -L$HOME/local/include -L$HOME/local/include/ncurses -L$HOME/local/lib"
```

**Agora, basta um comando _make_   ; como não somos root não usaremos _make install_**

### Para finalizar:
#### Vamos colocar o caminho para o executável do TMUX em nosso PATH, permitindo que ele possa ser chamado de qualquer diretório:

* No seu .bashrc ou .bash_profile :

```
 PATH=$PATH:$HOME/bin:$HOME/tmuxsource/tmux-2.5
 export PATH
```
E é isso!

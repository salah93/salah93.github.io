---
layout: post
category : python
tagline:
tags : [python3.6, vim, python]
---
{% include JB/setup %}

Recently I started using [black](https://github.com/psf/black) for my code formatting. I set it up in vim with [ALE](https://github.com/dense-analysis/ale), but the only catch was that it required vim with python3.6 support.


# installing python3.6+
## Ubuntu
```bash
sudo add-apt-repository ppa:jonathonf/python-3.6
sudo apt-get update
sudo apt-get install python3.6
sudo ln -sf /usr/bin/python3.6 /usr/bin/python
sudo ln -sf /usr/bin/python3.6 /usr/bin/python3
sudo apt-get install python3.6-dev
sudo apt-get install python3-gdbm
```

# install vim dependencies/remove vim
refer to this helpful [guide](https://github.com/ycm-core/YouCompleteMe/wiki/Building-Vim-from-source) with regards to dependencies


# clone vim

```bash
cd ~
git clone https://github.com/vim/vim.git
cd vim/
```


# Run Configure script
## Fedora

set the appropriate config directory

```bash
CFLAGS=-fPIC ./configure \
    --with-features=huge \
    --enable-python3interp \
    --enable-multibyte \
    --enable-rubyinterp=yes \
    --with-python3-config-dir=/lib64/python3.7/config-3.7m-x86_64-linux-gnu/ \
    --enable-perlinterp=yes \
    --enable-luainterp=yes \
    --enable-gui=gtk2 \
    --enable-cscope \
    --prefix=/usr/local

```


## Ubuntu

```bash
./configure \
    --with-features=huge \
    --enable-multiby \
    --enable-rubyinterp=y \
    --enable-python3interp=y \
    --with-python3-config-dir=/usr/lib/python3.6/config-3.6m-x86_64-linux-g \
    --enable-perlinterp=y \
    --enable-luainterp=yes \
    --enable-gui=gtk2 \
    --enable-csco \
    --prefix=/usr/local
```

# run make
```bash
cd ~/vim
make VIMRUNTIMEDIR=/usr/local/share/vim/vim81
```

# install
## fedora
```bash
sudo make install
```

## ubuntu
```bash
sudo apt install checkinstall
cd ~/vim
sudo checkinstall
```


# install black
```bash
sudo python3.6 install black
```

# Fin
you should be good to go


here is part of my `.vimrc`
```vimscript
set nocompatible

" Install plugins with vundle
filetype off
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
Plugin 'gmarik/Vundle.vim'
Plugin 'w0rp/ale'
    let g:ale_lint_on_text_changed = 0
    let g:ale_lint_on_enter = 0
    let g:ale_lint_on_save = 1
    let g:ale_fix_on_save = 1
    let b:ale_fixers = {
    \ 'python': ['black'],
    \ }
    let g:ale_linters = {
    \ 'python':  ['flake8'],
    \ }
Plugin 'psf/black'
```

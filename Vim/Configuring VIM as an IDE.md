# Configuring VIM as IDE

```
pacman -S vim
```

Consider using [[ Neovim ]] though, as it support lua scripts and is easier to work with.

## Installing a plugin

To install any plugin, we must perform the following steps:

- Create `.vim/bundle` directory in user's home directory
- Copy plugin inside the directory
- Set runtime path in vim

```bash
mkdir -p ~/.vim/bundle
cd ~/.vim/bundle/
git clone https://github.com/sjl/badwolf.git 
echo "set runtimepath^ = ~/.vim/bundle/badwolf" > ~/.vimrc
```

Now plugin is installed, we can use badwolf color scheme as follows:

```
:colorscheme badwolf
```

## Using Vundle as a plugin manager

Install

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

Configure `.vimrc`

```
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
```



## Using Vim as IDE

We can configure VIM to use it as an IDE. 

### Syntax highlightimg

```
:syntax on
```

### Smart indentation

```
set autoident
set smartindent
set cident
```

### Bounce

If you are using a programming language which uses curly braces to combine multiple statements then the `%` key will be your friend. This key will jump between the start and the end of curly braces quickly.

### Execute shell commands

To execute single command from Vim editor user

```
:!<command>
:!pwd
```

If you want to execute muiltiple commands:

```
:shell
```


## Sources

- [https://www.tutorialspoint.com/vim/vim_plug_ins.htm](https://www.tutorialspoint.com/vim/vim_plug_ins.htm)
- [https://www.tutorialspoint.com/vim/vim_using_vim_as_ide.htm](https://www.tutorialspoint.com/vim/vim_using_vim_as_ide.htm)
- [https://github.com/VundleVim/Vundle.vim](https://github.com/VundleVim/Vundle.vim)
- [https://coderoncode.com/tools/2017/04/16/vim-the-perfect-ide.html](https://coderoncode.com/tools/2017/04/16/vim-the-perfect-ide.html)
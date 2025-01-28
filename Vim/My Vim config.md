# Vim Tutor
+ **h:** Left
+ **j:** Down
+ **k:** Up
+ **l:** Right
+ **w:** Jumps to the begin of the next word
+ **e:** Jumps to the end of the next word
+ **b:** Jumps to the begin of the previous word

# Configuration
| Description           | Neovim                                                | VSCode                           | JetBrains                           |
| --------------------- | ----------------------------------------------------- | -------------------------------- | ----------------------------------- |
| Config file           | ~/AppData/Local/nvim/init.lua                         | settings.json, keybindings.json  | ~/.ideavimrc                        |
| Enter Config file     | leader + cc                                           | Ctrl + Shift + P                 | leader + cc                         |
| Relative number       | vim.opt.relativenumber = true                         | "editor.lineNumbers": "relative" | set relativenumber                  |
| Leader key            | vim.g.mapleader = ' '                                 | space                            | let mapleader = ' '                 |
| System clipboard      | vim.opt.clipboard = 'unnamedplus'                     | "vim.useSystemClipboard": true   | set clipboard^=unnamed, unnamedplus |
| ignorecase            | vim.opt.ignorecase = true<br>                         |                                  | set ignorecase<br>                  |
| smartcase             | vim.opt.smartcase = true                              |                                  | set smartcase                       |
| incsearch             | default                                               | "vim.incsearch": true,           | set incsearch                       |
| Remove hlsearch       | vim.keymap.set('n', '\<Esc>', ':nohlsearch\<cr>')<br> |                                  | noremap \<Esc> :nohlsearch\<cr><br> |
| Add <:> to matchpairs | vim.opt.matchpairs:append("<:>")                      | No supported by vim-extension    | set matchpairs+=<:><br>             |
| Showmatch             | vim.opt.showmatch = true                              | Default                          | set showmatch                       |
|                       |                                                       |                                  |                                     |


# My Keybinds
## Motion
- j = Left
- k = Down
- l = Up
- ; = Right
- U = Redo
- p = paste without overwritting in visual mode
- \ = Move to the next characted occured using f, t, F, T
- | = Move to the previous character occured using f, t, F, T
- % = Move between pair of brackets [:], {:}, (:), <:>
- J = Smart line join




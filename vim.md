# basic

## feature

## file search:

fzf

## split window

command: sp vs

moving cursor to other windows:

  up: CTRL-W k (CTRL k)

  (when CTRL k not work, try CTRL-W k)

  down: CTRL-W j (CTRL j)

  ...

## call lua

check:

vim --version | grep lua

https://vi.stackexchange.com/questions/13017/how-to-use-lua-in-vim

https://dev.to/2nit/how-to-write-neovim-plugins-in-lua-5cca

## get current file path

https://vi.stackexchange.com/questions/104/how-can-i-see-the-full-path-of-the-current-file

echo expand('%p')

## document in other language

https://mounui.com/244.html

set helplang=cn

## copy paste cut with system clipboard

## terminal

version>=8.1

:term

tab not work

iterm2 shortcut not work

https://stackoverflow.com/questions/1236563/how-do-i-run-a-terminal-inside-of-vim

## mouse

set mouse=a

"a" for GUI, MS-DOS and Win32

## vim help document jump

CTRL-] : goto

CTRL-T CTRL-O g<RightMouse> <C-RightMouse> : back

## show command map

https://stackoverflow.com/questions/7642746/is-there-any-way-to-view-the-currently-mapped-keys-in-vim

https://dev.to/iggredible/basic-vim-mapping-5ahj

https://vi.stackexchange.com/questions/7722/how-to-debug-a-mapping

https://stackoverflow.com/questions/24842063/how-to-search-in-the-vim-mapping-listing

## browser web

https://github.com/browsh-org/browsh

Firefox binary not found: /Applications/Firefox.app/Contents/MacOS/firefox

/Applications/Firefox\ Nightly.app/Contents/MacOS/firefox

./browsh --firefox.path "/Applications/Firefox Nightly.app/Contents/MacOS/firefox"

./browsh --firefox.path /Applications/Firefox\ Nightly.app/Contents/MacOS/firefox

## Plugins

https://github.com/mileszs/ack.vim

NERDTree

ale

### NERDTree

toggle: (map <Leader>) <Leader>nn

## Refs

https://vim.fandom.com/wiki/Example_vimrc

https://vim.fandom.com/wiki/Using_marks

https://vim.fandom.com/wiki/Mapping_keys_in_Vim_-_Tutorial_(Part_1)

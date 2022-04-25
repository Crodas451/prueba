set number
set mouse=a
syntax enable
set showcmd
set encoding=utf-8
set showmatch
set relativenumber
set sw=2
set clipboard=unnamedplus

call plug#begin('~/.vim/plugged')
"temas
Plug 'sainnhe/gruvbox-material'
"LSP
Plug 'neovim/nvim-lspconfig'
Plug 'nvim-lua/completion-nvim'
"pluginns js
Plug 'pangloss/vim-javascript'
Plug 'maxmellon/vim-jsx-pretty'

Plug 'mattn/emmet-vim'

Plug 'tpope/vim-commentary'

Plug 'Yggdroot/indentLine'

Plug 'vim-airline/vim-airline'

Plug 'scrooloose/nerdtree'

Plug 'ryanoasis/vim-devicons'
Plug 'neovim/nvim.net'
Plug 'OmniSharp/omnisharp-vim'
call plug#end()

"GRUVBOX CONFIGURACION DEL TEMA
set background=dark
let g:gruvbox_material_background='mediun'
colorschem gruvbox-material

lua <<EOF
require'lspconfig'.tsserver.setup{on_attach=require'completion'.on_attach}
require'lspconfig'.csharp_ls.setup{" csharp-ls "," cs " , AutomaticWorkspaceInit =  verdadero }
require'lspconfig'.please.setup{ "plz", "tool", "lps","bzl" }
EOF

"EMMET para las etiquetas html
let g:user_emmet_mode='n'
"autocompletar la etiqueta
let g:user_emmet_leader_key=','
let g:user_emmet_settings={
\ 'javascript':{
\ 'extends':'jsx'
\}
\}

" Use the stdio version of OmniSharp-roslyn - this is the default
 let g:OmniSharp_server_stdio = 1
"
" " Use the HTTP version of OmniSharp-roslyn:
 let g:OmniSharp_server_stdio = 0
command! -nargs=0 Prettier :CocCommand prettier.formatFile
nnoremap <C-D> :Prettier<CR>

"confi de comentarios
nnoremap <space>/ :Commentary<CR>
vnoremap <space>/ :Commentary<CR>

"conif airline
let g:airline#extensions#tabline#enabled = 1

"NERDTREE confi atajso de abrir y cerrar
let NERDTreeQuitOnOpen=1
nnoremap <silent> <F2> :NERDTreeFind<CR>
nnoremap <silent> <F3> :NERDTreeToggle<CR>

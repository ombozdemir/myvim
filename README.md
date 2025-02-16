call plug#begin('~/.vim/plugged')

Plug 'neoclide/coc.nvim', {'branch': 'release'}
Plug 'preservim/nerdtree'
Plug 'Xuyuanp/nerdtree-git-plugin'
Plug 'tpope/vim-fugitive'
Plug 'airblade/vim-gitgutter'
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
Plug 'tpope/vim-commentary'
Plug 'jiangmiao/auto-pairs'
Plug 'alvan/vim-closetag'
Plug 'ctrlpvim/ctrlp.vim'

Plug 'pangloss/vim-javascript'
Plug 'maxmellon/vim-jsx-pretty'
Plug 'leafgarland/typescript-vim'
Plug 'peitalin/vim-jsx-typescript'
Plug 'styled-components/vim-styled-components', { 'branch': 'main' }

Plug 'StanAngeloff/php.vim'
Plug 'phpactor/phpactor', {'for': 'php', 'do': 'composer install'}

Plug 'ap/vim-css-color'
Plug 'iamcco/coc-tailwindcss', {'do': 'npm install'}
Plug 'hail2u/vim-css3-syntax'

Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }
Plug 'junegunn/fzf.vim'

Plug 'dense-analysis/ale'
Plug 'puremourning/vimspector'

call plug#end()

set number
set relativenumber
syntax on
filetype plugin indent on
set expandtab
set tabstop=2
set shiftwidth=2
set softtabstop=2
set autoindent
set smartindent
set cursorline
set mouse=a
set ignorecase
set smartcase
set incsearch
set hlsearch
set undofile
set undodir=~/.vim/undodir
set autoread
set clipboard=unnamedplus

let g:coc_global_extensions = [
  \ 'coc-tsserver',
  \ 'coc-json',
  \ 'coc-eslint',
  \ 'coc-phpactor',
  \ 'coc-css',
  \ 'coc-tailwindcss',
  \ 'coc-highlight',
  \ 'coc-snippets',
  \ 'coc-pairs',
  \ ]

inoremap <expr> <Tab> pumvisible() ? "<C-n>" : "<Tab>"
inoremap <expr> <S-Tab> pumvisible() ? "<C-p>" : "<C-h>"
inoremap <expr> <CR> pumvisible() ? "<C-y>" : "<C-g>u<CR>"

nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gy <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)
nmap <silent> gr <Plug>(coc-references)

let g:ale_fixers = {
  \ 'javascript': ['eslint'],
  \ 'typescript': ['eslint'],
  \ 'php': ['php_cs_fixer'],
  \ 'css': [],
  \ }

let g:ale_linters = {
  \ 'javascript': ['eslint'],
  \ 'typescript': ['eslint'],
  \ 'php': ['php'],
  \ 'css': ['stylelint'],
  \ }

let g:ale_fix_on_save = 1
let g:ale_sign_error = '✘'
let g:ale_sign_warning = '⚠'

let g:vimspector_enable_mappings = 'HUMAN'
nmap <leader>dd :call vimspector#Launch()<CR>
nmap <leader>de :call vimspector#Reset()<CR>
nmap <leader>dc :call vimspector#Continue()<CR>
nmap <leader>dt :call vimspector#ToggleBreakpoint()<CR>
nmap <leader>dT :call vimspector#ClearBreakpoints()<CR>

nnoremap <C-n> :NERDTreeToggle<CR>

nnoremap <C-p> :Files<CR>
nnoremap <C-f> :Rg<CR>
nnoremap <C-b> :Buffers<CR>
nnoremap <C-g> :GFiles<CR>

nnoremap <leader>w :w<CR>
nnoremap <leader>q :q<CR>
set clipboard=unnamed


//////////////7


# Node.js ve npm
sudo apt install nodejs npm

# PHP ve Composer
sudo apt install php php-cli composer

# Prettier, ESLint, Tailwind CSS
npm install -g prettier eslint stylelint

# PHP-CS-Fixer (PHP formatlama)
composer global require friendsofphp/php-cs-fixer

# FZF (Fuzzy Finder)
sudo apt install fzf

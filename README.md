curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

////////////////////////

" Vim-plug ile eklentileri yükle
call plug#begin('~/.vim/plugged')

" Genel Geliştirme Araçları
Plug 'neoclide/coc.nvim', {'branch': 'release'} " Otomatik tamamlama ve LSP desteği
Plug 'preservim/nerdtree' " Dosya gezgini
Plug 'Xuyuanp/nerdtree-git-plugin' " NERDTree'de Git durumu
Plug 'tpope/vim-fugitive' " Git entegrasyonu
Plug 'airblade/vim-gitgutter' " Git değişikliklerini göster
Plug 'vim-airline/vim-airline' " Durum çubuğu
Plug 'vim-airline/vim-airline-themes' " Durum çubuğu temaları
Plug 'tpope/vim-commentary' " Kod yorumlama
Plug 'jiangmiao/auto-pairs' " Otomatik parantez kapatma
Plug 'alvan/vim-closetag' " HTML/JSX otomatik tag kapatma

" JavaScript/React/Next.js
Plug 'pangloss/vim-javascript' " JavaScript syntax
Plug 'maxmellon/vim-jsx-pretty' " JSX syntax
Plug 'leafgarland/typescript-vim' " TypeScript syntax
Plug 'peitalin/vim-jsx-typescript' " TSX syntax
Plug 'styled-components/vim-styled-components', { 'branch': 'main' } " Styled Components

" PHP
Plug 'StanAngeloff/php.vim' " PHP syntax
Plug 'phpactor/phpactor', {'for': 'php', 'do': 'composer install'} " PHP LSP desteği

" CSS/Tailwind/Bootstrap
Plug 'ap/vim-css-color' " CSS renk önizleme
Plug 'iamcco/coc-tailwindcss', {'do': 'npm install'} " Tailwind CSS desteği
Plug 'hail2u/vim-css3-syntax' " CSS3 syntax
Plug 'bootstrap-vim/bootstrap-vim' " Bootstrap syntax

" FZF (Fuzzy Finder)
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } } " FZF kurulumu
Plug 'junegunn/fzf.vim' " FZF Vim entegrasyonu

" Diğer Araçlar
Plug 'dense-analysis/ale' " Linting ve formatlama
Plug 'prettier/vim-prettier', { 'do': 'npm install' } " Prettier formatlama
Plug 'puremourning/vimspector' " Debugger

call plug#end()

" Temel Ayarlar
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

" Coc.nvim Ayarları
let g:coc_global_extensions = [
  \ 'coc-tsserver',
  \ 'coc-json',
  \ 'coc-eslint',
  \ 'coc-prettier',
  \ 'coc-phpactor',
  \ 'coc-css',
  \ 'coc-tailwindcss',
  \ 'coc-highlight',
  \ 'coc-snippets',
  \ 'coc-pairs',
  \ ]

inoremap <silent><expr> <TAB>
      \ pumvisible() ? "\<C-n>" :
      \ <SID>check_back_space() ? "\<TAB>" :
      \ coc#refresh()
inoremap <expr><S-TAB> pumvisible() ? "\<C-p>" : "\<C-h>"

function! s:check_back_space() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction

inoremap <expr> <cr> pumvisible() ? "\<C-y>" : "\<C-g>u\<CR>"

nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gy <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)
nmap <silent> gr <Plug>(coc-references)

" Prettier Formatlama
command! -nargs=0 Prettier :call CocAction('runCommand', 'prettier.formatFile')

" ALE Linting Ayarları
let g:ale_fixers = {
  \ 'javascript': ['eslint', 'prettier'],
  \ 'typescript': ['eslint', 'prettier'],
  \ 'php': ['php_cs_fixer'],
  \ 'css': ['prettier'],
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

" Vimspector Debugger Ayarları
let g:vimspector_enable_mappings = 'HUMAN'
nmap <Leader>dd :call vimspector#Launch()<CR>
nmap <Leader>de :call vimspector#Reset()<CR>
nmap <Leader>dc :call vimspector#Continue()<CR>
nmap <Leader>dt :call vimspector#ToggleBreakpoint()<CR>
nmap <Leader>dT :call vimspector#ClearBreakpoints()<CR>

" NERDTree Ayarları
nnoremap <C-n> :NERDTreeToggle<CR>

" FZF Ayarları
nnoremap <C-p> :Files<CR>
nnoremap <C-f> :Rg<CR>
nnoremap <C-b> :Buffers<CR>
nnoremap <C-g> :GFiles<CR>

" Prettier Formatlama Kısayolu
nnoremap <Leader>p :Prettier<CR>

" Dosya Kaydetme ve Çıkış
nnoremap <C-s> :w<CR>
nnoremap <C-q> :q<CR>

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

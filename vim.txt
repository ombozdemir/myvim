  call plug#begin('~/.vim/plugged')
  
  " Eklentiler buraya eklenecek
  Plug 'neoclide/coc.nvim', {'branch': 'release'}
  Plug 'junegunn/fzf'
  Plug 'junegunn/fzf.vim'
  Plug 'vim-airline/vim-airline'
  Plug 'vim-airline/vim-airline-themes'
  
  call plug#end()
  " coc.nvim ayarları
  set hidden
  set updatetime=300
  set shortmess+=c
  set signcolumn=yes
  
  " Kısayollar
  nmap <silent> gd <Plug>(coc-definition)
  nmap <silent> gy <Plug>(coc-type-definition)
  nmap <silent> gi <Plug>(coc-implementation)
  nmap <silent> gr <Plug>(coc-references)

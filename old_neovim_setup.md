# Old neovim setup using kickstart

# please refer to [https://github.com/vishmaycode/lazyvim-setup](https://github.com/vishmaycode/lazyvim-setup) for latest configs

[https://github.com/nvim-lua/kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim) <-- for your next setup (very imp)


### NVIM installation
this installs old version = 0.7
 ```shell
sudo apt install neovim
```

so instead do (0.10):
```shell
wget https://github.com/neovim/neovim/releases/latest/download/nvim.appimage
chmod 775 nvim.appimage
sudo mv nvim.appimage  /usr/local/bin/nvim
```

- Install python3-jedi

### nvim config
```shell
mkdir -p .config/nvim/
vim init.vim
```

with chagnes regarding keybindings
[https://github.com/NeuralNine/config-files/blob/master/init.vim](https://github.com/NeuralNine/config-files/blob/master/init.vim)


in command line
```shell
:PlugInstall - to install plugins
:call coc#util#install() - to update coc plugin

:CocInstall coc-python
```

### show git branch
```shell
Plug 'https://github.com/tpope/vim-fugitive' " for git branch showing in airline
let g:airline#extensions#branch#enabled = 1
```


### all coc plugins

coc-prettier
coc-html
coc-vetur
coc-tsserver
coc-sql
coc-sh
coc-rls
coc-python
coc-perl
coc-markdownlint
coc-json
coc-jedi
coc-java
coc-go
coc-flutter
coc-css
coc-cmake
coc-clangd
coc-snippets

### treesitter installation

```shell
:TSUpdate

:TSInstall bash c cpp
:TSInstall c_sharp css diff elixir
:TSInstall elm go graphql haskell html
:TSInstall javascript json lua make markdown
:TSInstall markdown_inline matlab ninja php
:TSInstall python r ruby rust scala
:TSInstall scheme sql swift typescript vim yaml
:TSInstall awk cmake csv dockerfile dart
:TSInstall git_config git_rebase gitattributes gitcommit gitignore
:TSInstall http ini java jsonc meson
:TSInstall regex requirements scss tmux xml
```


### coc-settings.json
```shell
{
  "snippets.ultisnips.pythonPrompt": false,
  "languageserver": {
    "intelephense": {
      "command": "intelephense",
      "args": ["--stdio"],
      "filetypes": ["php"]
    }
  },
  "prettier.tabWidth": 4,
  "prettier.useTabs": false
}
```


#### init.vim 

```shell
syntax on

set number
set relativenumber
set autoindent
set tabstop=4
set shiftwidth=4
set smarttab
set softtabstop=4
set mouse=a
" set foldmethod=syntax
" set foldlevel=99
set clipboard=unnamedplus
set hlsearch " Highlights search results
set incsearch " Incrementally highlights search matches as you type
set termguicolors
set foldlevel=20
set foldmethod=expr
set foldexpr=nvim_treesitter#foldexpr()

call plug#begin()

Plug 'http://github.com/tpope/vim-surround' " Surrounding ysw)
Plug 'https://github.com/preservim/nerdtree' " NerdTree
Plug 'https://github.com/tpope/vim-commentary' " For Commenting gcc & gc
Plug 'https://github.com/vim-airline/vim-airline' " Status bar
Plug 'https://github.com/vim-airline/vim-airline-themes' " Themes for airline
Plug 'https://github.com/lifepillar/pgsql.vim' " PSQL Pluging needs :SQLSetType pgsql.vim
Plug 'https://github.com/ap/vim-css-color' " CSS Color Preview
Plug 'https://github.com/rafi/awesome-vim-colorschemes' " Retro Scheme
Plug 'https://github.com/neoclide/coc.nvim'  " Auto Completion
Plug 'https://github.com/ryanoasis/vim-devicons' " Developer Icons
Plug 'https://github.com/tc50cal/vim-terminal' " Vim Terminal
Plug 'https://github.com/preservim/tagbar' " Tagbar for code navigation
Plug 'https://github.com/terryma/vim-multiple-cursors' " CTRL + N for multiple cursors
Plug 'https://github.com/tpope/vim-fugitive' " for git branch showing in airline
Plug 'https://github.com/folke/which-key.nvim' " for keyboard shortcuts in popup
Plug 'https://github.com/lewis6991/gitsigns.nvim' " for git blame and more
Plug 'https://github.com/nvim-lua/plenary.nvim' " Required dependency for Telescope
Plug 'https://github.com/nvim-telescope/telescope.nvim' " better file manager
Plug 'https://github.com/norcalli/nvim-colorizer.lua' " for css colors 
Plug 'https://github.com/xiyaowong/transparent.nvim' " for background transparancy
Plug 'https://github.com/christoomey/vim-tmux-navigator' " for vim tmux navigation ease
Plug 'https://github.com/nvim-treesitter/nvim-treesitter', {'do': ':TSUpdate'} " for language parsing

set encoding=UTF-8

call plug#end()

set completeopt-=preview " For No Previews

autocmd FileType python setlocal foldmethod=indent

colorscheme jellybeans

let g:NERDTreeDirArrowExpandable="+"
let g:NERDTreeDirArrowCollapsible="~"

" --- Just Some Notes ---
" :PlugClean :PlugInstall :UpdateRemotePlugins
"
" :CocInstall coc-python
" :CocInstall coc-clangd
" :CocInstall coc-snippets
" :CocCommand snippets.edit... FOR EACH FILE TYPE

" air-line
let g:airline_powerline_fonts = 1
let g:airline#extensions#branch#enabled = 1
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#show_buffers = 1

if !exists('g:airline_symbols')
    let g:airline_symbols = {}
endif

" unicode symbols
let g:airline_left_sep = '»'
let g:airline_left_sep = '▶'
let g:airline_right_sep = '«'
let g:airline_right_sep = '◀'
let g:airline_symbols.linenr = '␊'
let g:airline_symbols.linenr = '␤'
let g:airline_symbols.linenr = '¶'
let g:airline_symbols.branch = '⎇'
let g:airline_symbols.paste = 'ρ'
let g:airline_symbols.paste = 'Þ'
let g:airline_symbols.paste = '∥'
let g:airline_symbols.whitespace = 'Ξ'

" airline symbols
let g:airline_left_sep = ''
let g:airline_left_alt_sep = ''
let g:airline_right_sep = ''
let g:airline_right_alt_sep = ''
let g:airline_symbols.branch = ''
let g:airline_symbols.readonly = ''
let g:airline_symbols.linenr = '  '

let g:airline_theme = 'bubblegum' " or any other theme name


" Keyborad Shortcuts
" Leader Key
let mapleader = "\<Space>"  " Use space as the leader key

" Coc
inoremap <expr> <Tab> pumvisible() ? coc#_select_confirm() : "<Tab>"
nnoremap <leader>jd :call CocActionAsync('jumpDefinition')<CR>  

" NERDTree
nnoremap <leader>nf :NERDTreeFocus<CR>
nnoremap <leader>nt :NERDTreeToggle<CR>
"nnoremap <C-N> :NERDTree<CR>

" Tagbar/Preview
nmap <F8> :TagbarToggle<CR>

" Tabs
nnoremap <leader>tc :tabnew<CR>
nnoremap <leader>tn :tabnext<CR>
nnoremap <leader>tp :tabprevious<CR>
nnoremap <leader>tq :tabclose<CR>

" Buffers
nnoremap <leader>bn :bnext<CR>
nnoremap <leader>bp :bprevious<CR>

" Code Formatting
nnoremap <leader>cf :CocCommand prettier.formatFile<CR>

" Telescope basic keybindings
nnoremap <leader>ff :Telescope find_files no_ignore=true<CR>
nnoremap <leader>fg :Telescope live_grep<CR>
nnoremap <leader>fb :Telescope buffers<CR>
nnoremap <leader>fh :Telescope help_tags<CR>

" Transparancy
nnoremap <leader>tt :TransparentToggle <CR>

lua << EOF
	require('which-key').setup {}
	require 'colorizer'.setup()
	require('gitsigns').setup {
	  current_line_blame = true,  -- disable blame by default
	  on_attach = function(bufnr)
		local gs = package.loaded.gitsigns
		-- Toggle current line blame with <leader>gb
		vim.api.nvim_buf_set_keymap(bufnr, 'n', '<leader>gb', '<cmd>lua require"gitsigns".toggle_current_line_blame()<CR>', { noremap = true, silent = true })
	  end
	}
	require('telescope').setup{
	  defaults = {
		prompt_prefix = "> ",
		selection_caret = "> ",
		sorting_strategy = "ascending",
		file_ignore_patterns = { 
		  "node_modules",
		  "venv",
		  "__pycache__",
		  ".git",
		  "build",
		  ".vscode",
		  ".idea",
		  "dist",
		},
		vimgrep_arguments = {
		  "rg",
		  "--follow",        -- Follow symbolic links
		  "--hidden",        -- Search for hidden files
		  "--no-heading",    -- Don't group matches by each file
		  "--with-filename", -- Print the file path with the matched lines
		  "--line-number",   -- Show line numbers
		  "--column",        -- Show column numbers
		  "--smart-case",    -- Smart case search

		  -- Exclude some patterns from search
		  "--glob=!**/.git/*",
		  "--glob=!**/.idea/*",
		  "--glob=!**/.vscode/*",
		  "--glob=!**/build/*",
		  "--glob=!**/dist/*",
		  "--glob=!**/yarn.lock",
		  "--glob=!**/package-lock.json",		
		},
		pickers = {
			find_files = {
			  hidden = true,
			  -- needed to exclude some files & dirs from general search
			  -- when not included or specified in .gitignore
			  find_command = {
				'fd',
				'--type',
				'f',
				'--no-ignore-vcs',
				'--color=never',
				'--hidden',
				'--follow',
				"rg",
				"--files",
				"--hidden",
				"--glob=!**/.git/*",
				"--glob=!**/.idea/*",
				"--glob=!**/.vscode/*",
				"--glob=!**/build/*",
				"--glob=!**/dist/*",
				"--glob=!**/yarn.lock",
				"--glob=!**/package-lock.json",
			  },
			},
		},
		layout_config = {
		  horizontal = {
			preview_width = 0.5,
		  },
		},
	  },
	}
	require('transparent').setup({
    enable = true, -- boolean: enable this plugin (default: true)
    extra_groups = { -- table: extra groups that should be transparent, see `:h highlight-args`
        'NormalFloat', 'FloatBorder', 'NormalNC', 'SignColumn', 'EndOfBuffer'
    },
    exclude_groups = {}, -- table: groups you don't want to be transparent
})
EOF
```

# My vimrc settings

Based on the awesome configuration from amix/vimrc.
* **Awesome**: This includes a ton of useful plugins, color schemes and configurations


## How to install the Awesome version?
The awesome version includes a lot of great plugins, configurations and color schemes that make Vim a lot better. To install it simply do following:

	git clone git://github.com/amix/vimrc.git ~/.vim_runtime
  git submodule init
  git submodule update
	sh ~/.vim_runtime/install_awesome_vimrc.sh

The taglist.vim plugin will require ctags (http://ctags.sourceforge.net) (Debian: apt-get install ctags)

I also recommend using [Source Code Pro font from Adobe](http://store1.adobe.com/cfusion/store/html/index.cfm?event=displayFontPackage&code=1960) (it's free and awesome font for writing and programming). The Awesome vimrc is already setup to try to use it


## How to update to latest version?

Simply just do a git rebase!

    cd ~/.vim_runtime
    git pull --rebase


## Included Plugins

I recommend reading the docs of these plugins to understand them better. Each of them provide a much better Vim experience!

* [pathogen.vim](https://github.com/tpope/vim-pathogen): Manages the runtime path of the plugins
* [YankRing](https://github.com/vim-scripts/YankRing.vim): Maintains a history of previous yanks, changes and deletes
* [snipMate.vim](https://github.com/garbas/vim-snipmate): snipMate.vim aims to be a concise vim script that implements some of TextMate's snippets features in Vim
* [NERD Tree](https://github.com/scrooloose/nerdtree): A tree explorer plugin for vim
* [ack.vim](https://github.com/mileszs/ack.vim): Vim plugin for the Perl module / CLI script 'ack'
* [ctrlp.vim](https://github.com/kien/ctrlp.vim): Fuzzy file, buffer, mru and tag finder. In my config it's mapped to `<Ctrl+F>`, because `<Ctrl+P>` is used by YankRing
* [open_file_under_cursor.vim](https://github.com/amix/open_file_under_cursor.vim): Open file under cursor when pressing `gf`
* [emmet-vim](https://github.com/mattn/emmet-vim): Expanding abbreviation like zen-coding, very useful for editing XML, HTML.
* [vim-indent-object](https://github.com/michaeljsmith/vim-indent-object): Defines a new text object representing lines of code at the same indent level. Useful for python/vim scripts
* [taglist.vim](https://github.com/vim-scripts/taglist.vim): Source code browser (supports C/C++, java, perl, python, tcl, sql, php, etc)
* [vim-multiple-cursors](https://github.com/terryma/vim-multiple-cursors): Sublime Text style multiple selections for Vim, CTRL+N is remapped to CTRL+S (due to YankRing)
* [vim-expand-region](https://github.com/terryma/vim-expand-region): Allows you to visually select increasingly larger regions of text using the same key combination.
* [vim-airline](https://github.com/bling/vim-airline): Lean & mean status/tabline for vim that's light as air (replacing powerline)
Remove all clutter and focus only on the essential. Similar to iA Writer or Write Room [Read more here](http://amix.dk/blog/post/19744)
* [vim-commentary](https://github.com/tpope/vim-commentary): Comment stuff out.  Use `gcc` to comment out a line (takes a count), `gc` to comment out the target of a motion. `gcu` uncomments a set of adjacent commented lines.
* [syntastic](https://github.com/scrooloose/syntastic): Syntax checking hacks for vim


## Included color schemes

* [gruvbox](https://github.com/morhetz/gruvbox)


## Included modes

* [vim-less](https://github.com/groenewege/vim-less)


## How to include your own stuff?

After you have installed the setup you can create **~/.vim_runtime/my_configs.vim** to fill in any configurations that are important for you. For instance, my **my_configs.vim** looks like this:

	~/.vim_runtime (master)> cat my_configs.vim
	map <leader>ct :cd ~/Desktop/Todoist/todoist<cr>
	map <leader>cw :cd ~/Desktop/Wedoist/wedoist<cr>

You can also install your own plugins, for instance, via pathogen we can install [vim-rails](https://github.com/tpope/vim-rails):

	cd ~/.vim_runtime
	git clone git://github.com/tpope/vim-rails.git sources_non_forked/vim-rails

Now you have vim-rails installed ;-)


## Key Mappings

### Plugin related mappings

Open [ctrlp.vim](https://github.com/kien/ctrlp.vim) plugin:

    let g:ctrlp_map = '<c-f>'

Managing the [NERD Tree](https://github.com/scrooloose/nerdtree) plugin:

    map <leader>nn :NERDTreeToggle<cr>
    map <leader>nb :NERDTreeFromBookmark
    map <leader>nf :NERDTreeFind<cr>

### Normal mode mappings

Fast saving of a buffer:

	nmap <leader>w :w!<cr>

Treat long lines as break lines (useful when moving around in them):

	map j gj
	map k gk

Map `<Space>` to `/` (search) and `<Ctrl>+<Space>` to `?` (backwards search):

	map <space> /
	map <c-space> ?
	map <silent> <leader><cr> :noh<cr>

Disable highlight when `<leader><cr>` is pressed:

	map <silent> <leader><cr> :noh<cr>

Smart way to move between windows:

	map <C-j> <C-W>j
	map <C-k> <C-W>k
	map <C-h> <C-W>h
	map <C-l> <C-W>l

Closing of current buffer(s):

	" Close current buffer
	map <leader>bd :Bclose<cr>

	" Close all buffers
	map <leader>ba :1,1000 bd!<cr>

Useful mappings for managing tabs:

	map <leader>tn :tabnew<cr>
	map <leader>to :tabonly<cr>
	map <leader>tc :tabclose<cr>
	map <leader>tm :tabmove

	" Opens a new tab with the current buffer's path
	" Super useful when editing files in the same directory
	map <leader>te :tabedit <c-r>=expand("%:p:h")<cr>/

Switch CWD to the directory of the open buffer:

	map <leader>cd :cd %:p:h<cr>:pwd<cr>

Open vimgrep and put the cursor in the right position:

	map <leader>g :vimgrep // **/*.<left><left><left><left><left><left><left>

Vimgreps in the current file:

	map <leader><space> :vimgrep // <C-R>%<C-A><right><right><right><right><right><right><right><right><right>

Remove the Windows ^M - when the encodings gets messed up:

	noremap <leader>m mmHmt:%s/<C-V><cr>//ge<cr>'tzt'm

Quickly open a buffer for scripbble:

	map <leader>q :e ~/buffer<cr>

Toggle paste mode on and off:

	map <leader>pp :setlocal paste!<cr>


### Insert mode mappings

Quickly insert parenthesis/brackets/etc.:

    inoremap $1 ()<esc>i
    inoremap $2 []<esc>i
    inoremap $3 {}<esc>i
    inoremap $4 {<esc>o}<esc>O
    inoremap $q ''<esc>i
    inoremap $e ""<esc>i
    inoremap $t <><esc>i

Insert the current date and time (useful for timestamps):

    iab xdate <c-r>=strftime("%d/%m/%y %H:%M:%S")<cr>


### Visual mode mappings

Visual mode pressing `*` or `#` searches for the current selection:

	vnoremap <silent> * :call VisualSelection('f')<CR>
	vnoremap <silent> # :call VisualSelection('b')<CR>

When you press gv you vimgrep after the selected text:

	vnoremap <silent> gv :call VisualSelection('gv')<CR>

When you press `<leader>r` you can search and replace the selected text:

	vnoremap <silent> <leader>r :call VisualSelection('replace')<CR>

Surround the visual selection in parenthesis/brackets/etc.:

    vnoremap $1 <esc>`>a)<esc>`<i(<esc>
    vnoremap $2 <esc>`>a]<esc>`<i[<esc>
    vnoremap $3 <esc>`>a}<esc>`<i{<esc>
    vnoremap $$ <esc>`>a"<esc>`<i"<esc>
    vnoremap $q <esc>`>a'<esc>`<i'<esc>
    vnoremap $e <esc>`>a"<esc>`<i"<esc>


### Command line mappings

$q is super useful when browsing on the command line. It deletes everything until the last slash:

    cno $q <C-\>eDeleteTillSlash()<cr>

Bash like keys for the command line:

    cnoremap <C-A>		<Home>
    cnoremap <C-E>		<End>
    cnoremap <C-K>		<C-U>

    cnoremap <C-P> <Up>
    cnoremap <C-N> <Down>

Write the file as sudo (only on Unix). Super useful when you open a file and you don't have permissions to save your changes. [Vim tip](http://vim.wikia.com/wiki/Su-write):

    :W


### Spell checking
Pressing `<leader>ss` will toggle and untoggle spell checking

    map <leader>ss :setlocal spell!<cr>

Shortcuts using `<leader>` instead of special chars

    map <leader>sn ]s
    map <leader>sp [s
    map <leader>sa zg
    map <leader>s? z=

### Cope
Do :help cope if you are unsure what cope is. It's super useful!

When you search with vimgrep, display your results in cope by doing:
`<leader>cc`

To go to the next search result do:
`<leader>n`

To go to the previous search results do:
`<leader>p`

Vimscript mappings:

    map <leader>cc :botright cope<cr>
    map <leader>co ggVGy:tabnew<cr>:set syntax=qf<cr>pgg
    map <leader>n :cn<cr>
    map <leader>p :cp<cr>

## Useful blog tips regarding my Vim setup

* [Vim: Annotate strings with gettext (the macro way)](http://amix.dk/blog/post/19678#Vim-Annotate-strings-with-gettext-the-macro-way)
* [vimgrep: Searching through multiple file extensions](http://amix.dk/blog/post/19672#vimgrep-Searching-through-multiple-file-extensions)
* [Filtering through vimgrep results using regular expressions](http://amix.dk/blog/post/19666#Filtering-through-vimgrep-results-using-regular-expressions)
* [Vim 7.3: Persistent undo and encryption!](http://amix.dk/blog/post/19548#Vim-7-3-Persistent-undo-and-encryption)
* [Vim tips: Visual Search](http://amix.dk/blog/post/19334#Vim-tips-Visual-Search)
* [Folding in Vim](http://amix.dk/blog/post/19132#Folding-in-Vim)

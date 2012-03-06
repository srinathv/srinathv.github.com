Vim ideas
=========

MacVim Background Transparancy:
You have to start the experimental render in perferences > advance:
Then you can "set transperancy = 15" in your .gvimrc


http://vim.wikia.com/wiki/Best_Vim_Tips
delete all lines containing a pattern

 

Using etags: Ctrl-] and Ctrl-T (returns)

Using cscope: Ctrl-\s and Ctrl(space)s

  

For Fortran free highlighting fix, your .vimrc needs:

filetype plugin indent on

syntax on

let s:extfname = expand("%:e")
     if s:extfname ==? "f90"
      let fortran_free_source=1
      unlet! fortran_fixed_source
    else
      let fortran_fixed_source=1
     unlet! fortran_free_source
    endif
  

Bufexplorer:

With bufexplorer, you can quickly and easily switch between buffers by using the one of the default public interfaces: 

  '\be' (normal open)  or 
  '\bs' (force horizontal split open)  or 
  '\bv' (force vertical split open) 

Avoiding the Esc keyEdit
Pressing Ctrl-[ (control plus left square bracket) is equivalent to pressing Esc. On a US keyboard, pressing Ctrl-[ is an easy way to exit from insert mode. 

change highlighting (space to get rid of after search)
:noremap <silent> <Space> :silent noh<Bar>echo<CR>


to upper or lower case

To
make text lowercase use ``gu'' or ``gugu''

:h gu
:h gugu

or for uppercase

:h gU
:h gUgU

jumping to matching braces:

The % key can be used:

To jump to a matching opening or closing parenthesis, square bracket or a curly brace: ([{}])
To jump to start or end of a C-style comment: /* */.
To jump to a matching C/C++ preprocessor conditional: #if, #ifdef, #else, #elif, #endif.
To jump between appropriate keywords, if supported by the ftplugin file, for example, between begin and end in a Pascal program
 
Working with multiple files

:e filename - Edit a file in a new buffer
:bnext (or :bn) - go to next buffer
:bprev (of :bp) - go to previous buffer
:bd - delete a buffer (close a file)
:sp filename - Open a file in a new buffer and split window
ctrl+ws - Split windows
ctrl+ww - switch between windows
ctrl+wq - Quit a window
ctrl+wv - Split windows vertically
formatting stuff:

from:Garrett's vi page 

 
:.!fmt	Format the current line only (Unix)
!}fmt	Format the current paragraph, (e.g., to next whitepspace; UNIX)
!3}fmt	Format the current and next two paragraphs (or next n-1; UNIX)
So an easy way to format the a paragraph to 80 characters is, with the cursor anywhere on the paragraph:

!}fmt -45
will format to 45 columns.

!Gfmt -80

will  format everything from the current location to the end of the file to 80 column.



yiw	yank inner word (copy word under cursor, say "first").
...	Move the cursor to another word (say "second").
viwp	select "second", then replace it with "first".
...	Move the cursor to another word (say "third").
viw"0p	select "third", then replace it with "first".
Copy a line and paste it over other lines:
yy	yank current line (say "first line").
...	Move the cursor to another line (say "second line").
Vp	select "second line", then replace it with "first line".
...	Move the cursor to another line (say "third line").
V"0p	select "third line", then replace it with "first line".




Opening and closing foldsEdit
The command zc will close a fold (if the cursor is in an open fold), and zo will open a fold (if the cursor is in a closed fold). It's easier to just use za which will toggle the current fold (close it if it was open, or open it if it was closed).
The commands zc (close), zo (open), and za (toggle) operate on one level of folding, at the cursor. The commands zC, zO and zA are similar, but operate on all folding levels (for example, the cursor line may be in an open fold, which is inside another open fold; typing zC would close all folds at the cursor).

The command zr reduces folding by opening one more level of folds throughout the whole buffer (the cursor position is not relevant). Use zR to open all folds.

The command zm gives more folding by closing one more level of folds throughout the whole buffer. Use zM to close all folds.

Date and time insert:
:r !date

Using MacVim as your SVN or GIT editor.
In your .bashrc use
GIT_EDITOR='mvim -f'

You need to run mvim with the -f flag so that it stays in the foreground. By default, it forks and returns control to the terminal which makes subversion think it is done.

vi / vim show line number command

To display line numbers along the left side of a window, type any one of the following:
:set number

or
:set nu


(Fig.01: Vi / Vim line numbers in action - click to enlarge image)
To turn off line number again enter the same command:
:set nu!

If you need number every time you start vi/vim, append following line to your ~/.vimrc file:
set number


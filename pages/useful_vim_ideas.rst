Vim ideas
=========
.. contents:: Making Vim work for me.

.. highlight:: vim

MacVim Background Transparancy
______________________________

You have to start the experimental render in perferences > advance:
Then you can::

  set transperancy = 15
 
in your .gvimrc

Making MacVim case sensitive to file names
__________________________________________

Clone from github: https://github.com/b4winckler/macvim

Build instruction here: https://github.com/b4winckler/macvim/wiki/Building

Uncomment the following 2 in os_mac.h::

  #define CASE_INSENSITIVE_FILENAME   /* ignore case when comparing file names */
  #define USE_FNAME_CASE                /* make ":e os_Mac.c" open the file in its
                                   original case, as "os_mac.c" */
I did by adding at the end of the file::
  #undef CASE_INSENSITIVE_FILENAME 
  #undef USE_FNAME_CASE 

And follow the direction for build and install.




Delete lines with a pattern
___________________________


http://vim.wikia.com/wiki/Best_Vim_Tips

delete all lines containing a pattern

 
Etags
_____


Using etags: Ctrl-] and Ctrl-T (returns)

Using cscope: Ctrl-\s and Ctrl(space)s

  

For Fortran free highlighting
_____________________________

In your .vimrc ::

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
  

Bufexplorer
___________

With bufexplorer, you can quickly and easily switch between buffers by using the one of the default public interfaces: 

  '\be' (normal open)  or 

  '\bs' (force horizontal split open)  or 

  '\bv' (force vertical split open) 

Avoiding the Esc keyEdit
________________________

Pressing ::

  Ctrl-[ (control plus left square bracket)

is equivalent to pressing Esc. On a US keyboard, pressing Ctrl-[ is an easy way to exit from insert mode. 

To clear highlighting
_____________________

In order to use "space" to get rid of highlighting after a search, add the following to your .vimrc ::

  :noremap <silent> <Space> :silent noh<Bar>echo<CR>

Upper and lower casing
______________________


To make text lowercase use ::

  :gu 


or ::

  :gugu

or for uppercase::

  gU

or::

  gUgU

Matching braces and more with use if "%"
________________________________________

To jump to the matching parenthesis, square bracket or a curly brace, place the cursor the first, the press "%"
and you will jump to the match.  This works with C-style comments, preprocessor conditionals, and keywords
stated in support ftplugin files.

Working with multiple files
___________________________

:e filename - Edit a file in a new buffer

:bnext (or :bn) - go to next buffer

:bprev (of :bp) - go to previous buffer

:bd - delete a buffer (close a file)

:sp filename - Open a file in a new buffer and split window

ctrl+ws - Split windows

ctrl+ww - switch between windows

ctrl+wq - Quit a window

ctrl+wv - Split windows vertically


Formatting text
_______________
 
:.!fmt	Format the current line only (Unix)

!}fmt	Format the current paragraph, (e.g., to next whitepspace; UNIX)

!3}fmt	Format the current and next two paragraphs (or next n-1; UNIX)

So an easy way to format the a paragraph to 80 characters is, with the cursor anywhere on the paragraph ::

  !}fmt -45

will format to 45 columns. ::

  !Gfmt -80

will  format everything from the current location to the end of the file to 80 column.


Replacing example 
_________________

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




Opening and closing folds
_________________________

The command zc will close a fold (if the cursor is in an open fold), and zo will open a fold (if the cursor is in a closed fold). It's easier to just use za which will toggle the current fold (close it if it was open, or open it if it was closed).
The commands zc (close), zo (open), and za (toggle) operate on one level of folding, at the cursor. The commands zC, zO and zA are similar, but operate on all folding levels (for example, the cursor line may be in an open fold, which is inside another open fold; typing zC would close all folds at the cursor).

The command zr reduces folding by opening one more level of folds throughout the whole buffer (the cursor position is not relevant). Use zR to open all folds.

The command zm gives more folding by closing one more level of folds throughout the whole buffer. Use zM to close all folds.

Date and time insert
____________________

To insert date ::

  :r !date

Using MacVim as your SVN or GIT editor
______________________________________

In your .bashrc use::

  GIT_EDITOR='mvim -f'

You need to run mvim with the -f flag so that it stays in the foreground. By default, it forks and returns control to the terminal which makes subversion think it is done.

Display line numbers in left column
___________________________________

To display line numbers along the left side of a window, type any one of the following::
  :set number

or ::
  :set nu

To turn off line number again enter the same command::

  :set nu!

If you need number every time you start vi/vim, append following line to your ~/.vimrc file ::

  set number


MacVim and Ipython
__________________

use https://github.com/jkitzes/ipyqtmacvim/

The comands are :
Command-4: send line to ipython qtconsole
Command-5: run entire file.


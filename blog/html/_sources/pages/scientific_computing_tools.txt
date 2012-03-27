Scientific computing tools
==========================
.. contents:: Help me plot, calculate, run many times with easy documention


.. highlight:: bash
   
This will test github math rendering.

.. math:: a^2

Does this work :math:`x \rightarrow \int dy`.
Yes this works.

But what about math lines

Parallel debugging with GDB
___________________________

This method latches an instance of *gdb* to each process.::
  
  $mpirun -np <NP> xterm -e gdb ./program 

which launches a *xterm* for each process.  You will have to::

  $run <arg1> <arg2> ... <argN>

in each *xterm* window before the program executes.

Cron stuff
__________

crontab -l :lists contents of crontab
crontab -e :edits contents of crontab

Python stuff
____________

The ipython community has done a fantastic job turning your browser into an interface.::

  ipython notebook --pylab inline

I use::

  ipython qtconsole --pylab inline

which requires a stable QT build.

GCC and OpenMP
______________

With the current GCC suite, adding *-fopenmp* will include the correct libraries.

Documentating
_____________

Sphinx
~~~~~~

Good restructured text reference http://docutils.sourceforge.net/docs/user/rst/quickref.html

Ecplise
_______

I am very new to Ecplise.  Need more here as I learn things.

Fortran 2003
____________

The Object Oriented concepts implemented in fortran are nicely detailed here at http://www.pgroup.com/lit/articles/insider/v3n1a3.htm
and at http://www.pgroup.com/lit/articles/insider/v3n2a2.htm 

PGI CUDA and more
~~~~~~~~~~~~~~~~~

http://www.pgroup.com/resources/articles.htm#articles is a great resource for current fortran and other PGI activity.

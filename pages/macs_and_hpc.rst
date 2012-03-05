Macs and HPC 
============

.. highlight:: bash

Macports does help
-------------------

I like using macports since it really handles package dependencies well.  
I have had great sucess with macport's built GNU compilers.  I need to 
investigate when ports use the LLVM vs. the gcc, but other than that most 
things are clear.  This is what I have :download:`installed <./files/sv_mp_installed.txt>`.
 


Making macports packages defaults
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Most macports built packages have the executables namespaced as 
not clash with the system ones.  It is nice to have the option
of making a macport built package default by changing the name. ::

  port select --list
  Error: port select [--list|--set|--show] <group> [<version>]

  port select --list python
  Available versions for python:
	  none
	  python24
	  python25
	  python25-apple
	  python26
	  python26-apple
	  python27 (active)
	  python32

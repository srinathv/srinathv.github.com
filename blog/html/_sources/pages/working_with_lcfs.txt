Working with LCFs
=================


.. contents:: Gett'n Git Gone


.. highlight:: bash


Links for Jaguar/Titan
_______________________

It is easier to go to one place and find useful links:

PGI Accelerator
~~~~~~~~~~~~~~~

http://www.olcf.ornl.gov/titan/development-tools/accelerator-compiler-directives/#PGI_Accelerator

Interactive Que
~~~~~~~~~~~~~~~
http://www.olcf.ornl.gov/support/user-guides-policies/jaguar-xk6-user-guide/#6237

CrayPat: Cray profiler
~~~~~~~~~~~~~~~~~~~~~~

http://www.olcf.ornl.gov/kb_articles/software-jaguar-craypat/

There is system variable that lets you change the location of .craypat, which seems to hold all the object files that have
interted hooks for profiling.  Search for *.craypat* in this webpage.

User Manual
~~~~~~~~~~~

http://www.olcf.ornl.gov/support/user-guides-policies/jaguar-xk6-user-guide/

How to figure out "size" and flags to aprun
___________________________________________

How big must you specify *size* to PBS so you can run what you want how you want to: specifiying number of cores,
threads, considering the numa connection, and GPU use?

I have made a text file for the :download:`man of aprun <./files/aprun.txt>`.

We will make examples for different combinations is a bit.

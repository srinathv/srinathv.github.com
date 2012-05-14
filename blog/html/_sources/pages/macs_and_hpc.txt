Macs and High Performance Computing 
===================================

.. contents:: What helps Macs with HPC

.. highlight:: bash

Macports does help
-------------------

I like using macports since it really handles package dependencies well.  
I have had great sucess with macport's built GNU compilers.  I need to 
investigate when ports use the LLVM vs. the gcc, but other than that most 
things are clear.  This is what I have :download:`installed <./files/sv_mp_installed.txt>`.

Lion and Xcode >=4.3
~~~~~~~~~~~~~~~~~~~~

It seems that there are some issues with the new Xcodes being placed only
in the */Applications* folder.  After you have installed Xcode and activated the 
"Command Tools" from the *Downloads* selection of Xcode's preferences, then run ::
  
  $xcode-select /Aplications/Xcode

I believe that sets where *xcodebuild* thinks Xcode lives, and now
`Macports for lion <https://distfiles.macports.org/MacPorts/MacPorts-2.0.4-10.7-Lion.dmg>`_
will install.
   
Xcode on Mac OS-X
+++++++++++++++++

One of the great things about cmake is that it supports multiple GUI development environments, 
including Xcode on the Mac, Microsoft Visual Studio on Windows, and KDevelop on Linux (and even on Mac!).

Here's how you generate an Xcode project ::

  mkdir build_xc # or whatever
  cd build_xc
  cmake -G Xcode ../

This creates a directory called <projname>.xcodeproj, which you can directly open in xcode, e.g., in the finder or at the command line ::

  open <projname>.xcodeproj

This knows all about running maketa and everything!

 


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

Mac SSD needing some help
-------------------------

Sometimes it seems that the SSD on my mac has issues.  I noticed that Utilities > Disk repair noted the disc needed
repairs.  To do this I used SuperDuper to clone the drive, then I boot from the clone and ran disk repair.  That did the
trick.  But, I also saw the need may arise to recondition the drive.  This website has useful information on this: http://macperformanceguide.com/Storage-SSD-Reconditioning.html

System profiling from command line
----------------------------------

If you want to know what makes up your machine (from the command line), then *system_profile* is what to use.::

  $system_profile | more

should give all the specs of your machine.


GPUs and the Macs
-----------------

GP-GPU programming is gaining massive momentum and lots of developers use Macs for the computing power and ease in a
nice, not too heavy case.  Nvidia makes the CUDA toolkit available for free, which will allow for CUDA-C programming on
your mac, as long as it has an NVIDIA GPU graphics card.


OPENCL
~~~~~~

Need something here



OPENACC
~~~~~~~

Need something here


Portland Group Compilers
~~~~~~~~~~~~~~~~~~~~~~~~

Cool commands ::

  $pgcpuid

and ::

  $pgaccelinfo



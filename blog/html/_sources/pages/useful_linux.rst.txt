Useful Linux commands
======================


.. contents:: Useful Linux commands


.. highlight:: bash

Print path with file name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When I grep source code to find an instance of a word or the like, I need to see what is the actual file, so a full path
helps. So at the top level of the source code you are searching, try ::

  $find . -type f -print | grep -i timer
  ./libs/utils/timer.c
  ./physics/crcp/timers/README
  ./physics/crcp/timers/makefile
  ./physics/crcp/timers/timebase32.s
  ./physics/crcp/timers/timebase64.s
  ./physics/crcp/timers/timers.c
  ./src/share/timer.h
  ./utils/csm_share/shr_timer_mod.F90

The file wanted was *timer.h*, so now I know where to look.


What shell am I?
~~~~~~~~~~~~~~~~

Sometimes you can not tell what shell you are using when you have logged into a machine.  Try running::

  $ ps -p $$

So what is $ argument passed to -p option? Remember $ returns the PID (process identification number) of the current process, and the current process is your shell. So running a ps on that number displays a process status listing of your shell. In that listing you will find the name of your shell (look for CMD column) .

So you want to disassemble...
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Some people say know what a computer program does.  But to really know, you have to look at the assembly code used by
the machine.  Try::

  $objdump -d <executable>

Now, this GNU binutils utility may not be available on your machine.  Or it may be namespaced with a "g"::

  $gobjdump -d <executable>

which is how things are namespaced on a Mac if using Macports to load things::

  $port install binutils

What is my machines processor?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following will give details about the cores of the machine you are running on (according to the OS).
Do note that the list of cores may be exaggerated due to the hardware implemented Simultaneous Multi-Threading (SMT) ::

  $less /proc/cpuinfo

How to make directories executable and files readable to all users
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To recursively give directories read&execute privileges::

  find /path/to/base/dir -type d -exec chmod 755 {} +

To recursively give files read privileges::

  find /path/to/base/dir -type f -exec chmod 644 {} +

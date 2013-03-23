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

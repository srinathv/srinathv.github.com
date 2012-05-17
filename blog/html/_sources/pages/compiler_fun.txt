Compiler Fun
============

.. contents:: Necessary Evils. 


.. highlight:: bash


GCC 4.6.3
---------

compiling on 64bit linux build error (1):
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I recently have been working to build this on a 64bit linux machine (with serious GPU power) and hit a big road block.
I installed the newest versions of *gmp,mpfr,mpc*.  The compilation of GCC kept failing.
This was my configure::

  cd gcc_4_6_3/
  srinath@mg1:/scr_0/srinath/gcc_4_6_3$ cat thisconfig.sh 
  ./configure \
    --prefix=/scr_0/srinath/gcc_suite \
    --with-gmp=/scr_0/srinath/gmp \
    --with-mpfr=/scr_0/srinath/mpfr \
    --with-mpc=/scr_0/srinath/mpc \
    --with-mpc-lib=/scr_0/srinath/mpc/lib \
    --enable-shared --enable-threads=posix --enable-checking=release \
    --enable-languages=c,c++,objc,obj-c++,java,fortran \
    --with-system-zlib --enable-__cxa_atexit \
    --disable-libunwind-exceptions --enable-libgcj-multifile \
    --enable-java-awt=gtk --disable-dssi --disable-plugin \
    --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-1.4.2.0/jre \
    --with-cpu=generic 

The compilation kept failing at a configure step in *libgcc* using the bootstrap compiler.::

  error: cannot compute suffix of object files: cannot compile 

referring to ::
  
  no libmpc.so.2 file found.

After search the web, I realized that the dynamic loader was never told where to look for these dynamic libraries, thus
I needed to::
  
  $export LD_LIBRARY_PATH=/scr_0/srinath/gmp/lib:/scr_0/srinath/mpc/lib:/scr_0/srinath/mpfr/lib:$LD_LIBRARY_PATH

to get the correct paths set for the dynamic loader.  This trick got me past the above hurdle.



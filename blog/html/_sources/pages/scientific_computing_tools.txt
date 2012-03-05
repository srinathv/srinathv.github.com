Scientific computing tools
==========================

This will test github math rendering.

.. math:: a^2

Does this work :math:`x \rightarrow \int dy`.
Yes this works.

But what about math lines


Xcode on Mac OS-X
_________________

One of the great things about cmake is that it supports multiple GUI development environments, including Xcode on the Mac, Microsoft Visual Studio on Windows, and KDevelop on Linux (and even on Mac!). Here's how you generate an Xcode project:

 mkdir build_xc # or whatever
 cd build_xc
 cmake -G Xcode ../
This creates a directory called <projname>.xcodeproj, which you can directly open in xcode, e.g., in the finder or at the command line:

 open <projname>.xcodeproj
This knows all about running maketa and everything!




Cron stuff
__________

crontab -l :lists contents of crontab
crontab -e :edits contents of crontab

Python stuff
____________

 ipython notebook --pylab inline
I use: ipython qtconsole --pylab inline

GCC and OpenMP
--------------

adding -fopenmp will include the correct libraries.

Documentating
-------------

Sphinx
~~~~~~

Good restructured text reference http://docutils.sourceforge.net/docs/user/rst/quickref.html_

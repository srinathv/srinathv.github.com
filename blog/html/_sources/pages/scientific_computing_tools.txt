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

The best place to get started is http://sphinx.pocoo.org/tutorial.html

Good restructured text reference http://docutils.sourceforge.net/docs/user/rst/quickref.html

Another primer for reStructuredText http://sphinx.pocoo.org/rest.html

Pandoc
~~~~~~

This a pretty good text file converter http://johnmacfarlane.net/pandoc/.
I used this to conver Latex to rst. Worked quite well.


Ecplise
_______

I am very new to Ecplise.  Need more here as I learn things.

Fortran 2003
____________

The Object Oriented concepts implemented in fortran are nicely detailed here at http://www.pgroup.com/lit/articles/insider/v3n1a3.htm
and at http://www.pgroup.com/lit/articles/insider/v3n2a2.htm 

PGI CUDA and more
_________________

http://www.pgroup.com/resources/articles.htm#articles is a great resource for current fortran and other PGI activity.

SSH keygen"ing"
_______________

Many remote systems require ssh for interaction.  Normally you would have to enter your login and password for that
particular remote machine to gain access.  Instead, you can generate a ssh key-pair, of which you place the public part
of the key on every remote machine you access.  This way, you only need to remember one password (which is the password
you use on your local machine).

Github uses the sshkey for access and has a great link at http://help.github.com/linux-set-up-git/.  The following is
taken directly from the github page, but placed here for convinience.

1.Check for SSH keys. Have an existing key pair? You can skip to Step 4.
First, we need to check for existing ssh keys on your computer::

  $ cd ~/.sshChecks to see if there is a directory named ".ssh" in your user directory

If it says “No such file or directory“ skip to step 3. Otherwise continue to step 2.

2.Backup and remove existing SSH keys.
Since there is already an SSH directory you’ll want to back the old one up and remove it::

  $ ls
  config	id_rsa	id_rsa.pub	known_hosts
  $ mkdir key_backup  
  $ cp id_rsad
  $ rm id_rsa

3. Generate a new SSH key.
To generate a new SSH key, enter the code below. We want the default settings so when asked to enter a file in which to save the key, just press enter.::

  $ ssh-keygen -t rsa -C "your_email@youremail.com"
  Generating public/private rsa key pair.
  Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<press enter>

Now you need to enter a passphrase.  You must do this to insure security. ::

  Enter passphrase (empty for no passphrase):<enter a passphrase>
  Enter same passphrase again:<enter passphrase again>

Which should give you something like this::

  Your identification has been saved in /Users/your_user_directory/.ssh/id_rsa.
  Your public key has been saved in /Users/your_user_directory/.ssh/id_rsa.pub.
  The key fingerprint is:
  01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db user_name@username.com
  The key's randomart image is:
  +--[ RSA 2048]----+
  |     .+   +      |
  |       = o O .   |
  |        = * *    |
  |       o = +     |
  |      o S .      |
  |     o o =       |
  |      o . E      |
  |                 |
  |                 |
  +-----------------+

Now there is a file called *.ssh/id_rsa.pub* on your local machine.  This is the public key that will be placed on the
remote computers.

You enable key-based authentication by distributing your public key to the remote machines you wish to access. 
This can be done with the following::

 $scp ~/.ssh/id_rsa.pub username@volt:

Next, ssh to the remote machine (you will still have to enter your password)and append the public key to the ~/.ssh/authorized_keys file::

  $cat id_rsa.pub >> ~/.ssh/authorized_keys
  $chmod 700 .ssh
  $chmod 600 .ssh/authorized_keys
  $rm id_rsa.pub
  $exit

You should install the public key in this manner on every remote machine you want to access using key-based authentication. To test your keys, try to ssh into the remote machine::

  $ssh <user@<remotemachine>
  Enter passphrase for key '/home/username/.ssh/id_rsa'

Hopefully that helps reduce the number of passwords you must remember.

GNU SCREEN
__________

Launching GNU screen on a remote machine is probably the first thing you should do.  Consider it as a text-based window system that keeps running in the background, even if you "detatch" because of any type of severed connection, even unintential.  A great website is https://wiki.archlinux.org/index.php/GNU_Screen .  I launch screen when I first log into a machine:: 

  $screen 

And when I relog into a system I look for active screens::

  $screen -ls

To reattach to a single active screen::

  $screen -r

This will only improve how you work with a remote machine.

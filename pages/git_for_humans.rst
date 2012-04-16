Git for humans
==============

.. contents:: Gett'n Git Gone


.. highlight:: bash

Big rules
~~~~~~~~~
I think these are important ideas to keep in mind while using git:

- git commit individual files will verbose comments

- remote repos are better off as "bare" repos 

  - these are repos that are created with::
      
      $ git clone --bare fooRepo.git

  - you can/should not manipulate any files in this particular directory.

- dedicated local branches tracking remotes is very useful

Want to see what will be pushed
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This will allow you to see the difference of branch (ie. the remote) ::

  git diff --stat origin/master

Want to see URL of remote
~~~~~~~~~~~~~~~~~~~~~~~~~

To see what is the URL of a remote and branches on the remote::

  git remote show origin

or "origin" should be the nickname of the remote.


Want see repo at a certain version
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You could "reset" your repository to any commit you want (e.g. 1 month ago).

Use git-reset for that::

    git clone [remote_address_here] my_repo
    cd my_repo
    git reset --hard [ENTER HERE THE COMMIT HASH YOU WANT]

Pushing to another non-bare repo using ssh
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

First, the *remote* repo must not be checked out to the branch you will push to.  You can be in the branch you will
push. ::
  $git checkout foo-branch
  $git push ssh://<username>@<machine.here.com>/<path to remote repo> <remote-branch name>


Undoing a "git add"
~~~~~~~~~~~~~~~~~~~

Say you did a git add on a directory and there was a hidden directory that got added::

  $ git add foo/
  $ git status
  new file:  foo/.svn/blah blah blah

To get rid of the ".svn" directory from being committed::

  $git rm -r --cached foo/.svn

The "-r" allows for the recursive removal.

Creating a "bare" repo
~~~~~~~~~~~~~~~~~~~~~~

What I have done is take an active git repo an do the following::

  $git clone --bare <URL/location of source git repo> <name of new bare repo>.git

I think the .git suffix helps denote that this is a bare repo.  All the repos on GitHub have the .git suffix.



Tracking a remote repo as branch
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Say you have 2 repos that you want to work with and one of these is a bare repo.
You can set it up as a remote as::

  $ git remote add <remote branch Nick name> <URL to bareFoo.git>

Then you must get git to understand to interact with the remote once before tracking.  This remote may have a slew of branches.::

  $git fetch <remote branch Nick Name>

Once that is done then the following will create a branch that will track this repo::

  $ git branch --track <local Branch name> <branch Nick Name>

Bam...now you have a branch that will pull from the <bareFoo> git repo. 
To make all pushes automatically go to tracked remote branches do::

  $git config --global push tracking



Submodules
~~~~~~~~~~

This is the equivalent to svn:externals with always updating with the top level updated/
Here is a great web link that explains in simple examples how to use use submodules.

http://chrisjean.com/2009/04/20/git-submodules-adding-using-removing-and-updating/

Git – setting up a remote repository and doing an initial ‘push’

http://thelucid.com/2008/12/02/git-setting-up-a-remote-repository-and-doing-an-initial-push/

So, firstly setup the remote repository::

  ssh git@example.com
  mkdir my_project.git
  cd my_project.git
  git init --bare
  git-update-server-info # If planning to serve via HTTP
  exit

On local machine::

  cd my_project
  git init
  git add *
  git commit -m "My initial commit message"
  git remote add origin git@example.com:my_project.git
  git push origin master



All things RESET
~~~~~~~~~~~~~~~~

Knowing this helps your "get GIT". http://progit.org/2011/07/11/reset.html



Making a shared repo
~~~~~~~~~~~~~~~~~~~~

In the bare repo itself do::

  $git repo-config core.sharedRepository true

Clean up a repo
~~~~~~~~~~~~~~~

Recompresses history and states.::

  $git gc

Switching remote
~~~~~~~~~~~~~~~~

If you created your repo copy by “clone” operation you will have “origin” remote branch defined. This remote can be used to pull/push changes.::

  $ git remote -v
  origin zeus.aplikacja.info:cust-proj1

If you decide to change this definition later you can issue the following commands::

  $ git remote rm origin
  $ git remote add origin git@github.com:aplikacjainfo/proj1.git
  $ git config master.remote origin
  $ git config master.merge refs/heads/master


How to prevent a bad push

To not allow a repo to accept a push that would fast forward which will screw up the local history::

  $git config --system receive.denyNonFastForwards true

(from http://randyfay.com/node/89)




The unspeakable: reverting a git push
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  http://stackoverflow.com/questions/3012929/can-i-undo-the-last-git-push



How to create branches on remotes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  http://progit.org/book/ch3-5.html

Note:  The line "git checkout -b serverfix origin/serverfix" really should have a "-B", because that will reset the properties of an existing branch, while "-b" only creates new ones with trailing properties.



Another Git tutorial
~~~~~~~~~~~~~~~~~~~~

  The Git Guys http://www.gitguys.com/topics/

Post-recieve hooks
~~~~~~~~~~~~~~~~~~

A very nice way of activating post-recieve hook for a git repo via `git notifier.  <http://www.icir.org/robin/git-notifier>`.  

Splitting up commits to make it more understandable
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Commit splitting in Git can be found `here <http://plasmasturm.org/log/530/>`.

Using github.com as webserver
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It is possible now to have github serve your webpages (obvious because you can see this page's URL).

It is important to note that the github webserver uses Jekyll, and to bypass it:

  From: Petros Amiridis (GitHub Staff)
  Subject: issue with srinathv.github.com
  

  *We use Jekyll by default when we build you site. Jekyll ignores all directories that start with an underscore.  
  It is now possible to completely bypass Jekyll processing on GitHub Pages by creating a file named* **.nojekyll** 
  *in the root of your pages repo and pushing it to GitHub. This should only be necessary if your site uses files 
  or directories that start with underscores since Jekyll considers these to be special resources and 
  does not copy them to the final site.*

A must for Vim users
~~~~~~~~~~~~~~~~~~~~

  https://github.com/tpope/vim-fugitive  via. https://github.com/tpope/vim-pathogen

Gitting a SVN repo
~~~~~~~~~~~~~~~~~~

*git-svn* is the intrinsic command that allows one to git clone an existing SVN repo.  

Handling svn:exernals
*********************

Since git and SVN are fundamentally different, one must devise a way to handle svn:externals.  There are a few exisiting
collections of scripts that try to address this.

https://github.com/andrep/git-svn-clone-externals

https://github.com/stettberger/metagit/wiki/Git-svn

Want to see what is in a commit
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A nifty way to sho commit logs and diff output each commit introduces ::

  git whatchanged <SHA>

where <SHA> is for a specific commit.  

Using Dropbox as a Git repository
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yup ... to cool to be true.::

  $cd ~/Dropbox
  $mkdir -p myrepos/foo.git
  $cd myrepos/foo.git
  $git init --bare

Now you have the bare repo in you Dropbox space.  Fairly secure place for personal stuff.  Maybe even worth paying for
som emore space.  You can now clone from the repo (which is empty) or

Pushing to Dropbox repo
-----------------------  
push to it from an existing repo *foo*.::

  $cd ~/myWork/foo 
  $git remote add dropbox file://$HOME/Dropbox/myrepos/foo.git
  $git push dropbox master

And you have just pushed your local *master* to the *dropbox* remote.

Pulling from Dropbox repo on a different computer
-------------------------------------------------

Say you jumped on a computer that is logged into your Dropbox account, but have not cloned your *foo* repo yet.  You want to::
  
  $mkdir ~/myWork
  $cd ~/myWork
  $git clone -o dropbox file://$HOME/Dropbox/myrepos/foo.git

which will make the local repo *foo* with the correct remote called *dropbox* that will merge with *master*.

Want to diff two files in different branches
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Say you want to compare two files that live in different branches ::

  $git difftool branch1:File1 branch2:File2

It is necessary to have *difftool* set in your *.gitconfig* global file.

Want to create your local branch on remote
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Suppose you branched locally to do some great development.  Now, you want to have this work also available on a remote
(possibly at github), then you first::

  $less .git/config

to get the nickname of the remote you want this new branch to also reside. Then::

  $git push -u <remote-name> <local-branch-name>

As easy as that.  The *"-u"* will make sure your local branch now *tracks (makes the upstream)* the *new*-branch on the
remote. Merge managment is now a must. 






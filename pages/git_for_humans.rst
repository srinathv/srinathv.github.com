Git for humans
==============


Commit splitting in Git can be found `here <http://plasmasturm.org/log/530/>`_.

Big rules
_________

I think these are important ideas to keep in mind while using git:

- git commit individual files will verbose comments

- remote repos are better off as "bare" repos 

  - these are repos that are created with
    $ git clone --bare fooRepo.git

  - you can/should not manipulate any files in this particular directory.

- dedicated local branches tracking remotes is very useful

- 



Want to see what will be pushed
-------------------------------

git diff --stat origin/master
Want see repo at a certain version:
You could "reset" your repository to any commit you want (e.g. 1 month ago).

Use git-reset for that:

git clone [remote_address_here] my_repo
cd my_repo
git reset --hard [ENTER HERE THE COMMIT HASH YOU WANT]

Undoing a "git add":
Say you did a git add on a directory and there was a hidden directory that got added:
$ git add foo/
$ git status
    new file:  foo/.svn/blah blah blah
To get rid of the ".svn" directory from being committed:
$git rm -r --cached foo/.svn
The "-r" allows for the recursive removal.

Creating a "bare" repo.
What I have done is take an active git repo an do the following:
$git clone --bare <URL/location of source git repo> <name of new bare repo>.git
I think the .git suffix helps denote that this is a bare repo.  All the repos on GitHub have the .git suffix.



Tracking a remote repo as branch:
Say you have 2 repos that you want to work with

Say one of these is a bare repo.
You can set it up as a remote as:
$ git remote add <remote branch Nick name> <URL to bareFoo.git>
Then you must get git to understand to interact with the remote once before tracking.  This remote may have a slew of branches.
$git fetch <remote branch Nick Name>
Once that is done then the following will create a branch that will track this repo/
$ git branch --track <local Branch name> <branch Nick Name>

Bam...now you have a branch that will pull from the <bareFoo> git repo. 
To make all pushes automatically go to tracked remote branches do:
$git config --global push tracking



Submodules.
This is the equivalent to svn:externals.
Here is a great web link that explains in simple examples how to use use submodules.
http://chrisjean.com/2009/04/20/git-submodules-adding-using-removing-and-updating/

Git – setting up a remote repository and doing an initial ‘push’

http://thelucid.com/2008/12/02/git-setting-up-a-remote-repository-and-doing-an-initial-push/

So, firstly setup the remote repository:

ssh git@example.com
mkdir my_project.git
cd my_project.git
git init --bare
git-update-server-info # If planning to serve via HTTP
exit
On local machine:

cd my_project
git init
git add *
git commit -m "My initial commit message"
git remote add origin git@example.com:my_project.git
git push origin master
All things RESET: Knowing this helps your "get GIT". 

http://progit.org/2011/07/11/reset.htmlDone!



Making a shared repo:

Make sure to do :git repo-config core.sharedRepository true

Clean up a repo:
git gc

Switching remote:
If you created your repo copy by “clone” operation you will have “origin” remote branch defined. This remote can be used to pull/push changes.

$ git remote -v
origin zeus.aplikacja.info:cust-proj1
If you decide to change this definition later you can issue the following commands:

$ git remote rm origin
$ git remote add origin git@github.com:aplikacjainfo/proj1.git
$ git config master.remote origin
$ git config master.merge refs/heads/master


How to prevent a bad push: from http://randyfay.com/node/89

git config --system receive.denyNonFastForwards true



Doing the unspeakable: reverting a git push:

hhttp://stackoverflow.com/questions/3012929/can-i-undo-the-last-git-push



How to create branches on remotes:

http://progit.org/book/ch3-5.html

Note:  The line "git checkout -b serverfix origin/serverfix" really should have a "-B", because that will reset the properties of an existing branch, while "-b" only creates new ones with trailing properties.



Looks like there a new Git tutorial: The Git Guys http://www.gitguys.com/topics/

A very nice what of activating post-recieve hook for a git repo via `git notifier.  <http://www.icir.org/robin/git-notifier>`_.  


A must for Vim users:

https://github.com/tpope/vim-fugitive  via. https://github.com/tpope/vim-pathogen



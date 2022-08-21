#Introduction
**Git** is a source code management tool, that comes with a command-line tool for its users.
## A Practical Guide:bookmark:
A particularity about Git, is that it’s designed to be useable without a central repository (you can **pull** code from your friend’s computer, and **push** you work back there, for instance), but not many people use it that way. There is usually a central Git server that the whole team **pushes** code to and **pulls** code from; however, that explains why it is often referred as a “decentralized” system.

So that you can work without a server, the **commit** operation is local, no one other than your computer knows you committed something. You can make several commits however you want, but when you want the server to know about it, you must **push** them there.

You want to be **pulling** from the repository often if other people may be working on the same branch as you, because each **pull** performs a merge operation between the code you didn’t have, and the code you recently committed locally. Therefore, in order to let you **push** , Git will sometimes demand that you **pull** first, so that the **merge** can be done on your computer, and you take care of potential **conflicts**.

Sometimes, you may have modified 3 files, but there are only two that you wish to include in the commit you’re about the make. Therefore, Git has a notion of “ index”, in which you add your modified files so that they’re included in the next commit you register.

How to configure the remote servers your local repository is talking to? They’re called remotes , and you can configure however many you need. The main one is typically named origin (that’s the name that is setup by default when you clone a project from a remote location in the first place). You can also configure however many branches you need, and name them as you please, and the default one is usually called master.

Some UI tools for Git exist, but Git is able to do so many things, that they don’t represent the magnitude of cases for which you need Git. You really want to learn to use it with the command line. Here are some commands:
~~~~
$ git clone url_of_your_remote_repository   # Clone a repository from a remote repository  
$ git add file1 file2    # will add those two files to the index if they were modified  
$ git commit -m "Meaningful commit message"   # will commit those two files (locally)  
$ git add .   # will add all of the modified files to the index at once  
$ git commit -m "Other meaningful commit message"   # will commit all of those files together  
$ git push origin master   # send all commit to the remote server
~~~~
Now, let’d do this again, but by on a branch:
~~~~
$ git branch my_feature   # Creating the branch  
$ git checkout my_feature   # Changing the codebase so that we're on that branch now  
$ git checkout -b my_feature   # This does the two previous operations in one ;)  
$ git add file1 file2  
$ git commit -m "Meaningful commit message"   # We didn't just commit this on the master branch like last time, but on the my_feature one  
$ git add .  
$ git commit -m "Other meaningful commit message"  
$ git push origin my_feature   # Notice: we're not pushing master anymore, you just create a new remote branch
~~~~
Next time you want to work on that branch, you should probably do this first:
~~~~
$ git checkout my_feature   # Just making sure you're currently on the right branch!  
$ git pull origin my_feature   # Pulling what your coworkers have done so far.
~~~~
And when you’re done with the whole feature and want to merge it to master:
~~~~
$ git checkout master  
$ git merge my_feature
~~~~
One other pretty neat thing: if you have a non-Git directory in your computer, and you want to turn it into a Git repository, it’s that easy:
~~~~
$ git init   # You're done!  
$ git remote add origin url_of_your_git_server   # So that you can push your code somewhere.
~~~~
When you’re in a Git repository, and want to know which files are modified but not in the index, and those that are modified and are in the index, you can run:
~~~~
$ git status  
~~~~
Git provides many more abilities, such as rewriting pieces of the history of the project if you feel the commits were not meaningful enough, displaying the history in visually meaningful ways, …

For instance, you should run this right now, and see how a complex history can be viewed really nicely:
~~~~
$ git clone [https://github.com/loverajoel/jstips.git](https://github.com/loverajoel/jstips.git)   # You will need a GitHub account for this to work  
$ cd jstips   # changing your directory into the one you just downloaded  
$ git log --graph --pretty=tformat:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%an %cr)%Creset' --abbrev-commit --date=relative
~~~~
Cool, right?       

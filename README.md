# Git and github with R Workshop - November 2019 👩‍💻 👨‍💻

This workshop makes use of different sources of online learning materials. 

### Preparation (before the workshop)
**(1) Complete section 1 of the happywithgithr workshop (“Installation”)**

1. Register on GitHub. https://happygitwithr.com/github-acct.html
2. Install or update R and Rstudio https://happygitwithr.com/install-r-rstudio.html
3. Install git https://happygitwithr.com/install-git.html
4. Configure git https://happygitwithr.com/hello-git.html
5. Install a git client: I will not cover all the git clients. 
	- I will show you how to use GitHub desktop (for Mac and Windows users), download here: https://desktop.github.com/. 
	- If you are a linux user I recommend gitkraken instead (and will be happy to show you that too). 

*For people with more  experience in bash/terminal/programming, please consider also doing this next step. If you don’t feel comfortable doing this or are having issues with this, do not worry. Reach out to me a prior to the training so that I can help you.*

**(2) Complete one step from section 2 of the happywithgithr workshop (“Connect Git, GitHub, RStudio”). Set up SSH keys** https://happygitwithr.com/ssh-keys.html. This step is important because it allows you not to have to put in your password all the time every time you push or pull.  

## Part 1: Introduction
### Linus Torvalds, the git hero 🦸‍♂️
The mind behind linux (listen until ~9:20): https://youtu.be/o8NPllzkFhE?t=433
Linus Torvalds created git because he was frustrated with existing version control softwares (like cvs https://www.nongnu.org/cvs/). Now, thousands of people use it. **Today you are going to become one of those people! 🎉**

### What is git? "Git for humans" by Alice Bartlett
Alice Bartlett (https://github.com/alicebartlett) from the Financial times has made a great set of introductory slides to explain **5 key things** about git: 
https://speakerdeck.com/alicebartlett/git-for-humans

## Part 2: Hands-on
*The following is inspired from the excellent tutorial https://happygitwithr.com/ Thanks to them!*

### Exercise 1: Once upon a commit... 📖

Let's start by creating a new repo (i.e. a directory that is tracked by git) in your home directory.
```bash
cd ~ 			# Go to your home directory
mkdir gitWorkshop 	# Creates a new directory called gitWorkshop in your home directory
cd gitWorkshop 		# Moves to inside the new directory
```
To make git work you need to initialize it. It's simple: 
```bash
git init		# This initialize git in your directory
```
Let's create a file that is important to us. We want to track all the changes to this file. 
```bash
touch script_1.R	# Creates the file
nano script_1.R		# This opens the nano Text editor. 
```
You could of course have edited this in a separate. You can then close the editor with `ctrl+X` type `y` for yes and press `enter`. We can now start to use git to track the changes we made to this file. 
Let me introduce you to your first git tool, the `status` command.
```bash
ls			# This lists the files in the directory. You should see your file listed!
git status		# Shows the current status of your repo with regards to git
```
Here `status` shows you multiple things: the branch you are on (the master branch, more on that later). It lists the latest commit (none yet) and the changes you've made since the last commit. Here the `script_1.R` is shown as untracked. Let's change that. To do so, here is a second command: `add`.
```bash
git add -A		# This adds ALL (hence the -A) the changes you made to the git index. Your changes are now registered 
git status 		# Status now shows, in green, which changes have to be committed
```
It's now time to commit! Note that you could do more changes, you could then choose or not to `add` them to the index, before committing, or you could add them after committing. This would later be part of a different commit. To commit your changes, simply use the `commit` command, along with a (useful) message 
```bash
git commit -m "First commit - adding script1"	# the -m flag adds a message to a commit
git log						# Git log shows you the history
```
Git will print a message summarising the changes you've made. Well done! You now master the very basics of git. Easy peasy lemon squizzy 🍋🍹. The git `log` command shows you the recent commit history. 

### Exercise 2: All roads lead to GitHub 🚦🛣️

After having created a repo on your local machine (and provided that you have configured git on your computer), you will be able to copy your repo to GitHub, an online hub for repositories. We call this "pushing". After pushing, a copy of your repo will live on the github servers and will remain linked to the original copy. The GitHub copy is called a "remote". 
- The first thing to do is to create the remote on github.com 
	- log in at github.com 
	- click on the green folder
	- Give a name to your repo. It's good practice to the use the same name than your local git repo (it's also easier to remember that way!).
	- DO NOT add a `README.md` or `.gitignore`. The repo needs to be empty.
- The next thing is to tell your local git that you have created a new remote. You will name this the "origin" remote. 
```bash
git remote add origin https:...	   # Add here the URL of your git repo, for instance https://github.com/VLucet/gitWorkshoptest
```
- Finally, it is time to push your repo. The first time you push, you have to tell git that the remote is an upstream branch (more on that later).
```bash 
 git push --set-upstream origin master	# This pushes and sets the remote as "upstream"
 git push origin master			# If you try to push again, it will tell you that everything is up to date!
```
There you go! you now have a copy of your repo on GitHub. Well done!
**NOTE:** it is also possible to start the repo on GitHub and download a clone (see next exercise)

### Exercise 3: The client is king: GitHub Desktop 👑

What if you don't want to type in commands all the time? You can use a GitHub client. It's a program that will provide an more user-friendly interface with git and GitHub. 
***\[Demonstrastion of GitHub Desktop\]***
- Open GitHub Desktop. 
- You have the choice between adding a local repository or cloning one (downloading from GitHub). We will add the local repo we created 
- Go to File => Add local repository => navigate to the path. Your repo is now added! 
- You can open your text file again and change it. You can use the interface to ignore, remove or add changes and for commiting. Even better, pushing (and pulling) is only one click away!

### Exercise 4: Team Work makes the Dream Work 👩‍💻 👨‍💻

Form teams of 3. The youngest of the team will be the repo owner for this exercise. 
- Repo Owner, head over to github to create a new online repository. 
	- This time, make sure to initiate this repository with a ReadMe file.
- In this read me file, type in the name of the best movie of all time. You heard me, write it down and commit it to your repo.
- Next step is for you to make a team. Navigate to your repo settings and add the member of your team (see demo)
- You can now all clone the repo. You can use GitHub desktop or the command line. Using the command line: 
```bash
cd ~ 			# Navigate to your home folder again 
git clone *URL* 	# The URL of the repo created by the repo owner
```
Well done, you have no set up a team and you are now technically working on the same repo.

### Exercise 5: (Do The) Push and Pull ⬆️➡️🔄➡️⬇️

You are now ready to experience the true git experience: pushing and pulling. 
To do so, we are going to use the repo you cloned at the previous exercise. The first step is to make sure you are up to date with the version of  the repo that is on GitHub. To do so, we use the `fetch` command. 
```bash 
git fetch  # Fetch compares your local version with the remote version but does not apply the new changes (if there are any)
```
The next step is for one of the team members (other than the repo owner) to make a change. Make a change to the Readme file for instance (maybe you think the best movie of all time is *not* Sharknados 3. You'd be wrong, but still, you're welcome to change that...)
``` 
nano README.md	# Reminder: nano is the console editor
```
Then, add, commit and push those changes
```bash
git add -A 				# Once again, add all the changes
git commit -m "modified the README"	# Always add a useful message (unless it's 2:32am and then you can just say "gazoub."
git push origin master			# Push it!
```
Now, two of the team member are not in sync with the changes. You can see it with a `fetch`
```bash
git fetch	# This will download the changes pushed by your team member
git status	# Always good to run status once in a while. Here it will tell you that you are 1 commit behind! 
```
To remedy to this, it is as simple as "pulling" the changes in your local repo. 
```bash
git pull origin master	# Nice! Git will print a nice summary with green + and red -. How cute. 
```
Well done! You now know how to `push` and `pull`, `fetch` and `status` your way around a shared repo. You're the best.

### Exercise 6: Git of war 💣💥🤯

Now, let's do it again but a little differently. The one person in the group to not have edited the README should do it now on their machine. Please add and commit BUT DO NOT PUSH.
```bash
git add -A 				# Once again, add all the changes
git commit -m "modified the README"	# Do not push!
```
Now, repo owner will go on github and change the file. There are many types of files that can be edited directly on GitHub, and the README file is one of them. For this exercise, please change the same line than the previous person. Commit the change to the repo.
Now, the person to have just changed the file on their machine will do the pulling procedure:
```bash
git fetch 	# This fetches the changes
git status 	# WOW! Status says that the commits are different... this might cause a problem
git pull 	# There is now a "conflict" and you need to resolve it
```
Are you proud of yourself? You've created a conflict 😱. A conflict typically happens when you have commited a local change and are pulling a commit from remote that was made on that same line of code you just changed. See it illustrated below: 

![Git conflict illustrated](https://blog.developer.atlassian.com/wp-content/uploads/dac-import/merge-conflict.png)

Git doesn't know which changes to keep and which one to throw away. We need to make a choice: we call that doing a "commit merge", as illistrated below: 

![Commit merge](https://blog.developer.atlassian.com/wp-content/uploads/dac-import/merge-result.png)

You have 2 options: you can use the nano editor: or you can use a combination of GitHub Desktop/External editor. The Atom editor is especially useful. If using `nano`:
```bash
nano *file*	# Opens file in nano 
```
When you open the conflicted file you will see code that is enclosed within `<<<<<<< HEAD` and `=======`. This corresponds to your local version of this line of code. Then between `=======` and `>>>>>>> 3f74688ab...` is the version corresponding to the commit (with the hash `3f74688ab...`) that you pulled from remote. You need to edit the file so that these various things, `<<<<<<< HEAD` and `=======` and `>>>>>>> 3f74688ab...` are no longer there. You can choose to keep either of the changes or both. 
Once you have made your changes, it is time to commit your change, and merge it with the remote repo. 
```bash
git add -A 				# Once again, add all the changes
git commit -m "fixed the conflict"	# You fixed the conflict, better put a messgae indicating it!
git push origin master			# Push it!
git status				# All is good!
```
Well done! You've learned how to deal with conflicts! 💪

### Exercise 7: The tree of git 🌳

A great way to make conflicst much more manageable is to use the magic of branching. Branches are like alternate timelines that allow you to work on a snapshot of the repo at a given time. You start by "branching out of the master branch": this copies the current version of the repo and allows you to make changes on a separate "branch". 
One of the team members should do the following. The first thing is to create the branch:
```bash
git branch mynewbranch		# This simply creates the new branch
```
The branch is created, but you are still on the master branch. To be able to switch to the new branch, we need to "checkout' the branch:
```bash 
git checkout mynewbranch	# This makes you switch to the new branch
git status 			# You are now on the new branch
``` 
***note***: *there is a shortchut to do those 2 commands in one line: `git checkout -b mynewbranch`*
You are now on the new branch! This branch is only on your local machine for now. Let's add some changes and then commit and push so that you branch is saved on the remote!
```bash
# Do some changes in your repo! They will only be part of the commit hostory of your branch
git commit -a -m 'added some changes to the new branch'  # Another shorcut to add and commit at the same time!
git push origin mynewbranch 				 # Pushing to the new branch - you can also just type in "git push"
```
Awesome! Now, while one of the team member is adding commits to their new branch, someone else should keep adding changes to the master branch. Once this is done, it is time to merge the new branch with the master branch. 
To do so, there are two ways to do it. I will show you how to do it by the command line and then on github desktop. Merging means doing a "pull request": you are pulling the new branch into the master branch. You therefore need to checkout the master branch and then *pull* the new branch into the master.
```bash
git checkout master	# You've switched to the master branch
git merge mynewbranch	# this merges (opens a pull request and checks it against the master)
git push 		# this pushes the merging of the two branches 
```
Additionnaly, you can do all this by creating a pull request on github \[DEMO]. 

### Exercise 8: What R your new skills? ✨

Now I will show you how to integrate R and Rstudio \[DEMO].

# Git and github with R Workshop - November 2019 👩‍💻 👨‍💻

This workshop makes use of different sources of online learning materials. 

## Part 1: Introduction

### Linus Torvalds, the git hero 🦸‍♂️
The mind behind linux (listen until ~9:20): https://youtu.be/o8NPllzkFhE?t=433
Linus Torvalds created git because he was frustrated with existing version control softwares (like cvs https://www.nongnu.org/cvs/). Now, thousands of people use it. **Today you are going to become one of those people! 🎉**

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

### What is git? "Git for humans" by Alice Bartlett
Alice Bartlett (https://github.com/alicebartlett) from the Financial times has made a great set of introductory slides to explain **5 key things** about git: 
https://speakerdeck.com/alicebartlett/git-for-humans

## Part 2: Hands-on

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
touch topsecretfile.txt	# Creates the file
nano topsecretfile.txt	# This opens the nano Text editor. 
```
Type in your **top secret 🙊** message. You can then close the editor with `ctrl+X` type `y` for yes and press `enter`. We can now start to use git to track the changes we made to this file. 
Let me introduce you to your fisrt git tool, the `status` command.
```bash
ls			# This lists the files in the directory. You should see your file listed!
git status		# Shows the current status of your repo with regards to git
```
Git status shows you multiple thing: the branch you are on (the master branch). It lists the latest commit (none yet) and more importantly, the changes you've made since the last commit. Here the `topsecretfile.txt` is shown as untracked. Let's remedy to that. To do so, here is a second command: `add`.
```bash
git add -A		# This adds ALL (hence the -A) the changes you made to the git index. Your changes are now registered 
git status 		# Status now shows, in green, which changes have to be committed
```
It's now time to commit! Note that you could do more changes, you could then choose or not to `add` them to the index, before committing, or you could add them after committing. This would later be part of a different commit. To commit your changes, simply use the `commit` command, along with a (useful) message 
```bash
git commit -m "First commit"	# the -m flag adds a message to a commit
```
Git will print a message summarising the changes you've made. Well done! You now master the very basics of git. Easy peasy lemon squizzy 🍋🍹

**On your own**: make another change to your file, then add and commit. Then use `git log` to print the commit history!

### Exercise 2: All roads lead to GitHub 🚦🛣️

This is nice and all, but git becomes even more useful when you pair it with GitHub. After having created a repo on your local machine (and provided that you have configured git on your computer), you will be able to "send" your repo to GitHub, an online hub for remote repositories. We call this "pushing". After pushing, a copy of your repo will live on the github servers and will remain linked to the original copy. The GitHub copy is called a "remote". 
- The fisrt thing to do is to create the remote on github.com (log in, click on the green folder thingy, gite it a name). You should give it the same name than your local git repo (it's easier to remember that way!).
- The next thing is to tell your local git that you have created a new remote. You will name this the "origin" remote. 
```bash
git remote add origin *URL* 	# Add here the URL of your git repo, for instance https://github.com/VLucet/gitWorkshoptest
```
- Finally, it is time to push your repo. The first time you push, you have to tell git that the remote is an upstream branch (more on that later).
```bash 
 git push --set-upstream origin master	# This pushes and sets the remote as "upstream"
 git push origin master			# If you try to push again, it will tell you that everything is up to date!
```
There you go! you now have a copy of your repo on GitHub. Well done!

### Exercise 3: The client is king: GitHub Desktop 👑

What if you don't want to type in commands all the time? You can use a GitHub client. It's a program that will provide an more user-friendly interface with git and GitHub. 
***\[Demonstrastion of GitHub Desktop\]***
- Open GitHub Desktop. 
- You have the choice between adding a local repository or cloning one (downloading from GitHub). We will add the local repo we created 
- Go to File => Add local repository => navigate to the path. Your repo is now added! 
- You can open your text file again and change it. You can use the interface to ignore, remove or add changes and fpr commiting. Even better, pushing (and pulling) is only one click away!

### Exercise 4: Team Work makes the Dream Work 👩‍💻 👨‍💻

Form teams of 3. The youngest of the team will be the repo owner for this exercise. 
- Repo Owner, head over to github to create a new online repository. Make sure to initiate this repository with a ReadMe file.
- In this read me file, type in the name of the best movie of all time. You heard me, write it down and commit it to your repo.
- Next step is for you to make a team. Navigate to your repo settings and add the member of your team (see demo)
- You can now all clone the repo. You can use GitHub desktop or the command line. Using the command line: 
```bash
cd ~ 			# Navigae to your home folder again 
git clone *URL* 	# The URL of the repo created by the repo owner
```
Well done, you have no set up a team and you are now technically working on the same repo.

### Exercise 5: (Do The) Push and Pull ⬆️➡️🔄➡️⬇️
🎶 https://www.youtube.com/watch?v=jngwoLvW8UY 🎶

You are now ready to experience the true git experience: pushing and pulling. 
To do so, we are going to use the repo you cloned at the previous exercise. The first step is to make sure you are up to date with the version of  the repo that is on GitHub. To do so, we use the `fetch` command. 
```bash 
git fetch  # Fetch compares your local version with the remote version but does not apply the new changes (if there are any)
```
The next step is for one of the team member (othr than the repo owner) to make a change. Make a change to teh Readme file for instance (maybe you think the best movie of all time is *not* Sharknados 3. You'd be wrong, but still, you're welcome to change that...
``` 
nano README.md	# Reminder: nano is the console editor
```
Then, add, commit and push thsoe changes
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

Now, let's do it a little differently. The one person in the group to not have edited the README should do it now on their machine. Please add and commit BUT DO NOT PUSH
Now, repo owner will go on github and change the file (teach how to edit in github)
Now last to edit:
```bash
git fetch
git status #different
git pull # conflict
```
Are you proud of yourself? You've created a conflict. A conflict typically happens when 1) you've made a local change and are pulling has already been made and therefore, git doesn't
```bash
nano file 
```

### Exercise 7: The tree of git 🌳

A great way to avoid conflics is to use the magic of branching. Branches are like alternate timelines. TBC...

### Exercise 8: What R your new skills? ✨

Rstudio.

# Setting Up Git

If you haven't installed Git, do so first. This guide is best supplimented with https://github.com/git-guides. 

## Git Config 

First we will set up our global git enviroment. This only need to be done once on a given machine. This section is taken largely from https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup.

Now that you have Git on your system, you’ll want to do a few things to customize your Git environment. You should have to do these things only once on any given computer; they’ll stick around between upgrades. 

### Your Identity

The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information, and it’s immutably baked into the commits you start creating:

```
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

Again, you need to do this only once if you pass the --global option, because then Git will always use that information for anything you do on that system. If you want to override this with a different name or email address for specific projects, you can run the command without the --global option when you’re in that project.

Many of the GUI tools will help you do this when you first run them.

### Your Default Branch Name

By default Git will create a branch called master when you create a new repository with git init. From Git version 2.28 onwards, you can set a different name for the initial branch.

To set main as the default branch name do:

```
git config --global init.defaultBranch main
```

Main seems to be the standard for most projects so I recommend running the command above.

### Checking Your Settings

To check your setting use the command below to list all the setting git can find at this point.

```
git config --list
```

## New Git Repo

Head to github and make a new repo there. It is more tricky to make a repo locally and push it to git then make it on git and clone it to your local machine.

Repo naming convention should follow kebab-case (dash seperate strings). If this is to be an open source project and people can do whatever they want with the files, use the MIT license. 

### Cloning

Navigate to where you want your local github repo to live. Note that it will by default make a new directory, so you should be in a top level directoy where other github project folders are. Clone with:

```
git clone "https://github.com/YourUsername/your-project"
```

## Contribution Pattern

The pattern to contribute to a repo will differ depending on the repo. If you are the only contributor, there is no harm to pushing to the main branch in most cases. To collaborate with others best practice is to create a new branch, commit to the new branch, then merge the new branch back into main. This is to allow others to commit changes to the repo between when you pull the main and merge back into the main. 

For instance lets say we have versions of the main branch called main1.0 main2.0 main3.0. If you and someone both pull main1.0, but they make their changes before you and commit to main1.0 they will create main2.0. If you then go and try to commit to the main branch, you will also be trying to create main2.0! If you both branch main1.0 instead, forming branches mine1.0 and yours1.0, changes can be commited to these branches. Then branch yours1.0 can be merged into main1.0, creating main2.0. Following this, mine1.0 can be merged into main2.0, creating main3.0. 

A merge will try and take the newest version of each line of code from each branch to produce a new up-to-date branch. For more details check out https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging.

### Single Contributor Repo

You should always pull a repo before making changes to ensure you have an up-to-date version of the files. To pull the current branch is as easy as:

```
git pull
```

As you're working, you change and save a file, or multiple files. Then, before you commit, you must git add. This step allows you to choose what you are going to commit. Commits should be logical, atomic units of change - but not everyone works that way. Maybe you are making changes to files that aren't logical or atomic units of change. git add allows you to systematically shape your commits and your history anyway. The two common add types are to add a file to the staging area, or add all changed files.

Add a file:
``` 
git add filename
```
Add a directory:
```
git add /directoryname
```
Add all changed files:
``` 
git add .
```

Git add will also stage the deletion of files you have deleted. If you are working on a solo project, you can usually just use the ```git add .``` version, although it is considered bad practise if your commit is broad in scope. (eg makes more than one bug fix or feature change). 

After adding it is a good idea to check the status of the staging area. This will give you an idea of what changes you have made, and allow you to throw changes out as required. 

``` 
git status
```

It anything is being modified that should not be, add can be reverse with reset.

```
git reset
```

If the status looks good, it's time to commit! Commits should always use the ```-m``` flag to add a message alongside the commit which describes the changes you have made. 

```
git commit -m "a short description of the changes in this commit"
```

Finally we are ready to push to the main branch. 

```
git push
```

### Multiple Contributor Repo

The main difference when multiple contributors are present if the requirement for branching as described above. The pattern is as follows. 

Pull the main branch before making any changes. 

```
git pull
```

Make a new branch and move to it so that your changes will be commited there. This step can happen before or after making changes and before or after the add step, but MUST TAKE PLACE BEFORE COMMIT. ```checkout``` changes branches and can create a new branch with the ```-b``` flag. 

```
git checkout -b informative-branch-name
```

As you're working, you change and save a file, or multiple files. Then, before you commit, you must git add. This step allows you to choose what you are going to commit. Commits should be logical, atomic units of change - but not everyone works that way. Maybe you are making changes to files that aren't logical or atomic units of change. git add allows you to systematically shape your commits and your history anyway. The two common add types are to add a file to the staging area, or add all changed files.

Add a file:
``` 
git add filename
```
Add a directory:
```
git add /directoryname
```
Add all changed files:
``` 
git add .
```

Git add will also stage the deletion of files you have deleted. If you are working on a collaborate project, you can still use the ```git add .``` version, although it is considered bad practise if your commit is broad in scope. (eg makes more than one bug fix or feature change). You can always make multiple commits on the branch before merging back into main if you have done multiple units of work. This allows for better versioning history and is helpful if you wish to revert part of the work completed or encounter merge conflicts! 

After adding it is a good idea to check the status of the staging area. This will give you an idea of what changes you have made, and allow you to throw changes out or add more changed files as required. 

``` 
git status
```

If the status looks good, it's time to commit! Commits should always use the ```-m``` flag to add a message alongside the commit which describes the changes you have made. 

```
git commit -m "a short description of the changes in this commit"
```

Repeat the add and commit steps until your branch is updated with all the changes you've made. Now if can be merged back into the main branch. Start by moving back to the main branch.

```
git checkout main
```

Now merge your branch into main.

```
git merge informative-branch-name
```

Now you can delete the branch you used to make changes. It will still exist in the version history, but you will no longer be able to commit to it. This is the desired state as it has been merged back into main. 

```
git branch -d informative-branch-name
```

Lastly, push! This is an important step as otherwise all the local work you have done will not match the remote repo. 

```
git push
```


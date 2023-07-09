# Setting Up Git

If you haven't installed Git, do so first. 

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

## Pulling and Pushing

To collaborate or keep files up to date between a server and your local machine, pull and push operations are essential. 

### Pulling

You should always pull a repo before making changes to ensure you have an up-to-date version of the files. To pull the current branch is as easy as:

```
git pull
```

### Pushing

Once you have fully implemented (and tested!) your changes, it is time to push. There are three components to pushing. Adding, commiting, and pushing. The add step adds all the local changes in your working directoy to the git staging area. In most cases you will be adding all changes, which can be done with:

``` 
git add .
```

If you need to add specific files only, there are many options and regex patterns to do so. 

After adding it is a good idea to check the status of the staging area. This will give you an idea of what changes you have made, and allow you to throw changes out as required. 

``` 
git status
```

If the status looks good, it's time to commit! Commits should always use the ```-m``` flag to add a message alongside the commit which describes the changes you have made. 

```
git commit -m "a short description of the changes in this commit"
```

Finally we are ready to push. 

```
git push
```



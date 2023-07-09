# Example Project 
### Flask, Javascript, HTMl, CSS, Git, venv

## Git

If you haven't installed Git, do so first. 

### Git Config 

First we will set up our global git enviroment. This only need to be done once on a given machine. This section is taken largely from https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup.

Now that you have Git on your system, you’ll want to do a few things to customize your Git environment. You should have to do these things only once on any given computer; they’ll stick around between upgrades. 

#### Your Identity

The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information, and it’s immutably baked into the commits you start creating:

```
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

Again, you need to do this only once if you pass the --global option, because then Git will always use that information for anything you do on that system. If you want to override this with a different name or email address for specific projects, you can run the command without the --global option when you’re in that project.

Many of the GUI tools will help you do this when you first run them.

#### Your Default Branch Name

By default Git will create a branch called master when you create a new repository with git init. From Git version 2.28 onwards, you can set a different name for the initial branch.

To set main as the default branch name do:

```
git config --global init.defaultBranch main
```

#### Checking Your Settings

To check your setting use the command below to list all the setting git can find at this point.

```
git config --list
```

### New Git Repo

Start by creating a new directory where the project will live. Standard project naming convention should use CamelCase (strings with upper case first characters). Run the following command to start git at that location.

```
git init .
```

Head to github and make a new repo there. Repo naming convention should follow kebab-case (dash seperate strings) and match the strings used for the project directory. 


# Git

Git is a command line tool that many developers rely on to keep their work safe and collaborate with others. With a few commands in your toolbelt, you should be up and running in no time!

## Git vs. GitHub
Despite the name, git is not the same thing as GitHub. You can think of GitHub like Dropbox. It is a place where you can keep your code and share it with others. Git, on the other hand, is a tool on your computer that lets you upload and download files from a centralized location. It also lets you keep track of various "states" of your work at any given point on your local machine. You can use git and GitHub for any kind of files, not just code, but we will assume that you are using it to work with code throughout this doc.

## Definitions
**commit** = a commit is a record of the state of your code

**push** = uploading code to a central location

**pull** = retrieving code from a central location

**branch** = a copy of the code that is separate from the source of truth of the code

**pull request (PR)** = a request to add code from a branch to the source of truth

**main** = sometimes referred to as the `master` branch, it is the source of truth of your code

## Connecting your code to GitHub

### If you already have code and you want to add it to GitHub...
On GitHub, create a new repository, give it a name, and do not select any of the options to initialized the repository. Next, in your terminal, `cd` into the folder of the project you want to add to GitHub. GitHub will give you the commands to run in that repository and they will look something like: 
```sh
git remote add origin git@github.com:<REPOSITORY_NAME>.git
git branch -M main
git push -u origin main
```
This will set up the branch named `main` as your default branch (or source of truth for your code) and push the contents of the folder you are in to GitHub.

### If you are starting from scratch...
On GitHub, create a new repository, give it a name, and then select one of the options to initialize the repository. At least initialize it with a README. Once it creates the repo, click the green `code` button and copy the link it gives you. In your terminal, `cd` to the directory where you want the project and run the command: 
```sh
git clone <CLONE_LINK>
```
Now, you can start working on your code within the directory it creates!

## Creating a branch
In your terminal, make sure you are on the default branch (most likely `main`) and pull the most recent code with `git pull`. Next, you will run `git checkout -b <BRANCH_NAME>` and it will create the new branch and switch your directory to that branch.

I have trouble remembering that command, so I alias that command to `nb` and then just run `nb <BRANCH_NAME>` when creating a new branch.

## Updating your branch with changes from the default branch
Sometimes your branch will become **outdated** if someone else has pushed to the default branch while you are working on it. This is okay! If you haven't been working in the same files, then you just need to run:
```sh
git fetch origin # updates your local main branch with what is currently on GitHub
git pull origin main # updates your branch with those changes
```

If you were modifying that file, there likely will be something called a **merge conflict**. Don't panic! It will look scary, but all you need to do is delete the lines of code that aren't right. For example: 
```sh
random text
blah blah blah
<<<<<<< HEAD
this is some content to mess with
content to append
=======
totally different content to merge later
>>>>>>> new_branch_to_merge_later
more random text
blah blah blah
```
The content between `<<<<<<< HEAD` and `=======` is what is currently in the `main` branch. The content between `=======` and `>>>>>>> new_branch_to_merge_later` is the code on your hypothetical branch `new_branch_to_merge_later`. Now you simply delete what shouldn't be there and keep what should. Also delete the `<<<<<<< HEAD`, `=======`, and  `>>>>>>> new_branch_to_merge_later` lines. So if, for example, your goal was to replace `content to append` with `totally different content to merge later`. You would update that file to:
```sh
random text
blah blah blah
this is some content to mess with
totally different content to merge later
more random text
blah blah blah
```
and then push your code!

## Pushing your code
To update GitHub with your current code, you only need a few commands:
```sh
git status
```
**git status** shows what files have changed since you last committed your code.
```sh
git diff
```
**git diff** shows exactly what has changed since your last commit.
```sh
git add .
# or
git add /path/to/file
```
Once you are ready to stage your code to be committed, you will run `git add .` if you want all changes to be staged or `git add /path/to/file` if you only want to stage a single file. You can run this multiple times with the files you want to commit.
```sh
git commit -m "<COMMIT_MESSAGE>"
```
Now, you are ready to commit! the `-m` is a flag that adds a message and you add a description of your changes inside the parenthases.
```sh
git push origin <BRANCH_NAME>
```
Finally, you run **git push** when you are ready to send your changes to GitHub. `origin` is what tells git you want to send this to GitHub and the branch name specifies the branch you are pushing.

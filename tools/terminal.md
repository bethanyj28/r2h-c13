# Terminal Basics

Getting comfortable with using a terminal makes certain tasks easier. While it seems daunting at first, using the terminal can become second-nature with some practice and helpful tips.

## Definitions
**Directory** = a folder in your file system.

**root** = The top-level folder in your file system. Typically contains your `Documents`, `Downloads`, etc. folders.

**CLI** = Command Line Interface, a program that you interact with using your terminal.

## The structure of a command
Typically commands are in the same format: `<command> <flags> <argument>`. 

### Command
The **command** is what tells the terminal what it should be doing, or where it should look for instructions of what the command does. Some commands are default to the terminal, like `cd`, `rm`, etc. Some commands reference a Command Line Interface (CLI), like `git`, `npm`, `docker` etc. 


### Flag
The **flag** passes additional information to the code that executes when you run the command. For example, let's look at the `ls` command. `ls` is used to list the contents of your current directory. For example:
```sh
~/road-to-hire-reference (main) : ls
LICENSE     README.md   javascript/ terminal/
```
This is helpful information, but sometimes you want more. So you can append **flags** to acheive that. One helpful flag is `-a`, which prints hidden files (files beginning with a *.*), as well:
```sh
~/road-to-hire-reference (main) : ls -a
./          ../         .git/       LICENSE     README.md   javascript/ terminal/
```
Notice that there is now three additional contents in the directory that weren't there before!

I mentioned that `ls -a` prints all the contents in a directory. The *a* in this case stands for **all**. Many flags have a short form and a long form (or one of the two). This lets you abbreviate the flag. With the short form, you only need a single `-`, but with the long form you need two `--`. For example, the long form of `ls -a` is `ls --all`.

You can also combine flags. For example:
```sh
~/road-to-hire-reference (main) : ls -al
total 16
drwxr-xr-x   7 bjanos  REDVENTURES\Domain Users   224B Nov  4 11:56 ./
drwxr-xr-x@ 77 bjanos  REDVENTURES\Domain Users   2.4K Nov  4 11:55 ../
drwxr-xr-x  12 bjanos  REDVENTURES\Domain Users   384B Nov  4 11:55 .git/
-rw-r--r--   1 bjanos  REDVENTURES\Domain Users   1.0K Nov  4 11:55 LICENSE
-rw-r--r--   1 bjanos  REDVENTURES\Domain Users    24B Nov  4 11:55 README.md
drwxr-xr-x   4 bjanos  REDVENTURES\Domain Users   128B Nov  2 16:41 javascript/
drwxr-xr-x   2 bjanos  REDVENTURES\Domain Users    64B Nov  2 15:06 terminal/
```
Here I used `ls -al`. The command runs `ls -a`, since it is showing the hidden files. The command also runs `ls -l`, which formats the output differently. So rather than typing those separately, you can combine them!

Most flags are available in documentation and aren't something you're expected to memorize.

### Argument
The **argument** is something you type to provide input into the command. Sometimes this can be in the format of `<command> <flag> <argument> <flag> <argument>`, and sometimes it's `<command> <flags> <argument>`. This is something you'd have to look at documentation to know which to use.

Using our `ls` example above, it was using the default argument, which referenced the current directory. The same thing will print if I give it the argument `.` (referencing the current directory):
```sh
~/road-to-hire-reference (main) : ls -al .
total 16
drwxr-xr-x   7 bjanos  REDVENTURES\Domain Users   224B Nov  4 11:56 ./
drwxr-xr-x@ 77 bjanos  REDVENTURES\Domain Users   2.4K Nov  4 11:55 ../
drwxr-xr-x  12 bjanos  REDVENTURES\Domain Users   384B Nov  4 11:55 .git/
-rw-r--r--   1 bjanos  REDVENTURES\Domain Users   1.0K Nov  4 11:55 LICENSE
-rw-r--r--   1 bjanos  REDVENTURES\Domain Users    24B Nov  4 11:55 README.md
drwxr-xr-x   4 bjanos  REDVENTURES\Domain Users   128B Nov  2 16:41 javascript/
drwxr-xr-x   2 bjanos  REDVENTURES\Domain Users    64B Nov  2 15:06 terminal/
```

I can also provide another directory to list the contents of as an argument:
```sh
~/road-to-hire-reference (main) : ls -al javascript/
total 16
drwxr-xr-x  4 bjanos  REDVENTURES\Domain Users   128B Nov  2 16:41 ./
drwxr-xr-x  7 bjanos  REDVENTURES\Domain Users   224B Nov  4 11:56 ../
-rw-r--r--  1 bjanos  REDVENTURES\Domain Users   2.9K Nov  2 15:37 declaring_variables.md
-rw-r--r--  1 bjanos  REDVENTURES\Domain Users   2.6K Nov  2 16:41 numbers.md
```

Most commands will define what you can input as arguments, but make sure you understand what you're doing before running any commands! They can sometimes have unintended consequences.

Here you can find a downloadable cheat sheet with basic commands. A lot of these aren't super relevant, so don't feel overwhelmed if you don't understand all the commands. You'll mostly want to reference the **File Commands** and the **Shortcuts** sections: https://cheatography.com/nexwebsites/cheat-sheets/basic-linux-commands/

## Making it easier: your .bash\_profile

You might be wondering how you're going to memorize all these commands. A lot of it comes from practice, but a lot of it also comes from mapping commands to names that are easy to remember. Enter your `.bash_profile`!

Your `.bash_profile` is literally just a file you make. If you do not see this file in your root directory, run this command in your root directory: `touch .bash_profile`. Type `cd` to get to your root directory.

Now, you can create what's called an *alias*. These are super helpful because you can create whatever names for a command that you want. For example:
```sh
  alias gs='git status'
  alias gco='git checkout'
  alias nb='git checkout -b'
  alias yeet='git stash'
  alias ls='ls -a'
```

In this example, I aliased some git commands to different mappings. So I only have to type `gs` to run `git status` and `yeet` to run `git stash`. You might notice that I overwrote the `ls` command to instead run `ls -a` whenever I run `ls`.

Whenever you update your `.bash_profile`, you either need to restart your terminal or type `source ~/.bash_profile` to see the changes.

## The danger zone: using sudo

Occassionally you'll want to run commands that require priviledged access. This is your terminal trying to prevent you from making any big mistakes. In these situations, you type `sudo` before the command. *sudo* is short for *super user do* and you might hear people pronouncing it *sue-dough* or *sue-doo*. Make sure you know what you're running before using this, though, otherwise it could be bad!

## What do all these symbols mean?

You can navigate directories with respect to the current directory using variations of `.` or `..`. A single period references the **current directory**. So when we ran `ls -al .` that meant "list all the contents of the current directory". Double periods means the **parent directory**. For example, typing `cd ..` would take you back a directory, `ls ..` would list the contents of the parent directory, etc. You can also chain these to go back multiple directories. So `cd ../../..` would take you back **3** directories.

Another helpful positional component is `~`. This will reference your *root* directory. For example, typing `cat ~/.bash_profile` will print out the contents of your `.bash_profile` in your root directory.

Two other symbols that you might see are `|` and `>`. You probably won't be using these starting out, but they're helpful to know. `|` is known as a pipe, it directs the output of one command to another so you can chain commands, like `ls | sort` would sort your directory list. `>` is a redirect. It redirects the output of one command to a file. `>` will rewrite the file every time if it exists, where `>>` will append to the file.

## Practice
Choose the right commands to do the following actions (there might be multiple that are correct):

1. Create a directory off of your root directory called *my_temp_directory*.
2. Enter into that directory.
3. Using terminal commands, create a file in that directory called *my_test_file.txt*.
4. **Bonus!** Using terminal commands (not VScode or Vim!), append "Hello, world" to the file.
5. Print the contents of the file to the terminal.
6. Delete the file
7. Go back one directory
8. Delete the folder

**Options**
1. `rm -rf my_temp_directory`
2. `rm my_test_file.txt`
3. `cd my_temp_directory`
4. `echo "Hello, world" > my_test_file.txt`
5. `cat "Hello, world" > my_test_file.txt`
6. `cat my_test_file.txt`
8. `mkdir my_temp_directory`
9. `cd`
10. `cd ..`
11. `rm my_temp_directory`
12. `touch my_test_file.txt`
13. `mkdir hello_world`

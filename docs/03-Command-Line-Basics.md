# Command Line Basics

## Hello Terminal!

Once you have opened up Terminal or Git Bash then you should see a window that 
looks something like this:

![](img/shell1.png)

What you're looking at is the bash shell! Your shell will surely look different 
than mine, but all bash shells have the same essential parts. As you can see in
my shell it says `seans-air:~ sean$`. This string of characters is called the
**prompt**. You type command line commands after the prompt. The prompt is just
there to let you know that the shell is ready for you to type in a command.
Press `Enter` on your keyboard a few times to see what happens with the prompt.
Your shell should now look like this:

![](img/shell2.png)

If you don't type anything after the prompt and you press enter then nothing
happens and you get a new prompt under the old prompt. The white rectangle 
after the prompt is just a cursor that allows you to edit what you've typed
into the shell. Your cursor might look like a rectangle, a line, or an
underscore, but all cursors behave the same way. After typing something into
the command line you can move the cursor back and forth with the left and right
arrow keys.

Don't you think your shell looks messy with all of those old prompts? Don't
worry, you're about to learn your first shell command which will clean your
shell up! Type `clean` at the prompt and then hit enter. Voila! Your shell
is back to how you started.

Every command line command is actually a little computer program, even commands
as simple as `clean`. These commands all tend to have the following structure:

```
[command] [options] [arguments]
```

Some simple commands like `clean` don't require any options or arguments.
Options are usually preceded by a hyphen (`-`) and they tweak the behavior
of the command. Arguments can be names of files, raw data, or other options
that the command requires. A simple command that has an argument is `echo`.
The `echo` command prints a phrase to the console. Enter `echo "Hello World!"`
into the command line to see what happens:


```bash
echo "Hello World!"
```

```
## Hello World!
```

We'll be using the above syntax for the rest of the book, where on one line there
will be a command that I've entered into the command line, and then below that
command the console output of the command will appear (if there is any
console output). You can use `echo` to print any phase surrounded by double
quotes (`""`) to the console.

### Exercises

1. Print your name to the terminal.
2. Clean up your terminal after completing #1.

## Navigating the Command Line

You've learned two command line commands (`clear` and `echo`) which is pretty
good! Before you learn more commands we need to discuss how files and folders 
are organized on your computer.

Computers are organized in a hierarchy of folders, where a folder can contain 
many folders and files. People who use Unix often refer to folders as 
directories and these terms are interchangeable. This directory hierarchy forms 
a tree, like the diagram below. You can use the command line to navigate these
trees on your computer.

![](img/musictree1.png)

As you can see in the image below, my Debussy directory is contained in my Music 
directory. This is the simplest case of how directories are structured.

![](img/musictree2.png)

The directory structure on most computers is much more complicated, but the 
structure on your computer probably looks something like this:

![](img/bigtree1.png)

There are a few special directories that you should be aware of on your 
computer. The directory at the top of this tree is called the root directory. 
The root directory contains all other directories, and is represented by a 
slash (`/`).

The home directory is another special directory that is represented by a tilde 
(`~`). Your home directory contains your personal files, like your photos, 
documents, and the contents of your desktop. When you first open up your shell
you usually start off in your home directory. Imagine tracing all of the 
directories from your root directory to the directory you're currently in. This
squence of directories is called a **path**. The diagram below illustrates the
path from a hypothetical root directory to the home directory.

![](img/redtree.png)

This path can be written as `/Users/sean`.

Open the command line if you closed it (either **Terminal** or **Git Bash**).
Your shell starts in your home directory. Whatever directory your shell is in
is called the **working directory**. Enter the `pwd` command into your shell
to **p**rint the **w**orking **d**irectory.


```bash
pwd
```

```
## /Users/sean
```

You can change your working directory using the `cd` command. If you use the
`cd` command without any arguments then your working directory is changed
to your home directory.

Enter `cd` into the command line and then enter `pwd`.


```bash
cd
pwd
```

```
## /Users/sean
```

You were in your working directory to start, and by entering `cd` into the
command line you did technically **c**hange **d**irectory, you just changed it
to your home directory (the directory you were in to begin with). To use `cd` to
change your working directory to a directory other than your home directory, you
need to provide `cd` with the path to another directory as an argument. You can
specify a path as either a path that is **relative** to your current directory,
or you can specify the **absolute** path to a directory starting from the root
of your computer. Let's say we simply want to change the working directory to
one of the folders that is inside our home directory. First we need to be able to
see which folders are in our working directory. You can list the files and
folders in a directory using the `ls` command. Let's use the `ls` command in our
home directory to list the files and folders contained within it.


```bash
ls
```

```
## Desktop
## Documents
## Photos
## Music
## todo.txt
```

It looks like I have four folders and one text file in my home directory. Now
let's switch into the Music directory:


```bash
cd Music
```

As you can see the path to the current working directory has changed:


```bash
pwd
```

```
## /Users/sean/Music
```

I specified a **relative** path when I entered `cd Music`. The path to the 
Music directory is just `Music/` relative to my previous working directory.
I can go back to `/Users/sean/` with the command `cd ..` which changes the
working directory to the folder above the current working directory:


```bash
cd ..
pwd
```

```
## /Users/sean
```

Notice that `..` is also a relative path, since it specifies the directory above
your current working directory. Similarly `.` is the path to your current
working directory. Therefore since my current working directory is `/Users/sean`
then `cd Music` is the same as `cd ./Music`.

I can `cd` to any folder as long as I know the **absolute** path to that folder.
For example I can `cd` to `/Users/sean/Music` by entering the following into 
the shell:


```bash
cd ~/Music
pwd
```

```
## /Users/sean/Music
```

It doesn't matter what directory I'm in since I'm using a absolue path, I can
jump straight to that directory (Remember that `~` is a shortcut for the path to
your home folder). Of course you shouldn't expect yourself to have every
absolute path on your computer memorized! You can use a terminal feature called
**tab completion** in order to speed up typing paths and other commands. Enter
the following into your shell, and then try pressing the `Tab` key (on some
machines you need to press it twice):


```bash
cd ~/
```

(press `Tab`)

```
## Desktop
## Documents
## Photos
## Music
## todo.txt
```

Pressing tab shows you a list of all files and folders inside of the `~/`
directory. Now I'm going to type `~/D` into my terminal and you can see what
happens when I press tab again:


```bash
cd ~/D
```

(press `Tab`)

```
## Desktop
## Documents
```

Since I added a "D" to the path, only folders with names that start with a "D"
are listed. If I type `cd ~/De` into the console and then press `Tab` then the
command will autocomplete to `cd ~/Desktop/`. If I press tab again, the console
will list all of the files and folders on my desktop.

Make sure to pause and try this yourself in your own terminal! You won't have
the same files or folders that I do, but you should try using `cd` and tab 
completion with directories and files that start with the same letters.

### Exercises

1. Set your working directory to the root directory.
2. Set your working directory to your home directory using three different 
commands.
3. Find a folder on your computer using your file and folder browser, and then
set your working dorectory to that folder using the terminal.
4. List all od the files and folders in the directory you navigated to in #3.

## Creation, Migration, Inspection, and Destruction

Now that you can fluidly use your terminal to bound between directories all
over your computer I'll show you some actions you can perform on folders and
files. One of the first actions you'll probably want to take when opening up a
fresh terminal is to create a new folder or file. You can **m**a**k**e a 
**dir**ectory with the `mkdir` command, followed by the path to the new
directory. First let's look at the contents of my home directory:


```bash
cd
ls
```

```
## Desktop
## Documents
## Photos
## Music
## todo.txt
```

I want to create a new directory to store some code files I'm going to write
later, so I'll use `mkdir` to create a new directory called `Code`:


```bash
mkdir Code
ls
```

```
## Desktop
## Documents
## Photos
## Music
## todo.txt
## Code
```

It worked! Notice that the argument `Code` to `mkdir` is a relative path, 
however I could have specified an absolute path. In general you should
expect Unix tools that take paths as arguments to accept both relative and
absolute paths.

### Exercises

1. Create and remove the same directory using three different path arguments.
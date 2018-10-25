# Shell Lessons

# Getting started

In your browser

* Open a tab and go to the etherpad
* Open a tab and go to Github and login with your account
* Open a tab and go to the website and make sure you have installed the required software for your system. `Red sticky` if you need help. 
* Open a tab and go to [Explain Shell](http://explainshell.com/)
* Open a tab and go to the Shell Share in the link in the Etherpad

## What is the shell?

[Software Carpentry Intro to Shell](https://swcarpentry.github.io/shell-novice/01-intro/index.html)

The shell is a program that gives you a way to access commands that let you do stuff on your computer. 

We are going to learn all of the most common commands and how we can combine them to automate complex tasks.

It is also called the command-line interface because you type commands on a line like this:

> ```$ ls -la ```

In this case we are using BaSh (Born Again Shell), but there are lots of differnet shells. BaSh is very common on UNIX and Linux operating systems.

## The three shells used in this workshop

### Windows

If you are on Windows you are using the BsSh emulator that you installed with Git. This is an emulator because it basically fakes the real BaSh commands to make them work on Windows.

### MacOS

MacOS is built on UNIX so it has a built-in command-line with all of the UNIX commands we need for this workshop.

### Linux

Most versions of Linux come with BaSh by default.

## What is it good for?

The shell provides a lot of commands that you can combine to manage and process your data. You can use these commands to build scripts that you can to automate repetitive tasks.

For example, many researchers use the bash commands to convert their unstructured data into structured data.

# Navigating Files and Folders (Directories)

[Software Carpentry Navigating Files and Folder](https://swcarpentry.github.io/shell-novice/02-filedir/index.html)

Open File Explorer and go to the `home` directory. Snap this window next to the terminal or git-bash window so you can see them side-by-side. 

(Windows people can use Window-key + arrow to snap windows)

```
C:\Users\<your user name here>
```

Let's start with listing files and folders.

```
$ ls
```

What did you see? Does it look the same as what you saw in File Explorer?

`ls` lists files and folders.

## Where am I?

Knowing where you are in the filesystem is harder on the command line, but we have a command to help us with that.

```
pwd
```

`pwd` stands for `pesent working directory` and it will tell you the `path` to where you are in the filesystem. It starts with the root.

In UNIX this is `/` and in Windows this will likely be something like `C:\`.

What did you see? Does it look like the path you see in File Explorer?

## `ls` (list files and folders)

Let's get back to `ls`.

`ls` has lots of options that you can use to sort and format the listing, just like you can do in File Explorer.

Let's see what they are.

```
ls --help
```

What did you see? A description and lots of options? Great.

Let's try one of the options.

```
ls -l
```

What did you see? It looks a little different than the output from 

```
ls
```

Try them both. See the differnce?

`ls -l` shows us more details about the files:

* permissions
* last date modified (or created)
* size

This is called the `long` format, hence `-l`.

Sometimes there are hidden files and folders. These start with a `.`. `ls` won't show hidden things unless you give it that option.

```
ls -a
```

Now you will see all files or folders.

You can also combine options like this:

```
ls -la
```

or like this

```
ls -l -a
```

Try them both. You should see the same output.

This shows all files and outputs the long format.

> REMEMBER: You can combine options for any of the shell commands that have options.

## Moving around

You know how you can double-click on a folder to see inside of it? There is a command for that in shell. 

```
cd --help
```

`cd` stands for `change dirctories`.

There are two ways to `change directories`.

`cd` plus a `path` to where you want to go
```
cd /lets/go/here
```
`cd` plus `..` to go up one level in the filesystem (go into the parent folder)
```
cd ..
```
### Going home
We are currently in the `home directory`. This is a location in the filesystem where your your personal files are stored by default. It is a common operting system convention.

On Windows this will be:
```
C:\Users\<your user name here>
```

There is a shortcut for something called the `home` directory. 

```
cd ~
```

If you ever get lost and need to get back home, use the above command. Try it now and then list the files.

```
cd
ls -la
```

Do you see the same thing you did before?

## Absolute paths and relative paths

Let's talk about paths some more. We can get to directories with a `relative` path or an `absolute` path.

### Absolute paths

Absolute paths always start from the `root` of the filesystem.

```
/c/folderA/folderB/folderC
```

### Relative paths

Relative paths are relative to the current location

```
folderB/folderC
```

You can also go up levels `relative` to the current location.

```
cd ../../..
```

## ASSESSMENT

How do I get to my home directory?

1) cd ~
2) ls ~
3) cd /
4) cd /c/home
5) cd /c/Users/marneedearman

# Working with Files and Directories

[Software Carpentry Working with Files and Directories](https://swcarpentry.github.io/shell-novice/03-create/index.html)

We can create folders and files. Let's setup the directory structure that we will use for the rest of the workshop. It is going to look like this:

```
SDC_10-27-2018
    |
    analyses
    data 
        |
        original_data
        processd_data
```

Let's create the `SDC` folder withe `make directory` command.

```
mkdir SDC_10-27-2018
```

Now we can use `tab complete` to create the rest of the directories.

```
mkdir SDC_10-27-2018/analyses
mkdir SDC_10-27-2018/data
```

```
mkdir SDC_10-27-2018/data/original_data
mkdir SDC_10-27-2018/data/processed_data
```

Let's go into the `SDC` directory. We will spend the rest of the workshop here.

How do we get there?

```
cd SDC_10-27-2018
```

Also use File Explorer to drill into this folder. Do you see the sub-folders?

Let's see what's in here. How do I list the files and folders?

```
ls -la
```

Do you see the analyses and data folder?

What is under data? How do I list it?

> use the relative path

```
ls -la data
```

Do you see the directories? 

TAKE A BREAK and LET"S REVIEW

# Github and git and our source files
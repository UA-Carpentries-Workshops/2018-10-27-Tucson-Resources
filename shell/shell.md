# Shell Lessons

# Getting started

In your browser

* Open a tab and go to the Etherpad
* Open a tab and go to Github and login with your account
* Open a tab and go to the website and make sure you have installed the required software for your system. `Red sticky` if you need help. 
* Open a tab and go to [Explain Shell](http://explainshell.com/)
* Open a tab and go to the Shell Share in the link in the Etherpad
* Open `Terminal` or `git bash` and enter `nano` to make sure you have `nano` installed.
* Open a tab and go to our Github repository. Use the link in the Etherpad.

## What is the shell?

[Software Carpentry Intro to Shell](https://swcarpentry.github.io/shell-novice/01-intro/index.html)

The shell is a program that gives you a way to access commands that let you do stuff on your computer. 

We are going to learn all of the most common commands and how we can combine them to automate complex tasks.

It is also called the command-line interface because you type commands on a line like this:

> ```$ ls -la ```

In this case we are using BaSh (Born Again Shell), but there are lots of different shells. BaSh is very common on UNIX and Linux operating systems.

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

`pwd` stands for `present working directory` and it will tell you the `path` to where you are in the filesystem. It starts with the root.

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

Try them both. See the difference?

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

`cd` stands for `change directories`.

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
We are currently in the `home directory`. This is a location in the filesystem where your your personal files are stored by default. It is a common operating system convention.

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
    thesis
    analyses
    data 
        |
        original_data
        processed_data
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

> use the absolute path and the shortcut to home

```
ls -la ~/SDC_10-27-2018/data
```

Do you see the directories? Were they the same for each path you used?

LET'S REVIEW

> Use `cd` to move around in the SDC folder. See if you can use relative and absolute paths to move around. Check where you are are `pwd`. Do you end up where you expected to be?

When you are done playing around, make sure you are in the SDC folder.

How do you do that?

```
cd ~/SDC_10-27-2018
```

## Creating and Editing Files

Let's create a file called. There are two ways of doing this.

### use `nano`

`nano` is a file editor like Notepad or the Mac equivalent.

Let's use it to create a new file.

```
nano thesis.txt
```

This will open `nano`.

> Let's learn about nano. All of the nano commands are shown at the bottom of the window

Start typing in the nano window. You see text.

If you want to save, hit 

```
Ctl + o
```

If you want to exit, hit

```
Ctl + x
```

Check to see if the file is there.

```
ls -la
```

### use touch

Let's create a new file but without using a file editor.

```
touch thesis2.txt
```

```
ls -la
```

Do you see your two files?

Open thesis2.txt in nano. How do you do that?

```
nano thesis2.txt
```

You should see nano and no text. 

Exit nano. Do you remember how to do that?

```
ls -la
```

# Moving files around

You know how you can click and drag files around in File Explorer? We can move files around using the shell too.

To move files we use the `mv` command. `mv` stands for `move`.

Let's move thesis.txt into the thesis directory.

To do this you use the `mv` command and tell it the `path to` and the `name of` the file you want to move and the path to the new location. You can use the relative or absolute path. Let's use the relative path.

```
mv thesis.txt thesis/
```

What happened? Let's list the files.

```
ls -la
```

You dont see thesis.txt where you created it, but you should see it where you moved it.

```
ls -la thesis/
```

> You can also use mv to rename files

Let's rename thesis.txt to thesis_final.txt

```
mv thesis/thesis.txt thesis/thesis_final.txt
```

```
ls -la thesis/
```

You should see the new file name.

## Copying files

Let's make a copy of thesis_final.txt. To do this you use the `cp` command.  Just like `mv`, you tell it the `path to` and the `name of` the file you want to move and the path to the new location. You can use the relative or absolute path. Let's use the relative path.

```
cp thesis/thesis_final.txt thesis/thesis_copy.txt
```

```
ls -la thesis
```

Do you see your two files?


## Delete files and directories

To delete a file we use the `rm` command. `rm` stands for `remove`.

Let's try to delete thesis2.txt

```
rm thesis2.txt
```

What happened?

```
ls -la
```

You should not see thesis2.txt.

# Github and git and our source files

We are going to be working with a number of data files for the rest of the workshop. We will get those from Github and we will use `git` to pull them down from Github.

Go to this link (it is in the Etherpad)

> https://github.com/UA-Carpentries-Workshops/2018-10-27-Tucson-Resources

Go to the top right corner of the page where it says `Fork`

Click `Fork`

This will make a copy of our `repository` in your account.

We will download a copy of the repository using `git clone`.

> Make sure you are in the SDC directory

```
pwd
```

## git clone

On your Github account's repository page, click the Big Green Button and then click the clipboard button. This will copy the URL of the files to your clipboard.

Go back to the shell and type

```
git clone 
```

and then paste the URL so that it looks like this

```
git clone https://github.com/UA-Carpentries-Workshops/2018-10-27-Tucson-Resources
```

Hit enter

Some things happened. Once it is done, list the files and folder. Do you see a new directory?

It is named the same as the name of the repository you cloned.

List what is inside of that directory. Do you see the `data` folder? This is the source data for our workshop.

Let's prepare it for our workshop.

## copy the cloned data files into the original_data folder

What is the copy command?

Let's try to guess how to copy. We tried to do this with a single file at a time, but we need the content of the data directory copied to the data/original_data directory.

To copy a directory we need to use the `-r` option. This tells the copy command that it needs to be `recursive`, meaning that it needs to dig through the directory.

```
cp -r
```

We also need to tell the copy command what files to copy. To copy the contents of a directory we put in the path to the directory and add a *. This is the syntax that tells the cp command to get the contents but not the directory.

```
cp -r 2018-10-27-Tucson-Resources/data/* data/original_data/
```

What was copied? List the contents of the original_data directory.

```
ls -la data/original_data
```

What is inside the gapminder_by_country directory?

```
ls -la data/original_data/gapminder_by_country
```

That's a lot of files. Let's start working with them.

# Pipes and filters and output



## Gapminder

The gapminder study collected data on GDP and life expectancy over time for a bunch of countries. In the gapminder_by_country you see all of the countries with their GDP data. Let's look at one of them.


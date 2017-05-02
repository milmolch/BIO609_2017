Modified from https://github.com/datacarpentry/shell-genomics/blob/gh-pages/lessons/01_the_filesystem.md


# The Shell

## What is the shell?

The *shell* is a program that presents a command line interface
which allows you to control your computer using commands entered
with a keyboard instead of controlling graphical user interfaces
(GUIs) with a mouse/keyboard combination.

There are many reasons to learn about the shell.

* For most bioinformatics tools, you have to use the shell. There is no
graphical interface. If you want to work in metagenomics or genomics you're
going to need to use the shell.
* The shell gives you *power*. The command line gives you the power to do your work more efficiently and
more quickly.  When you need to do things tens to hundreds of times,
knowing how to use the shell is transformative.
* To use remote computers or cloud computing, you need to use the shell.


![Automation](IMG/gvng.jpg)



## Starting with the shell

We will spend most of our time learning about the basics of the shell
by manipulating some experimental data.

Now we're going to download the data for the tutorial. For this you'll need
internet access, because you're going to get it off the web.  

You need to download some files to follow this lesson:  
1. Open a terminal  
2. Download bashScripting.zip (prepared by Heidi): `https://www.dropbox.com/s/fa2ga0ioc0ua8vt/bashScripting.zip`  
3. Unzip the file doing: `unzip bashScripting.zip`  

Let's check out the example data.

Let's go into the sample data directory
```
cd bashScripting
```

**cd** stands for 'change directory'

Let's see what is in here. Type
```
ls
```

You will see
```
BashScripting_solutions.sh  data_script    script.sh
data                        script_mod.sh
```

**ls** stands for 'list' and it lists the contents of a directory.

There are 5 items listed. What are they? We can use a command line argument with 'ls' to get more information.

```
ls -F
BashScripting_solutions.sh*  data/  data_script/  script_mod.sh*  script.sh*
```

Anything with a `/` after it is a directory.  
Things with a `*` after them are programs.  
If there are no decorations, it's a file.

You can also use the command
```
ls -l
-rwxrwxr-x 1 student student 2092 Apr 19 17:42 BashScripting_solutions.sh
drwxrwxr-x 2 student student 4096 Apr 19 17:38 data
drwxrwxr-x 2 student student 4096 Mai  9 19:11 data_script
-rwxrwxr-x 1 student student 2331 Apr 21 13:08 script_mod.sh
-rwxrwxr-x 1 student student 3112 Apr 19 17:44 script.sh
```

to see whether items in a directory are files or directories. `ls -l` gives a lot more
information too.

Let's go into the data_script directory and see what is in there.
```
cd data_script
ls -F
chr20.fa               ERR000061_500_2.fastq  ERR000064_200_2.fastq
ERR000061_500_1.fastq  ERR000064_200_1.fastq
```

There are 5 items in this directory with no trailing slash, so they are files.


## Arguments

Most programs take additional arguments that control their exact
behavior. For example, `-F` and `-l` are arguments to `ls`.  The `ls`
program, like many programs, takes a lot of arguments. Another useful one is '-a',
which show everything, including hidden files.  How do we
know what the options are to particular commands?

Most commonly used shell programs have a manual. You can access the
manual using the `man` program. Try entering:
```
    man ls
```

This will open the manual page for `ls`. Use the space key to go
forward and b to go backwards. When you are done reading, just hit `q`
to quit.

Programs that are run from the shell can get extremely complicated. To
see an example, open up the manual page for the `find` program.
No one can possibly learn all of
these arguments, of course. So you will probably find yourself
referring back to the manual page frequently.


## The Unix directory file structure (a.k.a. where am I?)

As you've already just seen, you can move around in different directories
or folders at the command line. Why would you want to do this, rather
than just navigating around the normal way.

When you're working with bioinformatics programs, you're working with
your data and it's key to be able to have that data in the right place
and make sure the program has access to the data. Many of the problems
people run in to with command line bioinformatics programs is not having the
data in the place the program expects it to be.


## Moving around the file system

Let's practice moving around a bit.

First we did something like go to the folder of our username. Then we opened
'bashScripting' then 'data_script'

Let's draw out how that went.

Now let's draw some of the other files and folders we could have clicked on.

This is called a hierarchical file system structure, like an upside down tree
with root (/) at the base that looks like this.


![Unix](IMG/Slide_Path2.png)

That (/) at the base is often also called the 'top' level.

When you are working at your computer or log in to a remote computer,
you are on one of the branches of that tree, your home directory (/home/student)

Now let's go do that same navigation at the command line.

Type
```
     cd
```
This puts you in your home directory. This folder here.

Now using `cd` and `ls`, go in to the 'bashScripting' directory and list its contents.

Let's also check to see where we are. Sometimes when we're wandering around
in the file system, it's easy to lose track of where we are and get lost.

If you want to know what directory you're currently in, type
```
     pwd
```

This stands for 'print working directory'. The directory you're currently working in.

What if we want to move back up and out of the 'data_script' directory? Can we just
type `cd bashScripting`? Try it and see what happens.

To go 'back up a level' we need to use `..`

Type
```
     cd ..
```

Now do `ls` and `pwd`. See now that we went back up in to the 'bashScripting'
directory. `..` means go back up a level.


## Examining the contents of other directories

By default, the `ls` commands lists the contents of the working
directory (i.e. the directory you are in). You can always find the
directory you are in using the `pwd` command. However, you can also
give `ls` the names of other directories to view. Navigate to the
home directory if you are not already there.

Type:
```
    cd
```

Then enter the command:
```
    ls bashScripting
```

This will list the contents of the `bashScripting` directory without
you having to navigate there.

The `cd` command works in a similar way. Try entering:
```
    cd
    cd bashScripting/data_script
```
and you will jump directly to `data_script` without having to go through
the intermediate directory.

### Exercise

List the 'ERR000061_500_1.fastq' file from your home directory without changing directories



## Full vs. Relative Paths

The `cd` command takes an argument which is the directory
name. Directories can be specified using either a *relative* path or a
full *path*. The directories on the computer are arranged into a
hierarchy. The full path tells you where a directory is in that
hierarchy. Navigate to the home directory. Now, enter the `pwd`
command and you should see:
```
    /home/student
```
which is the full name of your home directory. This tells you that you
are in a directory called `student`, which sits inside a directory called
`home` which sits inside the very top directory in the hierarchy. The
very top of the hierarchy is a directory called `/` which is usually
referred to as the *root directory*. So, to summarize: `student` is a
directory in `home` which is a directory in `/`.

A relative path is like getting directions
from someone on the street. They tell you to "go right at the Stop sign, and
then turn left on Main Street". That works great if you're standing there
together, but not so well if you're trying to tell someone how to get there
from another country. A full path is like GPS coordinates.
It tells you exactly where something
is no matter where you are right now.

You can usually use either a full path or a relative path
depending on what is most convenient. If we are in the home directory,
it is more convenient to just enter the relative path since it
involves less typing.

Over time, it will become easier for you to keep a mental note of the
structure of the directories that you are using and how to quickly
navigate amongst them.

### Exercise

Now, list the contents of the /bin directory. Do you see anything
familiar in there? 
How can you tell these are programs rather than plain files?


## Saving time with shortcuts, wild cards, and tab completion

### Shortcuts

There are some shortcuts which you should know about. Dealing with the
home directory is very common. So, in the shell the tilde character,
`~`, is a shortcut for your home directory. Navigate to the `data_script`
directory:
```
    cd
    cd bashScripting/data_script
```
Then enter the command:
```
    ls ~
```
This prints the contents of your home directory, without you having to
type the full path. The shortcut `..` always refers to the directory
above your current directory. Thus:
```
    ls ..
```
prints the contents of the `/home/student/bashScripting`. You can chain
these together, so:
```
    ls ../../
```
prints the contents of `/home/student` which is your home
directory. Finally, the special directory `.` always refers to your
current directory. So, `ls`, `ls .`, and `ls ././././.` all do the
same thing, they print the contents of the current directory. This may
seem like a useless shortcut right now, but we'll see when it is
needed in a little while.

To summarize, while you are in the `shell` directory, the commands
`ls ~`, `ls ~/.`, `ls ../../`, and `ls /home/student` all do exactly the
same thing. These shortcuts are not necessary, they are provided for
your convenience.

### Our data set: FASTQ files

We did an experiment and want to look at the sequencing results.
We want to be able to look at these files and do some things with them.

### Shortcut: Tab Completion

Navigate to the home directory. Typing out directory names can waste a
lot of time. When you start typing out the name of a directory, then
hit the tab key, the shell will try to fill in the rest of the
directory name. For example, type `cd` to get back to your home directy, then enter:
```
    cd ba<tab>
```
The shell will fill in the rest of the directory name for
`bashScripting`. Now go to bashScripting/data_script
```
    ls ER<tab><tab>
```
When you hit the first tab, nothing happens. The reason is that there
are multiple directories in the home directory which start with
`ER`. Thus, the shell does not know which one to fill in. When you hit
tab again, the shell will list the possible choices.

Tab completion can also fill in the names of programs. For example,
enter `e<tab><tab>`. You will see the name of every program that
starts with an `e`. One of those is `echo`. If you enter `ec<tab>` you
will see that tab completion works.


### Wild cards

Navigate to the `~/bashScripting/data_script` directory. This
directory contains our FASTQ files.

The `*` character is a shortcut for "everything". Thus, if
you enter `ls *`, you will see all of the contents of a given
directory. Now try this command:
```
    ls *fastq
```
This lists every file that ends with a `fastq`. This command:
```
    ls /usr/bin/*.sh
```
Lists every file in `/usr/bin` that ends in the characters `.sh`.
```
    ls *_1.fastq
```
lists only the file(s) ending with '_1.fastq'

So how does this actually work? Well...when the shell (bash) sees a
word that contains the `*` character, it automatically looks for filenames
that match the given pattern. 

We can use the command 'echo' to see wildcards are they are intepreted by the shell.
```
   echo *.fastq
   ERR000061_500_1.fastq ERR000061_500_2.fastq ERR000064_200_1.fastq ERR000064_200_2.fastq
```
The '*' is expanded to include any file that ends with '.fastq'


### Exercise

Do each of the following using a single `ls` command without
navigating to a different directory.

1.  List all of the files in `/bin` that start with the letter 'c
2.  List all of the files in `/bin` that contain the letter 'a'
3.  List all of the files in `/bin` that end with the letter 'o'

BONUS: List all of the files in '/bin' that contain the letter 'a' or 'c'



## Command History

You can easily access previous commands.  Hit the up arrow.
Hit it again.  You can step backwards through your command history.
The down arrow takes your forwards in the command history.

^-C will cancel the command you are writing, and give you a fresh prompt.

^-R will do a reverse-search through your command history.  This
is very useful.

You can also review your recent commands with the `history` command.  Just enter:
```
    history
```
to see a numbered list of recent commands, including this just issues
`history` command.  You can reuse one of these commands directly by
referring to the number of that command.

If your history looked like this:
```
    259  ls *
    260  ls /usr/bin/*.sh
    261  ls *_1*fastq
```
then you could repeat command #260 by simply entering:
```
    !260
```
(that's an exclamation mark).  You will be glad you learned this when you try to re-run very complicated commands.

### Exercise

1. Find the line number in your history for the last exercise (listing
files in /bin) and reissue that command.



## Examining Files

We now know how to switch directories, run programs, and look at the
contents of directories, but how do we look at the contents of files?

The easiest way to examine a file is to just print out all of the
contents using the program `cat`. Enter the following command:
```
    cat ERR000064_200_1.fastq
```
This prints out the all the contents of the the `ERR000064_200_1.fastq` to the screen.


### Exercises

1.  Print out the contents of the `~/bashScripting/data_script/chr20.fa`
    file. What does this file contain?

2.  From your home directory, without changing directories,
    use one short command to print the contents of all of the files in
    the `/home/student/bashScripting/data_script` directory.


```
    cd ~/bashScripting/data_script
```

`cat` is a terrific program, but when the file is really big, it can
be annoying to use. The program, `less`, is useful for this
case. Enter the following command:
```
    less ERR000064_200_1.fastq
```
`less` opens the file, and lets you navigate through it. The commands
are identical to the `man` program.

**Some commands in `less`**

| key     | action |
| ------- | ---------- |
| "space" | to go forward |
|  "b"    | to go backwarsd |
|  "g"    | to go to the beginning |
|  "G"    | to go to the end |
|  "q"    | to quit |

`less` also gives you a way of searching through files. Just hit the
"/" key to begin a search. Enter the name of the word you would like
to search for and hit enter. It will jump to the next location where
that word is found. Try searching the `dictionary.txt` file for the
word "cat". If you hit "/" then "enter", `less` will just repeat
the previous search. `less` searches from the current location and
works its way forward. If you are at the end of the file and search
for the word "cat", `less` will not find it. You need to go to the
beginning of the file and search.

For instance, let's search for the sequence `GATAAAATATTTGCAAAGTATCTATC` in our file.
You can see that we go right to that sequence and can see
what it looks like.

Remember, the `man` program actually uses `less` internally and
therefore uses the same commands, so you can search documentation
using "/" as well!

There's another way that we can look at files, and in this case, just
look at part of them. This can be particularly useful if we just want
to see the beginning or end of the file, or see how it's formatted.

The commands are `head` and `tail` and they just let you look at
the beginning and end of a file respectively.
```
head 
tail ERR000064_200_1.fastq
```
The `-n` option to either of these commands can be used to print the
first or last `n` lines of a file. To print the first/last line of the
file use:
```
head -n 1 ERR000064_200_1.fastq
tail -n 1 ERR000064_200_1.fastq
```
there is also a short form
```
head -1 ERR000064_200_1.fastq
tail -1 ERR000064_200_1.fastq
```


## Creating, moving, copying, and removing

Now we can move around in the file structure, look at files, search files,
redirect. But what if we want to do normal things like copy files or move
them around or get rid of them. Sure we could do most of these things
without the command line, but it's often
faster to do it at the command line, or you'll be on a remote server
where you won't have another option.


Our raw data in this case is fastq files.  We don't want to change the original files,
so let's make a copy to work with.

Lets copy the file using the `cp` command. The `cp`
command backs up the file. Navigate to the `data` directory and enter:
```
    cp ERR000064_200_1.fastq ERR000064_200_1-copy.fastq
    ls -F
```
Now ERR000064_200_1-copy.fastq has been created as a copy of ERR000064_200_1.fastq

Let's make a `backup` directory where we can put this file.

The `mkdir` command is used to make a directory. Just enter `mkdir`
followed by a space, then the directory name.
```
    mkdir backup
```
We can now move our backed up file in to this directory. We can
move files around using the command `mv`. Enter this command:
```
    mv *-copy.fastq backup
    ls -al backup
    total 121576
    drwxr-xr-x  3 swyder  staff       102  9 Mai 14:54 .
    drwxr-xr-x  8 swyder  staff       272  9 Mai 14:53 ..
    -rw-r--r--  1 swyder  staff  62243181  9 Mai 14:54 ERR000064_200_1-copy.fastq    
```
The `mv` command is also how you rename files. Since this file is so
important, let's rename it:
```
    cd backup
    mv ERR000064_200_1-copy.fastq ERR000064_200_1-copy.fastq_DO_NOT_TOUCH!
    ls 
    ERR000064_200_1-copy.fastq_DO_NOT_TOUCH!
```
    Finally, we decided this was silly and want to start over.
```
    rm backup/ERR*
```
The `rm` file permanently removes the file. Be careful with this command. It doesn't
just nicely put the files in the Trash. They're really gone.



### Exercise

Do the following:

1.  Create a backup of your fastq files
2.  Create a backup directory 
3.  Copr your backup files there


By default, `rm`, will NOT delete directories. You can tell `rm` to
delete a directory using the `-r` option. Let's delete that `new` directory
we just made. Enter the following command:

    rm -r backup

**Be careful with removing files/directories, removed files can not be recovered - there is no trash bin**


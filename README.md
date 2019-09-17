
<!-- MDTOC maxdepth:6 firsth1:1 numbering:1 flatten:0 bullets:1 updateOnSave:1 -->

- 1. [Introducing the Shell](#introducing-the-shell)   
- 2. [Navigating Files and Directories](#navigating-files-and-directories)   
   - 2.1. [General syntax of a shell command:](#general-syntax-of-a-shell-command)   
         - 2.1.0.1. [Contents of a different directory:](#contents-of-a-different-directory)   
      - 2.1.1. [Changing location](#changing-location)   
         - 2.1.1.1. [Moving down the directory tree](#moving-down-the-directory-tree)   
         - 2.1.1.2. [Moving up](#moving-up)   
      - 2.1.2. [Organizing files](#organizing-files)   
- 3. [Working With Files and Directories](#working-with-files-and-directories)   
   - 3.1. [Creating directories](#creating-directories)   
      - 3.1.1. [Create a directory](#create-a-directory)   
      - 3.1.2. [Good names for files and directories](#good-names-for-files-and-directories)   
      - 3.1.3. [Create a text file](#create-a-text-file)   
   - 3.2. [Moving files and directories](#moving-files-and-directories)   
   - 3.3. [Copying files and directories](#copying-files-and-directories)   
   - 3.4. [Removing files and directories](#removing-files-and-directories)   
   - 3.5. [Operations with multiple files and directories](#operations-with-multiple-files-and-directories)   
      - 3.5.1. [Copy with Multiple Filenames](#copy-with-multiple-filenames)   
      - 3.5.2. [Using wildcards for accessing multiple files at once](#using-wildcards-for-accessing-multiple-files-at-once)   
- 4. [Pipes and filters](#pipes-and-filters)   
   - 4.1. [Checking Files](#checking-files)   
- 5. [Loops](#loops)   
   - 5.1. [Processing Files](#processing-files)   
      - 5.1.1. [Command history:](#command-history)   
         - 5.1.1.1. [Other ways to use history](#other-ways-to-use-history)   
- 6. [Shell scripts](#shell-scripts)   
      - 6.0.1. [Passing arguments to a script](#passing-arguments-to-a-script)   
      - 6.0.2. [Improving  script readabitity by adding comments](#improving-script-readabitity-by-adding-comments)   
      - 6.0.3. [Passing all command line arguments to a script](#passing-all-command-line-arguments-to-a-script)   
      - 6.0.4. [Creating a script from the history](#creating-a-script-from-the-history)   
   - 6.1. [Creating a data processing script](#creating-a-data-processing-script)   
- 7. [Finding things](#finding-things)   
   - 7.1. [GREP](#grep)   
   - 7.2. [FIND](#find)   
   - 7.3. [Combining tools in a different (not piping) way](#combining-tools-in-a-different-not-piping-way)   

<!-- /MDTOC -->

# Introducing the Shell

# Navigating Files and Directories

Questions

- How can I move around on my computer?
- How can I see what files and directories I have?
- How can I specify the location of a file or directory on my computer?

Objectives
- Explain the similarities and differences between a file and a directory.
- Translate an absolute path into a relative path and vice versa.
- Construct absolute and relative paths that identify specific files and directories.
- Demonstrate the use of tab completion, and explain its advantages.


The file system
- Part of OS managing files and dirs
- Organizes data into files and dirs
- Dirs hold files and other dirs

Commands:

- inspect
- create
- rename
- delete
---

**Where are we?**

We are in the home directory.

`pwd`

Variations of the home:

C:\Documents and Settings\instructor
/home/instructor

**Home directory, where is it in the filesystem?**

`tree -L 1 /`

**Slashes**

/ at the front of a name means top level

Some high level dirs:  bin, Users, tmp

/ inside of a path is a separator

`tree -L 1 /Users`

**Inspecting contents**
By default new shell opens in your home directory
Contents of the working directory:

`ls -F`


## General syntax of a shell command:
*[command options arguments]*

`ls -F /`

Getting help: man, --help

`man ls`

navigating manuals: B, space, /, q

---
#### Contents of a different directory:

`ls -F Desktop`

Now look what is inside the data-shell:

`ls -F Desktop/data-shell`

---

### Changing location
#### Moving down the directory tree
Move into the Desktop/data-shell/data:

`cd Desktop`

`cd data-shell`

`cd data`

We are now in /Users/nelle/Desktop/data-shell/data

`pwd`

`ls -F`

How to move up the tree?

`cd data-shell`

cd can only see subdirectories
#### Moving up
`cd ..`

*.. is the parent directory*

`pwd`

".." directory does not show up when we use ls -F.
*All files and folders starting with "." are hidden*
Show hidden files:
`ls -F -a` or `ls -Fa`

"." means “the current working directory”
*Other files and directorues starting with "." usually contain configuration settings for dirrerent programs*

---

`cd`

*Without an argument "cd" returns to the home directory*

`pwd`

Go from the home directory to the data in one step:

`cd Desktop/data-shell/data`


*The **relative path**, the path from the current location*

*The **absolute path**, the entire path from the root directory*


Two more shortcuts: "~" and "-"
"~" - the home directory
"-" - the previous directory

---

### Organizing files

What files are in the "north-pacific-gyre/2012-07-03" ?

`ls north-pacific-gyre/2012-07-03`

or use auto completion feature of the shell (Tab):

`ls nor`


# Working With Files and Directories

`cd /Users/instructor/Desktop/data-shell`

Start with checking where you are and what you already have

`pwd`

`ls -F`

## Creating directories
`cd /Users/instructor/Desktop/data-shell`

### Create a directory
`mkdir thesis`

### Good names for files and directories
- Avoid spaces. Spaces separate command line options and arguments.
- Don't begin the name with '-'
- It is safe to use numbers, ".", "_" and "-".

### Create a text file
`cd thesis`

`nano draft.txt `

*It's not "publish or perish" any more,
it's "share and trive".*

Other editors: emacs, vi, notepad, gedit
Filename extensions - just a convention.



## Moving files and directories
`cd ~/Desktop/data-shell/`

`mv thesis/draft.txt thesis/quotes.txt`

`ls thesis`

- Take care not to overwrite something important!
- You can use "mv -i", then mv  will ask you for confirmation before overwriting.
- You can move also directories

Let’s move quotes.txt into the current working directory

`mv thesis/quotes.txt .`

`ls thesis`

`ls quotes.txt`

## Copying files and directories
`cd ~/Desktop/data-shell/`

Copy file:
`cp quotes.txt thesis/quotations.txt`

`ls quotes.txt thesis/quotations.txt`
Copy directory:
`cp -r thesis thesis_backup`

`ls thesis thesis_backup`

## Removing files and directories
`cd ~/Desktop/data-shell/`

`rm quotes.txt`

`ls quotes.txt`

Deleting is permanent, consider "rm -i"

`rm thesis`

`rm -r thesis`

## Operations with multiple files and directories
`cd ~/Desktop/data-shell/data`

### Copy with Multiple Filenames
- When multiple filenames are given, the last argument should be a directory
`mkdir backup`

`cp amino-acids.txt animals.txt backup/`

### Using wildcards for accessing multiple files at once
\* is a wildcard, which matches zero or more characters

`ls pdb/*.pdb`

`ls pdb/p*.pdb`

? is a wildcard matching exactly one character

`ls pdb/?ethane.pdb`

`ls pdb/*ethane.pdb`

wildcards can be combined

`ls pdb/???ane.pdb`

Shell expands the wildcard to create a list of matching filenames before running the command

# Pipes and filters
`cd /Users/instructor/Desktop/data-shell`

**Questions**
- How can I combine existing commands to do new things?

**Objectives**
- Redirect a command’s output to a file.
- Process a file instead of keyboard input using redirection.
- Construct command pipelines with two or more stages.
- Explain what usually happens if a program or pipeline isn’t given any input to process.
- Explain Unix’s ‘small pieces, loosely joined’ philosophy.


Now that we know a few basic commands, we can finally look at the shell’s most powerful feature: the ease with which it lets us combine existing programs in new ways. We’ll start with a directory called molecules

---

`cd ~/Desktop/data-shell`

`ls molecules`

Directory molecules contains 6 pdb files (text)

`cd molecules`

Count lines in all pdb files:
`wc -l *.pdb`

We can also count words -w or characters -c

If you by mistake entered

`wc -l`

The program will be counting lines in standard input. It waits for input to complete. CTRL-C will terminate the process. CTRL-D will signal the end of input.

Which of these files contains the fewest lines?
The first step is to save the output of the wc command into a file:

`wc -l *.pdb > lengths.txt`

`ls lengths.txt`

The cat command gets its name from “concatenate” i.e. join together, and it prints the contents of files one after another.

`cat lengths.txt`

Output Page by Page: less

`sort -n lengths.txt`

`sort -n lengths.txt > sorted-lengths.txt`

`head -n 1 sorted-lengths.txt`

Do not redirect into the same file, e.g.
`sort -n lengths.txt > lengths.txt`

Combine sort and head

Send the output of sort to head:
`sort -n lengths.txt | head -n 1`

Send the output of wc to sort:
`wc -l *.pdb | sort -n`

Chain all 3 together:
`wc -l *.pdb | sort -n | head -n 1`

*This idea of linking programs together is why Unix has been so successful.
 Instead of creating enormous programs that try to do many different things, Unix programmers focus on creating lots of simple tools that each do one job well, and that work well with each other.
 This programming model is called “pipes and filters”. We’ve already seen pipes; a filter is a program like wc or sort that transforms a stream of input into a stream of output.
 Almost all of the standard Unix tools can work this way: unless told to do otherwise, they read from standard input, do something with what they’ve read, and write to standard output.
The key is that any program that reads lines of text from standard input and writes lines of text to standard output can be combined with every other program that behaves this way as well. You can and should write your programs this way so that you and other people can put those programs into pipes to multiply their power.*

## Checking Files
`cd ~/Desktop/data-shell/north-pacific-gyre/2012-07-03`
Check the number of lines
`wc -l *.txt`
Do any of the files have less data than the others?
`wc -l *.txt | sort -n | head -n 5`
Do any of the files have more data than the others?

All files for the analysis should end with A.txt or B.txt
`ls *Z.txt`
`ls *[AB].txt`

# Loops
Questions
- How can I perform the same actions on many different files?

Objectives
- Write a loop that applies one or more commands separately to each file in a set of files.
- Trace the values taken on by a loop variable during execution of the loop.
- Explain the difference between a variable’s name and its value.
- Explain why spaces and some punctuation characters shouldn’t be used in file names.
- Demonstrate how to see what commands have recently been executed.
- Re-run recently executed commands without retyping them.

---

`cd ~/Desktop/data-shell/creatures`

Loops allow us to repeat a command or set of commands for each item in a list. As such they are key to productivity improvements through automation. Similar to wildcards and tab completion, using loops also reduces the amount of typing required (and hence reduces the number of typing mistakes).

Files with genome data.
Print out the classification for each species, (the second line of the file)

`for file in basilisk.dat unicorn.dat`
  `do`
     `head -n 2 $file | tail -n 1`
  `done`

Keyword for tells shell to repeat commands given in the body of the loop once for each item in the list
Each time the loop iterrates it will assign a filename to the varible `file` and execute the `head` command.
The first time the `$file` is `basilisk.dat`. The interpreter runs the command `head` on `basilisk.dat` and pipes the first two lines to the `tail` command, which then prints the second line of `basilisk.dat`.\
For the second iteration, `$filename` becomes `unicorn.dat`.The interpreter runs the command `head` on `unicorn.dat` and pipes the first two lines to the `tail` command, which then prints the second line of `unicorn.dat`.
Since the list was only 2 items, the shell exits the `for` loop.

- The variable name does not matter for shell. Use a name that has a meaning, this helps to inderstand the code

- $ and > as prompt vs as instructions from you

- variable in curly brackets ${file} to clearly delimit the variable name

Continue with more compex loop:

`for filename in *.dat`
  `do`
     `echo $filename`
     `head -n 100 $filename | tail -n 20`
  `done`

prints the filename followed by the lines 81-100

Spaces in names: use quotes to prevent splitting.

`for file in "red basilisk.dat" "purple unicorn.dat"`
  `do`
     `head -n 2 "$file" | tail -n 1`
  `done`


We would like to modify each of the files in data-shell/creatures, but also save a version of the original files, naming the copies original-basilisk.dat and original-unicorn.dat

`cp *.dat original-*.dat` expands to:
`cp basilisk.dat unicorn.dat original-*.dat`

Solution:

`for filename in *.dat`
 `do`
    `cp $filename original-$filename`
 `done`

 Use echo to test the loop without executing commands:

 `for filename in *.dat`
  `do`
     `echo cp $filename original-$filename`
  `done`

  ## Processing Files
`cd ~/Desktop/data-shell/north-pacific-gyre/2012-07-03/`
Process all data files using  `goostats` script. It takes 2 arguments:

- input filename (the raw data)
- output filename (where to save results)

Confirm that we loop over all datafiles:
`for datafile in NENE*[AB].txt`
 `do`
    `echo $datafile`
 `done`

How to call output files?

`for datafile in NENE*[AB].txt`
 `do`
    `echo $datafile stats-$datafile`
 `done`

### Command history:
- press up arrow to retrieve the last command:
`for datafile in NENE*[AB].txt; do echo $datafile stats-$datafile; done`
- modify the command and run it:
`for datafile in NENE*[AB].txt; do bash goostats $datafile stats-$datafile; done`
- the script does not print antything, kill it
- make it to print the current filename
`for datafile in NENE*[AB].txt; do echo $datafile; bash goostats $datafile stats-$datafile; done`

#### Other ways to use history
- By history number
`history | tail -n 20`
`!290`
- Ctrl-R enters a history search mode, searches for the most recent command matching the text you enter
- !! retrieves and executes the last command
- !$ retrieves the last word of the last command and executes it

# Shell scripts
Questions
- How can I save and re-use commands?

Objectives
- Write a shell script that runs a command or series of commands for a fixed set of files.
- Run a shell script from the command line.
- Write a shell script that operates on a set of files defined by the user on the command line.
- Create pipelines that include shell scripts you, and others, have written.

---

- We are finally ready to see what makes the shell such a powerful programming environment.
- We are going to take a set of the commands we need to perform a complex computational task and save them a file so that we can re-run all those operations again later by typing a single command.
-  A bunch of commands saved in a file is usually called a shell script.
-  Shell scripts are actually small programs.


`cd ~/Desktop/data-shell/molecules/`

- create the file middle.sh
`nano middle.sh`
- Insert the line:
`head -n 15 octane.pdb | tail -n 5`
- press CTRL-O to save the file and exit nano
- check that the file exists
- ask shell to execute the commands from the datafile
`bash middle.sh`
- the output is the same as what we would get by running the command directly

What if we want to execute the commands for some other datafile? We could change the filename inside of the script by editing it, but it would take a lot of time.
### Passing arguments to a script
Instead of the explicit filename we can use a special shell variable `$1`. When we execute a script the value of this variable is set to the first command argument on the command line.

- replace octane.pdb with "\$1" in the script:
 `head -n 15 "$1" | tail -n 5`

 - we can now run the script for different files:
 `bash middle.sh octane.pdb`
 `bash middle.sh cubane.pdb`

 We still need to edit the script to adjust the range of lines. Let's fix it by using the varibles $2 and $3:

 `head -n "$2" "$1" | tail -n "$3"`

 We can now run:

 `bash middle.sh pentane.pdb 15 5`
 `bash middle.sh pentane.pdb 20 5`

### Improving  script readabitity by adding comments
\# Select lines from the middle of a file.
\# Usage: bash middle.sh filename end_line num_lines

### Passing all command line arguments to a script
What if we want to process many files in a single pipeline?
For example, to sort our .pdb files by length we could do:

`wc -l *.pdb | sort -n`

We want to be able to get a sorted list of other kinds of files as well
- we need a way to get all those names into the script.
- we don't know how many files are there, so we cannot use \$1, \$2 .. etc.
- we will use the special variable \$@, which means: all of the command-line arguments to the shell script.

`nano sorted.sh`

`# Sort filenames by their length.`
`# Usage: bash sorted.sh one_or_more_filenames`
`wc -l "$@" | sort -n`

We can now use it:
`bash sorted.sh *.pdb ../creatures/*.dat`

### Creating a script from the history
We have done somethng useful and want to reproduce it.
We can save a set of the last commands from the history into a file instead of retyping them:

`history | tail -n 5 > redo-something.sh`

- Only need to remove line numbers and the last line to get a working script

## Creating a data processing script
It is very important to be able to reproduce all data analysis steps. THis can be easily achieved by capturing all the steps in a script.

`cd ~/Desktop/data-shell/north-pacific-gyre/2012-07-03/`

`nano do-stats.sh`

`# Calculate stats for data files.`
`for datafile in "$@"`
`do`
    `echo $datafile`
    `bash goostats $datafile stats-$datafile`
`done`

Run the script:
`bash do-stats.sh NENE*[AB].txt`

We could also do:
`bash do-stats.sh NENE*[AB].txt | wc -l`
so the output is just a number of processed files

We could have specified the files inside of the script:
`# Calculate stats for Site A and Site B data files.`
`for datafile in NENE*[AB].txt`
`do`
...

But then the script would always select the same files, be less flexible


# Finding things

Questions
- How can I find files?
- How can I find things in files?

Objectives
- Use grep to select lines from text files that match simple patterns.
- Use find to find files and directories whose names match simple patterns.
- Use the output of one command as the command-line argument(s) to another command.
- Explain what is meant by ‘text’ and ‘binary’ files, and why many common tools don’t handle the latter well.

---

## GREP
**Global Regular Expression Print**

grep is the program that finds and prints lines in files that match a pattern.

For our examples, we will use a file that contains three haikus taken from a 1998 competition in Salon magazine
In 1998, Salon Magazine ran a competition challenging readers to submit error messages written as Haiku poems

`cd ~/Desktop/data-shell/writing`

`cat haiku.txt`

- find lines that contain the word “not”
`grep not haiku.txt`

- find the pattern: “The”
`grep The haiku.txt`

- find the pattern: "The" as a whole word only
`grep -w The haiku.txt`
-w includes the start and end of line

- find a phrase
`grep -w "is not" haiku.txt`

- number the lines
`grep -n "it" haiku.txt`

- combine operations
`grep -n -w "the" haiku.txt`

- search is case sensitive by default
`grep -n -w -i "the" haiku.txt`

- invert the search
`grep -n -w -v "the" haiku.txt`

- lots of other options
`man grep`

Grep patterns can include wildcards, called *regular expressions*
Regular expressions are complex and powerful

Example: find each line that has "o" at the second place.

^ matches start of the line
. matches a single character
`grep '^.o' haiku.txt`

## FIND

The find command finds files, has lots of options.
We will use the following tree:
`tree ../writing`

- Run fund in the current directory. The first argument is where to start search.
`find .`
- Find only directories
`find . -type d`
- Find only files
`find . -type f`
- Match by name
`find . -name *.txt`
Found only 1 file? The shell expanded *.txt into haiku.txt because it it the only file in the working directory.
`find . -name '*.txt'`

## Combining tools in a different (not piping) way
`find . -name '*.txt'` gives us a list of all text files. How to count lines in all of these files?

One way is to do
`wc -l $(find . -name '*.txt')`
The shell first runs the command `find . -name '*.txt'`. It then replaces the $() expression with that command’s output. SInce result of the find command is a list of 4 files, the shell constructs the command:

`wc -l ./data/one.txt ./data/LittleWomen.txt ./data/two.txt ./haiku.txt`

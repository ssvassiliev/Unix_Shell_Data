
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
## Navigating Files and Directories

**The file system is**
- Part of OS managing files and dirs
- Organizes data into files and dirs
- Dirs hold files and other dirs

**Operating system has commands to:**
- inspect
- create
- rename
- delete
files and directories
---

**Where are we?**

We are in the home directory.

`pwd`

Variations of the home:

Windows: C:\Documents and Settings\username
Linux: /home/username
MacOS: /Users/username

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

**--> Slide 1 <--**
### General syntax of a shell command:
*[command options arguments]*

`ls -F /`

Getting help: man, --help

`man ls`

navigating manuals: B, space, /, q

### Contents of a different directory:

`ls -F Desktop`

Now look what is inside the data-shell:

`ls -F Desktop/data-shell`

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

`cd`

*Without an argument "cd" returns to the home directory*

`pwd`

Go from the home directory to the data in one step:

`cd Desktop/data-shell/data`
*******************
**--> Slide 2 <--**
*******************
*The **relative path**, the path from the current location*

*The **absolute path**, the entire path from the root directory*


Two more shortcuts: "~" and "-"
*******************
**--> Slide 3 <--**
*******************
"." - the current directory
".." -the parent directory
"/" - the root directory
"~" - the home directory
"-" - the previous directory

#### Listing files, autocompletion

What files are in the "north-pacific-gyre/2012-07-03" ?

`ls north-pacific-gyre/2012-07-03`

or use *auto completion* feature of the shell (Tab):

`ls nor`

## Working With Files and Directories

`cd /Users/instructor/Desktop/data-shell`

Start with checking where you are and what you already have

`pwd`

`ls -F`

### Creating directories

`cd /Users/instructor/Desktop/data-shell`

#### Create a directory

`mkdir thesis`

#### Good names for files and directories
- Avoid spaces. Spaces separate command line options and arguments.
- Don't begin the name with '-'
- It is safe to use numbers, ".", "_" and "-".

#### Create a text file
`cd thesis`

`nano draft.txt `

*It's not "publish or perish" any more,
it's "share and trive".*

Other editors: emacs, vi, notepad, gedit
Filename extensions - just a convention.

### Moving files and directories
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

### Copying files and directories
`cd ~/Desktop/data-shell/`

Copy file:
`cp quotes.txt thesis/quotations.txt`

`ls quotes.txt thesis/quotations.txt`

Copy directory:
`cp -r thesis thesis_backup`

`ls thesis thesis_backup`

### Removing files and directories
`cd ~/Desktop/data-shell/`

`rm quotes.txt`

`ls quotes.txt`

Deleting is permanent, consider "rm -i"

`rm thesis`

`rm -r thesis`

### Operations with multiple files and directories
`cd ~/Desktop/data-shell/data`

#### Copy with Multiple Filenames
When multiple filenames are given, the last argument should be a directory

`mkdir backup`

`cp amino-acids.txt animals.txt backup/`

#### Using wildcards for accessing multiple files at once
" \* " is a wildcard, which matches zero or more characters

`ls pdb/*.pdb`

`ls pdb/p*.pdb`

" ? " is a wildcard matching exactly one character

`ls pdb/?ethane.pdb`

`ls pdb/*ethane.pdb`

wildcards can be combined

`ls pdb/???ane.pdb`

Shell expands the wildcard to create a list of matching filenames before running the command

*******************
**--> Slide 3 <--**
*******************
## Pipes and filters
`cd /Users/instructor/Desktop/data-shell`

**Questions**
How can we combine existing commands to do new things?

Now that we know a few basic commands, we can finally look at the shell’s most powerful feature: the ease with which it lets us combine existing programs in new ways. We’ll start with a directory called molecules

---

`cd ~/Desktop/data-shell`

`ls molecules`

Directory molecules contains 6 pdb files (text)

`cd molecules`


**wc**, word count

Count lines in all pdb files
`wc -l *.pdb`

We can also count words -w or characters -c

If you by mistake entered

`wc -l`

The program will be counting lines in standard input. It waits for input to complete. CTRL-C will terminate the process. CTRL-D will signal the end of input.

#### How to find out which of these files contains the fewest lines?
The first step is to save the output of the wc command into a file:

`wc -l *.pdb > lengths.txt`

`ls lengths.txt`

**cat** The cat command gets its name from “concatenate” i.e. join together, and it prints the contents of files one after another.

`cat lengths.txt`

**less** Output page by page

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

*This idea of linking programs together is why Unix has been so successful. Instead of creating enormous programs that try to do many different things, Unix programmers focus on creating lots of simple tools that each do one job well, and that work well with each other.

This programming model is called “pipes and filters”. We’ve already seen pipes; a filter is a program like wc or sort that transforms a stream of input into a stream of output.
Almost all of the standard Unix tools can work this way: unless told to do otherwise, they read from standard input, do something with what they’ve read, and write to standard output.

The key is that any program that reads lines of text from standard input and writes lines of text to standard output can be combined with every other program that behaves this way as well. You can and should write your programs this way so that you and other people can put those programs into pipes to multiply their power.*

## Checking the number of lines in files
`cd ~/Desktop/data-shell/north-pacific-gyre/2012-07-03`

#### Check the number of lines
`wc -l *.txt`

Do any of the files have less data than the others?
`wc -l *.txt | sort -n | head -n 5`

Do any of the files have more data than the others?

## Selecting files for analysis
All files for the analysis should end with A.txt or B.txt

`ls *Z.txt`
`ls *[AB].txt`

## Loops

`cd ~/Desktop/data-shell/creatures`

Loops allow us to repeat a command or set of commands for each item in a list. As such they are key to productivity improvements through automation. Similar to wildcards and tab completion, using loops also reduces the amount of typing required (and hence reduces the number of typing mistakes).

---

### Analyze files with genome data.

#### Let's print out classification for each species found in the second line of a file.

`for file in basilisk.dat unicorn.dat`
  `do`
     `head -n 2 $file | tail -n 1`
  `done`

Keyword `for` tells shell to repeat commands given in the body of the loop once for each item in the list.

Each time the loop iterrates it will assign a filename to the varible `file` and execute the `head` command.

The first time the `$file` is `basilisk.dat`. The interpreter runs the command `head` on `basilisk.dat` and pipes the first two lines to the `tail` command, which then prints the second line of `basilisk.dat`.

For the second iteration, `$filename` becomes `unicorn.dat`.The interpreter runs the command `head` on `unicorn.dat` and pipes the first two lines to the `tail` command, which then prints the second line of `unicorn.dat`.
Since the list was only 2 items, the shell exits the `for` loop.

- The variable name does not matter for shell. Use a name that has a meaning, this helps to inderstand the code

- Meaning of `$` and `>` as prompt

- Use curly brackets `${file}` to clearly delimit the variable name

#### Continue with more compex loop: print out a middle section from each file

`for filename in *.dat`
  `do`
     `echo $filename`
     `head -n 100 $filename | tail -n 20`
  `done`

This loop prints the filename followed by the lines 81-100

**Spaces in names: use quotes to prevent splitting.**

`for file in "red basilisk.dat" "purple unicorn.dat"`
  `do`
     `head -n 2 "$file" | tail -n 1`
  `done`

#### Modify each of the files in a directory and save an original version of each file.

We would like to modify each of the files in data-shell/creatures, but also save a version of the original files, naming the copies original-basilisk.dat and original-unicorn.dat

`cp *.dat original-*.dat` expands to:
`cp basilisk.dat unicorn.dat original-*.dat`

Solution:

`for filename in *.dat`
 `do`
    `cp $filename original-$filename`
 `done`

 **Use echo to test the loop without executing commands:**

 `for filename in *.dat`
  `do`
     `echo cp $filename original-$filename`
  `done`

### Processing Files using a Program

`cd ~/Desktop/data-shell/north-pacific-gyre/2012-07-03/`

Process all data files using  `goostats` script. It takes 2 arguments:

1. Input filename (the raw data)
2. Output filename (where to save results)

All files for the analysis should end with A.txt or B.txt.

Confirm that we loop over all datafiles:

`for datafile in NENE*[AB].txt`
 `do`
    `echo $datafile`
 `done`

We also need to make names for output files.
How to call output files? Prepend `stats-`:

`for datafile in NENE*[AB].txt`
 `do`
    `echo $datafile stats-$datafile`
 `done`

### Command history:
Ppress up arrow to retrieve the last command:

`for datafile in NENE*[AB].txt; do echo $datafile stats-$datafile; done`

Modify the command and run it:

`for datafile in NENE*[AB].txt; do bash goostats $datafile stats-$datafile; done`

The script does not print antything, kill it

Make it to print the current filename

`for datafile in NENE*[AB].txt; do echo $datafile; bash goostats $datafile stats-$datafile; done`

#### Other ways to use history
By history number

`history | tail -n 20`
`!290`

Ctrl-R enters a history search mode, searches for the most recent command matching the text you enter

!! retrieves and executes the last command

!$ retrieves the last word of the last command and executes it

## Shell scripts

---

- We are finally ready to see what makes the shell such a powerful programming environment.
- We are going to take a set of the commands we need to perform a complex computational task and save them a file so that we can re-run all those operations again later by typing a single command.
-  A bunch of commands saved in a file is usually called a shell script.
-  Shell scripts are actually small programs.

`cd ~/Desktop/data-shell/molecules/`

create the file middle.sh

`nano middle.sh`

Insert the line:

`head -n 15 octane.pdb | tail -n 5`

Press CTRL-O to save the file and exit nano
Check that the file exists
Ask shell to execute the commands from the datafile

`bash middle.sh`

the output is the same as what we would get by running the command directly

What if we want to execute the commands for some other datafile? We could change the filename inside of the script by editing it, but it would take a lot of time.

### Passing arguments to a script
Instead of the explicit filename we can use a special shell variable `$1`. When we execute a script the value of this variable is set to the first command argument on the command line.

Replace octane.pdb with "\$1" in the script:

 `head -n 15 "$1" | tail -n 5`

 We can now run the script for different files:

 `bash middle.sh octane.pdb`
 `bash middle.sh cubane.pdb`

 We still need to edit the script to adjust the range of lines. Let's fix it by using the varibles $2 and $3:

 `head -n "$2" "$1" | tail -n "$3"`

 We can now run:

 `bash middle.sh pentane.pdb 15 5`
 `bash middle.sh pentane.pdb 20 5`

### Improving  script readabitity by adding comments

`# Select lines from the middle of a file`
`# Usage: bash middle.sh filename end_line num_lines`

### Passing all command line arguments to a script

What if we want to process many files from different deirectories in a single pipeline?

For example, to sort our .pdb files by length we could do:

`wc -l *.pdb | sort -n`

We want to be able to get a sorted list of other kinds of files as well

We need a way to get all those names into the script.
We don't know how many files are there, so we cannot use \$1, \$2 .. etc.

We will use the special variable `$@`, which means:
all of the command-line arguments to the shell script.

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

Only need to remove line numbers and the last line to get a working script

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

But then the script would always select the same files, be less flexible


# Finding things

Questions
- How to find files?
- How to find things in files?
---

## GREP
**Global Regular Expression Print**

grep is the program that finds and prints lines in files that match a pattern.

For our examples, we will use a file that contains three haikus taken from a 1998 competition in Salon magazine
In 1998, Salon Magazine ran a competition challenging readers to submit error messages written as Haiku poems

`cd ~/Desktop/data-shell/writing`

`cat haiku.txt`

Find lines that contain the word “not”
`grep not haiku.txt`

Find the pattern: “The”
`grep The haiku.txt`

Find the pattern: "The" as a whole word only
`grep -w The haiku.txt`
-w includes the start and end of line

Find a phrase
`grep -w "is not" haiku.txt`

Number the lines
`grep -n "it" haiku.txt`

Combine operations
`grep -n -w "the" haiku.txt`

Search is case sensitive by default
`grep -n -w -i "the" haiku.txt`

Invert the search
`grep -n -w -v "the" haiku.txt`

Lots of other options
`man grep`

Grep patterns can include wildcards, called *regular expressions*
Regular expressions are complex and powerful

Example: find each line that has "o" at the second place.

^ matches start of the line
. matches a single character
`grep '^.o' haiku.txt`

## FIND Files

The find command finds files, has lots of options.
We will use the following tree:
`tree ../writing`

Run find in the current directory. The first argument is where to start search.
`find .`

Find only directories
`find . -type d`

Find only files
`find . -type f`

Match by name
`find . -name *.txt`
Found only 1 file? The shell expanded *.txt into haiku.txt because it it the only file in the working directory.
`find . -name '*.txt'`

## Combining tools in a different (not piping) way
`find . -name '*.txt'` gives us a list of all text files. How to count lines in all of these files?

One way is to do
`wc -l $(find . -name '*.txt')`
The shell first runs the command `find . -name '*.txt'`. It then replaces the $() expression with that command’s output. SInce result of the find command is a list of 4 files, the shell constructs the command:

`wc -l ./data/one.txt ./data/LittleWomen.txt ./data/two.txt ./haiku.txt`


## Checking GPU usage of a running job
`-i 1` query every 1 sec
`-l 1` query gpu:1
`-f nv.log` send output to file
`timeout 100` do it for 100 sec

`timeout 100 nvidia-smi --query-gpu=index,utilization.gpu,utilization.memory --format=csv -l 1  -i 1`

## Multicore namd demo simulation 

Files are in `/home/svassili/demo/PSII_mdrun`
To run:
`run_salloc 8`
`run_namd 8`

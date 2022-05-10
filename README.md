# simple_shell
# Group work simple shell
# 0x16. C - Simple Shell
# Resources
Read or watch:
✅ Unix shell
✅ Thompson shell
✅ Ken Thompson
Everything you need to know to start coding your own shell concept page
man or help:
sh (Run sh as well)
# General
Who designed and implemented the original Unix operating system
Who wrote the first version of the UNIX shell
Who invented the B programming language (the direct predecessor to the C programming language)
Who is Ken Thompson
How does a shell work
What is a pid and a ppid
How to manipulate the environment of the current process
What is the difference between a function and a system call
How to create processes
What are the three prototypes of main
How does the shell use the PATH to find the programs
How to execute another program with the execve system call
How to suspend the execution of a process until one of its children terminates
What is EOF / “end-of-file”?
Requirements
# General
Allowed editors: vi, vim, emacs
All your files will be compiled on Ubuntu 20.04 LTS using gcc, using the options -Wall -Werror -Wextra -pedantic -std=gnu89
All your files should end with a new line
A README.md file, at the root of the folder of the project is mandatory
Your code should use the Betty style. It will be checked using betty-style.pl and betty-doc.pl
Your shell should not have any memory leaks
No more than 5 functions per file
All your header files should be include guarded
Use system calls only when you need to (why?)
# Output
Unless specified otherwise, your program must have the exact same output as sh (/bin/sh) as well as the exact same error output.
# Simple Shell
What really happens when you type a command into a shell? How
does it know how to run programs and interprets user inputs? Well, you are in the right pod! This project dissects the shell program that allows you to even [explain to anyone](https://fs.blog/2012/04/feynman-technique/) without the use of the internet :) Excited? noe let's dig in!
![alt text](https://s3.amazonaws.com/intranet-projects-files/holbertonschool-low_level_programming/235/shell.jpeg)
## Description
The simple shell is an application that reads lines from either a file or the terminal, interprets them, and executes them. I most cases, it provides a command line user interface for Unix-like operating systems, where can interactively type directly to the running shell or pipe in shell scripts. [read more](https://en.wikipedia.org/wiki/Unix_shell). In this project, we designed and implemented a simple UNIX command line interpreter from the ground ^-^.

## General requirements to consider
- All our files will be compiled on Ubuntu 14.04 LTS
- Our C programs and functions will be compiled with gcc 4.8.4 using the flags ```-Wall -Werror -Wextra and -pedantic ```
- Our files ends end with a new line, with no memory leaks
- Our code will use the [Betty style](https://github.com/holbertonschool/Betty). It will be checked using ```betty-style.pl and betty-doc.pl```.
- system calls will be used when necessary ([why?](https://www.quora.com/Why-are-system-calls-expensive-in-operating-systems))

## Program Output
- Our program have the exact same output as ```sh (/bin/sh)``` as well as the exact same error output.
- The only difference is when you print an error, the name of the program must be equivalent to the ``argv[0]``

### Example of error with sh:
```Bash
$ echo "Ian" | /bin/sh
/bin/sh: 1: qwerty: not found
$ echo "Ian" | /bin/../bin/sh
/bin/../bin/sh: 1: qwerty: not found
$
```
### Same error with our program hsh:
```Bash
$ echo "kanneh" | ./hsh
./hsh: 1: qwerty: not found
$ echo "kanneh" | ./././hsh
./././hsh: 1: qwerty: not found
$
```
## List of functions and system calls we used
```Bash 
- access (man 2 access)
- chdir (man 2 chdir)
- close (man 2 close)
- closedir (man 3 closedir)
- execve (man 2 execve)
- exit (man 3 exit)
- _exit (man 2 _exit)
- fflush (man 3 fflush)
- fork (man 2 fork)
- free (man 3 free)
- getcwd (man 3 getcwd)
- getline (man 3 getline)
- isatty (man 3 isatty)
- kill (man 2 kill)
- malloc (man 3 malloc)
- open (man 2 open)
- opendir (man 3 opendir)
- perror (man 3 perror)
- read (man 2 read)
- readdir (man 3 readdir)
- signal (man 2 signal)
- stat (__xstat) (man 2 stat)
- lstat (__lxstat) (man 2 lstat)
- fstat (__fxstat) (man 2 fstat)
- strtok (man 3 strtok)
- wait (man 2 wait)
- waitpid (man 2 waitpid)
- wait3 (man 2 wait3)
- wait4 (man 2 wait4)
- write (man 2 write)
```

## Project Compilation
You can compile our shell using:
```Bash
gcc -Wall -Werror -Wextra -pedantic *.c -o hsh
```
## Testing
Our shell should work like this in interactive mode:
```Bash
$ ./hsh
($) /bin/ls
hsh main.c shell.c
($)
($) exit
$
```
#### Also in non-interactive mode:
```Bash
$ echo "/bin/ls" | ./hsh
hsh main.c shell.c test_ls_2
$
$ cat test_ls_2
/bin/ls
/bin/ls
$
$ cat test_ls_2 | ./hsh
hsh main.c shell.c test_ls_2
hsh main.c shell.c test_ls_2
$
```
## The Project's Implementation in Review
#### Submission requirements:
1. Write a beautiful code that passes the Betty checks
2. Write a UNIX command line interpreter.

## Functionalities
#### Our Shell does the following:
- Display a prompt and wait for the user to type a command, ending wih a new line.
- The prompt is displayed again each time a command has been executed.
- The command lines are simple, no semicolons, no pipes, no redirections or any other advanced features.
- The command lines are made only of one word. No arguments will be passed to programs.
- If an executable cannot be found, an error message is displayed to the user, and then display the prompt again.
- We will handle errors, including the “end of file” condition (Ctrl+D)

## Using the man_1_simple_shell page
- Display the page
```Bash
 man ./man_1_simple_shell
```


### Contributors
|Names                | Emails                 |
|---------------------|------------------------|
| Musa Selekie Kanneh | musas.kanneh@gmail.com |
| Obutho Ian Odhiambo | ianodhiambo9@gmail.com |
The only difference is when you print an error, the name of the program must be equivalent to your argv[0] (See below)
# Tasks
0. Write a beautiful code that passes the Betty checks.
1. Write a UNIX command line interpreter
2. Simple shell 0.1 + handle command lines with arguments
3. Simple shell 0.2 +

Handle the PATH
fork must not be called if the command doesn’t exist
4. Simple shell 0.3 +

Implement the exit built-in, that exits the shell
Usage: exit
You don’t have to handle any argument to the built-in exit
5. Simple shell 0.4 +

Implement the env built-in, that prints the current environment
6. Simple shell 0.1 +

Write your own getline function
Use a buffer to read many chars at once and call the least possible the read system call
You will need to use static variables
You are not allowed to use getline
You don’t have to:

be able to move the cursor
7. Simple shell 0.2 +

You are not allowed to use strtok
8. Simple shell 0.4 +

handle arguments for the built-in exit
Usage: exit status, where status is an integer used to exit the shell.
9. Simple shell 1.0 +

Implement the setenv and unsetenv builtin commands

setenv
Initialize a new environment variable, or modify an existing one
Command syntax: setenv VARIABLE VALUE
Should print something on stderr on failure
unsetenv
Remove an environment variable
Command syntax: unsetenv VARIABLE
Should print something on stderr on failure.
10. Simple shell 1.0 +

Implement the builtin command cd:

Changes the current directory of the process.
Command syntax: cd [DIRECTORY]
If no argument is given to cd the command must be interpreted like cd $HOME
You have to handle the command cd -
You have to update the environment variable PWD when you change directory
man chdir, man getcwd
11. Simple shell 1.0 +

Handle the commands separator ;
12. Simple shell 1.0 +

Handle the && and || shell logical operators
13. Simple shell 1.0 +

Implement the alias builtin command
Usage: alias [name[='value'] ...]
alias: Prints a list of all aliases, one per line, in the form name='value'
alias name [name2 ...]: Prints the aliases name, name2, etc 1 per line, in the form name='value'
alias name='value' [...]: Defines an alias for each name whose value is given. If name is already an alias, replaces its value with value
14. Simple shell 1.0 +

Handle variables replacement
Handle the $? variable
Handle the $$ variable
15. Simple shell 1.0 +

Handle comments (#)
16. Simple shell 1.0 +

Usage: simple_shell [filename]
Your shell can take a file as a command line argument
The file contains all the commands that your shell should run before exiting
The file should contain one command per line
In this mode, the shell should not print a prompt and should not read from stdin

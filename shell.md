## Shell variables
shell variables are untyped - consider them as strings - where 1 is equivalent "1"

shell variables are not declared and shell variables do not need initialization.

Only one scope - no local variables
- except sub-shells and functions
- changes to variables in sub-shells have no effect outside sub-shell
- components of pipleline executed in sub-shell

```$name``` replaced with value of variable name.

```name=value``` assigns value to variable name - note that no spaces around '='.

## $(command) - command expansion
- ```$(command)``` is evaluated by running ```command```
- stdout is captured from ```command```
- ```$(command)``` is replaced with the entire captured stdout
- ````command`(backticks)``` is equivalent to ```$(command)```

```
now=$(date)
echo $now
-- This will do the date command and print the current time
```

## '' - single quotes
single quotes ```''``` group the characters within into a single word
- no characters interpreted specially inside single quotes
- a single quote can not occur within single quotes
- you can put a double quote between single-quotes

```
echo '!@#$%^&*()_'
-- this will print !@#$%^&*()_
```

## "" - double quotes
double quotes ```""``` group the characters characters within into a single word
- variables and commands are expanded inside double-quotes
- backslash can be used to excape 
- other characters not interpreted specially inside double quotes
- you can put a single quote between double-quotes

```
answer=42
echo "The answer is $answer."
-- this will print The answer is 42.
```

## << - here documents
- << word called a here document
- following lines until word specifically multi-line string as command input
- variables and commands expanded - same as  double quotes
- <<'word' variables and commands not expanded - same as single quotes

```
name=Andrew
tr a-z A-Z << END
hello $name
howa are you
END
HELLO ANDREW
HOW ARE YOU
```

## $((expression))
$((expression)) is evaluated as an arithmetic expression
- expression is evaluated as c-like integer arithmetic
- and is replaced with the result
- the ```$``` on variables can be omitted in expressions

```
x=8
answer=$((x*x - 3*x + 2))
echo $answer
-- this will print 42
```

## word splitting
``` python
import sys
print(f'sys.argv = {sys.argv}')
```
```
print_argv.py hello andrew
-- output is sys.argv = ['./print_argv.py', 'hello', 'andrew']
```
```
print_argv.py "$y $((6*7)) $(date)"
-- all these will be interpreted
```

## *?[]! - pathname globbing
- ```*?[]!``` characters cause a word to be matched against pathnames
- ```*``` matches 0 or more of any character - equivalent to regex ```.*```
- ```?``` matches any one characters - equivalent to regex ```.```
- ```[characters]``` matches 1 of characters - same as regex ```[]```
- ```[!characters]``` matches 1 character not in characters - same as regex ```[^]```
- if no pathname matches the word is unchanged
- aside: globbing also availavle in Python, Perl, C and other languages

```
echo *.[ch]
-- will git functions.c functions.h i.h main.c
-- which is any file end with .c or .h
```

## I/O redirection
stdin, stdout and stderr for a command can be directed to/from files
- ```< infile``` - connect stdin to the file infile
- ```> outfile``` - send stdout to the file outfile
- ```>> outfile``` - append stdout to the file outfile
- ```2> outfile``` - send stderr to the file outfile
- ```2>> outfile``` - append stderr to the file outfile
- ```> outfile 2>&1``` - send stderr+stdout to outfile
- ```1>&2``` - send stdout to stderr

## Pipelines
- command1 | command2 | command3
- stdout of command(n-1) connected to stdin of command(n), which means command(n) takes the output of command(n-1)
- beware changes to variables in pipeline are lost

## searching PATH for the program
- first word on line specifies command to be run.
- if first word is not the full (absolute) pathname of a file the colon-separated list of directory specified by the variable PATH is searched.
- for example if ```PATH=/bin/:/usr/bin:/home/z1234567/bin``` and the command is ```kitten``` the shell will check these files in order: ```/bin/kitten``` ```/usr/bin/kitten``` ```/home/z1234567/bin```. 
- or ```.``` in PATH causes the current directory to be checked.
- if ```.``` is not last in PATH then programs in the current directory may be unexpectedly run.
- this can also happen inside run shell scripts or other programs you run.

## Shell scripts
```
cat hello
echo Hello, John Connor - the time is $(date)
sh hello
Hello, John Connor - the time is Fri 29 ...
```
``` shell
$ cat >cat
#!/bin/sh
echo miaou
-- this is using cat to create a shell script called cat.
-- first two bytes (i.e. characters) of a script (#!) are read by the operating system 
-- to signify that the commands in the script should be fed to the indicated interpreter (/bin/sh).
-- In this instance the only command in the script is echo, which just writes whatever it's given (miaou) to stdout.
```

## Shell built-in variables
- ```$0``` - the name of the command
- ```$1``` - the first command-line argument
- ```$2``` - the second command-line argument
- ```$#``` - the count of command-line arguments
- ```$*``` - command-line arguments (don't use)
- ```$@``` - also command-line arguments (don't use)
- ```"$*"``` - all the command-line arguments with word-splitting (don't use)
- ```"$@"``` - all the command-line arguments without splitting (use)
- ```$?``` - exit status of the most recent command
- ```$$``` - process ID of this shell

```
echo name is "$0"
echo process ID is $$
echo I have $# arguments
echo The 4th argument is "'$4'"
```
```
./args.sh hi how are you
```
```
name is ./args.sh
process ID is 101236
I have 4 arguments
The 5th argument is 'you'
```

## Debugging shell scripts
- test parts of shell script from command line
- use ```echo``` to print the value of variables
- add ```set -x``` to see commands being executed (or equivalently run ```/bin/dash -x script.sh```)

## Exit status and control
when unix-like programs finish they give the operating system an **exit status**
- the return value of main becomes the exit status of a C program
- or if exit is called, its argument is the exit status
- in Python exit status is supplied as an argument to sys.exit

an exit status is an integer
- by convention a zero exit status indicated normal execution
- a non-zero exit status indicates an error occurred
- which non-zero integer might indicate the nature of the problem

program exit status is often ignored
- not important writing single programs
- very important when combining multiple programs

flow of execution in shell scripts based on exit status
- if/while statement conditions use exit status

two weird utilities
- /bin/true does nothing and always exits with status 0
- /bin/false does nothing and always exits with status 1

## if statements in shell
``` shell
if gcc main.c
then 
  echo your C compiles
elif python3 main.c
  echo you have written Python not C
else
  echo program broken - send help
fi
``` 

## while statements in shell
``` shell
last=$1
number=1
while test $number -le "$last"
do
  echo $number
  number=$((number + 1))
done
```

## for statements in shell
``` shell
for a in $*
do
  echo "$a"
done
```

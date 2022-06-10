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

# regular expression

regular expression is a concise powerful notation for sets of strings

## Regular expression basics

Unless a character has a special meaning it matches itself
- e.g. ```a``` has no special meaning so it matches ```a```

```p*``` denotes zero or more repetitions of p.
- e.g. ```b*``` matches the ```empty string and b, bb, bb, bbb ...```
- note this is an infinite set of strings

```pattern1 | pattern2``` denotes the union of pattern1 and pattern2
- e.g. ```perl | python | ruby``` matches any of perl, python or ruby
- ```|``` is sometimes called **alternation**

```parentheses()``` are used for grouping
- e.g. ```c(,c)*``` matches ```c c,c c,c,c ...```
- and ```(d|e)*(f|g)``` matches ```f, g, df, dg, ef, eg, ddf, deg ...```

```backslash\``` removes any special meaning of the following character
- e.g. ```\*``` matches an ```*``` instead of indicating repetition

Any regular expression can be written using only ```()*|\```
- but many syntax features are present for convenience and clarity.

```dot.``` matches any single character

```square brackets[]``` provide convenient matching of any one of a set of characters.

```[listOfCharacters]``` matches any single character from listOfCharacters
- e.g. ```[aeiouAEIOU]``` matches any English vowel

A shorthand is available for ranges of characters [first-last]
- e.g. ```[a-e], [a-z], [0-9], [a-zA-Z], [a-zA-Z0-9]```

```Square brackets[]``` matching can be inverted with an ```^```

```[^listOfCharacters]``` matches any single character except those in listOfCharacter.
- e.g. ```[ˆa-e]``` matches any character except one of the first five lowercase letters

Ohter characters lose their special meaning inside ```bracket[]``` expression.
- ```[^x]*x``` matches any characters up to and including the first x.

regular expressions may be used to match against a whole string
- e.g. ```re.fullmatch``` in python

regular expressions are often used to match a substring(part of a string)
- e.g. ```grep``` prints lines containing a substring matching the regular expression
- e.g. ```re.search``` in Python (```re.match``` matches only at start of string)

when matching part of a string you can limit matches to the start or end of a string (or both)

start of the string is denoted by ```^(uparrow)```
- ```^hello``` matches a string starting with hello
- note ```^``` has two meanings in regular expressions
- e.g. ```^[abc]``` matches a or b or c at the start of a string
- e.g. ```[^abc]``` matches any character except a or b or c

the end of the string is denoted by ```$(dollar)```
- ```cat$``` matches ```cat``` at the end of a string
- ```cat.*dog$``` matches any string starting cat and finishing dog

```p+``` denotes one or more repetitions of p
- e.g. ```[0-9]+``` matches any sequence of digits

```p?``` denotes zero or one occurence of p

```p{n}``` denotes n repetitions of p
- e.g. ```z[0-9]{7}``` matches a UNSW zid

```p{n, m}``` denotes n to m repetitions of p

```p{n,}``` denotes n or more repetitions of p

### grep
```grep``` copies to stdout lines that match a specified regular expression

Some useful ```grep``` options:
- ```-i```    ignore upper/lower case difference in matching
- ```-v```    only display lines that do not match the pattern
- ```-c```    print a count of mathcing lines
- ```-w```    only match pattern if it makes a complete word

```fgrep``` or ```grep -F``` match strings only (no regular expressions)
- use if you don't need regex
- faster
- avoids bugs from regex syntax accidentally occuring in your match string

```grep -G``` or ```grep``` matches a subset of regular expressions, e.g. ```no + ? | {} ()```
- faster than ```grep -E``` but this is rarely important these days
- generally just use ```grep -E```

```grep -E``` or ```egrep``` matches full POSIX regular expressions
- ```grep -E``` is what you want most of the time

```grep -P``` POSIX regular expressions + Perl extentions
- standard Python regexes include some but not all Perl extentions
- use if you need Perl/Python regex extensions
- PCRE libraty widely used (e.g. Apache)

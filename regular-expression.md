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

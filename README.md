# COMP2041

## Filter
A filter is a program that transforms a byte stream.

On Unix-like systems, filters are commands that:
- read bytes from their standard input or specified files
- perform useful transformations on the stream
- write the transformaed bytes to their standard output
- most filters work on text, UTF-8 or perhaps just ASCII
- most filters are line-based, a few are byte based or character-based

```cat``` is the simplest filter - it passes the byte stream unchanged.

Unix filters use common conventions for command line arguments:
- input can be specified by a list of file names
- if no files are mentioned, the filter reads from standard input
- the filename - corresponds to standard input
``` python
# read from the file data1
filter data1
# or
filter < data1
# read from the files data1 data2 data3
filter data1 data2 data3
# read from data1, then stdin, then data2
filter data1 - data2
```

Most filters have many options for controlling their behaviour. Unix manual entries describe how each option works.

Some useful ```cat``` options:
- -n - number output lines
- -A - display non-printing characters - handy for debugging
- -s - squeeze consecutive blank lines into single blank line

```wc``` is word counter to summarize its input as a single line. This is often used as last command in pipeline.

Some useful ```wc``` options:
- -c  print the number of characters
- -w  print the number of words
- -l  print the number of lines only

By default, ```wc``` prints the number of line, words, characters in its input.

```tr``` is transliterate characters which reads chars and writes characters, mapping some chars with others. The synrtax is ```tr sourceChars destChars```

```tr``` doesn't accept file names on the command line - it uses stdin only. ```tr``` is not line-based, it works with individual chars.

Some useful ```tr``` options:
- -c  map all bytes not occurring in sourceChars (complement)
- -s  squeezze adjacent repeated characters out (only copy the first)
- -d  delete all characters in sourceChars (not destChars)

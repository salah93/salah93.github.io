Title: ipython tips
Date: 2017-09-17 10:00
Category: python

IPython is a very helpful tool in prototyping and testing code in python. Its many rich features make exploring code base's painless and easy.

## installation
```bash
pip install -U ipython
ipython
```
## magic
ipython has a set of "magic" commands
+ %load - loads file (copies file into repl)
+ %run - runs file (global variables and functions enter namespace)
+ %magic - list magic variables
+ %hist - history of current or previous repl sessions
+ %timeit - time execution of python statement

## help
### question mark
Using the "?" we can find methods that match certain patterns and we can look up docstrings/source code.
This can help us understand parameters and method function. The "?" can also be used with magic commands!
+ np.*load*?
+ requests.get?? => source code
+ requests.get? => docstring
+ %timeit?
+ %magic
+ %help

# debugging
+ %pdb => automatically jump into debugger when exception occurs
+ %debug => jump into debugger on last exception
+ %run -d filename.py => execute program via debugger
+ %whos

## recalling past commands
where X is the number of the output/input
+ output: \_X
+ input:  \_iX

## logging sessions
+ %logstart -ort
+ %logoff
+ %logon
+ %logstate

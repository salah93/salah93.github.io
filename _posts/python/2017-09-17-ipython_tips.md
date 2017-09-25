---
layout: post
category : command-line
tagline:
tags : [awk, intro, beginner, commandline, unix]
---
{% include JB/setup %}

IPython is a very helpful tool in prototyping and testing code in python. Its many rich features make exploring code base's painless and easy.

## magic
+ %load
+ %run
+ %magic
+ %hist
+ %timeit
+ %time

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

## logging
+ %logstart -ort
+ %logoff
+ %logon
+ %logstate
+ %logstop


## profiling
+ python -m cProfile cprofile_example.py
+ %prun -s cumulative -l 7 run_experiment()
+ %run -p -s cumulative run_experiment.py
+ line_profiler

```bash
pip install line_profiler
ipython profile create default
echo "c.TerminalIPythonApp.extensions = ['line_profiler']" >> ~/.ipython/profile_default/ipython_config.py
cat <<EOF > cprofile_example.py
def long_f():
    long_num = 1000
    long_arr = range(long_num)
    other_arr = range(long_num)
    result = []
    for i in long_arr:
        for j in other_arr:
            z = i * j
            result.append(z)
    return z
long_f()
EOF
ipython
# %run cprofile_example.py
# %lprun -f long_f long_f()
```

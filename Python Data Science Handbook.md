
## Running External Code: %run
```
#-------------------------------------# file: myscript.py
def square(x):
"""square a number"""
	return x ** 2

for N in range(1, 4):
	print(N, "squared is", square(N))


In [6]: %run myscript.py
1 squared is 1
2 squared is 4
3 squared is 9
```

## Timing Code Execution: %timeit
### The execution time of the single-line Python 
```
In [8]: %timeit L = [n ** 2 for n in range(1000)]
1000 loops, best of 3: 325 μs per loop
```


### multiple  runs 
```
In [9]: %%timeit   
...: L = []   
...: for n in range(1000):   
...:     L.append(n ** 2)   
...:
1000 loops, best of 3: 373 μs per loop
```

## Input and Output History
### IPython’s In and Out Objects
- In IPython, In and Out are objects and can access through index

```
In [6]: print(In[1])
import math

In [7]: print(Out[2])
0.9092974268256817
```

- For  accessing  a  batch  of  previous  inputs  at  once,  the  %history  magic  command  isvery helpful
```
In [16]: %history -n 1-4   
1: import math   
2: math.sin(2)   
3: math.cos(2)   
4: print(In)
```


## IPython and Shell Commands
### Shell Commands in IPython
- start with "!"
```
In [1]: !ls
myproject.txt
In [2]: !pwd
/home/jake/projects/myproject
In [3]: !echo "printing from the shell"
printing from the shell
```

### Passing Values to and from the Shell
```
In [4]: contents = !ls
In [5]: print(contents)
['myproject.txt']
In [6]: directory = !pwd
In [7]: print(directory)
['/Users/jakevdp/notebooks/tmp/myproject']
```


## Errors and Debugging
### Controlling Exceptions: %xmode
- %xmode  takes  a  single  argument,  the  mode,  and  there  are  three  possibilities:  Plain,Context, and Verbose.


### Debugging: When Reading Tracebacks Is Not Enough

```
In[7]: %debug
> <ipython-input-1-d849e34d61fb>(2)func1()
      1 def func1(a, b):
----> 2     return a / b      
	  3

ipdb> print(a)
1
ipdb> print(b)
0
ipdb> quit
```

```
In[8]: %debug
> <ipython-input-1-d849e34d61fb>(2)func1()
      1 def func1(a, b):
----> 2     return a / b
      3 

ipdb> up
> <ipython-input-1-d849e34d61fb>(7)func2()
      5     a = x      
      6     b = x - 1
----> 7     return func1(a, b)

ipdb> print(x)
1
ipdb> up
> <ipython-input-6-b2e110f6fc8f>(1)<module>()
----> 1 func2(1)

ipdb> down
> <ipython-input-1-d849e34d61fb>(7)func2()
      5     a = x      
      6     b = x - 1
----> 7     return func1(a, b)

ipdb> quit
```




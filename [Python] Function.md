# Python Function

- A function is an organized, reusable piece of code that implements a single or related function.
- Functions can improve the modularity of the application and the reuse rate of the code.



## Define a function

Define a function that does what you want, following simple rules:

- A function code block begins with the `def` keyword, followed by the function identifier name and parentheses ().
- Any incoming parameters and independent variables must be placed between parentheses, which can be used to define parameters.
- The first statement of the function can optionally use a docstring - used to store the function description.
- Function content begins with a colon : and is indented.
- return [expression] end the function, optionally return a value to the caller, return without expression is equivalent to returning None.



## Grammar

Python defines functions using the def keyword, and the general format is as follows:

```python
def function name(parameters):
    body
```

### Example

```python
#!/usr/bin/python3

def hello():
    print("Hello World!!")
    
hello()
```

```python
#!/usr/bin/python3
def max(a,b):
    if a > b:
        return a
    else:
        return b
    
a = input("a is ")
b = input("b is ")
print(max(a,b))
```

### Calculate the area function

```python
def areaa(width, height):
    return width * height

def print_welcome(name):
    print("Welcome", name)
    
print_welcome("lanyang")
w = 4
h = 5
print("width =",w,"hight =",h," area =",area(w,h))
```



## Function Call

Define a function: Give the function a name, specify the parameters contained in the function, and the code block structure. Once the basic structure of this function is complete, you can execute it through another function call, or directly from the Python command prompt. The following example calls the `printme()` function:

```python
#!/usr/bin/python3
def printme( str ):
    print(str)
    return

printme("I want to call function")
printme('call the same function again')
```



## Parameter Passing

```python
a = [1,2,3]
a = 'Lanyang'
```

In the above code, [1,2,3] is a List type, "Runoob" is a String type, and the variable a has no type, she is just a reference to an object (a pointer), which can point to a List type object, or It points to a String type object.



### Mutable and immutable objects

In python, strings, tuples, and numbers are immutable objects, while lists, dicts, etc. are modifiable objects.

- **Immutable type:** variable assignment a=5 and then assignment a=10, here is actually a newly generated int value object 10, and then let a point to it, and 5 is discarded, instead of changing the value of a, it is equivalent to newly generating a .
- **Variable type:** variable assignment la=[1,2,3,4] and then assignment la[2]=5 is to change the value of the third element of list la, la itself does not move, but only a part of its internal value was modified.

Parameter passing for python functions:

- **Immutable types:** C++-like value passing, such as integers, strings, tuples. For example, fun(a), only the value of a is passed, and the a object itself is not affected. If the value of a is modified inside fun(a), an object of a is newly generated.
- **Mutable types:** C++-like passing by reference, such as lists, dictionaries. Such as fun(la), it is to pass la to the past, and the la outside the fun will also be affected after modification

Everything in python is an object. Strictly speaking, we cannot say whether passing by value or passing by reference. We should say passing immutable objects and passing mutable objects.



### Pass immutable object instance

Use the id() function to view memory address changes:

```python
def change(a):
    print(id(a))
    a = 12
    print(id(a))

a=1
print(id(a))
change(a)
```

```python
2472141324528   
2472141324528   
2472141324880 
```



### Pass mutable object instance

The variable object modifies the parameters in the function, then in the function that calls this function, the original parameters are also changed. For example:

```python
def changeme(mylist):
    mylist.append([1,2,3,4])
    print("Value in the function: ", mylist)
    return

mylist = [10,20,30]
changeme(mylist)
print("Value is not in function: ", mylist)def changeme(mylist):
    mylist.append([1,2,3,4])
    print("Value in the function: ", mylist)
    return

mylist = [10,20,30]
changeme(mylist)
print("Value is not in function: ", mylist)
```

```python
[10, 20, 30, [1, 2, 3, 4]]
[10, 20, 30, [1, 2, 3, 4]]
```



## Parameter

The following are the official parameter types that can be used when calling a function:

- Required parameter
- Keyword parameter
- Default parameter
- Variable length parameter



### Required parameter

Required arguments must be passed to the function in the correct order. The number at call must be the same as at declaration. When calling the `printme()` function, you must pass in a parameter, otherwise a syntax error will occur:

```python
def printme( str ):
    print( str)
    return
printme()
```

```python
Traceback (most recent call last):
  File "test.py", line 10, in <module>
    printme()
TypeError: printme() missing 1 required positional argument: 'str'
```



### Keyword parameter

Keyword parameters are closely related to function calls, and function calls use keyword parameters to determine the incoming parameter values. Using keyword arguments allows the order of arguments to be different when the function is called than when it was declared, because the Python interpreter is able to match the argument values with the argument names. The following example uses parameter names when calling the function printme():

```python
def printme( str ):
    print( str )
    return

printme( str = "lanyang")
```

```python
lanyang
```

The following example demonstrates that the use of function parameters does not need to be specified in order:

```python
def printinfo(name, age):
    print('name: ', name)
    print('age: ', age)
    return

printinfo(age=50,name='lanyang')
```

```python
name:  lanyang
age:  50
```



### Default parameter

When using a function, if no parameters are passed, default parameters will be used. In the following example, if the age parameter is not passed in, the default value will be used:

```python
def printinfo(name, age=35):
    print('name: ', name)
    print('age: ', age)
    return

printinfo( age=50, name="lanyang" )
print ("------------------------")
printinfo( name="lanyang" )
```

```python
name: lanyang
age: 50
------------------------
name: lanyang
age: 35
```



### Variable length parameter

You may need a function that can handle more arguments than was originally declared. These parameters are called variable-length parameters. Unlike the above two types of parameters, they will not be named when they are declared. The basic syntax is as follows:

```python
def functionname([formal_args,] * var_args_tuple):
    function_suite
    return[expression]
```

Parameters with an asterisk * will be imported in the form of tuples, storing all unnamed variable parameters.

```python
def printinfo( arg1, *vartuple ):
    print('output: ')
    print(arge1)
    print(vartuple)
    
printinfo(70,60,50)
```

```python
output:
    70
    (60,50)
```



### Anonymous function

Python uses lambdas to create anonymous functions. The so-called anonymous means that a function is no longer defined in a standard form such as the def statement.

- `lambda` is just an expression, and the function body is much simpler than def.
- The body of a `lambda` is an expression, not a code block. Only limited logic can be encapsulated in lambda expressions.
- A `lambda` function has its own namespace and cannot access parameters outside its own parameter list or in the global namespace.
- Although it seems that the `lambda` function can only write one line, it is not equivalent to the inline function of C or C++. The purpose of the latter is to increase the operating efficiency by not occupying the stack memory when calling the small function.

```python
lambda [arg1 [,arg2,.....argn]]:expression
```



## Return statement

The `return` statement is used to exit a function, optionally returning an expression to the caller. A` return `statement with no parameter value returns None. None of the previous examples demonstrated how to return a value. The following example demonstrates the use of the `return` statement:

```python
def sum(rg1, arg2):
    totol = arg1 + arg2
    print('in function: ',total)
    return total

total = sum(10,20)
print('OUt function: ',total)
```

```python
in function:  30
Out function:  30
```



## Mandatory positional parameter

Python3.8 has added a new function parameter syntax / to indicate that the function parameter must use the specified position parameter, and cannot use the form of keyword parameter. In the following example, the parameters a and b must use specified positional parameters, c or d can be positional or keyword parameters, and e and f are required to be keyword parameters:

```python
def f(a, b, /, c, d, *, e, f):
    print(a, b, c, d, e, f)
```

The following usage is correct:

```python
f(10, 20, 30, d=40, e=50, f=60)
```








































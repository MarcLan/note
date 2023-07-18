# Python Namespace and Scope

## Namespace

### Definition

*A namespace is a mapping from names to objects. Most namespaces are currently implemented as Python dictionaries。*

- A namespace is a mapping from a name to an object, and most namespaces are implemented through Python dictionaries.
- Namespaces provide a way to avoid name conflicts in projects. Each namespace is independent and has no relationship, so a namespace cannot have duplicate names, but different namespaces can have duplicate names without any impact.



### There are generally three namespaces:

- **Built-in names**: Python language built-in names, such as function names `abs`, `char` and `exception` n `BaseException`,etc.
- **Global names**: The name defined in the module records the variables of the module, including functions, classes, other imported modules, module-level variables and constants.
- **Local names**: The name defined in the function records the variables of the function, including the parameters of the function and locally defined variables. (also defined in the class)

![image-20230717205711366](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230717205711366.png)



### Namespace lookup order:

Suppose we want to use the variable `lanyang`, then Python's search order is: local namespace -> global namespace -> built-in namespace. If the variable `lanyang` cannot be found, it will give up and raise a NameError:

```python
NameError: name 'lanyang' is not defined
```



### The life cycle of a namespace

The life cycle of a namespace depends on the scope of the object. If the object execution is completed, the life cycle of the namespace ends. Therefore, we cannot access objects of the inner namespace from the outer namespace.

```python
print('-----Namespace-----')
#var1 is global name
var1 = 5
def some_fuc():

    #var2 is local name
    var2 = 6
    def some_inner_func():

        # var3 is Embedded local name
        var3 = 7
```

As shown in the figure below, the same object name can exist in multiple namespaces

![image-20230717210424385](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230717210424385.png)



## Scope

> A scope is a textual region of a Python program where a namespace is directly accessible. "Directly accessible" here means that an unqualified reference to a name attempts to find the name in the namespace.

A scope is the textual area of a namespace that a Python program can directly access.

In a python program, directly accessing a variable will visit all scopes from inside to outside until it is found, otherwise an undefined error will be reported.

In Python, program variables are not accessible anywhere, and access rights depend on where the variable is assigned.

The scope of a variable determines which part of the program can access which particular variable name. There are four scopes in Python, namely:

There are four scopes:

- **L (Local)** : The innermost layer, containing local variables, such as inside a function/method.
- **E (Enclosing)** : Contains non-local (non-local) and non-global (non-global) variables. For example, two nested functions, a function (or class) A contains a function B, then for the name in B, the scope in A is nonlocal.
- **G (Global)** : The outermost layer of the current script, such as the global variable of the current module.
- **B (Built-in)** : Contains built-in variables/keywords, etc., and is finally searched.

Rule order: **L –> E –> G –> B** .

If you can’t find it locally, you will find it locally (such as closures), and if you can’t find it again, you will find it globally, and then you will find it in the built-in.

```python
print('-----Scope-----')
g_count = 0 # globe scope
def outer():
    o_count = 1 # In a function outside the closure function
    def inner():
        i_count = 2 # local scope
```

The built-in scope is implemented through a standard module called builtin, but the variable name itself is not put into the built-in scope, so this file must be imported to be able to use it. In Python 3.0, you can use the following code to see which variables are predefined:

```py
>>> import builtins
>>> dir(builtins)
```

In Python, only modules, classes, and functions (def, lambda) introduce new scopes, and other code blocks (such as if/elif/else/, try/except, for/while, etc.) are No new scope will be introduced, that is to say, the variables defined in these statements can also be accessed externally, as in the following code:

```py
>>> if True:
...  msg = 'I am from Runoob'
... 
>>> msg
'I am from Runoob'
>>> 
```

The msg variable in the instance is defined in the if statement block, but it can still be accessed from the outside. If msg is defined in a function, it is a local variable and cannot be accessed externally:

```PY
>>> def test():
...     msg_inner = 'I am from Runoob'
... 
>>> msg_inner
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'msg_inner' is not defined
>>> 
```

From the error message, it shows that msg_inner is undefined and cannot be used because it is a local variable and can only be used within the function.



### Global and local variables

Variables defined inside a function have a local scope, and variables defined outside a function have a global scope. Local variables can only be accessed within the function in which they are declared, while global variables can be accessed throughout the program. When a function is called, all variable names declared within the function will be added to the scope. Examples are as follows:

```PY
#!/usr/bin/python3
 
total = 0 # This is a global variable
def sum( arg1, arg2 ):

    total = arg1 + arg2 # total is local variable
    print ("The local variable in method: ", total)
    return total
 
# call sum()
sum( 10, 20 )
print ("The global variable out of method: ", total)
```



### global and nonlocal keywords

When the inner scope wants to modify variables in the outer scope, the global and nonlocal keywords are used.

```py
num = 1
def fun1():
    global num
    print(num)
    num = 123
    print(num)
fun1()
print(num)
```

```py
1
123
123
```

If you want to modify variables in the nested scope (enclosing scope, outer non-global scope), you need the nonlocal keyword, as shown in the following example:

```py
print('-----nonlocal-----')
def outer():
    num = 10
    def inner():
        nonlocal num # define nonlocal
        num = 100
        print(num)
    inner()
    print(num)
outer()
```

```python
100
100
```

 In addition, as a special case, suppose the following code is run:

```python
a = 10
def test():
    a = a + 1
    print(a)
test()
```

```PY
Traceback (most recent call last):
  File "test.py", line 7, in <module>
    test()
  File "test.py", line 5, in test
    a = a + 1
UnboundLocalError: local variable 'a' referenced before assignment
```

The error message is a local scope reference error, because a in the test function uses a local, undefined, and cannot be modified. Modify a to be a global variable:

```python
#!/usr/bin/python3
 
a = 10
def test():
    global a
    a = a + 1
    print(a)
test()
```

```py
11
```

It can also be passed as a function parameter:

```py
#!/usr/bin/python3
 
a = 10
def test(a):
    a = a + 1
    print(a)
test(a)
```




















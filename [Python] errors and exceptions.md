# Python Errors and Exceptions

As a Python beginner, when you first learn Python programming, you often see some error messages, which we did not mention before, and we will introduce them in this chapter.

There are two types of errors in Python that are easily recognizable: syntax errors and exceptions.

Python assert (assertion) is used to judge an expression and trigger an exception when the expression condition is false.

![img](https://static.runoob.com/images/mix/assets-py.webp)

## Grammatical errors

Python grammatical errors or parsing errors are often encountered by beginners, as shown in the following example

```python
>>> while True print('Hello world')
  File "<stdin>", line 1, in ?
    while True print('Hello world')
                   ^
SyntaxError: invalid syntax
```

In this example, the function print() is checked for an error because it is missing a colon **:** in front of it .

The parser points out the wrong line and marks a small arrow at the location of the first error found.

## abnormal

Even if the syntax of a Python program is correct, errors may occur when running it. Errors detected at runtime are called exceptions.

Most exceptions will not be handled by the program, and are displayed here in the form of error messages:

## example

```python
>>> 10 * (1/0)             # 0 cannot be used as a divisor, triggering an exception
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ZeroDivisionError: division by zero
>>> 4 + spam*3             # spam is not defined, trigger exception
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'spam' is not defined
>>> '2' + 2               # int cannot be added to str, triggering an exception
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

Exceptions occur in different types, which are all printed as part of the message: in the example types are ZeroDivisionError, NameError and TypeError.

The front part of the error message shows the context where the exception occurred, and the specific information is displayed in the form of a call stack.

## exception handling

### try/except

Exception capture can use **try/except** statement.

![img](https://www.runoob.com/wp-content/uploads/2019/07/try_except.png)

In the following example, let the user enter a legal integer, but allow the user to interrupt the program (using Control-C or the method provided by the operating system). User interrupted information will raise a KeyboardInterrupt exception.

```PY
while True:
    try:
        x = int(input("请输入一个数字: "))
        break
    except ValueError:
        print("您输入的不是数字，请再次尝试输入！")
```

The try statement works as follows;

- First, the try clause (the statement between the keyword try and the keyword except) is executed.
- If no exception occurs, ignore the except clause, and end after the try clause is executed.
- If an exception occurs during the execution of the try clause, the rest of the try clause is ignored. If the exception type matches the name after except, then the corresponding except clause will be executed.
- If an exception does not match any except, then the exception will be passed to the upper try.

A try statement may contain multiple except clauses to handle different specific exceptions. At most one branch will be executed.

The handler will only handle exceptions in the corresponding try clause, not exceptions in other try's handlers.

An except clause can handle multiple exceptions at the same time, and these exceptions will be placed in a parenthesis as a tuple, for example:

```PY
except (RuntimeError, TypeError, NameError):
    pass
```

The last except clause can omit the name of the exception, it will be used as a wildcard. You can use this method to print an error message and then throw the exception again.

```PY
import sys

try:
    f = open('myfile.txt')
    s = f.readline()
    i = int(s.strip())
except OSError as err:
    print("OS error: {0}".format(err))
except ValueError:
    print("Could not convert data to an integer.")
except:
    print("Unexpected error:", sys.exc_info()[0])
    raise
```



### try/except...else

**The try/except** statement also has an optional **else** clause. If this clause is used, it must be placed after all except clauses.

The else clause will be executed if no exception occurs in the try clause.

![img](https://www.runoob.com/wp-content/uploads/2019/07/try_except_else.png)

The following example judges whether the file can be opened in the try statement. If there is no exception when opening the file, execute the statement in the else part to read the file content:

```PY
for arg in sys.argv[1:]:
    try:
        f = open(arg, 'r')
    except IOError:
        print('cannot open', arg)
    else:
        print(arg, 'has', len(f.readlines()), 'lines')
        f.close()
```

Using the else clause is better than putting all the statements in the try clause, so as to avoid some unexpected exceptions that cannot be caught by except.

Exception handling not only handles exceptions that occur directly in the try clause, but also handles exceptions thrown in functions called in the clause (even indirectly called functions). For example:

```PY
>>> def this_fails():
        x = 1/0
   
>>> try:
        this_fails()
    except ZeroDivisionError as err:
        print('Handling run-time error:', err)
   
Handling run-time error: int division or modulo by zero
```



### try-finally statement

The try-finally statement executes the final code whether or not an exception occurs.

![img](https://www.runoob.com/wp-content/uploads/2019/07/try_except_else_finally.png)

The finally statement in the following example is executed regardless of whether an exception occurs:

## example

```PY
try:
    runoob()
except AssertionError as error:
    print(error)
else:
    try:
        with open('file.log') as file:
            read_data = file.read()
    except FileNotFoundError as fnf_error:
        print(fnf_error)
finally:
    print('This sentence will be executed regardless of whether an exception occurs.')
```



------

## Throw an exception

Python uses the raise statement to raise a specified exception.

The syntax format of raise is as follows:

```
raise [ Exception [, args [, traceback ]]]  
```

![img](https://www.runoob.com/wp-content/uploads/2019/07/raise.png)

The following example triggers an exception if x is greater than 5:

```PY
x = 10
**if** x > 5 :
  **raise** Exception ( 'x cannot be greater than 5. The value of x is: {}' . format ( x ) )
```

Executing the above code will trigger an exception:

```PY
Traceback ( most recent call last ): File "test.py" , line 3 , in <module> raise Exception ( 'x cannot be greater than 5. The value of x is: {}' . format ( x )) Exception : x cannot be greater than 5 . The value of x is: 10 
```

The only parameter to raise specifies the exception to be thrown. It must be an instance of an exception or an exception class (that is, a subclass of Exception).

If you just want to know if this threw an exception, and don't want to handle it, then a simple raise statement can raise it again.

```PY
>>> try:
        raise NameError('HiThere')  # 模拟一个异常。
    except NameError:
        print('An exception flew by!')
        raise
   
An exception flew by!
Traceback (most recent call last):
  File "<stdin>", line 2, in ?
NameError: HiThere
```



------

## user-defined exception

You can have your own exceptions by creating a new exception class. The exception class inherits from the Exception class and can be inherited directly or indirectly, for example:

```PY
>>> class MyError(Exception):
        def __init__(self, value):
            self.value = value
        def __str__(self):
            return repr(self.value)
   
>>> try:
        raise MyError(2*2)
    except MyError as e:
        print('My exception occurred, value:', e.value)
   
My exception occurred, value: 4
>>> raise MyError('oops!')
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
__main__.MyError: 'oops!'
```

In this example, the default __init__() of class Exception is overridden.

When creating a module that has the potential to throw many different exceptions, a common practice is to create a base exception class for the package, and then create different subclasses for different error conditions based on this base class:

```PY
class Error(Exception):
    """Base class for exceptions in this module."""
    pass

class InputError(Error):
    """Exception raised for errors in the input.

    Attributes:
        expression -- input expression in which the error occurred
        message -- explanation of the error
    """

    def __init__(self, expression, message):
        self.expression = expression
        self.message = message

class TransitionError(Error):
    """Raised when an operation attempts a state transition that's not
    allowed.

    Attributes:
        previous -- state at beginning of transition
        next -- attempted new state
        message -- explanation of why the specific transition is not allowed
    """

    def __init__(self, previous, next, message):
        self.previous = previous
        self.next = next
        self.message = message
```

Most exception names end with "Error", just like the standard exception names.

------

## Define cleanup behavior

The try statement has another optional clause, which defines the cleanup behavior to be performed no matter what the circumstances. For example:

```PY
>>> try:
...     raise KeyboardInterrupt
... finally:
...     print('Goodbye, world!')
... 
Goodbye, world!
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
KeyboardInterrupt
```

In the above example, regardless of whether there is an exception in the try clause, the finally clause will be executed.

If an exception is thrown in the try clause (or in the except and else clauses), and there is no except to catch it, then the exception will be thrown after the finally clause is executed.

Here's a more complex example (except and finally clauses in the same try statement):

```PY
>>> def divide(x, y):
        try:
            result = x / y
        except ZeroDivisionError:
            print("division by zero!")
        else:
            print("result is", result)
        finally:
            print("executing finally clause")
   
>>> divide(2, 1)
result is 2.0
executing finally clause
>>> divide(2, 0)
division by zero!
executing finally clause
>>> divide("2", "1")
executing finally clause
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "<stdin>", line 3, in divide
TypeError: unsupported operand type(s) for /: 'str' and 'str'
```



------

## Predefined Cleanup Behavior

Some objects define a standard cleanup behavior that will be performed once it is no longer needed, regardless of whether the system successfully uses it.

The following example shows an attempt to open a file and print the contents to the screen:

```PY
for line in open("myfile.txt"):
    print(line, end="")
```

The problem with the above code is that when execution is complete, the file remains open and is not closed.

The keyword with statement can ensure that objects such as files will correctly execute his cleanup method after use:

```PY
with open("myfile.txt") as f:
    for line in f:
        print(line, end="")
```

After the above code is executed, even if something goes wrong during processing, the file f will always be closed.

More with keyword content reference: [Python with keyword](https://www.runoob.com/python3/python-with.html)

------

## related information

[Python assert (assertion)](https://www.runoob.com/python3/python3-assert.html)

[Python with keyword](https://www.runoob.com/python3/python-with.html)
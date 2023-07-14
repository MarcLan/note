# Python3 module

In the previous chapters, we basically used the python interpreter to program. If you exit and enter from the Python interpreter, all the methods and variables you defined will disappear.

To this end, Python provides a way to store these definitions in files for use by some scripts or interactive interpreter instances. This file is called a module.

A module is a file with a .py extension that contains all the functions and variables you define. A module can be imported by other programs to use functions and other functions in the module. This is also the way to use the python standard library.

Below is an example using modules from the python standard library.

## Example (Python 3.0+)

\#!/usr/bin/python3 # File name: using_sys.py import sys print ( ' The command line parameters are as follows: ' ) for i in sys . argv :    print ( i ) print ( ' \n \n Python path is: ' , sys . path , ' \n ' )         

The execution result is as follows:

```python
$ python using_sys .py
 parameter 1 parameter 2 The command line parameters are as follows : 
using_sys .py parameter 1 parameter 2 




The Python path is: [ '/root' , '/usr/lib/python3.4' , '/usr/lib/python3.4/plat-x86_64-linux-gnu' , '/usr/lib/python3.4/ lib-dynload' , '/usr/local/lib/python3.4/dist-packages' , '/usr/lib/python3/dist-packages' ]        
```

- 1. import sys imports the sys.py module in the python standard library; this is the way to import a certain module.
- 2. sys.argv is a list containing command line parameters.
- 3. sys.path contains a list of paths where the Python interpreter automatically finds the required modules.

------

## import statement

To use a Python source file, just execute the import statement in another source file, the syntax is as follows:

```python
import module1 [, module2 [,... moduleN ]
```

When the interpreter encounters an import statement, the module is imported if it is in the current search path.

The search path is a list of all directories that the interpreter will search first. If you want to import the module support, you need to put the command at the top of the script:

## support.py file code

\#!/usr/bin/python3 # Filename: support.py def print_func ( par ) :     print ( " Hello : " , par ) return          

test.py introduces the support module:

## test.py file code

\#!/usr/bin/python3 # Filename: test.py # Import module import support # Now you can call the functions contained in the module support . print_func ( " Runoob " )     

The output of the above example:

```python
$ python3 test 
 .py Hello : Runoob   
```

[download code](https://static.runoob.com/download/runoob-python-module-test.zip)

A module is only imported once, no matter how many times you **import it** . This prevents imported modules from being executed over and over again.

When we use the import statement, how does the Python interpreter find the corresponding file?

This involves Python's search path, which is composed of a series of directory names, and the Python interpreter searches for imported modules from these directories in turn.

This looks a lot like environment variables, in fact, you can also determine the search path by defining environment variables.

The search path is determined when Python is compiled or installed, and it should be modified when new libraries are installed. The search path is stored in the path variable in the sys module. To do a simple experiment, in the interactive interpreter, enter the following code:

```python
>>> import sys
 >>> sys .path [ '' , '/usr/lib/python3.4' , '/usr/lib/python3.4/plat-x86_64-linux-gnu' , '/usr/ lib
 /python3.4/lib-dynload' , '/usr/local/lib/python3.4/dist-packages' , '/usr/lib/python3/dist-packages' ] >>>      
 
```

The output of sys.path is a list, the first item of which is an empty string '', which represents the current directory (if it is printed from a script, you can see which directory is more clearly), that is, we execute the python interpreter Directory (for scripts, the directory where the running script is located).

Therefore, if there is a file with the same name as the module to be imported in the current directory like me, the module to be imported will be blocked.

After understanding the concept of the search path, you can modify sys.path in the script to introduce some modules that are not in the search path.

Now, create a fibo.py file in the current directory of the interpreter or a directory in sys.path, the code is as follows:

## example

\# Fibonacci (fibonacci) sequence module def fib ( n ) :     # Define the Fibonacci sequence up to n a , b = 0 , 1 while b < n :         print ( b , end = ' ' ) a , b = b , a + b print ( ) def fib2 ( n ) : # return to the Fibonacci sequence of n result = [ ] a ,                                  b = 0 , 1 while b < n :         result . append ( b ) a , b = b , a + b return result                  

Then enter the Python interpreter and import this module with the following command:

```
>>> import fibo 
```

This does not write the names of the functions directly defined in fibo into the current symbol table, but just writes the name of the module fibo there.

Functions can be accessed using the module name:

## example

\>>> fibo . fib ( 1000 ) 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987  >>> fibo . fib2 ( 100 ) [ 1 , 1 , 2 , 3 , 5 , 8 , 13 , 21 , 34 , 55 , 89 ]  >>> fibo .                __name__ ' fibo '

If you plan to use a function frequently, you can assign it a local name:

```python
>>> fib = fibo . fib
 >>> fib ( 500 ) 1 1 2 3 5 8 13 21 34 55 89 144 233 377
             
```

------

## from ... import statement

Python's from statement allows you to import a specified part from a module into the current namespace. The syntax is as follows:

```python
from modname import name1 [, name2 [, ... nameN ]] 
```

For example, to import the fib function of module fibo, use the following statement:

```python
>>> from fibo import fib , fib2
 >>> fib ( 500 ) 1 1 2 3 5 8 13 21 34 55 89 144 233 377 
             
```

This statement does not import the entire fibo module into the current namespace, it only imports the fib function in fibo.

------

## from ... import * statement

It is also possible to import all the contents of a module into the current namespace, just use the following declaration:

```python
from modname import * 
```

This provides an easy way to import all projects in a module. However, this statement should not be used too much.

------

## in-depth module

In addition to method definitions, modules can also contain executable code. These codes are generally used to initialize the module. These codes are only executed the first time they are imported.

Each module has its own independent symbol table, which is used as a global symbol table for all functions inside the module.

Therefore, the author of the module can safely and boldly use these global variables inside the module without worrying about confusing the global variables of other users.

On the other hand, when you really know what you are doing, you can also access functions in modules through the modname.itemname notation.

Modules can import other modules. Use import at the top of a module (or script, or elsewhere) to import a module. Of course, this is just a convention, not mandatory. The name of the imported module will be placed in the symbol table of the currently operating module.

There is also an import method, you can use import to directly import the names (functions, variables) in the module to the current operation module. for example:

```python
>>> from fibo import fib , fib2
 >>> fib ( 500 ) 1 1 2 3 5 8 13 21 34 55 89 144 233 377 
             
```

This method of importing does not put the name of the imported module in the current glyph (so in this example, the name fibo is undefined).

Here is another way to import all (functions, variables) names in a module into the character table of the current module at once:

```python
>>> from fibo import * >>> fib ( 500 ) 1 1 2 3 5 8 13 21 34 55 89 144 233 377  

             
```

This will import all names, except those starting with a single underscore (_). In most cases, Python programmers do not use this method, because the introduction of naming from other sources is likely to override the existing definition.

------

## __name__ attribute

The first time a module is imported by another program, its main program will run. If we want a block in a module not to be executed when the module is imported, we can use the __name__ attribute to make that block only execute when the module itself is running.

```python
#!/usr/bin/python3 # Filename: using_name.py


if __name__ == '__main__' : print ( 'The program itself is running' ) else : print ( 'I am from another module' ) 
   

   
```

The output of the operation is as follows:

```python
$ python using_name .py
 program itself is running
$ python
 >>> import using_name
 i from another module >>> 
```

**Explanation:** Each module has a __name__ attribute. When its value is '__main__', it indicates that the module itself is running, otherwise it is imported.

Explanation: **__name__** and **__main__** are double underscores, and **_ _** removes the space in the middle.

------

## dir() function

The built-in function dir() finds all names defined within a module. Returned as a list of strings:

```python
>>> import fibo , sys
 >>> dir ( fibo ) [ '__name__' , 'fib' , 'fib2' ] >>> dir ( sys ) [ '__displayhook__' , '__doc__' , '__excepthook__' , '__loader__' , '__name__' , '__package__' , '__stderr__' , '__stdin__' , '__stdout__' , '_clear_type_cache' ,'_current_frames' , '_debugmallocstats' 
  
  
    
    
   , '_getframe' , '_home' , '_mercurial' , '_xoptions' , 'abiflags' , 'api_version' , 'argv' , 'base_exec_prefix' , 'base_prefix' , 'builtin_module_names' , 'byteorder' , 'call_tracing' , ' callstats' , 'copyright' , 'displayhook' , 'dont_write_bytecode' , 'exc_info' , 'excepthook' ,'exec_prefix' , 'executable' , 'exit' , 'flags' 
      
    
    
    
   , 'float_info' , 'float_repr_style' , 'getcheckinterval' , 'getdefaultencoding' , 'getdlopenflags' , 'getfilesystemencoding' , 'getobjects' , 'getprofile' , 'getrecursionlimit' , 'getrefcount' , 'getsizeof' , 'getswitchinterval' , ' gettotalrefcount' , 'gettrace' , 'hash_info' , 'hexversion' , 'implementation' ,'int_info' , 'intern' , 'maxsize' ,  
   
    
    
     
   'maxunicode' , 'meta_path' , 'modules' , 'path' , 'path_hooks' , 'path_importer_cache' , 'platform' , 'prefix' , 'ps1' , 'setcheckinterval' , 'setdlopenflags' , ' setprofile ' , 'setrecursionlimit ' , 'setswitchinterval' , 'settrace' , 'stderr' , 'stdin' , 'stdout' , 'thread_info' ,'version' , 'version_info' , 'warnoptions' ]   
     
    
     
    
```

If no arguments are given, the dir() function will list all names currently defined:

```python
>>> a = [ 1 , 2 , 3 , 4 , 5 ] >>> import fibo
 >>> fib = fibo . fib
 >>> dir () # Get a list of attributes defined in the current module [ '__builtins__' , '__name__' , 'a' , 'fib' , 'fibo' ,'sys' ] >>> a = 5 # create a new variable 'a' >>> dir () [ '__builtins__' ,     
  
     
  

 '__doc__' , '__name__' , 'a' , 'sys' ] >>> >>> del a # delete variable name a >>> >>> dir () [ '__builtins__' , '__doc__' , '__name__' , 'sys' ] >>>   

 


   
```

------

## standard module

Python itself comes with some standard module libraries, which will be introduced in the Python library reference document (that is, the "library reference document" below).

Some modules are directly built into the parser. Although these are not built-in functions of some languages, they can be used very efficiently, and even system-level calls are no problem.

These components will be configured in different forms according to different operating systems. For example, the winreg module will only be provided for Windows systems.

It should be noted that there is a special module sys which is built into every Python parser. The variables sys.ps1 and sys.ps2 define the strings corresponding to the primary and secondary prompts:

```python
>>> import sys
 >>> sys . ps1
 '>>> ' >>> sys . ps2
 '... ' >>> sys . ps1 = 'C> ' 
C > print ( 'Runoob!' ) Runoob ! 
C > 

  
 
```

------

## Bag

Packages are a form of managing Python module namespaces, using "dotted module names".

For example, the name of a module is AB, then it represents a submodule B in a package A.

Just like when using modules, you don't have to worry about the mutual influence of global variables between different modules, and you don't have to worry about the duplication of module names between different libraries when you use the form of dot module names.

This way different authors can contribute NumPy modules, or Python graphics libraries.

Let's say you want to design a set of modules (or call it a "package") that handles sound files and data uniformly.

There are many different audio file formats (basically distinguished by suffixes, such as: .wav, :file:.aiff, :file:.au,), so you need to have a growing set of modules for Convert between different formats.

And for these audio data, there are many different operations (such as mixing, adding echo, adding equalizer function, creating artificial stereo effect), so you also need a set of modules that can't be written to handle these operations.

Here is a possible package structure (in a hierarchical filesystem):

```python
sound / top - level package 
      __init__.py initializes sound package 
      formats / file format conversion sub                - package 
              __init__.py                                            
              wavread.py _ _
              wavwrite.py _ _
              aiffread.py _ _
              aiffwrite.py _ _
              auread.py _ _
              auwrite.py ...
               
      effects / sound effects subpackage 
              __init__.py _ _                  
              echo.py _ _
              surround.py _ _
              reverse.py ... 
      filters /                   filters subpackage 
              __init__.py _ _
               _ _
              equalizer.py _ _
              vocoder.py _ _
              karaoke.py ... _ _
              
```

When importing a package, Python will look for the subdirectories contained in the package according to the directories in sys.path.

A directory is only considered a package if it contains a file named __init__.py, mainly to avoid abusive names (such as strings) from inadvertently affecting valid modules on the search path.

In the simplest case, just put an empty :file:__init__.py. Of course, this file can also contain some initialization code or assign values to the __all__ variable (described later).

Users can only import specific modules in one package at a time, for example:

```PY
import sound . effects . echo
```

This will import the submodule: sound.effects.echo. He must use his full name to access:

```PY
sound . effects . echo . echofilter ( input , output , delay = 0.7 , atten = 4 )
```

Another way to import submodules is:

```py
from sound . effects import echo
```

This also imports submodules: echo, and it doesn't need those verbose prefixes, so it can be used like this:

```py
echo . echofilter ( input , output , delay = 0.7 , atten = 4 )
```

Another variation is to import a function or variable directly:

```py
from sound . effects . echo import echofilter
```

Similarly, this method will import the submodule: echo, and can use his echofilter() function directly:

```py
echofilter ( input , output , delay = 0.7 , atten = 4 )
```

Note that when using the form of **from package import item** , the corresponding item can be a submodule (subpackage) in the package, or other names defined in the package, such as functions, classes or variables.

The import syntax will first treat item as the name of a package definition, and if not found, try to import it as a module. If not found yet, raise an **:exc:ImportError** exception.

On the contrary, if you use the import form such as **import item.subitem.subsubitem** , except the last item, it must be a package, and the last item can be a module or a package, but it cannot be the name of a class, function or variable .

------

## import * from a package

What happens if we use **from sound.effects import \* ?**

Python will go to the file system, find all the submodules in this package, and import them one by one.

But this method does not work very well on the Windows platform, because Windows is a case-insensitive system.

On the Windows platform, we cannot determine whether a file called ECHO.py imports as a module echo or Echo, or ECHO.

To fix this, we just need to provide an index of an exact package.

The import statement follows the following rules: If there is a list variable called **__all__ in the package definition file** **__init__.py** , then all the names in this list are imported as the package content when using **from package import \* .**



**As the author of the package, don't forget to ensure that __all__** is also updated after updating the package .

The following example contains the following code in file:sounds/effects/__init__.py:



```py
__all__ = [ "echo" , "surround" , "reverse" ]   
```

This means that when you use from sound.effects import *, you will only import these three submodules in the package.

If **__all__** is really not defined, then using the syntax **from sound.effects import \* will not import any submodules in the package sound.effects.** It just imports the package sound.effects and everything defined in it (possibly running initialization code defined in __init__.py).

This will import all names defined in __init__.py. And it won't destroy all explicitly named modules we imported before this sentence. Take a look at this part of the code:

```py
import sound . effects . echo
 import sound . effects . surround
 from sound . effects import * 
```

In this example, before executing from...import, the echo and surround modules in the package sound.effects are imported into the current namespace. (Of course, it would be even better if __all__ is defined)

Usually we don't advocate using ***** this method to import modules, because this method often leads to less readable code. But this can indeed save a lot of keystrokes, and some modules are designed so that they can only be imported through specific methods.

Remember, it is never wrong to use **from Package import specific_submodule this way.** In fact, this is the recommended method as well. Unless the submodule you want to import may have the same name as the submodule of other packages.

If the package is a subpackage in the structure (such as the package sound in this example), and you want to import sibling packages (packages at the same level) you have to use the import path to import. For example, if the module sound.filters.vocoder is to use the module echo in the package sound.effects, you would write from sound.effects import echo.

```py
from . import echo
 from .. import formats
 from .. filters import equalizer     
```

Both implicit and explicit relative imports start from the current module. The name of the main module is always "__main__", and the main module of a Python application should always be referenced using an absolute path.

Packages also provide an additional attribute __path__. This is a list of directories, and each included directory has an __init__.py that serves this package. You have to define it before other __init__.py are executed. This variable can be modified to affect modules and subpackages contained in the package.

This function is not commonly used, and is generally used to extend the modules in the package.
# Python Interpreter

On Linux/Unix systems, the default python version is generally 2.x, and we can install python3.x in the `/usr/local/python3` directory. After the installation is complete, we can add the path `/usr/local/python3/bin `to the environment variables of your Linux/Unix operating system, so that you can enter the following command through the shell terminal to start Python3.

```python
$ PATH=$PATH:/usr/local/python3/bin/python3    # 设置环境变量
$ python3 --version
Python 3.4.0
```

In the Windows system, you can use the following commands to set Python environment variables, assuming your Python is installed under `C:\Python34`:



## Interactive Programming

```python
set path=%path%;C:\python34
```

After executing the above command, the following window information appears:

```python
$ python3
Python 3.4.0 (default, Apr 11 2014, 13:05:11) 
[GCC 4.8.2] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

Enter the following statement at the python prompt and press Enter to see the effect:

```python
Hello, Python!
```

Continuation lines are required when entering a multi-line structure. We can look at the following if statement:

```python
>>> flag = True
>>> if flag :
...     print("flag condition is True!")
... 
flag condition is True!
```

## Scripting

Copy the following code into the hello.py file:

```python
print ("Hello, Python!");
```

Execute the script with the following command:

```python
python3 hello.py
```

The output is:

```python
Hello, Python!
```

On Linux/Unix systems, you can add the following command at the top of the script to make the Python script directly executable like a SHELL script:

```shell
#! /usr/bin/env python3
```

Then modify the script permission to have execution permission, the command is as follows:

```shell
 chmod +x hello.py
```

Execute the following command:

```shell
./hello.py
```

The output is:

```shell
Hello, Python!
```







## 
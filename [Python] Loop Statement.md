# Python Loop Statement

## While

The general form of a while statement in Python:

```python
while (condition)：
    (statements)……
```

The following example uses while to calculate the sum from 1 to 100:

```python
n = 100
sum = 0
counter = 1

while counter <= n:
    sum = sum + counter
    counter += 1

print('1 - 100:', (n,sum))
```



### Infinite loop

```python
var = 1
while var == 1:
    num = int(input("enter number: "))
    print("enter number is: ", num)

print("good  bye!")
```

> You can use CTRL+C to exit the current infinite loop. Infinite loops are useful for real-time client requests on the server.



### While loop using else statement

The statement(s) block of expr is executed if the conditional statement is true, and additional_statement(s) if false. Loop out the numbers and judge the size:

```python
count = 0
while count < 5:
    count += 1
    print(count, "< 5")
else:
    print(count, " >= 5")
```

```python
1 < 5
2 < 5
3 < 5
4 < 5
5 < 5
5  >= 5
```



## For

A Python for loop can iterate over any iterable object, such as a list or a string. The general format of a for loop is as follows:

```python
for <variable> in <sequence>:
    <statements>
else:
    <statements>
```

```python
sites = ["aa","bb",'cc','dd']
for aaa in sites:
    print(aaa)
```

Can also be used to print each character in a string:

```python
word = 'lanyang'
for letter in word:
    print(letter)
```

Integer range values can be used with the range() function:

```python
for number in range(1, 6):
    print(number)
```



## for...else

In Python, the for...else statement is used to execute a block of code after the loop ends. The syntax format is as follows:

```python
for x in range(6):
    print(x)
else:
    print("finally finised!")
```

The break statement is used in the following for example, the break statement is used to jump out of the current loop body, and the else clause will not be executed:

```python
names = ['baidu','google','jingdong','taobao']
for name in names:
    if name == "jingdong":
        print("it's jd")
        break
    print("data" + name)
else:
    print("no data!")
print("loop complete!")
```



## range() 

To iterate over a sequence of numbers, you can use the built-in `range()` function. It generates arrays such as:

```python
for i in range(5)
	print(i)
```

Use `range()` to specify a range of values:

```python
for i in range(5,9):
    print(i)
```

Make range() start with a specified number and specify a different increment (it can even be negative, sometimes this is called a 'step size'):

```python
for i in range(0,10,3):
    print(i)
```

negative number:

```python
for i in range(-10,-100,-30):
    print(i)
```

range() and len() functions to iterate over the indices of a sequence, as follows:

```python
a = ['Google','Baidu','lanyang','taobao']
for i in range(len(a)):
    print(i,a[i])
```

Use the range() function to create a list:

```python
list(range(5))
[0,1,2,3,4]
```

More about the range() function usage reference: https://www.runoob.com/python3/python3-func-range.html



## `break` and `continue` statements and else clauses in loops

- The `break` statement can jump out of the loop body of for and while. If you terminate from a for or while loop, any corresponding loop else blocks will not execute.

- The `continue` statement is used to tell Python to skip the remaining statements in the current loop block and continue to the next loop.

```python
n = 5
while n > 0:
    n -= 1
    if n == 2:
    	break
    print(n)
print('loop end!')
```

```shell
4
3
loop end!
```

Use continue in while:

```python
for letter in 'lanyang':
    if letter == 'n':
        break
    print('leter is: ',letter)
    
var = 10
while var > 0:
    print('value is: ',var)
    var -= 1
    if var == 5:
        break
    print(var)
print('end!')
```

A loop statement can have an `else` clause, which is executed when the list is exhausted (in a for loop) or when a condition becomes false (in a while loop) causing the loop to terminate, but not when the loop is terminated by a `break`. The following example is used to query the cycle example of prime number:

```python
for n in range(2,10):
    for x in range(2,n):
        if n%x == 0:
            print(n,'=',x,'*',n//x)
            break
    else:
        print(n,'its odd')
```



## Pass

Python pass is an empty statement, in order to maintain the integrity of the program structure. pass does not do anything, it is generally used as a placeholder statement, as shown in the following example

```python
while True:
    pass
```



Minimal class:

```python
class MyEmptyClass
	pass
```



The following example executes the pass statement block when the letter is o:

```python
for letter in 'lanyang':
    if letter == 'a':
        pass
        print('do pass')
    print('current letter is: ', letter)
print('end!')
```


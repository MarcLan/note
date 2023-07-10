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
sites = ['aaa','bbb','ccc','ddd']
for site in sites:
    print("ok")
    break
print("data" + site)
    
```


















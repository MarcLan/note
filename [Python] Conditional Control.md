# Python Conditional Control

A Python conditional statement is a block of code that is determined by the execution result (True or False) of one or more statements.



## if statement

The general form of an if statement in Python is as follows:

```python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```

- If "condition_1" is True the "statement_block_1" block statement will be executed
- If "condition_1" is False, "condition_2" will be evaluated
- If "condition_2" is True the "statement_block_2" block statement will be executed
- If "condition_2" is False, the "statement_block_3" block statement will be executed

In Python, elif is used instead of else if, so the keywords of the if statement are: if – elif – else.

### Notice

- A colon : is used after each condition, indicating that the following is a block of statements to be executed after the condition is met.

- Use indentation to divide statement blocks, and statements with the same indentation number form a statement block together.
- There is no switch...case statement in Python, but match...case is added in Python3.10 version, and the function is similar

### Example

```python
#!/usr/bin/python3

var1 = 100
if var1:
    print('1 - if is true')
    print(var1)
    
var2 = 0
if var2:
    print("2 - if is true")
    print(var2)
print("Good bye!")
```

> From the result, we can see that because the variable var2 is 0, the statement in the corresponding if is not executed.



**The following example demonstrates the dog's age calculation judgment:**

```python
age = int(input("Dog's age"))
print("")
if age <= 0:
    print("No way")
elif age == 1:
    print("Equals to 14 years old man")
elif age == 2:
    print("Equals to 22 years old man")
elif age > 2:
    human = 22 + (age -2) * 5
    print("human age", human)
```



**The following are commonly used operation operators in if:**

| operator | describe                                      |
| :------- | :-------------------------------------------- |
| `<`      | less than                                     |
| `<=`     | less than or equal to                         |
| `>`      | more than the                                 |
| `>=`     | greater than or equal to                      |
| `==`     | equals, compares whether two values are equal |
| `!=`     | not equal to                                  |

```python

print(5 == 6)

x = 5
y = 8
print(x == y)
```

```python
False
False
```



**Demonstrates comparison operations for numbers:**

```python
number = 7
guess = -1
print("game!")
while guess != number:
    guess = int(input("enter number"))
    if guess == number:
        print("good")
    elif guess < number:
        print("smaller")
    elif guess > number:
        print("bigger")
```



## if nested

In nested if statements, you can place an if...elif...else structure inside another if...elif...else structure.

```python
num = int(input("enter number"))
if num % 2 == 0:
    if num % 3 == 0:
        print("2 & 3")
    else:
        print("2 but 3")
else:
    if num % 3 == 0:
        print("3 but 2")
    else:
        print("no 2 3")
```



## match...case

Python 3.10 adds the conditional judgment of match...case, so there is no need to use a series of if-else to judge. The object after the match will be matched with the content after the case in turn. If the match is successful, the matched expression will be executed, otherwise it will be skipped directly. _ can match everything. The syntax format is as follows:

```python
match subject:
    case <pattern_1>:
        <action_1>
    case <pattern_2>:
        <action_2>
    case <pattern_3>:
        <action_3>
    case _:
        <action_wildcard>
```
















# Loop Structure

## Application Scenario

A loop structure is a structure that controls the repeated execution of a certain or certain instructions in a program. There are two ways to construct a loop structure in Python, `for-in`，`while`.

## for-in

If you know exactly how many times the loop executes or you want to iterate over a container, use`for-in`

Calculate the result of the sum of 1~100 ($\displaystyle \sum \limits_{n=1}^{100}n$）

```python
sum = 0
for x in range(101):
    sum += x
print(sum)
```

It should be noted that the `range(1, 101)` in the above code can be used to construct a range from 1 to 100. When we put such a range in the` for-in` loop, we can take it out sequentially through the previous loop variable `x `An integer from 1 to 100. Of course, the usage of range is very flexible, an example is given below:

- `range(101)`: It can be used to generate an integer ranging from 0 to 100. It should be noted that 101 cannot be taken.

- `range(1, 101)`: It can be used to generate an integer ranging from 1 to 100, which is equivalent to a closed interval in front and an open interval in the end.
- `range(1, 101, 2)`: Can be used to generate odd numbers from 1 to 100, where 2 is the step size, which is the value by which the value is incremented each time.
- `range(100, 0, -2)`: Can be used to generate even numbers from 100 to 1, where -2 is the step size, the value by which the number is decremented each time.

### Realize the sum of even numbers between 1 and 100

```PYTHON
sum = 0
for x in range(2, 101, 2):
    sum += x
print(sum)
```

### The same function can also be achieved by using the branch structure in the loop

```PYTHON
sum = 0
for x in range(1, 101):
    if x % 2 == 0:
        sum += x
print(sum)
```

## while

If you want to construct a loop structure that does not know the specific number of loops, we recommend using a `while` loop. The `while` loop controls the loop through an expression that can generate or convert a `bool `value. If the value of the expression is `True`, the loop continues; if the value of the expression is `False`, the loop ends.

```python
import random
answer = random.randint(1, 100)
counter = 0
while True:
    counter += 1
    number = int(input('Enter a number: '))
    if number > answer:
        print('Bigger')
    elif number < answer:
        print('Smaller')
    else:
        print('Exactly')
        break
print('You have guess %d times in total' % counter )
if counter > 7:
    print('You are stupid')
```

The above code uses the `break` keyword to terminate the loop early. It should be noted that `break` can only terminate the loop it is in. This point needs to be paid attention to when using a nested loop structure (described below). In addition to `break`, there is another keyword is `continue`, which can be used to abandon the subsequent code of this loop and directly let the loop enter the next round.

Like the branch structure, the loop structure can also be nested, that is to say, the loop structure can also be constructed in the loop. The following example demonstrates how to output a nine-nine multiplication table through nested loops.

### Output multiplication formula table (99 table)

```python
for i in range(1, 10):
    for j in range(1, i + 1):
        print('%d*%d=%d' % (i, j, i * j), end='\t')
    print()
```












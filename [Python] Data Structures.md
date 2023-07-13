# Python Data Structures

In this chapter, we mainly introduce the Python data structure based on the knowledge points learned earlier.

------

## the list

Lists in Python are mutable, which is the most important feature that distinguishes them from strings and tuples. In one sentence, lists can be modified, but strings and tuples cannot.

Here are the methods for lists in Python:

| method            | describe                                                     |
| :---------------- | :----------------------------------------------------------- |
| list.append(x)    | Adds an element to the end of the list, equivalent to a[len(a):] = [x]. |
| list.extend(L)    | Extends the list by adding all elements of the specified list, equivalent to a[len(a):] = L. |
| list.insert(i, x) | Inserts an element at the specified position. The first parameter is the index of the element to be inserted in front of it, for example, a.insert(0, x) will be inserted before the entire list, and a.insert(len(a), x) is equivalent to a.append( x). |
| list.remove(x)    | Removes the first element in the list with value x. If there is no such element, an error is returned. |
| list.pop([i])     | Removes the element from the specified position in the list and returns it. If no index is specified, a.pop() returns the last element. The element is then removed from the list. (The square brackets around the i in the method indicate that the argument is optional, rather than requiring you to type a pair of square brackets, which you'll often encounter in the Python library reference manual.) |
| list.clear()      | Removes all items from the list, equals del a[:].            |
| list.index(x)     | Returns the index of the first element in the list whose value is x. An error is returned if there is no matching element. |
| list.count(x)     | Returns the number of times x occurs in the list.            |
| list.sort()       | Sort the elements in the list.                               |
| list.reverse()    | Inverts the elements in the list.                            |
| list.copy()       | Return a shallow copy of the list, equal to a[:].            |

The following example demonstrates most of the list methods:

## example

```python
>>> a = [66.25, 333, 333, 1, 1234.5]
>>> **print**(a.count(333), a.count(66.25), a.count('x'))
2 1 0
>>> a.insert(2, -1)
>>> a.append(333)
>>> a
[66.25, 333, -1, 333, 1, 1234.5, 333]
>>> a.index(333)
1
>>> a.remove(333)
>>> a
[66.25, -1, 333, 1, 1234.5, 333]
>>> a.reverse()
>>> a
[333, 1234.5, 1, 333, -1, 66.25]
>>> a.sort()
>>> a
[-1, 1, 66.25, 333, 333, 1234.5]
```

Note: Methods that modify lists like insert, remove or sort have no return value.

------

## Use a list as a stack

The list method makes it convenient to use the list as a stack. The stack is a specific data structure, and the first element entered is the last one released (last in, first out). An element can be added to the top of the stack with the append() method. An element can be released from the top of the stack with the pop() method without specifying an index. For example:

## example

```python
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack.append(7)
>>> stack
[3, 4, 5, 6, 7]
>>> stack.pop()
7
>>> stack
[3, 4, 5, 6]
>>> stack.pop()
6
>>> stack.pop()
5
>>> stack
[3, 4]
```



------

## Use a list as a queue

You can also use the list as a queue, but the first element added to the queue is the first to be taken out; but it is not efficient to use the list for this purpose. Adding or popping an element at the end of the list is fast, but inserting or popping from the head of the list is not so fast (since all other elements have to be moved one by one).

## example

```python
>>> **from** collections **import** deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")      # Terry arrives
>>> queue.append("Graham")      # Graham arrives
>>> queue.popleft()         # The first to arrive now leaves
'Eric'
>>> queue.popleft()         # The second to arrive now leaves
'John'
>>> queue              # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```



------

## list comprehension

List comprehensions provide an easy way to create lists from sequences. Usually applications apply some operation to each element of a sequence, use the result obtained as an element to generate a new list, or create a subsequence according to a certain decision condition.

Each list comprehension has a for followed by an expression, and then zero or more for or if clauses. The return result is a list generated from the following for and if contexts according to the expression. If you want the expression to deduce a tuple, you must use parentheses.

Here we multiply each value in the list by three to get a new list:

```python
>>> vec = [2, 4, 6]
>>> [3*x **for** x **in** vec]
[6, 12, 18]

Now let's play a little trick:

>>> [[x, x**2] **for** x **in** vec]
[[2, 4], [4, 16], [6, 36]]
```

Here we call a method on each element in the sequence one by one:

## example

```python
>>> freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
>>> [weapon.strip() **for** weapon **in** freshfruit]
['banana', 'loganberry', 'passion fruit']

We can use an if clause as a filter:

>>> [3*x **for** x **in** vec **if** x > 3]
[12, 18]
>>> [3*x **for** x **in** vec **if** x < 2]
[]

Here are some demonstrations of loops and other tricks:

>>> vec1 = [2, 4, 6]
>>> vec2 = [4, 3, -9]
>>> [x*y **for** x **in** vec1 **for** y **in** vec2]
[8, 6, -18, 16, 12, -36, 24, 18, -54]
>>> [x+y **for** x **in** vec1 **for** y **in** vec2]
[6, 5, -7, 8, 7, -5, 10, 9, -3]
>>> [vec1[i]*vec2[i] **for** i **in** range(len(vec1))]
[8, 12, -54]

List comprehensions can use complex expressions or nested functions:

>>> [str(round(355/113, i)) **for** i **in** range(1, 6)]
['3.1', '3.14', '3.142', '3.1416', '3.14159']
```



------

## nested list comprehension

Python lists can also be nested.

The following example shows a 3X4 matrix list:

```python
>>> matrix = [
...   [1, 2, 3, 4],
...   [5, 6, 7, 8],
...   [9, 10, 11, 12],
... ]
```

The following example converts a 3X4 matrix list into a 4X3 list:

```python
>>> [[row[i] **for** row **in** matrix] **for** i **in** range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

The following instance can also be implemented using:

```python
>>> transposed = []
>>> **for** i **in** range(4):
...   transposed.append([row[i] **for** row **in** matrix])
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

Another implementation method:

```python
>>> transposed = []
>>> **for** i **in** range(4):
...   # the following 3 lines implement the nested listcomp
...   transposed_row = []
...   **for** row **in** matrix:
...     transposed_row.append(row[i])
...   transposed.append(transposed_row)
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```



------

## del statement

Use the del statement to delete an element from a list by index rather than by value. This is different from using pop() to return a value. You can use the del statement to delete a cut from the list, or to empty the entire list (the method we described earlier was to assign an empty list to the cut). For example:

```python
>>> a = [-1, 1, 66.25, 333, 333, 1234.5]
>>> **del** a[0]
>>> a
[1, 66.25, 333, 333, 1234.5]
>>> **del** a[2:4]
>>> a
[1, 66.25, 1234.5]
>>> **del** a[:]
>>> a
```

Entity variables can also be deleted with del:

```
>>> del a
```

------

## tuples and sequences

A tuple consists of several comma-separated values, for example:

```python
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
```

As you can see, tuples are always output with parentheses in order to properly represent nested structures. They may or may not be entered with or without parentheses, but they are usually required (if the tuple is part of a larger expression).

------

## gather

A set is an unordered collection of unique elements. Basic functionality includes relationship testing and elimination of duplicate elements.

Collections can be created with braces ({}). Note: If you want to create an empty collection, you must use set() instead of {}; the latter creates an empty dictionary, and we will introduce this data structure in the next section.

Here is a simple demo:

```python
>>> basket = { 'apple' , 'orange' , 'apple' , 'pear' , 'orange' , 'banana' }
>>> **print** ( basket )            # delete duplicate
{ 'orange' , 'banana' , 'pear' , 'apple' }
>>> 'orange' **in** basket         # Detect members
True
>>> 'crabgrass' **in** basket
False

>>> # The following demonstrates the operation of two sets
...
>>> a = set ( 'abracadabra' )
>>> b = set ( 'alacazam' )
>>> a                  # unique letter in a
{ ​​'a' , 'r' , 'b' , 'c' , 'd' }
>>> > a - b                # letter in a but not in b
{ 'r' , 'd' , 'b' }
>>> a | b                # letter in a or b
{ 'a' , 'c', 'r', 'd', 'b' , 'm' , 'z' , 'l' }
>>> a & b                # letters in both a and b
{ 'a' , 'c' }
>>> a ^ b                # in A letter in a or b, but not both a and b
{ 'r' , 'd' , 'b' , 'm' , 'z' , 'l' }

Collections also support comprehensions:

>>> a = {x **for** x **in** 'abracadabra' **if** x **not** **in** 'abc'}
>>> a
{'r', 'd'}
```



------

## dictionary

Another very useful built-in Python data type is the dictionary.

Unlike sequences, which are indexed by consecutive integers, dictionaries are indexed by keys, which can be of any immutable type, usually strings or numbers.

The best way to think of a dictionary is as an unordered collection of key=>value pairs. Within the same dictionary, keys must be distinct from each other.

A pair of curly braces creates an empty dictionary: {}.

Here is a simple example of dictionary usage:

```python
>>> tel = {'jack': 4098, 'sape': 4139}
>>> tel['guido'] = 4127
>>> tel
{'sape': 4139, 'guido': 4127, 'jack': 4098}
>>> tel['jack']
4098
>>> **del** tel['sape']
>>> tel['irv'] = 4127
>>> tel
{'guido': 4127, 'irv': 4127, 'jack': 4098}
>>> list(tel.keys())
['irv', 'guido', 'jack']
>>> sorted(tel.keys())
['guido', 'irv', 'jack']
\>>> 'guido' **in** tel
True
>>> 'jack' **not** **in** tel
False
```

The constructor dict() builds a dictionary directly from a list of key-value tuples. If there is a fixed pattern, list comprehensions specify specific key-value pairs:

```python
>>> dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
{'sape': 4139, 'jack': 4098, 'guido': 4127}

Additionally, dictionary comprehensions can be used to create expressions dictionaries of arbitrary keys and values:

>>> {x: x**2 **for** x **in** (2, 4, 6)}
{2: 4, 4: 16, 6: 36}

If keywords are simply strings, it is sometimes more convenient to specify key-value pairs using keyword arguments:

>>> dict(sape=4139, guido=4127, jack=4098)
{'sape': 4139, 'jack': 4098, 'guido': 4127}
```



------

## traversal skills

When traversing through the dictionary, the key and the corresponding value can be interpreted at the same time using the items() method:

```python
\>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
\>>> **for** k, v **in** knights.items():
...   **print**(k, v)
...
gallahad the pure
robin the brave

When traversing in the sequence, the index position and corresponding value can be obtained at the same time using the enumerate() function:

\>>> **for** i, v **in** enumerate(['tic', 'tac', 'toe']):
...   **print**(i, v)
...
0 tic
1 tac
2 toe
```

Iterating over two or more sequences simultaneously can be combined using zip():

```python
\>>> questions = ['name', 'quest', 'favorite color']
\>>> answers = ['lancelot', 'the holy grail', 'blue']
\>>> **for** q, a **in** zip(questions, answers):
...   **print**('What is your {0}?  It is {1}.'.format(q, a))
What **is** your name?  It **is** lancelot.
What **is** your quest?  It **is** the holy grail.
What **is** your favorite color?  It **is** blue.
```

To traverse a sequence in reverse, first specify the sequence, then call the reversed() function:

```python
\>>> **for** i **in** reversed(range(1, 10, 2)):
...   **print**(i)
...
9
7
5
3
1

To traverse a sequence in order, use the sorted() function to return a sorted sequence without modifying the original value:

\>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
\>>> **for** f **in** sorted(set(basket)):
...   **print**(f)
...
apple
banana
orange
pear
```



------

## see documentation

- [Python3 list](https://www.runoob.com/python3/python3-list.html)
- [Python3 tuple](https://www.runoob.com/python3/python3-tuple.html)
- [Python3 dictionary](https://www.runoob.com/python3/python3-dictionary.html)
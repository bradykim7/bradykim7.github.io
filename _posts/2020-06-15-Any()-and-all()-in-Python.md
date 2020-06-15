---
title: "Any() and all() in Python with Examples"
date: 2020-06-15
categories:
  - Python3
tags:
  - Python3
  - function
---

### Any() and all() in Python with Examples
### Original from [HERE](https://stackabuse.com/any-and-all-in-python-with-examples/)


#### Introduction to any() and all()

In this tutorial, we'll be covering the `any()` and `all()` functions in Python.

이번 포스팅에서는 `any()` 와  `all()` 파이썬 함수에 대해 알아보자.

The `any(iterable)` and `all(iterable)` are built-in functions in Python and have been around since Python 2.5 was released. 
Both functions are equivalent to writing a series of `or` and `and` operators respectively between each of the elements of the passed `iterable`. 
They are both convenience functions that shorten the code by replacing boilerplate loops.

`any(iterable)` 와  `all(iterable)`는 파이썬 안의 내장되어있고, Python 2.5 버전 이후에 포함되 배포 되었다. 
두 개의 함수는 `or` 와 `and` 연산자로 이루어져있고, 각각의 요소들은 `iterable`을 통과할 수 있다.
그리고 동시에 2개의 함수는 boilerplate loop로 대체하여 줄어든 함수이다.

Both methods short-circuit and return a value as soon as possible, so even with huge iterables, they're as efficient as they can be.

두개의 메소드는 짧은 순환이고 또한 리턴값을 가능한 빠르게 반환한다. 심지어 큰 iterable을 가지고 있다고하더라도, 이 두 개의 함수는 매우 효율적으로 연산한다.

#### The and/or Operators

Let's remind ourselves how the `and`/`or` operators work, as these functions are based on them.

다시 한번 우리는 생각해보자, `and`/`or` 연산자가 어떻게 작동하는지 그리고 `any()` 와  `all()`는 모두 이를 바탕으로 만들어진 함수이다.

##### The "or" Operator

The `or` operator evaluates to `True` if any of the conditions (operands) are `True`.

`or` 연산자는 `True` 평가하는 연산자이며, 둘중 하나만 `True` 값이면 `True` 를 반환한다.

```python
print("(2 == 2) or (3 == 3) evaluates to: " + str((2 == 2) or (3 == 3)))
print("(2 == 2) or (3 == 2) evaluates to: " + str((2 == 2) or (3 == 2)))
print("(2 == 0) or (3 == 2) evaluates to: " + str((2 == 0) or (3 == 2)))
```

Output:
```python
(2 == 2) or (3 == 3) evaluates to: True
(2 == 2) or (3 == 2) evaluates to: True
(2 == 0) or (3 == 2) evaluates to: False
```

We can chain multiple `or`s in a single statement, and it will again evaluate to `True` if any of the conditions are `True`:
 
우리는 `or` 연산자를 연쇄적으로 사용할 수 있고, 이 또한 하나의 값이 `True`이면, `True` 값을 반환한다.

```python
print(str(False or False or False or True or False))
```

Result
```python
True
```

##### The "And" Operator

The `and` operator evaluates to `True` only if all conditions are `True`:
`and` 연산자는 모든 조건이 `True` 일 경우, `True` 을 반환한다.

```python
print("(2 == 2) and (3 == 3) evaluates to: " + str((2 == 2) and (3 == 3)))
print("(2 == 2) and (3 == 2) evaluates to: " + str((2 == 2) and (3 == 2)))
print("(2 == 0) and (3 == 2) evaluates to: " + str((2 == 0) and (3 == 2)))
```

Output:

```python
(2 == 2) and (3 == 3) evaluates to: True
(2 == 2) and (3 == 2) evaluates to: False
(2 == 0) and (3 == 2) evaluates to: False
```

Similarly to `or`, we can chain multiple `and` operators, and they will evaluate to `True` only if all the operands evaluate to `True`:

`or` 유사하게 `and` 연산자도 다중 연산이 가능하고, 이 또한 모든 조건이 `True` 값일 경우 `True`을 반환한다.

```python
print(str(True and True and True and False and True))
```

This results in:

```python
False
```

#### Any()

The method `any(iterable)` behaves like a series of `or` operators between each element of the `iterable` we passed. 
It's used to replace loops similar to this one:

`any(iterable)` 메소드는 `or` 연산자와 비슷하게 동작하고, 각 요소가 `iterable` 를 통과할 수 있다. 아래와 같은 루프처럼 쓰이기도 한다.

```python
for element in some_iterable:
    if element:
        return True
return False
```

We get the same result by simply calling `any(some_iterable)`:

우리는 `any(some_iterable)` 를 호출한 경우:

```python
print(any([2 == 2, 3 == 2]))
print(any([True, False, False]))
print(any([False, False]))
```

Running this piece of code would result in:

결과 코드는 아래와 같다.

```python
True
True
False
```

*Note*: Unexpected behavior may happen when using `any()` with dictionaries and data types other than boolean. 
If `any()` is used with a dictionary, it checks whether any of the keys evaluate to `True`, not the *values*:

```python
dict = {True : False, False: False}

print(any(dict))
```

This outputs:

```python
True
```

Whereas, if `any()` checked the values, the output would have been `False`.
The method `any()` is often used in combination with the `map()` method and list comprehensions:

```python
old_list = [2, 1, 3, 8, 10, 11, 13]
list_if_even = list(map(lambda x: x % 2 == 0, old_list))
list_if_odd = [x % 2 != 0 for x in old_list]

print(list_if_even)
print(list_if_odd)

print("Are any of the elements even? " + str(any(list_if_even)))
print("Are any of the elements odd? " + str(any(list_if_odd)))
```

This outputs:

```python
[True, False, False, True, True, False, False]
[False, True, True, False, False, True, True]
Are any of the elements even? True
Are any of the elements odd? True
```

*Note*: If an empty `iterable` is passed to `any()`, the method returns `False`.

If you'd like to read more about the map(), filter() and reduce() functions, we've got you covered!

#### all()

#### Boolean Conversion and any(), all() Functions

#### Conclusion

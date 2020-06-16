---
title: "Any() and all() in Python with Examples"
date: 2020-06-15
categories:
  - Python3
tags:
  - Python3
  - function
  - method
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

우리가 `any(some_iterable)` 를 호출한 경우:

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

*노트* : `any()` 함수와 함께 딕셔너리 혹은 boolean 타입이 아닌 다른 데이터 타입을 사용할 경우, 예상치 못한 결과를 낳을 수 있다. 만약 `any()` 함수를
딕셔너리와 함께 사용하고 자 한다면, 벨류값보다 키 값이 `True`인 것을 평가한다.  

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

반면에, `any()` 가 밸류값을 확인하고자 할 경우, 결과값이 `False`로 나타날 것이다.
메소드 `any()`는 종종 `map()` 혹은 리스트를 포함해서 같이 사용한다.

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

If you'd like to read more about the [map(), filter() and reduce()](https://stackabuse.com/map-filter-and-reduce-in-python-with-examples/_) functions, we've got you covered!

#### all()

The `all(iterable)` method evaluates like a series of `and` operators between each of the elements in the `iterable` we passed. It is used to replace loops similar to this one:

`all(iterable)` 메소드는 각각의  전달한 `iterable`한 요소들 사이에 일련의 `and` 연산자가 있는 것과 같다. 이는 종종 아래와 같은 루프로 대체되어 사용된다.

```python
for element in iterable:
    if not element:
        return False
return True
```

The method returns `True` only if every element in `iterable` evaluates to `True`, and `False` otherwise:
이 메소드는 `True` 값을 반환하는데 `iterable`에 존재하는 모든 원소가 `True` 혹은 `False`로 측정된다.

```python
print(all([2 == 2, 3 == 2]))
print(all([2 > 1, 3 != 4]))
print(all([True, False, False]))
print(all([False, False]))
```

This outputs:

```python
False
True
False
False
```

*Note*: Just like with `any()`, unexpected behavior may happen when passing dictionaries and data types other than `boolean`. 
Again, if `all()` is used with a dictionary, it checks whether all of the keys evaluate to `True`, not the values.

*Note*: `any()`와 마찬가지로, 우리가 딕셔너리형이나 `boolean`이 아닌 다른 데이터 타입을 넣을경우 예상치 못한 결과가 나올 수 있다.
다시 한번, `all()`가 딕셔너리와 함께 사용 된다면, 우리는 모든 모든 key 값을 `True`를 판별한다.(값을 평가하지 않음)

Another similarity with `any()` is that `all()` is also commonly used in combination with the `map()` function and `list` comprehensions:

`any()` 와 `all()` 가 유사한 점은 `map()` 메소드와 `list`와 함께 사용한다는 점이고, 

```python
old_list = ["just", "Some", "text", "As", "An", "example"]
list_begins_upper = list(map(lambda x: x[0].isupper(), old_list))
list_shorter_than_8 = [len(x) < 8 for x in old_list]

print(list_begins_upper)
print(list_shorter_than_8)

print("Do all the strings begin with an uppercase letter? " + str(all(list_begins_upper)))
print("Are all the strings shorter than 8? " + str(all(list_shorter_than_8)))
```

This outputs:

```python
[False, True, False, True, True, False]
[True, True, True, True, True, True]
Do all the strings begin with an uppercase letter? False
Are all strings shorter than 8? True
```

Note: If an empty `iterable` is passed to `all()`, the method returns `True`! This is because the code for `all()` 
checks if there are any `False` elements in the `iterable`, and in the case of an empty list there are no elements and therefore there are no `False` elements either.

#### Boolean Conversion and any(), all() Functions

A common cause of confusion and errors when using any logical operators, and therefore when using `any()` and `all()` as well,
 is what happens when the elements aren't of the `boolean` data type. In other words, when they aren't exactly `True` of `False` but instead have to be evaluated to `True` or `False`.

보통 논리 연산자들을 사용할 때 혼란을 많이 격고, 에러를 많이 만들어 낸다. `any()` 와 `all()` 도 마찬가지로, 우리가 요소들이 `boolean`의 데이터 타입이 아닐 경우 많이 실수를 
만들어 낸다. 다시 말하자면, 정확히 `boolean` 타입이 아닌, `True` 이나 `False` 으로 평가 될 수 있는 요소를 넣을 때 에러가 일어난다.

Some programming languages don't evaluate non-`boolean` data types to `boolean`s. For example Java would complain if you tried
something along the lines of `if("some string")` or `if(15)` and tell you that the type you used can't be converted to `boolean`.

몇몇의 프로그래밍 언어는 `boolean` 타입이 아닌 데이터는 `boolean`으로 평가하지 않는 언어도 존재한다. 예를 들어 자바의 경우, `if("some string")` 나 `if(15)` 를 
사용할 경우 `boolean`타입으로 변경할 수 없다고 말할 것이다.

Python on the other hand does no such thing, and will instead convert what you passed to `boolean` without warning you about it.

하지만 파이썬은 그렇게 출력하지 않는다. 어떠한 경고 없이 `boolean`타입이 아닌 데이터도 `boolean`으로 변환하여 반환해준다.

Python converts most things to `True` with a few exceptions:

몇몇의 경우를 제외하고 대부분의 경우를 `True`로 변환하여 준다.

* Any numerical value equal to 0 (including 0.0) is treated as `False`. A common misconception here is that negative values (-2, -3.3,...) are treated as `False` as well, they are not treated as `False`!
* Any empty sequence (or collection) is treated as `False`, including empty strings, empty lists, etc. Keep in mind that unexpected behavior might happen when using all() with an empty iterable (it will return True).
* The actual `boolean` value `False` is of course treated as `False` as well as the special value `None`.

* 어떠한 숫자로 표현한 값이 0 과 같으면 그 값은 `False` 으로 다뤄진다. 흔히 오해하는 것이 음수의 경우도 `False` 로 나타내어 질 것 같지만, 그것들은 `False` 값이 아니다!
* 빈 공간, 띄어 쓰기 혹은 컬랙션, 스트링 데이터, 리스트에서  빈 곳은 `False`로 다뤄진다. 명심해야되고 항상 조심 해야된다. 빈 공간이 존재 할 경우 `all()` 메소드를 사용할 경우 예상 하지 못한 값을 반환 받을 수 있다.
* `boolean` 타입의 `False` 또한 `False` 로 다뤄진다. 그리고 특별한 값인 `None` 값 또한 `False` 로 다뤄진다.

A few examples of how we can use the way Python "boolean-izes" other data types with `any()` and `all()`.

어떻게 우리가 `any()` 와 `all()` 메소드를 이용하여 "boolean-izes"를 하는지 알 수 있는 몇 가지의 예제이다.

```python
list_of_strings = ["yet", "another", "example",""]
print("Do all strings have some content?", all(list_of_strings))

list_of_ints = [0, 0.0, -2, -5]
print("Are any of the ints different than 0?", any(list_of_ints))
```

This outputs:

```python
Do all strings have some content? False
Are any of the ints different than 0? True
```

Keep in mind that you might still want to write more readable code by not using implicit `boolean` conversion like this.


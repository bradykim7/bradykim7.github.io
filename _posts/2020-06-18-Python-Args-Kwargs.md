---
title: "Python Args and Kwargs"
date: 2020-06-16
categories:
  - Python
tags:
  - Python
  - Basic
---
### Python Args and Kwargs
### Original from [HERE](https://realpython.com/python-kwargs-and-args/#unpacking-with-the-asterisk-operators)


#### Introductions : Python args and kwargs: Demystified

Sometimes, when you look at a function definition in Python, you might see that it takes two strange arguments: 
*args and **kwargs. If you’ve ever wondered what these peculiar variables are, or why your IDE defines them in main(), 
then this article is for you. You’ll learn how to use args and kwargs in Python to add more flexibility to your functions.

파이썬에서 가끔 너가 함수들을 들여다보면 이상한 매개변수들이 있을 것이다. *args 와 **kwargs 이다. 만약 이런 특이한 변수에 대해 궁금하고, 왜 IDE 메인 함수에서 
이들을 너에게 제공해주는지 궁금하다면 이번 포스트가 아주 적당한 것이다. 유연하게 너의 함수들을 바꿔주는 이 두 변수에 대하여 알아보자.

By the end of the article, you’ll know:

이 포스트를 다 읽고 나면 분명히 너는 

* What *args and **kwargs actually mean
* How to use *args and **kwargs in function definitions
* How to use a single asterisk (*) to unpack iterables
* How to use two asterisks (**) to unpack dictionaries

* *args 와 **kwargs 에 대해 분명하게 알게 될 것이고,
* *args 와  **kwargs 를 함수 정의에서 어떻게 써야 하는 지
* * 하나의 별표를 어떻게 사용하는지
* ** 두개의 별표 또한 어떻게 사용하는지 알게 될 것이다.

This post assumes that you already know how to define Python functions and work with lists and dictionaries.

이 포스트는 파이썬 함수, 리스트, 딕셔너리에 대한 이해가 있다고 가정한 후 진행하는 것이다.

#### Passing Multiple Arguments to a Function

*args and **kwargs allow you to pass multiple arguments or keyword arguments to a function. Consider the following example. 
This is a simple function that takes two arguments and returns their sum:

*args 와  **kwargs 는 너에게 여려개의 매개변수나 매개변수의 키워드를 함수에 전달해주는 것을 가능하게 해준다. 아래의 예제를 살펴보자. 이 간단한 예제는 두 개의 
매개변수를 넘겨 받고 두 변수의 합을 리턴한다.

```python
def my_sum(a, b):
    return a + b
```

This function works fine, but it’s limited to only two arguments. What if you need to sum a varying number of arguments, 
where the specific number of arguments passed is only determined at runtime? Wouldn’t it be great to create a function 
that could sum all the integers passed to it, no matter how many there are?

이 함수는 그럭저럭 잘 작동하지만, 이는 2개의 매개변수로 제한 되어 있다. 만약 너가 런타임 환경에서 변수의 갯수가 정해진다면, 여러개의 변수를 넘겨주는 일을 어떻게 해야할까?
그저 함수가 여러개의 정수를 받더라도 합을 전달해 주는 방법이 없는 것일까?

#### Using the Python args Variable in Function Definitions

There are a few ways you can pass a varying number of arguments to a function. The first way is often the most intuitive 
for people that have experience with collections. You simply pass a list or a set of all the arguments to your function. 
So for my_sum(), you could pass a list of all the integers you need to add:

이곳에 너가 다양한 갯수에 변수를 건내주는 방법이 존재한다. 첫번째 방법은 좀 컬랙션에 대한 경험이 있는 사람이라면 직관적인 방법이다. 너는 단순히 리스트를 건내주는 방식이다.
그래서 my_sum()함수를 위해 너는 int list를 전달해주는 것이다.

```python
# sum_integers_list.py
def my_sum(my_integers):
    result = 0
    for x in my_integers:
        result += x
    return result

list_of_integers = [1, 2, 3]
print(my_sum(list_of_integers))
```

This implementation works, but whenever you call this function you’ll also need to create a list of arguments to pass to it. 
This can be inconvenient, especially if you don’t know up front all the values that should go into the list.

이러한 구현 방식은 적절하게 동작하지만, 너가 함수를 호출 할때마다, 이를 위해 list 매개변수를 만들어야 하는 수고로움이 존재한다. 이는 불편하다 ! 특히 모든 값들이 
리스트에 제대로 들어갔는지 확인도 해야한다...

This is where *args can be really useful, because it allows you to pass a varying number of positional arguments. 
Take the following example:

이러한 함수에서 매우 유용하게 사용하는 것이 바로 *args 이다. 왜냐하면 이는 너에게 여러 개수의 매개변수를 전달 할 수 있게 해준다. 다음의 예제를 살펴보자.

```python
# sum_integers_args.py
def my_sum(*args):
    result = 0
    # Iterating over the Python args tuple
    for x in args:
        result += x
    return result

print(my_sum(1, 2, 3))
```

In this example, you’re no longer passing a list to my_sum(). Instead, you’re passing three different positional arguments. 
my_sum() takes all the parameters that are provided in the input and packs them all into a single iterable object named args.

위의 예제에서는 너는 더이상 my_sum() 함수에 List를 건내주지 않아도 된다. 대신 너는 3개의 다른 매개 변수를 전달한다. my_sum()은 모든 파라미터들을 수용해서,
이를 모든 인풋값으로 제공, 그들을 묶어서 하나의 순환가능한 객체로 만들고 이를 args라고 명명한다.

Note that args is just a name. You’re not required to use the name args. You can choose any name that you prefer, such as integers:

당연한 이야기겠지만, 이름이 꼭 *args 필요는 없다. 뭐 프로그래밍에서 흔히 있는 일인듯 관습적으로 이름을 *args 라고 지을 뿐이다.

```python
# sum_integers_args_2.py
def my_sum(*integers):
    result = 0
    for x in integers:
        result += x
    return result

print(my_sum(1, 2, 3))
```

The function still works, even if you pass the iterable object as integers instead of args. All that matters here 
is that you use the unpacking operator (*).

이 함수는 여전히 잘 동작할 것이고, 심지어 args 대신 integers를 순환 객체 이름을 대체해서 사용하면된다. 주의 해야할 것은 매개변수 앞에 * 를 사용함으로써, 
이 매개변수가 unpacking 되었다는 것을 명시해야한다 .

Bear in mind that the iterable object you’ll get using the unpacking operator * is not a list but a tuple. 
A tuple is similar to a list in that they both support slicing and iteration. However, tuples are very different
 in at least one aspect: lists are mutable, while tuples are not. To test this, run the following code. 
 This script tries to change a value of a list:

항상 조심해야 할 것은 너가 넘겨주는 반복 가능한 객체, * 연산자를 사용해서 unpacking을 나타내는 이 객체는 List가 아닌 Tuple 이다. Tuple은 List와 유사하게
Slicing 과  interation 이 가능하다. 하지만 Tuple이 가진 매우 다른 특징은, List 는 변경이 가능하다면, Tuple은 변경이 불가능하다는 점이다. 이 차이점을 
알아보기 위해서 아래의 예제를 살펴보자. 

```python
# change_list.py
my_list = [1, 2, 3]
my_list[0] = 9
print(my_list)
```

The value located at the very first index of the list should be updated to 9. If you execute this script, 
you will see that the list indeed gets modified:

위에 예제에서 첫번째 인덱스에 존재하는 값을 9로 변경하였다. 그리고 이를 script에서 실행시키면 아래와 같이 수정된 결과를 보여준다.

```shell script
$ python change_list.py
[9, 2, 3]
```

The first value is no longer 0, but the updated value 9. Now, try to do the same with a tuple:

더 이상 첫번째, 값이 0이 아닌 9의 값으로 변경 되엇다. 이제 같은 일을 Tuple에서 진행해보자.

```python
# change_tuple.py
my_tuple = (1, 2, 3)
my_tuple[0] = 9
print(my_tuple)
```

Here, you see the same values, except they’re held together as a tuple. If you try to execute this script, 
you will see that the Python interpreter returns an error:

앞서서 했던 같은 일을 반복하는 것이다. 달라진 것은 tuple에 하는것 뿐이다. 이를 Script에서 실행할 경우 아래와 같은 파이썬 에러를 보게 될 것이다.

```shell script
$ python change_tuple.py
Traceback (most recent call last):
  File "change_tuple.py", line 3, in <module>
    my_tuple[0] = 9
TypeError: 'tuple' object does not support item assignment
```

This is because a tuple is an immutable object, and its values cannot be changed after assignment. 
Keep this in mind when you’re working with tuples and *args.

이는 tuple 이 변경이 불가능한 객체이기 때문이다. 이는 객체안의 값들이 정해진 후에 바뀌는 것이 불가능하다는 것이다. 이를 항상 명심해라 튜플과 *args를 사용할때 !

#### Using the Python kwargs Variable in Function Definitions

Okay, now you’ve understood what *args is for, but what about **kwargs? **kwargs works just like *args,
 but instead of accepting positional arguments it accepts keyword (or named) arguments. Take the following example:

자 이제 충분히 *args 에 대해 이해했을 것이다. 이제 **kwargs 에 대해 알아봐야하지 않겠는가? **kwargs 도 상당 부분 *args와 비슷하게 동작한다. 
하지만 positional arguments 를 수용하는 대신에 arguments의 Keyword 를 수용한다. 이게 무슨말인지 예제를 통해 알아보자.

```python
# concatenate.py
def concatenate(**kwargs):
    result = ""
    # Iterating over the Python kwargs dictionary
    for arg in kwargs.values():
        result += arg
    return result

print(concatenate(a="Real", b="Python", c="Is", d="Great", e="!"))
```

When you execute the script above, concatenate() will iterate through the Python kwargs dictionary and concatenate all 
the values it finds:

위의 코드를 스크립트에서 수행 할 경우 concatenate() 함수는 파이썬 kwargs 딕셔너리를 통해 순환하고, 값들을 결합시킨다.  

```shell script
$ python concatenate.py
RealPythonIsGreat!
```

Like args, kwargs is just a name that can be changed to whatever you want. Again, what is important here is the use of 
the unpacking operator (**).

args와 마찬가지로, 이름은 성능에 전혀 문제가 되지 않느다. 다시한번 말하지만 이름이 문제가 아니라 **연산자의 사용이 더 중요하다.

So, the previous example could be written like this:

그래서 이전 예제와 유사하게, 이름을 바꿔 보았다.

```python
# concatenate_2.py
def concatenate(**words):
    result = ""
    for arg in words.values():
        result += arg
    return result

print(concatenate(a="Real", b="Python", c="Is", d="Great", e="!"))
```

Note that in the example above the iterable object is a standard dict. If you iterate over the dictionary and want to 
return its values, like in the example shown, then you must use .values().

위의 예제에서 보는 것과 같이 반복가능한 객체는 일반적인 딕셔너리이다. 만약 이 딕셔너리에서 값을 반환시키고 싶다면 너는 위에서 보는것과 같이 .values()를 이용해야한다.


In fact, if you forget to use this method, you will find yourself iterating through the keys of your Python kwargs dictionary 
instead, like in the following example:

```python
# concatenate_keys.py
def concatenate(**kwargs):
    result = ""
    # Iterating over the keys of the Python kwargs dictionary
    for arg in kwargs:
        result += arg
    return result

print(concatenate(a="Real", b="Python", c="Is", d="Great", e="!"))
```

Now, if you try to execute this example, you’ll notice the following output:

```shell script
$ python concatenate_keys.py
abcde
```

As you can see, if you don’t specify .values(), your function will iterate over the keys of your Python kwargs dictionary, 
returning the wrong result.

#### Ordering Arguments in a Function
Now that you have learned what *args and **kwargs are for, you are ready to start writing functions that take a varying number of input arguments. But what if you want to create a function that takes a changeable number of both positional and named arguments?

In this case, you have to bear in mind that order counts. Just as non-default arguments have to precede default arguments, so *args must come before **kwargs.

To recap, the correct order for your parameters is:

Standard arguments
*args arguments
**kwargs arguments
For example, this function definition is correct:

# correct_function_definition.py
def my_function(a, b, *args, **kwargs):
    pass
The *args variable is appropriately listed before **kwargs. But what if you try to modify the order of the arguments? For example, consider the following function:

# wrong_function_definition.py
def my_function(a, b, **kwargs, *args):
    pass
Now, **kwargs comes before *args in the function definition. If you try to run this example, you’ll receive an error from the interpreter:

$ python wrong_function_definition.py
  File "wrong_function_definition.py", line 2
    def my_function(a, b, **kwargs, *args):
                                    ^
SyntaxError: invalid syntax
In this case, since *args comes after **kwargs, the Python interpreter throws a SyntaxError.


#### Unpacking With the Asterisk Operators: * & **
You are now able to use *args and **kwargs to define Python functions that take a varying number of input arguments. Let’s go a little deeper to understand something more about the unpacking operators.

The single and double asterisk unpacking operators were introduced in Python 2. As of the 3.5 release, they have become even more powerful, thanks to PEP 448. In short, the unpacking operators are operators that unpack the values from iterable objects in Python. The single asterisk operator * can be used on any iterable that Python provides, while the double asterisk operator ** can only be used on dictionaries.

Let’s start with an example:

# print_list.py
my_list = [1, 2, 3]
print(my_list)
This code defines a list and then prints it to the standard output:

$ python print_list.py
[1, 2, 3]
Note how the list is printed, along with the corresponding brackets and commas.

Now, try to prepend the unpacking operator * to the name of your list:

# print_unpacked_list.py
my_list = [1, 2, 3]
print(*my_list)
Here, the * operator tells print() to unpack the list first.

In this case, the output is no longer the list itself, but rather the content of the list:

$ python print_unpacked_list.py
1 2 3
Can you see the difference between this execution and the one from print_list.py? Instead of a list, print() has taken three separate arguments as the input.

Another thing you’ll notice is that in print_unpacked_list.py, you used the unpacking operator * to call a function, instead of in a function definition. In this case, print() takes all the items of a list as though they were single arguments.

You can also use this method to call your own functions, but if your function requires a specific number of arguments, then the iterable you unpack must have the same number of arguments.

To test this behavior, consider this script:

# unpacking_call.py
def my_sum(a, b, c):
    print(a + b + c)

my_list = [1, 2, 3]
my_sum(*my_list)
Here, my_sum() explicitly states that a, b, and c are required arguments.

If you run this script, you’ll get the sum of the three numbers in my_list:

$ python unpacking_call.py
6
The 3 elements in my_list match up perfectly with the required arguments in my_sum().

Now look at the following script, where my_list has 4 arguments instead of 3:

# wrong_unpacking_call.py
def my_sum(a, b, c):
    print(a + b + c)

my_list = [1, 2, 3, 4]
my_sum(*my_list)
In this example, my_sum() still expects just three arguments, but the * operator gets 4 items from the list. If you try to execute this script, you’ll see that the Python interpreter is unable to run it:

$ python wrong_unpacking_call.py
Traceback (most recent call last):
  File "wrong_unpacking_call.py", line 6, in <module>
    my_sum(*my_list)
TypeError: my_sum() takes 3 positional arguments but 4 were given
When you use the * operator to unpack a list and pass arguments to a function, it’s exactly as though you’re passing every single argument alone. This means that you can use multiple unpacking operators to get values from several lists and pass them all to a single function.

To test this behavior, consider the following example:

# sum_integers_args_3.py
def my_sum(*args):
    result = 0
    for x in args:
        result += x
    return result

list1 = [1, 2, 3]
list2 = [4, 5]
list3 = [6, 7, 8, 9]

print(my_sum(*list1, *list2, *list3))
If you run this example, all three lists are unpacked. Each individual item is passed to my_sum(), resulting in the following output:

$ python sum_integers_args_3.py
45
There are other convenient uses of the unpacking operator. For example, say you need to split a list into three different parts. The output should show the first value, the last value, and all the values in between. With the unpacking operator, you can do this in just one line of code:

# extract_list_body.py
my_list = [1, 2, 3, 4, 5, 6]

a, *b, c = my_list

print(a)
print(b)
print(c)
In this example, my_list contains 6 items. The first variable is assigned to a, the last to c, and all other values are packed into a new list b. If you run the script, print() will show you that your three variables have the values you would expect:

$ python extract_list_body.py
1
[2, 3, 4, 5]
6
Another interesting thing you can do with the unpacking operator * is to split the items of any iterable object. This could be very useful if you need to merge two lists, for instance:

# merging_lists.py
my_first_list = [1, 2, 3]
my_second_list = [4, 5, 6]
my_merged_list = [*my_first_list, *my_second_list]

print(my_merged_list)
The unpacking operator * is prepended to both my_first_list and my_second_list.

If you run this script, you’ll see that the result is a merged list:

$ python merging_lists.py
[1, 2, 3, 4, 5, 6]
You can even merge two different dictionaries by using the unpacking operator **:

# merging_dicts.py
my_first_dict = {"A": 1, "B": 2}
my_second_dict = {"C": 3, "D": 4}
my_merged_dict = {**my_first_dict, **my_second_dict}

print(my_merged_dict)
Here, the iterables to merge are my_first_dict and my_second_dict.

Executing this code outputs a merged dictionary:

$ python merging_dicts.py
{'A': 1, 'B': 2, 'C': 3, 'D': 4}
Remember that the * operator works on any iterable object. It can also be used to unpack a string:

# string_to_list.py
a = [*"RealPython"]
print(a)
In Python, strings are iterable objects, so * will unpack it and place all individual values in a list a:

$ python string_to_list.py
['R', 'e', 'a', 'l', 'P', 'y', 't', 'h', 'o', 'n']
The previous example seems great, but when you work with these operators it’s important to keep in mind the seventh rule of The Zen of Python by Tim Peters: Readability counts.

To see why, consider the following example:

# mysterious_statement.py
*a, = "RealPython"
print(a)
There’s the unpacking operator *, followed by a variable, a comma, and an assignment. That’s a lot packed into one line! In fact, this code is no different from the previous example. It just takes the string RealPython and assigns all the items to the new list a, thanks to the unpacking operator *.

The comma after the a does the trick. When you use the unpacking operator with variable assignment, Python requires that your resulting variable is either a list or a tuple. With the trailing comma, you have actually defined a tuple with just one named variable a.

While this is a neat trick, many Pythonistas would not consider this code to be very readable. As such, it’s best to use these kinds of constructions sparingly.


#### Conclusion
You are now able to use *args and **kwargs to accept a changeable number of arguments in your functions. You have also learned something more about the unpacking operators.

You’ve learned:

What *args and **kwargs actually mean
How to use *args and **kwargs in function definitions
How to use a single asterisk (*) to unpack iterables
How to use two asterisks (**) to unpack dictionaries
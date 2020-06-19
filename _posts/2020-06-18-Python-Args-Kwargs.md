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

사실 만약 이 메소드를 사용하는 방법을 잊어버렸다면, 대신, 너 스스로 반복하는 파이썬 kwargs 딕셔너리의 키값들을 반환하는 것 이 보일 것이다.

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

이제 아래의 예제를 실행 보자. 그럼 결과값이 아래와 같을 것이다.

```shell script
$ python concatenate_keys.py
abcde
```

As you can see, if you don’t specify .values(), your function will iterate over the keys of your Python kwargs dictionary, 
returning the wrong result.

위에서 보는 것처럼, .values() 를 사용하지 않으면, 잘못된 결과를 반환하는 것을 보여줍니다.

#### Ordering Arguments in a Function

Now that you have learned what *args and **kwargs are for, you are ready to start writing functions that take a varying
 number of input arguments. But what if you want to create a function that takes a changeable number of both positional 
 and named arguments?

이제 *args 와 **kwargs 는 너는 이제 다양한 숫자의 매개변수를 사용한 함수를 만들 준비가 되어 있는 것이다. 하지만 만일 너가 매개변수의 수가 가능함과 동시에, 
매개변수가 지정 되어있는 함수는 어떻게 해야할까 ?

In this case, you have to bear in mind that order counts. Just as non-default arguments have to precede default arguments, 
so *args must come before **kwargs.

이러한 경우 너는 순서를 정하는 것을 생각해야한다. *args 는 반드시 **kwargs 앞에 선행 되어야한다.

To recap, the correct order for your parameters is:

간단하게 말해서 아래와 같은 순서로 해야한다. 

1. Standard arguments
2. *args arguments
3. **kwargs arguments

1. 기존 평범한 매개변수
2. *args 매개변수
3. **kwargs 매개변수 


For example, this function definition is correct:

아래와같은 함수의 정의가 맞는 예이다.

```python
# correct_function_definition.py
def my_function(a, b, *args, **kwargs):
    pass
```

The *args variable is appropriately listed before **kwargs. But what if you try to modify the order of the arguments? 
For example, consider the following function:

*args 변수가 **kwargs 이전에 선언되어있어서 적절한 예이다. 하지만 만약 매개변수의 순서를 바꾼다면 어떻게 될까? 
아래의 예제를 살펴보자.

```python
# wrong_function_definition.py
def my_function(a, b, **kwargs, *args):
    pass
```

Now, **kwargs comes before *args in the function definition. If you try to run this example, you’ll receive an error 
from the interpreter:

이제, **kwargs 이 *args 보다 먼저 나오게 정의하였고, 예제를 한번 실행시켜보면, 오류가 생기는것을 볼 수 있다.

```shell script
$ python wrong_function_definition.py
  File "wrong_function_definition.py", line 2
    def my_function(a, b, **kwargs, *args):
                                    ^
SyntaxError: invalid syntax
```

In this case, since *args comes after **kwargs, the Python interpreter throws a SyntaxError.

이 경우, 파이썬 인터프리터는 구문오류를 알려준다.

#### Unpacking With the Asterisk Operators: * & **

You are now able to use *args and **kwargs to define Python functions that take a varying number of input arguments. 
Let’s go a little deeper to understand something more about the unpacking operators.

이제 어느정도 적절하게 *args 와 **kwargs 를 파이썬 함수에서 정의할 수 있고, 또 다양한 매개변수를 사옹할 수 있게 되었다. 자 이번에는 *연산자와, **연산자에 대해 좀더
깊게 알아보자. 

The single and double asterisk unpacking operators were introduced in Python 2. As of the 3.5 release, they have become
 even more powerful, thanks to PEP 448. In short, the unpacking operators are operators that unpack the values from 
 iterable objects in Python. The single asterisk operator * can be used on any iterable that Python provides, 
 while the double asterisk operator ** can only be used on dictionaries.

Python 2 에서 하나 혹은 두개의 별표는 포장되어지지 않는 연산자가 소개 되었다. 그리고 Python3.5 가 배포 되면서, 그들은 좀더 강력해진 기능들이 생겼다. 짧게말해서
Unpacking 연산자는 값들을 즉, 반복가능한 객체들을 unpack하는 것이다. 하나의 별표 연산자 *는 파이썬이 제공하는 어떤 iterable 한 것들을 사용할 수 있고, **연산자는 
마찬가지로 딕셔너리가 사용하는 것들을 사용할 수 있다.
 
Let’s start with an example:

```python
# print_list.py
my_list = [1, 2, 3]
print(my_list)
```

This code defines a list and then prints it to the standard output:

아래의 코드는 리스트를 정의하고 이를 출력하는 것이다.

```shell script
$ python print_list.py
[1, 2, 3]
```

Note how the list is printed, along with the corresponding brackets and commas.

여기 이제 리스트를 출력했다.

Now, try to prepend the unpacking operator * to the name of your list:
이제 어떻게 *연산자를 사용했을때의 출력결과를 보자.

```python
# print_unpacked_list.py
my_list = [1, 2, 3]
print(*my_list)
```

Here, the * operator tells print() to unpack the list first.

여기 unpack된 리스트의 출력을 이제 살펴보자.

In this case, the output is no longer the list itself, but rather the content of the list:

이제 더 이상 스스로 리스트의 결과물을 출력하지 않고, 단지 내용만을 출력한다.

```shell script
$ python print_unpacked_list.py
1 2 3
```

Can you see the difference between this execution and the one from print_list.py? Instead of a list, print() has taken 
three separate arguments as the input.

이제 수행했을 때의 차이점을 알겠는가? 각각의 밸류값만 출력하는 것을 볼 수 있다.

Another thing you’ll notice is that in print_unpacked_list.py, you used the unpacking operator * to call a function, 
instead of in a function definition. In this case, print() takes all the items of a list as though they were single arguments.

다른 것을 너가 알아야 차려야 할 것은 * 연산자를 함수에서 사용하기 위해서는 함수정의에서 뿐만 아니라 호출시에도 사용한다는 것이다. 이 경우, print() 함수는 
모든 요소들을 리스트로써 받고, 하나의 매개변수로 취급한다.

You can also use this method to call your own functions, but if your function requires a specific number of arguments, 
then the iterable you unpack must have the same number of arguments.

너는 또한 이 매소드를 함수안에서 호출 할 수도 있다. 만약 너의 함수가 특정 숫자의 매개변수가 요구한다면, 너는 같은 숫자의 매개변수를 가져야한다.

To test this behavior, consider this script:
이를 테스트하기 위해서, 실행 해보자.

```python
# unpacking_call.py
def my_sum(a, b, c):
    print(a + b + c)

my_list = [1, 2, 3]
my_sum(*my_list)
```

Here, my_sum() explicitly states that a, b, and c are required arguments.

여기 위에 a,b,c를 나타내는 my_sum() 함수를 나타내었다.

If you run this script, you’ll get the sum of the three numbers in my_list:

이를 스크립트상에서 실행시키면, 3 숫자의 합이 출력된다.

```shell script
$ python unpacking_call.py
6
```

The 3 elements in my_list match up perfectly with the required arguments in my_sum().

3개의 요소가 my_list 와 완벽하게 갯수가 my_sum() 에서 맞아야 하는 것을 요구한다.

Now look at the following script, where my_list has 4 arguments instead of 3:

이제 만약 4가지의 매개변수를 넘길 경우 어떻게 되는지 살펴보자.

```python
# wrong_unpacking_call.py
def my_sum(a, b, c):
    print(a + b + c)

my_list = [1, 2, 3, 4]
my_sum(*my_list)
```

In this example, my_sum() still expects just three arguments, but the * operator gets 4 items from the list. 
If you try to execute this script, you’ll see that the Python interpreter is unable to run it:

이 예제는, 아직 까지 3개의 요소를 매개변수로 받지만, * 연산자로 넘기는 매개변수의 갯수를 4개로 해보겟다. 만약 이 코드를 실행한다면, 이는 파이썬 인터프리트가
실행하지 못한다.

```shell script
$ python wrong_unpacking_call.py
Traceback (most recent call last):
  File "wrong_unpacking_call.py", line 6, in <module>
    my_sum(*my_list)
TypeError: my_sum() takes 3 positional arguments but 4 were given
```

When you use the * operator to unpack a list and pass arguments to a function, it’s exactly as though you’re passing 
every single argument alone. This means that you can use multiple unpacking operators to get values from several lists
 and pass them all to a single function.

만약 * 연산자를사용할때, 이는 정확하게 각각의 매개변수 에 정확하게 맞아야한다. 이는 무슨 말이나면, unpacking 연산자를 사용해서 각각의 리스트들을 
전달 할 수 있다.(내가쓰고도 뭔말인지...) 뭐 리스트로 여러개를 넘길 수 있다는 말인 것같다.

To test this behavior, consider the following example:
이를 테스트하기 위해서 아래의 예제를 보자.

```python
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
```

If you run this example, all three lists are unpacked. Each individual item is passed to my_sum(), resulting in the following output:

만약 이를 실행 시킨다면, 모든 3개의 리스트들은 unpacked 상태이다. 이 각각의 아이템들은 my_sum()에게 전달하면 결과는 아래와 같을 것이다.

```shell script
$ python sum_integers_args_3.py
45
```

There are other convenient uses of the unpacking operator. For example, say you need to split a list into three 
different parts. The output should show the first value, the last value, and all the values in between. With the 
unpacking operator, you can do this in just one line of code:

```python
# extract_list_body.py
my_list = [1, 2, 3, 4, 5, 6]

a, *b, c = my_list

print(a)
print(b)
print(c)
```

In this example, my_list contains 6 items. The first variable is assigned to a, the last to c, and all other values 
are packed into a new list b. If you run the script, print() will show you that your three variables have the values 
you would expect:

위의 예제는 6개의 항목을 가진 리스트이다. 첫번 째 변수는 a에 할당되고, 마지막은 c에 할당 된다. 그리고 나머지 값들은 새로운 리스트 b에 뭉쳐진다. 만약 이를 
실행 시키면 다음과 같이 출력할 것이다.

```shell script
$ python extract_list_body.py
1
[2, 3, 4, 5]
6
```

Another interesting thing you can do with the unpacking operator * is to split the items of any iterable object. 
This could be very useful if you need to merge two lists, for instance:

다른 흥미로운 *연산자읭 특징은 어떠한 반복가능한 객체들을 쪼갤 수 있다. 이는 두개의 리스트를 합칠 때 유용하다.

```python
# merging_lists.py
my_first_list = [1, 2, 3]
my_second_list = [4, 5, 6]
my_merged_list = [*my_first_list, *my_second_list]

print(my_merged_list)
```

The unpacking operator * is prepended to both my_first_list and my_second_list.

unpacking 연산자 * 은 my_first_list 와  my_second_list에 사용된다.

If you run this script, you’ll see that the result is a merged list:

만약 이 코드를 실행시키면 아래와 같은 합성된 리스트를 얻을 수 있다.

```shell script
$ python merging_lists.py
[1, 2, 3, 4, 5, 6]
```

You can even merge two different dictionaries by using the unpacking operator **:

또한 ** 연산자를 통해 두 개의 딕셔너리를 합치는 것 또한 가능하다.

```python
# merging_dicts.py
my_first_dict = {"A": 1, "B": 2}
my_second_dict = {"C": 3, "D": 4}
my_merged_dict = {**my_first_dict, **my_second_dict}

print(my_merged_dict)
```

Here, the iterables to merge are my_first_dict and my_second_dict.

Executing this code outputs a merged dictionary:

여기 두 개의 딕셔너리를 합친 코드의 예제이다.

```shell script
$ python merging_dicts.py
{'A': 1, 'B': 2, 'C': 3, 'D': 4}
```

Remember that the * operator works on any iterable object. It can also be used to unpack a string:

연산자 *는 순환 간으한 모든 객체에서 사용이 가능해서 String에서 또한 사용이 가능하다.

```python
# string_to_list.py
a = [*"RealPython"]
print(a)
```

In Python, strings are iterable objects, so * will unpack it and place all individual values in a list a:

파이선에서 stringㄷ르은 반복 가능한 객체이다. 이를 리스트 대신해서 한번 사용해 보겠다.

```shell script
$ python string_to_list.py
['R', 'e', 'a', 'l', 'P', 'y', 't', 'h', 'o', 'n']
```

#### Conclusion
You are now able to use *args and **kwargs to accept a changeable number of arguments in your functions. You have also 
learned something more about the unpacking operators.

You’ve learned:

What *args and **kwargs actually mean
How to use *args and **kwargs in function definitions
How to use a single asterisk (*) to unpack iterables
How to use two asterisks (**) to unpack dictionaries
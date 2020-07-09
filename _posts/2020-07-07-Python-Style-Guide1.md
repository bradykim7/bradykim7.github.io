---
title: "Python-Style-Guide"
date: 2020-07-07
categories:
  - Python
  - Code
tags:
  - Python
---

### Python-Style-Guide
### Original from [HERE](https://www.analyticsvidhya.com/blog/2020/07/python-style-guide/) 

#### Introduction

This Article is focus on data science, but when talking with just code, it doesn't matter I think.


Have you ever come across a really poorly written piece of Python code? I’m talking about a tangled mess where you had to spend hours just trying to understand 
what piece of code goes where. I know a lot of you will nod your head at this.

한번 쯤 파이썬 코드가 아주 읽기 힘들게 작성된 것을 본적이 있는가? 뒤죽박죽 엉킨 코드를 의미하는 것이다. 단지 코드 조각이 어디로 가는지 이해하려고 몇 시간을 보내야 하는 그런 코드들 말이다.
그리고 많은 사람들이 이것에 고개를 끄덕일 것이라는 것을 안다.

Writing code is one part of a data scientist’s or analyst’s role. Writing beautiful and neat Python code, on the other hand, is a different ball game altogether. 
This could well make or break your image as a proficient programmer in the analytics or data science space (or even in software development).

코드 작성은 데이터 과학자 또는 분석가의 역할 중 하나이다. 반면에 아름답고 깔끔한 파이썬 코드를 쓰는 것은 완전히 다른 일이다. 
이렇게 생각하면 데이터 분석이나 데이터 사이언스에서 있는 저명한 프로그래머에 대한 이미지를 부실 수 도 있을 것이다.

Remember – our Python code is written once, but read a billion times over, potentially by viewers who are not accustomed to our style of programming. 
This takes on even more importance in data science. So how do we write this so-called beautiful Python code?

기억하자 - 우리의 파이썬 코드는 한번 작성되지만, 수천 수만번 읽히게 되고, 잠재적으로 프로그래밍에 익후사지 않은 사람들에 의해 읽혀진다.
이는 데이터 사이언스보다 더 중요하다. 그래서 어떻게 아름다운 파이썬 코드를 작성할 수 있을까? 

Welcome to the Python Style Guide!

#### Python Style Guide Contents

- Why this Python Style Guide is Important for Data Science?
- What is PEP8?
- Understanding Python Naming Conventions
- Python Style Guide’s Code Layout
- Getting Familiar with using Comments
- Whitespaces in your Python Code
- General Programming Recommendations for Python
- Autoformatting your Python code

##### Why this Python Style Guide is Important for Data Science?

데이터 사이언스 측면에서, 다른 스타일 가이드이기 때문에, 따로 해석 하지 않겠지만, 한번 읽어보는 정도는 좋겠다.

There are a couple of reasons that make formatting such an important aspect of programming, especially for data science projects:

- Readability
    + Good code formatting will inevitably improve the readability of your code. This will not only present your code as more organized but will also make it 
    easier for the reader to easily understand what is going on in the program. This will especially be helpful if your program runs into thousands of lines. 
    With so many dataframe, lists, functions, plots, etc. you can easily lose track of even your own code if you don’t follow the correct formatting guidelines!

- Collaboration
    + If you are collaborating on a team project, which most data scientists will be, good formatting becomes an essential task. This makes sure that the code 
    is understood correctly without any hassle. Also, following a common formatting pattern maintains consistency in the program throughout the project lifecycle.

- Bug fixes
    + Having a well-formatted code will also help you when you need to fix bugs in your program. Wrong indentation, improper naming, etc. can easily make debugging 
    a nightmare! Therefore, it is always better to start off your program on the right note!

With that in mind, let’s have a quick overview of the PEP-8 style guide we will cover in this article!

##### What is PEP8?

PEP-8, or Python Enhancement Proposal, is the style guide for Python programming. It was written by Guido van Rossum, Barry Warsaw, and Nick Coghlan. 
It describes the rules for writing a beautiful and readable Python code.

PEP-8, 나 Python Enhancement Proposal 는 파이썬 프로그래밍을 위한 스타일 가이드이다. 이는 Guido van Rossum, Barry Warsaw, 와 Nick Coghlan 가 작성했다.
이는 좋은 파이썬 코드 작성을 위해 묘사되어있다.

Following the PEP-8 style of coding will make sure there is consistency in your Python code, making it easier for other readers, contributors, or yourself, 
to comprehend it.

PEP-8 스타일의 코딩을 따르면 Python 코드에 일관성이 있는지 확인하여 다른 작성자, 기여자 또는 자신이 쉽게 이해할 수 있도록 할 것이다.

This article covers the most important aspects of the PEP-8 guidelines, like how to name Python objects, how to structure your code, when to include comments 
and whitespaces, and finally, some general programming recommendations that are important but easily overlooked by most Python programmers.

이 포스팅은 PEP-8 가이드 라인에서 가장 중요한 측면들 즉, 파이썬 객체 네이밍, 코드의 구조, 주석 포함하거나, 빈 공간 같은 측면들 다룰 것이고, 몇몇의 파이선 프로그래머들이 쉽게 간과 하는 일반적인 코드 작성법 들을 다룰 것이다.

Let’s learn to write better code!

이제 어떻게 더 나은 코드를 작성할 수 있는지 알아보자 ! 

The official PEP-8 documentation can be found [here](https://www.python.org/dev/peps/pep-0008/).

##### Understanding Python Naming Conventions

```python
# Function 1
def func(x):
   a = x.split()[0]
   b = x.split()[1]
   return a, b
print(func('Analytics Vidhya'))

# Function 2
def name_split(full_name):
   first_name = full_name.split()[0]
   last_name = full_name.split()[1]
   return first_name, last_name
print(name_split('Analytics Vidhya'))
```

Both the functions do the same job, but the latter one gives a better intuition as to what it is happening under the hood, even without any comments! 
That is why choosing the right names and following the right naming convention can make a huge difference while writing your program. That being said, 
let’s look at how you should name your objects in Python!

위에 있는 두가지 함수는 같은 역할을 한다. 하지만 후자의 것은 어떤 일들을 하는지 어떠한 설명도 없어도 무슨 일을 하는지 알 수 있다.
이 때문에, 왜 올바름 이름과 더불어 작명에 대한 습관이 잘 따라와야 되는지 중요해지는 것이다. 이제 어떻게 파이썬에서 객체들을 명명하는지 알아보자.
 
###### General Tips to Begin With
These tips can be applied to name any entity and should be followed religiously.

- Try to follow the same pattern – consistency is the key! 같은 패턴을 계속 유지한다.
```python
thisVariable, ThatVariable, some_other_variable, BIG_NO
```
- Avoid using long names while not being too frugal with the name either. 너무 긴 이름은 사용을 지양한다.
```python
this_could_be_a_bad_name = “Avoid this!”
t = “This isn\’t good either”
```
- Use sensible and descriptive names. This will help later on when you try to remember the purpose of the code. 간결하고 묘사가 좋은 네이밍이 필요하다. 코드의 목적을 기억하기 쉽다.
```python
X = “My Name”  # Avoid this
full_name = “My Name”  # This is much better
```
- Avoid using names that begin with numbers. 숫자로 시작하는 네이밍을 지양해라.
```python
1_name = “This is bad!”

```
- Avoid using special characters like @, !, #, $, etc. in names 특수문자 를 사용하는 것을 지양해야한다.
```python
phone_ # Bad name
```

###### Naming Variables

- Variable names should always be in lowercase. 항상 변수 이름은 소문자를 사용한다.
```python
blog = "Analytics Vidhya"
```
- For longer variable names, include underscores to separate_words. This improves readability. 긴 변수이름은 항상 _ 를 사용해서 사용한다. 가독성을 높여준다.
```python
awesome_blog = "Analytics Vidhya"
```
- Try not to use single-character variable names like ‘I’ (uppercase i letter), ‘O’ (uppercase o letter), ‘l’ (lowercase L letter). They can be indistinguishable from numerical 1 and 0. Have a look:
- 혼동할 수 있는 문자를 사용하지 않는다. 영어에서  I, 0 , O , 1 과 같은 것은 구별하기 힘들다.
```python
O = 0 + l + I + 1
```

- Follow the same naming convention for Global variables. 글로별 변수들도 이를 준수해야한다.

###### Naming Functions

- Follow the lowercase with underscores naming convention. 함수 네이밍 또한 소문자 사용과 언더바 '_' 규칙을 준수한다.
- Use expressive names. 좋은 이름을 사용한다.

```python
# Avoid
def con():
    ...
# This is better.
def connect():
    ...
```

- If a function argument name clashes with a keyword, use a trailing underscore instead of using an abbreviation.
 For example, turning break into break_ instead of brk. 만약 함수 매겨변수의 이름과 함수의 이름이 유사하다면, 언더바를 사용한다. 아래의 예제를 살펴보자.
 
```python
# Avoiding name clashes.
def break_time(break_):
    print(“Your break time is”, break_,”long”)
```

###### Class names

- Follow CapWord (or camelCase or StudlyCaps) naming convention. Just start each word with a capital letter and do not include underscores between words. 
- 클래스 네이밍은 CapWord, camelCase, StudlyCaps 방식의 네이밍을 사용한다. 각각 단어의 시작을 대문자로 시작하고 , 나머지 글자는 소문자로 표기한다.

```python
# Follow CapWord convention
class MySampleClass:
    pass
```

- If a class contains a subclass with the same attribute name, consider adding double underscores to the class attribute.
- 클래스가 하위 클래스를 가지고 있고, 같은 속성의 이름이 존재한다면, '__'를 사용하여 클래스의 속성을 구분한다.

This will make sure the attribute __age in class Person is accessed as _Person__age. This is Python’s name mangling and it makes sure there is no name collision
이는 속성 __age를 _Person__age로 접근가능하게 해줄 것이다. 이는 파이썬 적인 관리이고, 이름 충돌이 일어나지 않게 해준다.

```python
class Person:
    def __init__(self):
        self.__age = 18

obj = Person() 
obj.__age  # Error
obj._Person__age  # Correct
```

- Use the suffix “Error” for exception classes
- 예외 처리시에는 “Error” 를 사용한다. 

```python
class CustomError(Exception):
    “””Custom exception class“””

```

###### Naming Class Methods

- The first argument of an instance method (the basic class method with no strings attached) should always be self. This points to the calling object
- 인스턴스 매소드의 첫번째 매개변수는 거의 항상 self 이다. 이는 호출 객체를 가리킨다.

- The first argument of a class method should always be cls. This points to the class, not the object instance
- 클래스 매소드의 첫번째 매개변수의 이름은 항상 'cls'이다. 이는 클래스를 가리키며, 오브젝트의 인스턴스를 가리키지않는다.

```python
class SampleClass:
    def instance_method(self, del_):
        print(“Instance method”)

    @classmethod
    def class_method(cls):
        print(“Class method”)
```

###### Package and Module names

- Try to keep the name short and simple
- The lowercase naming convention should be followed
- Prefer underscores for long module names
- Avoid underscores for package names

모듈과 페키지 이름은 아래와 같은 조건을 지킨다.
- 가능한 간결한 이름을 사용한다.
- 소문자만 사용하여 이름 짓는다.
- 긴 모듈의 이름 같은 경우 '_'를 사용한다.
- 페키지 이름 같은 경우는 '_'를 지양한다.

```python
testpackage # package name
sample_module.py # module name
```

###### Constant names

- Constants are usually declared and assigned values within a module
- The naming convention for constants is an aberration. Constant names should be all CAPITAL letters
- Use underscores for longer names

- 상수는 대부분 모듈안에 할당되어 선언한다.
- 네이밍은 좀 다른 방식을 사용하는데, 모든 문자를 대문자로 표현한다.
- 마찬가지로 긴 네이밍에는 '_'를 이용한다.

```python
# Following constant variables in global.py module
PI = 3.14
GRAVITY = 9.8
SPEED_OF_Light = 3*10**8
```
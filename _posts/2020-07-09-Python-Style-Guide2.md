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

##### Python Style Guide’s Code Layout

Now that you know how to name entities in Python, the next question that should pop up in your mind is how to structure your code in Python!  
Honestly, this is very important, because without proper structure, your code could go haywire and can be the biggest turn off for any reviewer.

그전 포스팅에서 파이선 네이밍에 관해 알아보았다. 다음 질문은 어떻게 파이썬 코드의 구조를 적절하게 구성하는가? 이다. 이는 매우 중요하고, 적절한 구조 없이는 너의 코드가 잘못될 수 있고, 리뷰어들에게 외면받게 될 것이다.
  
So, without further ado, let’s get to the basics of code layout in Python!

자 그럼 이제부터 어떻게 해야하는지 알아보자 ! 

###### Indentation

It is the single most important aspect of code layout and plays a vital role in Python. Indentation tells which lines of code are to be included in the block 
for execution. Missing an indentation could turn out to be a critical mistake.

들여쓰기는 파이썬에 있어서 코드 구성 측면이나, 역할에 있어서 상당히 중요한 역할을 담당한다. 들여쓰기는 어떤 블록에 해당되어 있는지 우리에게 알려준다. 들여쓰기를 까먹는다는 것은  상당히 치명적인 실수를 저지른다는 것이다.

Indentations determine which code block a code statement belongs to. Imagine trying to write up a nested for-loop code. Writing a single line of code outside 
its respective loop may not give you a syntax error, but you will definitely end up with a logical error that can be potentially time-consuming in terms of 
debugging.

들여쓰기는 코드 블록이 어떤 곳에 소속 되어지는지를 결정한다. for-loop를 작성한다고 생각해보자. 한줄로 이 코드를 작성하는 것은 어떠한 구문오류를 만들지 않지만, 결정적으로 논리적 오류를 범할 수 있고, 이는 
디버깅시에 엄청난 시간을 소요하게 될 것이다.

Follow the below mentioned key points on indentation for a consistent structure for your Python scripts.

아래에의 들여쓰기 키포인트 들을 지켜서 파이선 스크립트의 구조를 지키자.

- Always follow the 4-space indentation rule, 항상 들여쓰기는 4개의 space를 기본으로한다.
```python
# Example
if value<0:
    print(“negative value”)

# Another example
for i in range(5):
    print(“Follow this rule religiously!”)
```

- Prefer to use spaces over tabs , TAB 보다는 Space를 사용하자.

It is recommended to use Spaces over Tabs. But Tabs can be used when the code is already indented with tabs.
TAB 키보다 Space 바를 사용하는 것을 추천한다. 하지만 이미 코드가 tab으로 만들어져있다면, 그대로 사용하자.

```python
if True:
    print('4 spaces of indentation used!')
```

- Break large expressions into several lines. 긴 표현식은 , 각각 구별된 라인으로 쪼개자.

There are several ways of handling such a situation. One way is to align the succeeding statements with the opening delimiter.

이를 다루는 여러 상황이 있다. 하나는 아래와 같은 상황이다. 하나의 방법은 괄호가 시작되는 지점을 기준으로 들여쓰기 하는 방식이다.
```python
# Aligning with opening delimiter.
def name_split(first_name,
               middle_name,
               last_name)

# Another example.
ans = solution(value_one, value_two,
               value_three, value_four)
```

A second way is to make use of the 4-space indentation rule. This will require an extra level of indentation to distinguish the arguments from the rest of the code inside the block.

다른 해결 방법은, 단지 4-space 으로 구별짓는 것이다. 

```python
# Making use of extra indentation.
def name_split(
        first_name,
        middle_name,
        last_name):
    print(first_name, middle_name, last_name)
```

Finally, you can even make use of “hanging indents”. Hanging indentation, in the context of Python, refers to the text style where the line containing a 
parenthesis ends with an opening parenthesis. The subsequent lines are indented until the closing parenthesis.

본문에서는 어려운 말로 설명하고 있지만, 이는 뭐 괄호 시작시에 다음 줄로 내려가 tab으로 부분지어 파라미터들을 대입하고, 마지막 파라미터에서 괄호를 닫는 형식을 사용하면 좋다는 뜻이다.

```python
# Hanging indentation.
ans = solution(
    value_one, value_two,
    value_three, value_four)
```

- Indenting if-statements can be an issue, IF문에서의 들여쓰기 오류.

if-statements with multiple conditions naturally contain 4 spaces – if, space, and the opening parenthesis. As you can see, this can be an issue. 
Subsequent lines will also be indented and there is no way of differentiating the if-statement from the block of code it executes. Now, what do we do?

위에 설명하것처럼 IF문을 작성시에 문제가 생길 수 있다. 아래의 예제를 보면 바로 드러나는 사실이다. 그렇다면 우리는 어떻게 해야할까? 

Well, we have a couple of ways to get our way around it:

```python
# This is a problem.
if (condition_one and
    condition_two):
    print(“Implement this”)
```

One way is to use an extra level of indentation of course!

좀 더 높은 차원의 들여쓰기 래밸을 사용하면 된다. 

```python
# Use extra indentation.
if (condition_one and
        condition_two):
    print(“Implement this”)
```

Another way is to add a comment between the if-statement conditions and the code block to distinguish between the two:

다른 방법은 주석을 추가하여, 혼동을 막는 방법이다.

```python
# Add a comment.
if (condition_one and
    condition_two):
    # this condition is valid
    print(“Implement this”)
```

- Brackets need to be closed. 괄호는 항상 닫혀야한다.

Let’s say you have a long dictionary of values. You put all the key-value pairs in separate lines but where do you put the closing bracket? 
Does it come in the last line? The line following it? And if so, do you just put it at the beginning or after indentation?

만약 긴 값들을 가진 dict 변수를 가지고 있다고 가정해보자. 너가 각각의 라인별로 Key , Values 값들을 넣어서 완성했다면, 닫는 괄호는 어디에 넣어야할까?
마지막 라인 ? 아니면 마지막 변수의 라인 ? 맨마지막 라인이라면 띄어쓰기를 해야할까 말아야할까 ?

There are a couple of ways around this problem as well.

이를 해결하는 방법은 여러 방법이 있다. 

One way is to align the closing bracket with the first non-whitespace character of the previous line.
하나의 방법은 마지막 변수의 다음 라인에 들여쓰기를 한 후 닫는 괄호를 추가하는 방법이다.

```python
# 
learning_path = {
    ‘Step 1’ : ’Learn programming’,
    ‘Step 2’ : ‘Learn machine learning’,
    ‘Step 3’ : ‘Crack on the hackathons’
    }
```

The second way is to just put it as the first character of the new line.
두번째 방법은 마지막 밸류의 다음 라인에 괄호를 닫는 것이다.

```python
learning_path = {
    ‘Step 1’ : ’Learn programming’,
    ‘Step 2’ : ‘Learn machine learning’,
    ‘Step 3’ : ‘Crack on the hackathons’
}
```

- Break line before binary operators. 이진 연산자가 나오기전에 다음줄로 넘어가자!

If you are trying to fit too many operators and operands into a single line, it is bound to get cumbersome. Instead, break it into several lines for better 
readability.

너무 많은 연산자들이 한줄에 있다면 거추장스러워 보일 수 있다. 이를 좀더 좋게 하려면 한줄 한줄에 연산자를 넣어, 가독성을 좋게 하는 방법도 있다.

Now the obvious question – break before or after operators? The convention is to break before operators. This helps to easily make out the operator and the
 operand it is acting upon.

그렇다면 분명한 질문이 생길 것이다. 연산자가 나온 전에 라인을 나눌까? 아니면 연산자가 나온 후에 라인을 나눠야할까?. 관행적으로는 연산자가 나오기 전에 줄을 나눈다.

```python
# Break lines before operator.
gdp = (consumption
      + government_spending
      + investment
      + net_exports
      )
```

###### Using Blank Lines

Bunching up lines of code will only make it harder for the reader to comprehend your code. One nice way to make your code look neater and pleasing to the eyes
 is to introduce a relevant amount of blank lines in your code.

여러줄의 코드는 읽기도 힘들뿐만 아니라 이해하기도 힘들어진다. 이를 좀더 나이스하고 정갈하게 보여주는 방법은 공백줄을 너의 코드안에서 사용하는 것이다.

- Top-level functions and classes should be separated by two blank lines. 
- 상위의 함수나 클래스들은 두개의 공백줄로 구분한다.

```python
# Separating classes and top level functions.
class SampleClass():
    pass


def sample_function():
    print("Top level function")
```

- Methods inside a class should be separated by a single blank line
- 클래스 안의 메소드들은 하나의 공백줄로 구분한다.

```python
# Separating methods within class.
class MyClass():
    def method_one(self):
        print("First method")

    def method_two(self):
        print("Second method")
```

Try not to include blank lines between pieces of code that have related logic and function

연관된 로직이나 함수들은 공백줄로 구분하지 않는다.

```python
def remove_stopwords(text): 
    stop_words = stopwords.words("english")
    tokens = word_tokenize(text) 
    clean_text = [word for word in tokens if word not in stop_words] 
      
    return clean_text
```

Blank lines can be used sparingly within functions to separate logical sections. This makes it easier to comprehend the code

공백줄들은 함수나 로직을 나누는데 사용한다. 이는 좀더 코드를 이해하기 쉽게 해준다.

```python
def remove_stopwords(text): 
    stop_words = stopwords.words("english")
    tokens = word_tokenize(text) 
    clean_text = [word for word in tokens if word not in stop_words] 

    clean_text = ' '.join(clean_text)
    clean_text = clean_text.lower()

    return clean_text
```

###### Maximum line length

- No more than 79 characters in a line
- 한줄에 79 캐릭터 이상을 작성하지 않도록한다.
 
When you are writing code in Python, you cannot squeeze more than 79 characters into a single line. That’s the limit and should be the guiding rule to keep 
the statement short.

파이썬 코드를 작성할때 79캐릭터 글자수 이상을 한줄에 적지 못한다. 이는 제한되어 있고, 짧고 간결한 코드를 작성하도록 권유한다.

- You can break the statement into multiple lines and turn them into shorter lines of code
- 하나의 상태를 여러 개의 라인으로 조개고 이를 좀더 짧은 코드로 만든다.

```python
# Breaking into multiple lines.
num_list = [y for y in range(100) 
            if y % 2 == 0 
            if y % 5 == 0]
print(num_list)
```

###### Imports

Part of the reason why a lot of data scientists love to work with Python is because of the plethora of libraries that make working with data a lot easier. 
Therefore, it is given that you will end up importing a bunch of libraries and modules to accomplish any task in data science.

데이터 과학자들이 파이썬으로 일하는것을 좋아하는 이유는 많은 라이브러리와 프레임워크들이 데이터를 다루기 쉽게 해주기 때문이다. 그러므로 너는 많은 수의 모듈과 라이브러리들을 상속하는 것을 잘해야한다.

- Should always come at the top of the Python script
- Separate libraries should be imported on separate lines

- 항상 파이선 스크립트 처음에 나와야한다.
- 다른 라이브러리에서 상속된 것은 각각 다른 줄에 표기되어야한다.

```python
import numpy as np
import pandas as pd

df = pd.read_csv(r'/sample.csv')
```

- Imports should be grouped in the following order:
    * Standard library imports
    * Related third party imports
    * Local application/library specific imports
   
- 상속은 다음과 같은 그룹화 규칙을 지킨다.
    * 표준 라이브러리
    * 서드파티 상속
    * 로컬 어플리케이션/ 라이브러리 상속
    
- Include a blank line after each group of imports

```python
import numpy as np
import pandas as pd
import matplotlib
from glob import glob
import spaCy 
import mypackage
```

- Can import multiple classes from the same module in a single line
- 같은 모듈에서 상속 받는 것은 한줄에 작성한다.

```python
from math import ceil, floor
```

##### Getting Familiar with using Comments

Understanding an uncommented piece of code can be a strenuous activity. Even for the original writer of the code, it can be difficult to remember what 
exactly is happening in a code line after a period of time.

주석이 없는 코드를 한번에 이해하는 것은 상당한 에너지를 요구한다. 심지어 원래 코드를 작성한 사람도 다시 코드를 살펴봐서 코드에 대한 이해를 하기 위해 상당한 노력이 필요하다.

Therefore, it is best to comment on your code then and there so that the reader can have a proper understanding of what you tried to achieve with that
 particular piece of code.

그래서 코드에 주석을 다는 것은 좀 더 코드를 일기 쉽게 하고, 이해하기 쉽게 해줄 것이다.

###### General Tips for Including Comments

- Always begin the comment with a capital letter
- Comments should be complete sentences
- Update the comment as and when you update your code
- Avoid comments that state the obvious
 
 일반적인 코드 주석의 팁
 - 항상 대문자로 시작한다.
 - 주석은 완성된 문장의형태로 적는다.
 - 너가 코드를 업데이트할때 마다 주석도 업데이트하라.
 - 분명한 사실을 적는 주석은 피해라.
 
###### Block Comments

- Describe the piece of code that follows them
- Have the same indentation as the piece of code
- Start with a # and a single space

- 다음에 따라오는 코드에 대한 주석이다
- 같은 들여쓰기를 가진 코드들에 대한 주석이다.
- # 과 한번의 Space 로 시작한다.

```python
# Remove non-alphanumeric characters from user input string.
import re

raw_text = input(‘Enter string:‘)
text = re.sub(r'\W+', '  ', raw_text)
```

###### Inline comments

- These are comments on the same line as the code statement
- Should be separated by at least two spaces from the code statement
- Starts with the usual # followed by a whitespace
- Do not use them to state the obvious
- Try to use them sparingly as they can be distracting

해당 줄에 대한 주석
- 이러한 주석은 코드와 같은 줄에 작성한다.
- 적어도 2개의 space를 만든 후 주석을 작성한다.
- 대부분 # 과 하나의 space '# ' 로 시작한다.
- 항상 너무 명확한 사실에 대한 주석은 작성하지 않는다.
- 주석이 과하다 싶을 정도로는 사용하지 말자.

```python
info_dict = {}  # Dictionary to store the extracted information
```

###### Documentation String

- Used to describe public modules, classes, functions, and methods
- Also known as “docstrings”
- What makes them stand out from the rest of the comments is that they are enclosed within triple quotes ”””
- If docstring ends in a single line, include the closing “”” on the same line
- If docstring runs into multiple lines, put the closing “”” on a new line

문서 문자열 형태
- public 모듈 클래스 함수 메소드들을 묘사할때 사용한다.
- docstring이라고도 부루린다.
- 이 주석을 표기할때는 """ 으로 시작하고 끝맺음한다.
- 만약 한줄 짜리 주석이라면 같은 줄에 """ 과 """을 사용한다.
- 여러 줄이라면 닫는 """은 다음줄에 표시한다.

```python
def square_num(x):
    """Returns the square of a number."""
    return x**2

def power(x, y):
    """Multiline comments.
       Returns x raised to y.
    """
    return x**y
```
    
##### Whitespaces in your Python Code

- Avoid putting whitespaces immediately within brackets
- 빈 공간은 괄호 바로 뒤에 나오지 않게 한다 .

```python
# Correct way
df[‘clean_text’] = df[‘text’].apply(preprocess)
```

- Never put whitespace before a comma, semicolon, or colon
- 절때로 빈 공간을 ',', ';', ':' 앞에 오지 않게 한다.

```python
# Correct
name_split = lambda x: x.split()
# Correct
```

- Don’t include whitespaces between a character and an opening bracket
- 문자 사이나 여는 괄호에 절때로 빈 공간을 포함시키지 않는다.

```python
# Correct
print(‘This is the right way’)
# Correct
for i in range(5):
    name_dict[i] = input_list[i]
```

- When using multiple operators, include whitespaces only around the lowest priority operator
- 여러개의 연산자를 사용할때 낮은 우선순위의 연산자를 표시할 때 빈 공간을 사용한다.
```python
# Correct
ans = x**2 + b*x + c
```

- In slices, colons act as binary operators
- 문자열 slice 에서는 ':'이 이진 연산자 처럼 사용된다.

They should be treated as the lowest priority operators. Equal spaces must be included around each colon

귿르은 가장 낮은 우선순위 연산자로 여겨져야한다. 같은 수의 Space가 항상 ':'을 둘러싸고 있어야한다.

```python
# Correct
df_valid = df_train[lower_bound+5 : upper_bound-5]
```

- Trailing whitespaces should be avoided
- Don’t surround = sign with whitespaces when indicating function parameters

- 마지막을 space로 끝내지 말아라
- 함수의 파라미티에서 '='를 사용할 때, 빈공간으로 둘러싸지말아라.

```python
def exp(base, power=2):
    return base**power
```

- Always surround the following binary operators with single whitespace on either side:
    * Assignment operators (=, +=, -=, etc.)
    * Comparisons (==, <, >, !=, <>, <=, >=, in, not in, is, is not)
    * Booleans (and, or, not)

- 항상 다음의 연산자들은 space 로 둘러 쌓여 있어야한다.
    * 할당 연산자 (=, +=, -=, etc.)
    * 비교 연산자 (==, <, >, !=, <>, <=, >=, in, not in, is, is not)
    * 참 거짓 연산자 (and, or, not)
    
```python
# Correct
brooklyn = [‘Amy’, ‘Terry’, ‘Gina’, 'Jake']
count = 0
for name in brooklyn:
    if name == ‘Jake’:
        print(‘Cool’)
        count += 1
```

##### General Programming Recommendations for Python

Often, there are a number of ways to write a piece of code. And while they achieve the same task, it is better to use the recommended way of writing cleaner code 
and maintain consistency. I’ve covered some of these in this section.

우리는 수많은 코드를 작성한다. 그리고 우리는 그 일을 수행할 때, 더 깨끗하고, 유지하기 쉬운 코드를 작성하는것이 좋다. 다음은 이를 위한 팁들이다.

- For comparison to singletons like None, always use is or is not. Do not use equality operators
- 비교를 위한 싱글톤 들 None 꽈 같은 것은 'is not'을 사용해라. '!=' 연산자를 버리고 ! 

```python
# Wrong
if name != None:
    print("Not null")
# Correct
if name is not None:
    print("Not null")
```

- Don’t compare boolean values to TRUE or FALSE using the comparison operator. While it might be intuitive to use the comparison operator, it is unnecessary 
to use it. Simply write the boolean expression

- boolean 값을 비교 연산자를 사용해서 사용하지 말아라. 그러니깐 간단하게 표기하라는 말이다. 굳이 boolean 타입을 참, 거짓을 판별할 이유는 없다. 

```python
# Correct
if valid:
    print("Correct")
# Wrong
if valid == True:
    print("Wrong")
```

- Instead of binding a lambda function to an identifier, use a generic function.  Because assigning lambda function to an identifier defeats its purpose. 
And it will be easier for tracebacks

- Lambda 함수를 바인딩하기 이전에 제네릭 함수를 이용하자. Lambda 함수를 할당하는 것은 그 목적성을 잃어버리기 때문이다. 

```python
# Prefer this
def func(x):
    return None

# Over this
func = lambda x: x**2
```

- When you are catching exceptions, name the exception you are catching. Do not just use a bare except. 
This will make sure that the exception block does not disguise other exceptions by KeyboardInterrupt exception when you are trying to interrupt the execution.

- Try, except 구문 작성시 Exception에 대한 이름을 작성해라. 아무것도 적지않은체로 방치하지말고. 이는 exception 상황발생시 정확한 원인을 찾는데 혼동을 줄 수 있다.

```python
try:
    x = 1/0
except ZeroDivisionError:
    print('Cannot divide by zero')
```

- Be consistent with your return statements. That is to say, either all return statements in a function should return an expression or none of them should. 
Also, if a return statement is not returning any value, return None instead of nothing at all

- retrun 상태에 대해 일관성을 유지해라. 리턴 상태를 가진 함수에서는 반드시 return 값이 존재해야한다. 또한 return 상태에서 어떠한 것도 리턴하지 않을 때, 적어도 아무것도 적는 것이 아닌 'None'을 리턴하자.

```python
# Wrong
def sample(x):
    if x > 0:
        return x+1
    elif x == 0:
        return
    else:
        return x-1

# Correct
def sample(x):
    if x > 0:
        return x+1
    elif x == 0:
        return None
    else:
        return x-1
```

- If you are trying to check prefixes or suffixes in a string, use ”.startswith() and ”.endswith() instead of string slicing.
 These are much cleaner and less prone to errors

- 만약 string 에서 접두사나 접미사를 찾고자 할 때는, 슬라이싱을 하기보다 ”.startswith() 와 ”.endswith() 함수를 사용해서 찾자. 이는 좀더 용이하고 에러의 가능성을 낮춰준다.

```python
# Correct
if name.endswith('and'):
    print('Great!')
```
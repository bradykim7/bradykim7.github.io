---
title: "Python Classes The Basic"
date: 2020-06-11
categories:
  - Python
tags:
  - Python
---

### Python Classes The Basic
### Original from [HERE](https://heartbeat.fritz.ai/python-classes-the-basics-ae221afcc450)


#### Introduction


Below is a conversation about python class basics. To help follow along, you may need to understand Python functions.

아래의 대화는 파이썬 베이직클래스에서의 대화내용이다. 파이썬 기능들을 이해하는데 도움이 될 것이야~

Anita: Hi DarkAnita. I’ve been trying to improve my Python skills by using Python classes, but it just looks so much like gibberish to me. Python functions, I totally understand those…but classes? Do you understand them?

Anita: 안녕 DarkAnita. 파이선 수업들을 들으면서 파이썬 스킬을 높이고 싶은데, 뭐라고 나한테 주절주절 떠드는지 모르겠어. 특히 파이썬 함수들, 나는 그것들이 클래스라고 이해했는데, 너는 그것들을 이해하고 있어 ...?

DarkAnita: True, Python classes are not very intuitive at first glance. But if you understand each component, you will appreciate them even more. Let's take a step back to define what Python is.

DarkAnita: 맞는말이야. 파이썬의 클래스들은 잠깐 힐끗 봐서는 알 수가 없지. 하지만 너가 가각의 구성요소들을 이해한다면, 너가 더 쉽게 이해할 수 있을꺼야. 잠깐 한걸음 물러서서 파이썬이 무엇인지 알아보자.

Anita: Python is an object-oriented programming language.

Anita: 파이썬은 객체지향 프로그래밍 언어야.

DarkAnita: Perfect. Since Python is an object-oriented programming language, it’s no surprise then that almost everything in Python is an object. This definition resonates even more when talking about Python classes.

DarkAnita: 맞아. 파이썬이 객체 지향 프로그래밍 언어이기 때문에, 파이썬의 모든 것들은 객체인 것이 당연한거지. 이러한 정의로 인해서 파이썬의 클래스들도 객체임을 말할 수 있지.

Anita: How?

Anita: 어떻게?

DarkAnita: It will make more sense once you know what a Python class is…

DarkAnita: 파이썬의 클래스가 뭔지를 알면 이해하기 쉬울 거야. 파이썬 클래스는 ...

A Python class is a technique used to logically organize data and functions in ways that make them easy to reuse and extend in the future. Technically, it’s the blueprint for creating Python objects.

파이썬의 클래스는 논리적으로 조직된 데이터들과 함수들은 확장과 재사용에 용이하게 하는 기술이다. 기술적으로 이는 파이썬 객체 만들기 위한 청사진이다. 
 
A Python object, on the other hand, is a particular instance of a class. In other words, an implementation or product of a class. For example, a class can be a Car blueprint, and the different cars built with the help of that blueprint design are instances of the class or objects.

다른 한편으로, 파이썬 객체는 클래스의 특정 인스턴스이다. 다시말해서, 클래스의 생산 혹은 실행임을 뜻한다. 예를 들어, 클래스는 자동차의 청사진이 될 수 있다. 그리고 각각 다른 차들은 청사진의 도움을 받아서 생성된 클래스나 객체의 인스턴스 이다.

Let's consider the car analogy a bit further:

차에 대한 비유를 좀 더 생각해보자.

A car built from a blueprint has certain characteristics and functionalities. Some characteristics include the color of the car, its energy source, capacity, price, etc. And some functionalities include that it can move, be upgraded(or pimped), the value can change, etc.

청사진(설계도)으로 만들어진 차는 어떤 특징과 기능들을 가지고 있다. 어떤 특징은 차의 색깔을 ,에너지원을, 용량, 가격 등을 말할 수 있다. 그리고 값이 변할수 있는지, 움직일 수 있는지, 업그레이드 할수 있는 기능들이 있다. 

Just like a car, a Python object has these two components, also known as attributes and methods.

자동차와 마찬가지로, 파이썬의 객체들도 두가지의 구성원이 있다. 잘알려진 애트리뷰트(속성) 와 매소드 이다.

An attribute refers to the characteristics of an object, while a method is more like the behavior or actions of an object. Characteristics are mostly nouns, while behaviors are generally verbs. 
When thinking about the components of a Python object, you can ask yourself questions like:

속성은 객체의 특징을 말하고 , 반면에 매소드는 객체의 행동이나 액션을 말한다. 특징은 좀 더 명사적이고, 행동은 동사적인 의미가 강하다. 우리가 파이썬 객체의 구성을 생각해 볼때, 너는 이렇게 질문 하는 것이 좋다.

* What does the object of the class have? i.e attributes
* What can that object of the class do? i.e method

* 객체의 클래스가 가지고 있는 것은 무엇인가?  애트리뷰트, 속성
* 객체의 클래스가 무엇을 하는가? 매소드 

Anita: Ah I see. Just to be sure I understand what a Class is based on the Car Analogy;

Anita: 아 알겠다. 차에 비유하면서 클래스를 이해한 것 같아.

In a Car factory, the car blueprint (which is the class) is to produce certain specifications of cars (which are the objects). 
Each car has a color, price, energy source, etc (which are the attributes), and each car can be upgraded and can have a price change ( which are the methods).

차 공장에서, 어떤 특징을 가진(객체) 자동차를 생산하기 위한 것이 자동차 설계(클래스)이다. 각각의 차는 색, 가격, 에너지원 등고(애트리뷰트, 속성)을 가지고 있고, 그리고 각가의 차는 업그래이드 되거나 가격이 변할 수 있다.(매소드)

DarkAnita: Exactly.

DarkAnita: 정확해 !

Here is a visual representation of a **class car** blueprint that produces other cars:

여기 다른 종류의 자동차를 생산하기 위한 설계도 즉, 자동차클래스를 시각화 해서 보여주겠다.

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p5.jpg" alt="">

In Python, a method is a Python function within a class. This is why a class is more of an organization of similar functions. 
With that in mind, this is what a typical class look like:

파이썬에서, 클래스안에 있는 파이썬의 함수를 매소드라고 부른다. 이것이 왜 클래스가 다른 함수들보다 더 조직적인지를 보여주는 이유이다. 이를 명심하고, 아래에 전형적인 파이선의 클래스를 살펴보자

```python
class class_name:
    """the class_name wnts to do something"""

    def __init__(self, attribute_1, atrribute_2):
        pass
    def second_method(self):
        pass
```

If you notice, there are 2 methods (functions in a class) in the above example. What else do you notice?

알아차렸다면, 2개의 메소드(클래스내의 함수)가 위의 예제에 있다. 그리고 다른 것도 찾을 수 있는가 ?

Anita: I notice five things

* The class command
* The two functions or methods
* The __init__ keyword
* The self parameter
* And the attribute 1,2 parameters

Anita: 5개를 찾을 수 있지
 
* class 명령어 
* 두개의 함수 혹은 매소드
* __init__ 키워드 
* self 라는 파라미터 
* attribute1 ,2 라는 파라미터들 

DarkAnita: Good observation.

DarkAnita: 좋은 관찰력이야 ! 

Let’s discuss each of these in more detail.

좀 더 디테일하게 다뤄 보자.

The **class** command/keyword is used to tell Python that you want to define a class or a blueprint. This **class** keyword must 
be followed by a **class_name** ( preferably a descriptive name). Conventionally, a class name uses a CamelCase format.

**class** 커맨드/키워드 는 파이썬에게 내가 어던 클래스(청사진)을 만들고 싶을때 사용한다. **class** 키워드는  항상 **class_name**(클래스의 이름)이 있어야한다. 관습적으로, 클래스의 이름은
CamelCase형식을 사용한다.

The **__init__()** method, also known as the initializer method, is used to initialize objects or help in building an object’s foundation. 
This instance method is where the object is built, along with all its attributes. This initializer method must be called **__init__()**, 
and there’s a 고 **self** argument this method takes. It is also the first argument and helps to differentiate and locate one object from another. 
The **__init__()** method is also the method that holds the attribute arguments and states the attributes of an object instantiated.

**__init__()** 메소드는, 초기화 메소드로 알려져있지, 그리고 객체를 초기화 할 때 사용하거나 혹은 객체의 기초를 만드는 것을 도와주지. 이 인스턴스 매소드는 객체가 모든 속성들과 함께
구체화 되는 곳이다. 이 초기화 메소드는 반드시 **__init__()**를 호출해야하고 의무적으로 **self** 라는 매개변수를 이 메소드는 가져야한다. 이는 첫번째 매개변수로 알려져 있고, 이는 다른 객체에 선언
되어있는 것과 구별하는 것을 도와 준다. **__init__()** 메소드는 속성 매개변수와 객체가 인스턴스화 되었을때의 상태를 지니고 있다. 

Examine this code snippet of a class—what are the attributes in this class?

아래 간단한 코드를 조사해서 어떤 것이 클래스의 속성인지 알아낼 수 있어? 

```python
class Shirt:

    def __init__(self,color,size,price):
        self.color = color
        self.size = size
        self.price = price
```

Anita: Color, price, and size

Anita: 색깔, 가격 그리고 사이즈

DarkAnita: Excellent!!

DarkAnita: 좋아 ! 

Finally, let's consider the second instance method, called **second_method** in the first example.

이제 우리는 두번째 인스턴스 매소드에 대해 생각해 볼 수 있겠어. 첫번째 예제의 두번째 매소드를 호출해보자.

This looks like a typical function, but while inside a class, it’s a method or the behavior of an object. If you’ll notice,
 this method also has the **self** argument. It’s safe to say that all methods in a class should have the **self** argument as their first parameter.

전형적인 함수처럼 생겻지만, 클래스 안에 있는 함수야. 이는 매소드 혹은 객체의 행동으로 부르지. 만약 눈치 챘다면, 이 매소드 또한 **self**를 가지고 있어. 모든 클래스 내의 메소드는 **self** 매개변수로
갖는 것이 안전하다고 말할 수 있어.

> Please note that **self** can be renamed as any other word, as long as you have an argument in the method that represents the object to be built.
> This should be the first argument, and it’s conventional to just call it **self**.

> **self** 는 다른 단어로 표시할 수 있습니다.
> 하지만 이는 반드시 첫번째 매개변수여야 합니다. 그리고 관습적으로 **self** 라고부릅니다.

You can have as many instance methods as you want in a **class**. However, make sure your **class** doesn’t become too clunky for readability purposes.

이제 넌 **class** 내에서 너가 원하는 만큼 매소드를 만들 수 있어. 하지만 명심해, 너의 **class** 객체가 읽기 너무 힘들어지지 않게 해야한다. 

Now, let's take a look at the complete **class** example. This time, you’re going to interpret what this **class** is doing:

**class** 예제를 마무리해보자. 이번 시간에는 **class**가 어떤 행동을 하는지 해석해보자.

```python
class Shirt:

    def __init__(self,color,size,price):
        self.color = color
        self.size = size
        self.price = price
    
    def change_price(self, new_price):
        self.price = new_price

    def discount(self, discount):
        discount_price = self.price * (1-discount)
        return discount_price
```

Anita: This is a Shirt class that’s used to initialize or create shirt objects that have color, size, and price characteristics, and that have the behavior to change prices and have discounted prices.

Anita: Shirt class 는 초기화 혹은 Shirt 색, 사이즈, 가격의 속성을 가진 객체를 만들기 위해 사용하고 그리고 가격바꾸기, 가격할인등의 행동을 한다.

DarkAnita: I see you have gotten the hang of Python classes…

DarkAnita: 이제 너가 파이썬 클래스에 대해 이해한 것 같구나

Anita: Yeah, but what are the actual use cases for classes?

Anita: 맞아, 근데 어떨때 이제 class들을 사용하지 ? 

DarkAnita: Hmm...Good question. Some of the use cases are:

DarkAnita: 좋은 질문이야, 활용되는 예는 : 

* For organization: Classes are used for grouping functions together with similar purposes. When your code starts having a lot of functions, it may be time to define a class.
* For reusability and readability — Since classes are a good way to keep similar functions together, it indirectly makes your code easy to read. Also, it makes it easier to modularize similar bits of code (i.e store code in modules or files) in order to be reused for another purpose.
* To track info — Attributes are like the metadata of an object. Classes are great for storing that kind of information. Imagine you run a school and you want to keep track of all the data for students enrolled, as well as their behavioral records—you can define classes to track all this info.

* 조직화를 위해 : 클래스들은 비슷한 목적을 가진 함수들을 묶기 위해 사용한다. 너의 코드가 많은 함수들을 가지기 시작한다면, 클래스를 만들 때가 된 것 이다.
* 재사용과 가독성을 위해 : 클래스는 비슷한 함수를 모아두기 위함이기 때문에, 이것은 간접적으로 너의 코드를 쉽게 읽을 수 있게 만들어 준다. 또한 이것은 코드의 부분 부분을 쉽게 모듈화 할 수 있게 해준다.
* 정보의 추적을 위해 : 속성은 객체의 매타데이터와 같다. 클래스들은 이러한 정보들을 저장하기에 아주 적당하다. 
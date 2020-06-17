---
title: "SOLID Principles every Developer Should Know Part2"
date: 2020-06-16
categories:
  - Design Pattern
  - Refactoring
tags:
  - Design Pattern
  - Refactoring
  - SOLID principle
---
### SOLID Principles every Developer Should Know Part 2
### Original from [HERE](https://blog.bitsrc.io/solid-principles-every-developer-should-know-b3bfa96bb688)


#### Liskov Substitution Principle

>A sub-class must be substitutable for its super-class

> 서브클래스는 수퍼클래스의 대체가 될 수 있어야한다 !

The aim of this principle is to ascertain that a sub-class can assume the place of its super-class without errors. 
If the code finds itself checking the type of class then, it must have violated this principle.

이 원칙의 목적은 서브 클래스가 오류 없이 슈퍼 클래스의 자리를 맡을 수 있음을 확인하기 위함이다.
만약 코드가 스스로 클래스 타입을 확인할 수 있다면, 그것은 무조건 원칙을 위반하는 것이다.

Let’s use our Animal example.

```python
# ...
def AnimalLegCount(Animal):
    for i in range(len(Animal)):
        if type(Animal[i]) == Lion:
            print(LionLegCount(Animal[i]))
        if type(Animal[i]) == Mouse:
            print(MouseLegCount(Animal[i]))
        if type(Animal[i]) == Snake:
            print(SnakeLegCount(Animal[i]))

AnimalLegCount(animals)
```

This violates the LSP principle, (and also the OCP principle). It must know of every Animal type and call the associated 
leg-counting function.

위는 LSP 원칙을 위반하고 또한 OCP 원칙 또한 위반하고 있다. 이것은 반드시 모든 Aniaml 타입과 연관된 Legcount 함수를 알아야 한다.
 
With every new creation of an animal, the function must modify to accept the new animal.

새로운 동물이 생길 때 마다, 우리는 새로운 동물을 수용하기 위해서 함수를 수정 해야 할 것 이다.

```python
# ...
class Pigeon(Animal):
    pass
animals = []
animals.append(Pigeon())

def AnimalLegCount(Animal):
    for i i range(len(Animal)):
        if 

function AnimalLegCount(a: Array<Animal>) {
    for(int i = 0; i <= a.length; i++) :
        if type(Animal[i]) == Lion:
            print(LionLegCount(Animal[i]))
        if type(Animal[i]) == Mouse:
            print(MouseLegCount(Animal[i]))
        if type(Animal[i]) == Snake:
            print(SnakeLegCount(Animal[i]))
        if type(Animal[i]) == Pigeon:
            print(PigeonLegcount(Animal[i]))

AnimalLegCount(animals)
```

To make this function follow the LSP principle, we will follow this LSP requirements postulated by Steve Fenton:

이 함수를 LSP 원칙을 따르게 하기 위해서는 우리는 Steve Fenton가 말하는 LSP 요구 사항을 따라야한다.

* If the super-class (Animal) has a method that accepts a super-class type (Animal) parameter, Its sub-class(Pigeon) should accept as argument a super-class type (Animal type) or sub-class type(Pigeon type).
* If the super-class returns a super-class type (Animal), Its sub-class should return a super-class type (Animal type) or sub-class type(Pigeon).

* 만약 슈퍼클래스가  슈퍼클래스 타입의 파라미터를 가진 메소드를 가진다면, 서브 클래스들은 슈퍼클래스와 같은 타입의 변수 혹은 서브클래스와 같은 타입의 변수를 가져야 한다.
* 만일 슈퍼 클래스가 슈퍼클래스 타입을 반환한다면, 이 서브클래스는 슈퍼클래스를 반환하거나 서브클래스 타입을 반환해야한다.

Now, we can re-implement AnimalLegCount function:

자 이제 AnimalCount 기능을 재구현 해보자:

```python
def AnimalLegCount(Animal):
    for i in range(len(Animal)):
        Animal.LegCount()

AnimalLegCount(animals)
```

The AnimalLegCount function cares less the type of Animal passed, it just calls the LegCount method. All it knows is that 
the parameter must be of an Animal type, either the Animal class or its sub-class.

이제 AnimalLegCount 함수는 Animal의 타입과 관계가 없어 졌고, 단지 LegCount 메소드를 호출 하면된다. 우리가 아는 것은 단지 Animaltype을 넘겨줘야되고
혹은 Animal 클래스나 , Sub class를  파라미터로 반드시 가져야한다.

The Animal class now have to implement/define a LegCount method:

Animal 클래스에 이재 LegCount 메소드를 구현해보자.

```python
class Animal:
    # ...
    def LegCount(self):
        pass
```

And its sub-classes have to implement the LegCount method:

그리고 서브클래스들은 반드시 LegCount 메소드를 구현해야한다.

```python
#...
class Lion(Animal):
    # ...
    def LegCount(self): 
        # ...

```

When it’s passed to the AnimalLegCount function, it returns the number of legs a lion has.

AnimalLegCount 함수를 호출 할 때, 우리는 사자의 다리 갯수를 반환 받을 것이다.

You see, the AnimalLegCount doesn’t need to know the type of Animal to return its leg count, it just calls the LegCount 
method of the Animal type because by contract a sub-class of Animal class must implement the LegCount function.

너가 보듯이, AnimalLegCount는 어떤 동물 타입을 반환하는지 알필요가 없고, 단지 LegCount()함수를 호출하기만 하면 된다. 왜냐하면 LegCount함수는 서브 클래스에
구현되어 있는 LegCount 함수에 종속되어 있기 때문이다.

#### Interface Segregation Principle

> Make fine grained interfaces that are client specific

> Clients should not be forced to depend upon interfaces that they do not use.

This principle deals with the disadvantages of implementing big interfaces.

이 원칙은 큰 인터페이스를 구현할 때의 단점을 다루게 될 것이다.

Let’s look at the below IShape interface:

아래의 IShape 인터페이스를 보자:

```python
class IShape:
    def drawCircle(self):
        pass
    def drawSquare(self):
        pass
    def drawRectangle(self):
        pass
```

This interface draws squares, circles, rectangles. class Circle, Square or Rectangle implementing the IShape interface must 
define the methods drawCircle(), drawSquare(),drawRectangle().

이 인터페이스 squares, circles, rectangles를 그린다. 그리고 class Circle, Square, Rectangle 를 구현할때 IShape의 인터페이스 메소드를 반드시 정의해야한다.

```python
class Circle(IShape):
    def drawCircle(self):
        pass
    def drawSquare(self):
        pass
    def drawRectangle(self):
        pass 

class Square(IShape):
    def drawCircle(self):
        pass
    def drawSquare(self):
        pass
    def drawRectangle(self):
        pass 

class Rectangle(IShape):
    def drawCircle(self):
        pass
    def drawSquare(self):
        pass
    def drawRectangle(self):
        pass 
```

It’s quite funny looking at the code above. class Rectangle implements methods (drawCircle and drawSquare) it has no use of, 
likewise Square implementing drawCircle, and drawRectangle, and class Circle (drawSquare, drawSquare).

위의 코드를 보면 좀 웃기지 않았나? 각각의 서브 클래스들은 자신이 필요로 하지 않는 인터페이스들을 구현하고 있다.

If we add another method to the IShape interface, like drawTriangle(),

우리가 다른 drawTriangle()와 같은 다른 메소드들을 구현한다면,

```python
class IShape: 
    def drawCircle(): pass
    def drawSquare(): pass
    def drawRectangle(): pass
    def drawTriangle(): pass
```

the classes must implement the new method or error will be thrown.

다른 클래스들을 새로운 메소드를 구현해야한다. 아니면 에러를 만들 것 이다.(파이썬은 아닌듯 ...)

We see that it is impossible to implement a shape that can draw a circle but not a rectangle or a square or a triangle. 
We can just implement the methods to throw an error that shows the operation cannot be performed.

우리는 사각형, 직사각형, 삼각형을 제외한 동그라미만 그리는 함수를 만들 수없다. 에러없이 구현하기 위해서는 모든 것을 구현해야한다.

ISP frowns against the design of this IShape interface. clients (here Rectangle, Circle, and Square) should not be forced 
to depend on methods that they do not need or use. Also, ISP states that interfaces should perform only one job 
(just like the SRP principle) any extra grouping of behavior should be abstracted away to another interface.

IShape 인터페이스는 ISP 디자인 패턴을 만족하지 않는다. 클라리언트(이곳에서는 직사각형, 원, 사각형)은 그들이 필요로 하지 않는 메소드에 대해서는 강요 받지 말아야한다.
또한 ISP는 인터페이스하나가 하나의 기능만을 해야한다.(SRP 원칙처럼).

Here, our IShape interface performs actions that should be handled independently by other interfaces.

이제 ISP를 만족하게끔 독립적으로 하나의 기능만을 담당하게 해보자.

To make our IShape interface conform to the ISP principle, we segregate the actions to different interfaces:

IShape 인터페이스를 ISP 원칙을 만족하게 하기 위해서 우리는 각각의 인터페이스를 분리시켜야한다. 

```python
class IShape:
    def draw(self): pass

class ICircle:
    def drawCircle(self): pass

class ISquare:
    def drawSquare(self): pass

class IRectangle:
    def drawRectangle(self): pass

class ITriangle:
    def drawTriangle(self): pass

class Circle(ICircle):
    def drawCircle(self) : pass
        #...

class Square(ISquare):
    def drawSquare(self) : pass
        #...

class Rectangle(IRectangle):
    def drawRectangle(self) : pass
        #...

class Triangle(ITriangle):
    def drawTriangle(self) : pass
        #...

class CustomShape(IShape):
   def draw(): pass
      #...
```

The ICircle interface handles only the drawing of circles, IShape handles drawing of any shape :), ISquare handles the 
drawing of only squares and IRectangle handles drawing of rectangles.

OR

Classes (Circle, Rectangle, Square, Triangle, etc) can just inherit from the IShape interface and implement their own draw behavior.

ICircle 인터페이스는 원을 그리는 것을 담당하고, IShape는 어떤 모양도 그리는 것이 가능하다. ISquare 사각형을 그리고, IRectangle은 직사각형만을 그린다. 

혹은 

클래스들 (Circle, Rectangle, Square, Triangle, etc) 는 단지 IShape interface로 부터 상속받고, 그들의 자신의 모습만을 그리게 구현해야한다.

```python
class Circle(IShape):
    def draw(self):
        # ...
        pass 

class Triangle(IShape):
    def draw(self): pass
        #...

class Square(IShape):
    def draw(self): pass
        #...


class Rectangle(IShape):
    def draw(self): pass
        #...    
```
                                     
We can then use the I -interfaces to create Shape specifics like Semi Circle, Right-Angled Triangle, Equilateral Triangle, Blunt-Edged Rectangle, etc.

우리는 I- 형태의 인터페이스를 사용함으로써, 모양들을 조금 더 세분화 해서 Semi Circle, Right-Angled Triangle, Equilateral Triangle, Blunt-Edged Rectangle 등과 같이 구체화 시킬 수 있다. 

#### Dependency Inversion Principle

> Dependency should be on abstractions not concretions

> A. High-level modules should not depend upon low-level modules. Both should depend upon abstractions.

> B. Abstractions should not depend on details. Details should depend upon abstractions.

There comes a point in software development where our app will be largely composed of modules. When this happens, we have 
to clear things up by using dependency injection. High-level components depending on low-level components to function.

소프트웨어 개발에서의 가장 큰 요소 중 하나는 모듈일 것이다. 그렇게 된다면 우리는 dependency injection을 사용하여 분명하게 해야한다. 높은 래밸의 구성원들이 낮은 
래밸의 구성원에 의존하게 만들어야 할 것이다.

```python
# extends from XMLHttpRequestService
class XMLHttpService(XMLHttpRequestService):
    pass 

class Http :
    def __init__(self, XMLHttpService):
        pass

    def get(self, url, options)
        self.xmlhttpService.request(url,'GET')

    def post(self):
        self.xmlhttpService.request(url,'POST')
    #...
```

Here, Http is the high-level component whereas HttpService is the low-level component. This design violates DIP A: High-level modules should not depend on low-level level modules. It should depend upon its abstraction.

Http, 는 높은 래밸의 구성요소인 반면 HttpService는 낮을 래밸의 구성 요소이다. 하지만 이 디자인은 DIP 요소중 A 항목을 위반하고 있다. 즉,높은 래밸의 모듈은 낮은 래밸의 모듈에 의존하면 안된다. 이는 추상화에 의존해야한다는 것이다.
 
Ths Http class is forced to depend upon the XMLHttpService class. If we were to change to change the Http connection service, maybe we want to connect to the internet through Nodejs or even Mock the http service. 는
We will painstakingly have to move through all the instances of Http to edit the code and this violates the OCP principle.

Http 클래스는 XMLHttpService 클래스에 의존하도록 강요되어진다. 만약 우리가 Http conntection 을 바꾸고 싶어 바꾸게 된다면, 우리는 아마 Nodejs 나 Mock 와 같은 Http 서비스를 이용하여 인터넷에 연결하고 싶은 것이다.
 우리는 공들여서 Http 클래스의 모든 인스턴스들을 움직여야서 코드를 수정해야 된다. 이는 OCP 원칙또한 위반하게 된다.
 
The Http class should care less the type of Http service you are using. We make a Connection interface:

Http 클래스는 Http를 사용하는 우리가 어떤 데이터 타입을 사용하던지 간에 관계가 없어야한다. Connection 인터페이스를 만들어 보자.

```python
# interface 
class Connection:
    def request(url, opts):
        pass
```

The Connection interface has a request method. With this, we pass in an argument of type Connection to our Http class:

이 Connection 인터페이스는 request 메소드를 가지고있다. 이 안에서 Http 클래스에 우리는 Connection 타입의 매개변수를 넘긴다.

```python
class Http :
    def __init__(self,Connection):
        pass
    def get(self,url, options):
        self.httpConnection.request(url,'GET')
    def post(self):
        self.httpConnection.request(url,'POST')
    # ...
```

So now, no matter the type of Http connection service passed to Http it can easily connect to a network without bothering 
to know the type of network connection.

그래서, 이제 어떤 타입의 http 연결 서비스가 오던지 간에 Http는 쉽게 네트워크에 연결할 수 있다. 우리가 어떤 타입의 네트워크 연결을 하던지 간에 말이다.

We can now re-implement our XMLHttpService class to implement the Connection interface:

이제 우리는 XMLHttpService 클래스를 재구현해서 Connection 인터페이스를 구성하기 위해 구현해보자.

```python
class XMLHttpService(Connection):
    xhr = XMLHttpRequest()
    # ... 
    def request(self, url, opts) :
        xhr.open()
        xhr.send()
```

We can create many Http Connection types and pass it to our Http class without any fuss about errors.

우리는 많은 Http Connection의 타입을 만들 수 있고, 어떠한 에러 없이 우리의 Http 클래스를 통과할 수 있다.

```python
class NodeHttpService(Connection):
    def request(self, url, opts):
        #...

class MockHttpService(Connection):
    def request(url, opts) :
        #...
```

Now, we can see that both high-level modules and low-level modules depend on abstractions. Http class(high level module)
 depends on the Connection interface(abstraction) and the Http service types(low level modules) in turn, depends on the Connection interface(abstraction).

Also, this DIP will force us not to violate the Liskov Substitution Principle: The Connection types Node-XML-MockHttpService 
are substitutable for their parent type Connection. 

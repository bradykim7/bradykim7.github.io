---
title: "SOLID Principles every Developer Should Know Part1"
date: 2020-06-16
categories:
  - Design Pattern
  - Refactoring
tags:
  - Design Pattern
  - Refactoring
  - SOLID principle
---
### SOLID Principles every Developer Should Know Part 1
### Original from [HERE](https://blog.bitsrc.io/solid-principles-every-developer-should-know-b3bfa96bb688)

#### Introduction 

Object-Oriented type of programming brought a new design to software development.

객체 지향 프로그래밍은 새로운 디자인 패턴을 소프트웨어 개발에 가져왔다.

This enables developers to combine data with the same purpose/functionality in one class to deal with the sole purpose 
there, regardless of the entire application.

이는 개발자들로 하여금 전체적인 어플리케이션의 목적과 관계없이 같은 목적과 기능을 가진 데이터를 하나의 클래스 안에 조합하고 하나의 목적 사용할 수 있게 했다.
  
But, this Object-oriented programming doesn’t prevent confusing or unmaintainable programs.

그러나 이 객체지향 프로그래밍에서는 혼란과 유지가 불가능한 프로그램을 만드는 것을 방지 하지 못했는데 ...

As such, five guidelines were developed by Robert C. Martin. These five guidelines/principles made it easy for developers 
to create readable and maintainable programs.

하지만 Robert C. Martin의 5가지의 가이드라인 를 따르게 된다면 이를 방지 할 수 있게 되었다. 이 가이드라인/원칙은 많은 개발자들로 하여금 가독성이 좋고, 유지보수가
뛰어난 프로그램을 만들 수 있게 해주었다.

These five principles were called the S.O.L.I.D principles (the acronym was derived by Michael Feathers).

이 5개 의 원칙은 S O L I D 으로 불렸다. 

> S: Single Responsibility Principle
> O: Open-Closed Principle
> L: Liskov Substitution Principle
> I: Interface Segregation Principle
> D: Dependency Inversion Principle

We will discuss them in detail below.

아래에서 이제 알아보자 !

Note: Most of the examples in this article, may not suffice as/for the real thing or not applicable in real world applications. 
It all depends on your own design and use case. The most important thing is to understand and know how to apply/follow the principles.

Tip: Use tools like Bit (GitHub) to easily share and reuse components (and small modules) across projects and applications. 
It also helps you and your team save time, stay in sync and build faster together. It’s free, give it a try.



#### Single Responsibility Principle

>“…You had one job” — Loki to Skurge in Thor: Ragnarok
>A class should have only one job.

A class should be responsible for only one thing. If a class has more than one responsibility, it becomes coupled. 
A change to one responsibility results to modification of the other responsibility.

클래스는 오직 하나의 기능만을 가져야한다. 만약 클래스가 하나이상의 역할을 맡는다면, 이는 잘못된건가 ? 만약 하나의 역할을 바꾸게 되면 다른 하나의 역할도 바꿔야한다.

Note: This principle applies not only to classes, but also to software components and microservices.

For example, consider this design:

아래의 디자인을 예로 들어보자:

```python
class Animal :
    def __init__(self, name):
        pass
    def getAnimalName(self):
        pass
    def saveAnimal(self, Animal):
        pass
```

The Animal class violates the SRP.
Animal 클래스는 SRP를 위반하고 있다.

How does it violate SRP?

그러면 SRP를 위반했다는 것은 무엇인가?

SRP states that classes should have one responsibility, here, we can draw out two responsibilities: animal database management 
and animal properties management. The constructor and getAnimalName manage the Animal properties while the saveAnimal manages 
the Animal storage on a database.

SRP 상태는 클래스는 하나의 역할만을 담당한다는 뜻이다. 위의 예제에서는 두개의 역할을 찾아 볼 수 있다. Animal 데이터베이스 관리 와 Animal 속성을 관리하는 기능 2가지이다.
초기화 메소드와 Animal의 이름을 가져오는 메소드는 Animal 클래스의 속성을 반면에 나머지 2개의 메소드는 Animal 클래스를 데이터베이스에 저장하는 기능이다.

How will this design cause issues in the future?

그렇다면, 이는 어떤 결과를 미래에 불러오게 될까? 

If the application changes in a way that it affects database management functions. The classes that make use of Animal properties 
will have to be touched and recompiled to compensate for the new changes.

만약 어플리케이션이 어떤 식으로든 바뀌게 되면, 이는 데이터베이스 관리 함수에 영향을 미치게 된다. Animal 속성들을 만드는 클래스들은 다시 손봐야하고 그리고 새로운 변화를 위해서
다시 컴파일 되어야 한다.

You see this system smells of rigidity, it’s like a domino effect, touch one card it affects all other cards in line.

너는 이런 경직된 시스템의 냄새를 맡을 수 있고, 이는 도니모 효과를 이르킨다. 하나의 카드가 한 줄에 있는 모든 카드에 영향을 주게 된다.

To make this conform to SRP, we create another class that will handle the sole responsibility of storing an animal to a database:

이를 SRP식으로 바꾸기 위해선 다른 클래스를 만들어야 되고, 이는 animal를 데이터베이스에 저장하는 하나의 역할을 담당하게 될 것이다.

```python
class Animal :
    def __int__(self, name):
        pass
    def getAnimalName(self):
        pass

class AnimalDB :
    def getAnimal(self , Animal):
        pass
    def saveAnimal(self, Animal):
        pass
```

> When designing our classes, we should aim to put related features together, so whenever they tend to change they change
> for the same reason. And we should try to separate features if they will change for different reasons. - Steve Fenton


With the proper application of these, our application becomes highly cohesive.

우리의 어플리케이션에 훨씬 더 견고하게 바꼈다.

#### Open-Closed Principle

> Software entities(Classes, modules, functions) should be open for extension, not modification.

Let’s continue with our Animal class.
계속 해서 Animal 클래스를 다뤄보자 

```python
class Animal :
    def __init__(self, name):
        pass
    def getAnimalName(self):
        pass
```

We want to iterate through a list of animals and make their sounds.

우리는 animals 의 리스트를 반복적으로 돌면서 그들의 동물 소리를 내게 만들 것이다.

```python
# ...
animals = []
animals.append(Animal('lion'))
animals.append(Animal('mouse'))

def AnimalSound(animals):
    for i in range(len(animals)):
        if animals[i].name == 'lion':
            print('roar')
        if animals[i].name == 'mouse':
            print('squeak')
AnimalSound(animals)
```

The function AnimalSound does not conform to the open-closed principle because it cannot be closed against new kinds of animals.
If we add a new animal, Snake:

AnimalSound 의 함수는 열고 닫는 원칙이 확실하지 않는데, 이느는 새로운 동물들이 추가 되었을때 닫히지 않기 때문이다.
뱀이라는 새로운 동물을 추가해 보자. 

```python
# ...
animals = []
animals.append(Animal('lion'))
animals.append(Animal('mouse'))
animals.append(Animal('snake'))
# ...
```

We have to modify the AnimalSound function:

AnimalSound 함수를 수정해보자 

```python
def AnimalSound(animals):
    for i in range(len(animals)):
        if animals[i].name == 'lion':
            print('roar')
        if animals[i].name == 'mouse':
            print('squeak')
        if animals[i].name == 'snake':
            print('hiss')

AnimalSound(animals)
```

You see, for every new animal, a new logic is added to the AnimalSound function. This is quite a simple example. 
When your application grows and becomes complex, you will see that the if statement would be repeated over and over again 
in the AnimalSound function each time a new animal is added, all over the application.

How do we make it (the AnimalSound) conform to OCP?

너가 볼 수 있듯이, 매번 새로운 동물을 추가할 때, 새로운 로직이 AnimalSound 함수에 추가되어야 한다. 지금 예제는 간단해서 별로 문제점이 드러나지 않지만, 너의 프로젝트가
점점 커지고 복잡해지면서 너는 AnimalSound 함수에 새로운 동물을 추가하고 싶을때 마다 이를 반복해야한다. 그렇다면 어떻게 해야 OCP로 바꿀 수 있을까?

```python
class Animal :
        def makeSound(self):
            pass
        #...
class Lion(Animal):
    def makeSound(self) :
        return 'roar'

class Squirrel(Animal) :
    def makeSound(self):
        return 'squeak'

class Snake(Animal):
    def makeSound(self): 
        return 'hiss'

# ...
def  AnimalSound(animals):
    for i in range(len(animals)):
        print(animals[i].makeSound())
AnimalSound(animals)
```

Animal now has a virtual method makeSound. We have each animal extend the Animal class and implement the virtual makeSound method.

이제 Animal 클래스는 가상의 메소드인 makeSound 가 생겻다. 우리는 각각의 동물들을 Animal을 상속받아 가상 메소드인 makeSound를 구현 할 수 있다.

Every animal adds its own implementation on how it makes a sound in the makeSound. The AnimalSound iterates through 
the array of animal and just calls its makeSound method.

모든 동물들은 각각의 구현체를 더해가면서 그들의 소리를 만들 수 있다. 그리고 동물소리는 반복적으로 Animal 리스트를 호출만 함으로써, makeSound 메소드를 호출할 수 있다.

Now, if we add a new animal, AnimalSound doesn’t need to change. All we need to do is add the new animal to the animal array.

이제 우리는 새로운 동물들을 추가 할때마다, AnimalSound를 바꿀 필요가 없어졌다. 단지 우리는 Animal 리스트에 새로운 동물만 추가하면된다.

AnimalSound now conforms to the OCP principle.

이제 AnimalSound OCP 원칙을 지키게 되었다.

Another example:

다른 예제이다.

Let’s imagine you have a store, and you give a discount of 20% to your favorite customers using this class:

우리가 가게를 가지고 있다고 가정해보자 ,그리고 우리의 단골 고객에게 20프로 할인해주는 것을 구현해보자.

```python
class Discount :
    def giveDiscount(self) :
        return self.price * 0.2
```

When you decide to offer double the 20% discount to VIP customers. You may modify the class like this:

또 우리는 VIP 고객에게 40프로의 할인을 해주는 것을 결정했을 때, 우리는 클래스를 이렇게 수정해야한다.

```python
class Discount :
    def giveDiscount(self):
        if(self.customer == 'fav') :
            return self.price * 0.2
    
        if(self.customer == 'vip') :
            return self.price * 0.4
```

No, this fails the OCP principle. OCP forbids it. If we want to give a new percent discount maybe, to a diff. type of customers, you will see that a new logic will be added.
To make it follow the OCP principle, we will add a new class that will extend the Discount. In this new class, we would implement its new behavior:

하지만 위처럼 하게 되면 OCP 원칙을 해칯게 된다. 만약 우리가 새로운 고객에게 새로운 할인율을 적용하고 싶다면 우리는 새로운 로직을 추가하는 것을 볼 수 있다.
만약 이를 방지하고 OCP 원칙을 지키고 싶단면 우린느 새로운 클래스를 상속해야한다. 이 새로운 클래스는 아래와 같이 만들 것이다.

```python
class VIPDiscount(Discount):
    def getDiscount(self):
        return super().getDiscount() * 2
```

If you decide 80% discount to super VIP customers, it should be like this:
만약 80 프로의 할인율을 VVIP 고객에게 제공하고 싶다면, 이렇게 바꾸면 된다.

```python
class SuperVIPDiscount(VIPDiscount):
    def getDiscount(self):
        return super().getDiscount() * 2;

```

You see, extension without modification.

너가 볼 수 있듯이, 어떠한 수정 없이 확장이 이루어졌다.

Continue on Part 2 
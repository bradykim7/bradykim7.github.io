---
title: "Django And Asynchronous Support: A Never Ending Story?"
date: 2020-07-02
categories:
  - Django
  - Python
tags:
  - Django
  - Python
---

### Django And Asynchronous Support: A Never Ending Story?
### Original from [HERE](https://hackernoon.com/django-and-asynchronous-support-a-never-ending-story-q0233uls) 

#### Introduction

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p1.jpg" alt="">

Last year, when Django 3.0 came out there was a lot of buzz in the developer community about how Django 3.0 has support for now but what does that mean for most developers? I guess we'll find out.

작년, Django 3.0 이 나온 이후로 많은 개발자 커뮤티니에서 Django 3.0 이 비동기 형식을 지원한다고 많은 잡음 이 있었다. 하지만 개발자들에게 이게 어떤 의미 일까?

While it's true that Django has developing support for asynchronous (“async”) Python, but it does not yet support asynchronous views or middleware; they will be coming sometime in a future release.

Django는 비동기 Python을 지원한다는 것은 사실이나, 비동기형식의 views 나 미들웨어들은 지원하지 않았다. 멀지 않은 미래에 지원할꺼라 생각된다.

As per the Django documentation,

Django 문서에 따르면

There is limited support for other parts of the async ecosystem; namely, Django can natively talk ASGI and some async safety support.

제한적인 비동기 생태계에 지원이 있는데, Django는 기본적으로 ASGI 와 비동기를 안전적으로 지원한다.

Alright, I get that some of you might not be knowing what 'asynchronous' really means cause maybe you've just been using Python the way it is. I'll clear that up.

좋아 , 이제 'asynchronous' 의 의미를 정확하게, 파이썬에서 알아보자.

#### What is asynchronous code?

Python is a single-threaded language unlike Java or some other multi-threaded applications translating to just running in a single sequence instead of doing multiple tasks at once.

파이썬은 다른 자바나 여러개의 테스크를 수행하는 대신에 싱글 시퀀스에서 돌아가게 해석하는 멀티스레드 어플리케이션과 다른 글스레드의 언어이다.

Since Django is a web framework built on top of Python, it's not asynchronous either and that means there are issues like a view in a Django application 
getting stuck in a case where one or more operations take too much time to complete. This can become an implication.

Django는 파이썬 위에 빌드된 웹 프레임 워크인데, 이는 비동기가 아니고, 이 말은 몇개의 이슈들이 있는데, Django 어플리케이션에서의 View 에서 하나 혹은 그 이상의 동작을 수행을 완료하기 위해 많은 시간이 걸릴 수 있다는 뜻이다.

If you try to simulate a blocking event in the view with the sleep set to a specific time ( sleep is from time library in Python ),
 you'll notice that the view gets stuck for the specific time before moving on.

만약 너가 블로킹 이벤트를 특정시간에 절전모드를 설정한 view에서 실험한다고 했을때, 너는 View 들이 특정시간에 들어가기 전에 고착된다는 것을 알아차릴 것이다.

We can draw from our observation that Django without queues is not really meant for I/O bound activities and that is a massive issue for some developers. 
Now, if you're a Python developer, you might already know how you could simply utilize the module `asyncio` to make your Python code asynchronous.

우리는 이러한 관찰을 통해서 이끌어 낼 수 있다. 큐가 없는 Django는 실제로 I/O 영역의 활동을 위한 것이 아니고, 이 주제가 개발자사이에서는 굉장한 이슈이다.
만약, 너가 파이썬 개발자이라면, 이미 `asyncio`라는 모듈을 사용해서 간단하게 파이선 코드를 비동기형태로 만드는 방법을 알것이다.

#### But hey, what about Django? How do I make that asynchronous?

Well, technically you can't BUT there's a sweet way around it and most developers don't seem to mind cause well, it just works. 
Even Instagram scaled with Django for its operations and is currently the largest deployment of Django at scale.

기술적으로, Django를 비동기로 만드는 것은 불가능 하다. 하지만 대부분의 개발자들이 별로 신경쓰지 않는 것 같다. 
인스타그램 조차 운영을 위해 Django를 사용하고 있으며, 현재 가장 큰 규모로는 Django 가 사용되 고 있다.

#### What's that sweet way around I was talking about earlier?

Celery. Yeah, Celery is exactly what you need.

Celery 라는 툴을 이용해서 비동기를 구현 할 수 있다.

Celery is an asynchronous task queue/job queue based on distributed message passing. It is focused on real-time operations but supports scheduling as well. 
So yeah you can have asynchronous like features in Django as well.

Celery 는 비동기 task queue/job queue 베이스로 메세지를 분산 해주는 것 이다. 이는 실시간 동작에 중점을 두고 있으면서도 스케쥴링도 지원한다. 그래서  Django에서 비동기를 구현 할 수 있다.

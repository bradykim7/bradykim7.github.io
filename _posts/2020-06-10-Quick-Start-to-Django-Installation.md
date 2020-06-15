---
title: "Quick Start to Django Installation"
date: 2020-06-08
categories:
  - Python
  - Django
tags:
  - Django
---


### Quick Start to Django Installation
### Original from [HERE](https://levelup.gitconnected.com/quick-start-to-django-installation-289a18d553f2)

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p3.jpg" alt="">

Get started on your own Django Web application using this quick start installation guide. It only takes a few minutes to 
get your Django project up and running on your local development server. Just follow the commands below and you'll soon 
see  your application running in your browser window.

이번 포스팅을 통해 Django 웹 어플리케이션을 만들어보자. 몇 분만 투자한다면, 바로 당신! 은 Django 프로젝트를 로컬 환경에서 만들 수 있다. 따라하기만하세요 그러면 
브라우저 윈도우를 통해 웹 어플리케이션을 볼 수 있을 것입니다.


#### Create a Virtual environment

```shell script
mkdir test
cd test
python3 -m venv env
cd env
source bin/activate
```

Open the Terminal and create a Python virtual environment, then activate it.

터미널 창을 열고 파이썬 가상 환경을 만든 후, 활성화 시키는 방법이다.


#### Install Django web Framework

```shell script
pip install django
```

Install **django** in your activated virtual environment.

Django를 가상 환경에 설치한 후 활성화 시킨다.


#### Create the project

```shell script
django-admin startproject mysite
```

Create a Django project named "mysite".

"mysite"라는 Django 프로젝트를 만든다.


#### Create the app

```shell script
cd mysite
python3 manage.py startapp main
```

Enter into the mysite folder then create a Django application named "main" with 
the command "python3 manage.py startapp main" or "py manage.py startapp main"

Mysite 디렉토리에 들어가서 "python3 manage.py startapp main" or "py manage.py startapp main" 를 입력하여
Django 어플리케이션을 만들어보자.

#### Run the Development Server

```shell script
python3 manage.py runserver
```

Result
<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p4.jpg" alt="">


#### Open in the Browser ! 

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p3.jpg" alt="">

Now you get the Django application ! 

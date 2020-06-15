---
title: "Python Django Web Framework "
date: 2020-06-11
categories:
  - Python3
tags:
  - Python3
  - Django
---

### Python Django Web Framework Tutorial
### Original from [HERE](https://www.youtube.com/watch?v=F5mRW0jo-U4&t=341s)


#### Introduction & Virtual Environment


Check the version of python
```shell script
python -V
python3 -V
```

Making project Directory 
```shell script
cd ~
mkdir trydjango
cd trydjango
```

Getting into Virtual Environment
```shell script
pip3 install virtualenv
virtualenv -p python3 . 
source bin/activate
```

Installing Django(In Virtualenv)
```shell script
pip install django
pip freeze
```

Create Django Project
```shell script
mkdir src
cd src
django-admin startproject trydjango .
python manage.py runserver
```

Setting (In virtual env)
```shell script
python manage.py migrate
```


Built in Component

1. Make super user.

```shell script
python manage.py createsuperuser 
```

First App component

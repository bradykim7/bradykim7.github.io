---
title: "How Web Frameworks Streamline And Structure Websites"
date: 2020-06-22
categories:
  - DesignPattern
tags:
  - MVT
  - Django
---

### How Web Frameworks Streamline and Structure Websites

### Original from [HERE](https://medium.com/towards-artificial-intelligence/how-web-frameworks-streamline-and-structure-websites-51fea99c2add)

#### Introductions 

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p7.jpg" alt="">

Web frameworks make building and deploying web applications simple and efficient. With them, we can make high-level 
applications without too much technical knowledge. Nonetheless, it is still important to be able to understand and even 
appreciate what goes on behind these frameworks.

웹 프레임 워크들은 웹 어플리케이션을 간단하고 효율적이게 배포하고 만드는 것을 도와준다. 프레임워크와 함께 우리는 높은 수준의 어플리케이션을 많은 기술적인 지식 없이도
만들어 낼 수 있다. 더불어 우리는 프레임워크 뒤에서 어떤일들이 일어나고 있는지 이해하는 것 또한 매우 중요하다.

In this article, I go over some of the processes and concepts that web development frameworks used to make dynamic web 
applications possible. I do this through the lens of a popular Python web framework Django. But although some of these 
features are specific to Django, the underlying processes and concepts are widely applicable elsewhere. For along the way, 
we can also acquire better programming habits and practices.

이번 포스트에서는 다이나믹한 웹 어플리케이션을 만들 수 있게 사용되는 웹 개발 프레임워크의 개념과 과정에 대해 알아가보자. 이를 유명한 Python Django로 예를 들어
진행할 것이다. 몇몇의 기능은 Django에 특화 되어 있는 기능이지만, 밑줄친 개념들은 널리 사용되는 기능들이니 걱정 말자. 이를 통해서 우리는 좀더 나은 프로그래밍 
습관들을 얻을 수 있을 것이다.

#### MVT Architecture

Django employs a Model-View-Template system to structure our web applications and keep our code clean. An important concept 
in programming is Separation of Concerns. This principle simply means that we, as developers should keep our code organized 
– separating backend from the frontend, etc. MVT architecture allows us to do just that. The backend data (Models) are kept
 separate from request handling (Views) and the frontend page that the user actually sees (Templates). Models can be thought 
 of as the raw data our application uses, while templates are the (mostly) HTML and CSS that our users can see. And of course,
  Views are the functions that mediate between the two.

Django 는 MVT 시스템을 우리의 웹어플리케이션 시스템 구조에 적용하고 우리의 코드를 깨끗하게 유지시켜준다. 가장 중요한 프로그래밍 개념은 개념의 분리 이다. 이 원칙은
간단하게 말하자면, 개발자들은 반드시 코드를 조직화하여 유지해야한다. 백엔드와 프론틀엔드를 분리하는 것처럼말이다. MVT 모델은 우리에게 이를 제공해준다. 백엔드 데이터(Models) 들은
요청을 다루는 Views 와 분리되어 있고, 프론트엔드 페이지들 즉, Templates들도 다 분리 되어 있다. Models 들은 어플리케이션에 사용되는 있는 그대로의 데이터라고 생각하기 쉽고,
Template 들은 HTML CSS 들과 같은 우리가 보는 요소들이다. 그리고 Views들은 우리가 이 2개를 중재하는 함수들이다.

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p8.jpg" alt="">

What makes MVT architecture so powerful is that it keeps our code DRY (don’t repeat yourself) and even makes it reusable. 
Models, for example, are just classes, hence they can be instantiated in different views. Additionally, Django and other
 frameworks allow entire apps to be reused. “Apps” in Django are parts of a project. But these apps can function independently 
 of each other, and can hence be employed in multiple projects.

MVT 모델링이 강력한 점은 우리의 코드를 드라이~ 하게 해준다. 또 재사용 가능하게 해준다. 예를 들어 Models 들은 단지 클래스이다. 하지만 이는 각각의 Views에서 초기화 된다.
게다가 추가적으로 Django 와 다른 Framework들은 전체적인 어플리케이션을 재사용 가능하게 해준다. "Apps"라고 불리는 부분이 Django 프로젝트의 부분이다. 하지만 이 앱들은은
함수로써 독립적일수 있지만, 우리는 다수의 프로젝트들을 배포할 수 있다.

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p9.jpg" alt="">

Another key advantage of MVT is security. We wouldn’t want to provide users with potentially malicious intent a one-way path
 to our models and database. The views in between allow us to insert authentication and validation. These act as gateways that 
 protect our web app, thereby increasing security.

다른 MVT 장점은 보안이다. 우리는 사용자에게 악의적인 의도로 단 방향 모델과 데이터베이스를 제공하길 원치 않습니다. Views 는 우리로 하여금 인증과 검증을 하게 해준다. 
이는 우리의 웹어플리케이션을 지켜주는 게이트 역할을 해줘서 보안성을 높여준다.

#### Url Dispatching

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p10.jpg" alt="">

In static websites, URLs point where to retrieve the file to be rendered in the site directory. For instance, 
mywebsite.com/blog/posts.html points to the posts.html page on the blog folder. While this is fine, there is also no option to 
customize how our URLs appear, and no way to add more functionality to them. Moreover, if we wanted a page for every post, 
we would need to make a new file for each new post. That is both tedious and unnecessary.

정적인 웹사이트들은 URLs 들이 파일들이 랜더링 되는 사이트의 디렉토리를 가리킨다. 예를들어, mywebsite.com/blog/posts.html 는 blog 폴더 안의 posts.html를 가리킨다.
이는 괜찮다. 만일 Urls를 표현하는 방법에 다른 방법이 없거나, 다른 기능적인 부분을 추가할 사항이 없다면 말이다. 우리가 포스트를 만들때마다 새로운 파일을 만들어야한다.
이는 불필요하고 안좋은 생각이다.

Url dispatching solves both of these problems. A URL dispatcher allows us to dictate how our URLs will look along with 
which view it will render. Through this, we can also use variables that function depending on what arguments are passed. 
Take the blog post example. With this feature, we can simply input a primary key (post/1) or a slug (post/this-is-a-post) 
variable to render a different page depending on the arguments.

Url 디스패칭은 이를 해결한다. URL dispatcher는 우리로 하여금 우리의 URL 어떻게 랜더링 되어 보여지는지 탐지한다. 이를 통해서 우리는 랜더링 되어 전달된 다양한 변수들을 사용한다.
예를들어 블로그 post를 들어보자. 이 때, 우리는 간단하게 식별키로 (post/1) 나 (post/this-is-a-post)를 다른 페이지들을 랜더링 할 수 있다. 단지 전달하는 변수만 바꿔서.

One thing we should avoid as developers is hard-coding URLs. This is because URLs are bound to change, and should be flexible
 to that. That said, we wouldn’t want to retype every instance of a URL when we change it. To solve this, Django has a name 
 argument that we can reference instead of the actual path. This allows us to change our URL patterns without having to edit 
 the places where they were referenced.

한가지 우리가 개발자로써 피해야 할 것은 , URL에 하드코딩하는 것이다. 이는 url은 늘 바뀌고 변화에 유동적이어야 한다. 이는 다시 말하자면 우리가 url를 바꾸고자 할 때,
 모든 URL의 인스턴스들을 재작성하길 원하지 않는다. 이를 해결하기 위해서 Django는 name 매개변수를 가지고 있고, 이를 실제 경로대신에 사용한다. 이는 우리로 하여금
 쉽게 URL패턴을 바꿀수 있게 해준다. 우리가 어떠한 행위를 해서 바꾸지 않더라도 말이다.

 
#### Templating

With URL dispatching, we mentioned how we can create URLs for multiple pages with only a single path. But we would still
 have to make a new .html file for each post, right? Well, we can make use of another feature called templates. 
 As the name suggests, templating lets us make a single template for all our post pages and simply put python variables 
 in place of the information, which will be provided by the associated view. (See again the beauty of MVT architecture?)

Url dispatching으로 우리는 여러개의 페이질을 한줄로 만들 수 있다고 했다. 그러나 우리는 새로운 html 파일을 각각의 포스트를 만들고 싶다. 이렇다면 우리는 Templates를 호출함으로써
이를 만들 수 있다. name 제안 과 같이 template는 우리로 하여금 모든 포스팅 페이지들을 하나의 Template로 만드는 것을 

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p11.jpg" alt="">

Although the example above is relatively simple, templates can be extremely powerful. They make it easier to render forms 
and pass user input. With templating, it’s a much simpler matter to integrate backend functionality to the frontend web page.

비록 위의 예제들이 상대적으로 간단하지만, Templates 들은 상당하게 강력한 기능이다. 그들은 우리가 일할 때, 쉽게 래더링 해주고, 쉽게 사용자의 데이터를 가져와준다. Template과 함께라면
벡엔드를 좀 더 기능적으로 쉽게 프론트와 병합할 수 있다.

#### Putting It All Together

To see how this all comes together, let us see the entire process from URL to web page.

각각을 살펴 보았으니 이제 하나씩 합쳐보자 !

##### Url

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p11.jpg" alt="">

Here our URL dispatcher matches the searched URL with our paths.

여기 URL dispatcher 가 우리의 경로 URL를 찾는다.

Once found, this path sends the associated view the request, along with the arguments (if any) in the URL.

이를 찾으면, 이 경로는 view request와 매칭되는 것을 보낸다. 

##### Views

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p12.jpg" alt="">

The view would then fetch the information the template might need to render the web page. This includes not just the models,
 but form classes, user authentication, and request validation. A view doesn’t have to do all of these. It all depends on the 
 type of request and what function the web page will serve.

View가 템플릿이 웹 페이지를 렌더링하는 데 필요한 정보를 가져오게 된다. 여기에는 모델뿐만 아니라 클래스, 사용자 인증 및 요청, 유효성 검사등도 포함 되있는 정보이다. 
하지만, View  모든 것을 할 필요는 없다.모든 것은 request와 웹페이지가 제공하는함수에 달려 있다.

##### Models

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p13.jpg" alt="">


Our view then interacts with the models, which in turn gets data from the database. Remember the argument(s) passed from the URL?
 Our model can use this to filter from a set of data and provide only the needed information.
 
우리의 View는 model들과 상호작용한다. 데이터를 데이터 베이스로 가져온다. url로 부터 전송된 매개변수를 기억하낟. 우리의 Model은 이러한 데이터를 걸러내는데 사용할 수 있다.
그리고 우리가 원하는 데이터들만 제공해준다.

Validation also occurs in the model. For instance, a field has a certain type and can have parameters specified. 
User input is valid only if it fits the field type and complies with the parameters.

검증 또한 Model 에서 일어난다. 예를 들어, 필드는 어떤 특적한 타입을 가지고 있고 이는 각각의 파라미터를 가지고 있다. 사용자의 데이터 입력값은 field 타입에 맞을때만
값이 들어가고, 파라미터로 컴파일링을 진행한다. 

##### Back To Views

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p14.jpg" alt="">

The information from the database and models is then passed back to the views, usually as a dictionary called “context”. 
The view can also provide other information or variables that the template would need.

데이터베이스와 모델로 부터 온 정보는 다시 View로 돌아가게 된다. dictionary 형태의 "context"이다. 이 View는 우리가 필요한 변수와 정보들을 준다.

##### Templates

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p15.jpg" alt="">

And finally, we get to the template. Recall, that it is this template that our users can actually see in the browser. 
The placeholders in the template are filled with the values in the context, which it got from the views.
And the final web page is ready.

마지막으로 우리는 Template를 가지게 된다. 다시 이 Template는 우리의 브라우저 상에서 우리가 실질적으로보는 부분이다. 이제 변수들은 우리가 View로 부터 전송한
데이터를 가져와 빈 공간을 채우게 된다.
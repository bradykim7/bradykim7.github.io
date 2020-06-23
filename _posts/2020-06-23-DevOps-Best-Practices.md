---
title: "DevOps Best Practices"
date: 2020-06-23
categories:
  - DevOps
tags:
  - DevOps
---


### DevOps Best Practices

### Original from [HERE](https://dzone.com/articles/devops-best-practices)

#### Introductions 


Traditional IT had two separate teams in any organization – the development team and the operations team. 
The development team works on the software, developing and releasing it after ensuring that the code works perfectly. 
The Operations team works on deployment, load balancing, and release management to make SaaS live. 

전통적으로 IT 조직에서는 두개의 팀으로 나눠지곦했다. '개발팀' 과 '운영팀'으로 말이다. 개발팀은 소프트웨어를 다루면 일을하고, 그들의 코드가 배포 후 에 완벽하게 
동작하기 위해 개발한다. 운영팀은 디플로이, 로드 밸런싱, 배포 관리등을 통해 SaaS(Software as a Service)를 실현시킨다. 

They check the application performance and report back any issues, if existent to the development team. 
These cycles went too long for companies and stimulated a need to build a team of mixed expertise of development, QA, 
and Operations, introducing the phenomenon of DevOps. DevOps bridges the gap between two teams and helps them operate 
and evolve applications quickly and reliably.

그들은 어플리케이션의 퍼포먼스를 체크하고, 어떤 이슈가 생기면 개발팀에게 리포트한다. 이러한 순환은 회사 입장에서 너무 길고, 개발, QA, 운영지식을 모두 보유한 팀을 
만드는 것에 대한 갈증을 일으켰다. 이것이 바로 DevOps가 나온 배경이다. DevOps들은 개발팀과 운영팀 사이의 다리같은 역할이다. 잘 동작하게 해주고, 어플리케이션이 신속하고
믿을 수 있게 도와준다.

The question is, how well do we really know DevOps and why do we need it? This post will address such questions and explain
 DevOps best practices that can help a business realize its true potential.

자 이제 질문은 우리가 얼만큼 DevOps에 대해 알고 있고, 그들이 왜 필요할까? 이 포스트는 이런 질문들에 대답해보고, DevOps에 가장 적합한 연습들에 대해 알아보자.

#### What Is DevOps?

As the name sounds, DevOps is related to development and operations. It defines a set of processes that brings a cultural 
shift to an organization by developing collaboration between the development and operations team. It has four key components: 
collaboration, practices, culture, and tools.

이름 그대로 DevOps 는 개발과 운영에 관련되어 있다. 이들은 어떤 개발의 과정을 정의하고 이는 개발팀과 운영팀간의 조화를 통해 조직 문화에 큰 변화를 가져왔다.
4가지의 중요한 요소 : collaboration, practices, culture, 그리고 tools

#### Why Do We Need DevOps?

DevOps brings the next level of collaboration and speed that enables organizations to deliver with improved time to market, 
enhanced productivity, reduced operational cost to serve customers efficiently, and stay competitive in the market. 
It also helps in faster product release, manage unplanned work, capture and solve the critical issues quicker.

DevOps 들은 한층 더 높은 수준의 협업을 가져오고, 조직들로 하여금 빠른시간안에 강력한 제품들을 선보일 수 있게해줬다. 심지어 소비자 입장에서의 부가적인 비용도 줄였고, 
지속적으로 시장에서 경쟁력 있게 해주었다. 그리고 제품을ㅇ 좀더 빠르게 배포하고, 일정에 없던 일들을 관리하고, 심각한 수준의 문제들을 빠르게 잡아내고 해결할 수 있게 도와준다.
 
#### Implementing DevOps Best Practices

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p15.jpg" alt="">

#### Setup Centralized Unit

DevOps uses various tools like Jenkins, Terraform, Nagios, Grafana, Prometheus, or Splunk. 
The organization should set-up a centralized unit for the creation and operation of these tools. 
This centralized unit is responsible for set-up agile practices in the development team. This team investigates new tools,
 upholds it, and provides guidance programs and training to implement DevOps.

DevOps 들은 다양한 툴들을 사용한다. Jenkins, Terraform, Nagios, Grafana, Prometheus, 나 Splunk 등등. 기업에서는 이런 툴들을 운용하기 위해
중점적으로 이용할 것을 정해야한다. 이 중앙화된 유닛은 개발팀에서 에자일한 연습을 책임지게 된다. 그리고 이 팀은 새로운 툴들을 조사하고, 업로드하고 프로그램 가이드르르 제공하고,
DevOps 트레이닝을 위한 것을 구현한다.

#### Continuous Integration (CI)

CI is a software development practice that improves collaboration amongst the team and helps to build high-quality software. 
The Development team regularly check-in code changes in the repository, CI executes automated builds and tests to validate 
the quality of code. Continuous Integration imposes practices that enable quick detection of challenges of the Software Development Life Cycle (SDLC) 
at an early stage which helps the development team to solve issues in the development phase itself.

CI는 팀 간의 협업을 개선하고 고품질 소프트웨어를 구축하는 데 도움을 주는 소프트웨어 개발 관행이다. 
개발 팀은 저장소의 코드 변경 사항을 정기적으로 체크인하고, CI는 자동 빌드 및 테스트를 실행하여 코드의 품질을 검증한다.
Continuous Integration로 개발 팀이 개발 문제를 해결하는 데 도움이 되는 SDLC(소프트웨어 개발 라이프 사이클)의 과제를 조기에 신속하게 감지할 수 있도록 해준다.


#### Continuous Deployment (CD)

The deployment process has various stages like Development → Build → Validation → Build versioning → Deployment → Post-deployment, 
etc. The idea of the Continuous Deployment process is to deploy developed code automatically to the production environment 
after build passes all stages of QA-staging-beta, Integration, UAT, etc. There are tools available like Spinnaker, Jenkins, 
Harness, Ansible, Chef, Puppet, etc. which enables the DevOps team to set-up automated pipelines to deploy on several 
environments with minimum human intervention.

개발은 여러단계로 구분된다; 개발 -> 빌드 -> 검증 -> 버전 빌딩 -> 배포 -> 마무 개발. Continuous Deployment 는 개발된 코드를 자동적으로 재품의 환경에 모든 QA, Integration, UAT 등과 과같은 것을 통한 후 
배포하기 위해서다. 이러한 툴들은 Spinnaker, Jenkins, Harness, Ansible, Chef, Puppet, 등이 있다. 이들은 Devops 팀이 자동적으로 파이프 라인을 구축하여
다양한 환경에서 적은 인간의 개입을 통해 배포를 할 수 있게 해준다.

Continuous Delivery is a DevOps practice where a new codebase gets tested by a QA team on different stages of automated 
and manual QA cycles. If the codebase passes the QA cycle and is approved by the QA team, it gets deployed to production.
 This is how DevOps enables the team to build, test, and release codebase quicker and frequently by dividing it into short cycles.
  This enables organizations to provide more releases, reduce manual deployments, and minimize failure risk in production.

Continuous Delivery 는 DevOps가 QA 팀에서 수동적인 QA 사이클과 각각의 자동적인 단계 테스트를 거친 새로운 코드 베이스를 다루는 일이다. 
만약 코드베이스가 QA 사이클과 QA 팀에의해 증명이 되었다면, 이는 재품에 배포가 되어야한다. 이는 어떻게 DevOps 들이 팀을 가능한 빠르고 빈번하게 짧은 사이클로 나누워 개발하고
테스트하고, 코드베이스를 릴리즈 할 수 있는 이유이다. 이는 기업이 재품에 대한 위험을 감소시키고, 수동적인 배포를 줄일 수 있게 도와준다.

#### Configuration Management (CM)

Configuration and Change Management are important parts of the DevOps cycle. Configuration Management is the automation 
of configuration, monitoring, managing, and maintenance of all entities of infrastructure and systems like servers, 
applications, storage, networks, and all managed services.

Configuration, Change Management은 DevOps 사이클에서 중요한 부분이다. Change Management 는 환경 설정, 모니터링, 관리 그리고 전체적인 구조와 서버, 
어플리케이션, 저장소, 네트워크 그리고 모든 관리해야하는 서비스들의 유지를 위한 것이다.

Configuration management brings in several advantages like simplifying new environment setup, reducing production 
configuration risks, and saves a lot of time for software development instead of investing time and efforts for 
initiating new services from scratch using Infrastructure-as-a-Code practice.

Configuration management는 다양한 이점을 가져온다. 예로, 새로운 환경 설정의 자동화, 재품 구성 설정의 위험도 감소, 그리고 소프트웨어 개발시에 새로운 서비스를 
시작하거나, 할때 개발이 아닌 다른 부분에 필요한 노력들을 줄여준다.
 
#### Change Management

Change management is a process of requesting, planning, implementing, and evaluating the changes that are needed to meet
 new requirements. During the configuration management, if there are any changes required in the existing system and 
 infrastructure, at that time change management comes into the picture. Operations teams need to provide their inputs, 
 reasons for change, and consequences might arise on a wider level including other systems that could be impacted with new changes.

Change management 는 새로운 요청들을 받았을 때의 변화를 요청, 계획, 이행, 평가하는 과정이다. Configuration Management를 하는 동안 만얀, 어떤 변화된 
요구사항이 존재한다면, 이와 동시에 관리하는 방법 또한 바껴야한다. 운영팀은 DevOps에게 변화에 따른 입력값을 제공해야하고, 더 넓은 수준에서 다른 시스템에 영향을 끼칠 수 있는 결과
들도 제공한다.  

#### Keep All Teams on the Same Page

DevOps works with different departments so communication is important. And it’s important to keep everyone on the same page 
to avoid conflicts in teams. To apply the strategy correctly, higher involvement and adoption is vital to keep all teams and
 members on the same page.

DevOps의 일은 다른 부서들이 잘 의사소통할 수 있게 해주는 역할이다. 모든 구성원들이 같은 단계에 있게 해주는 것이다. 서로의 충돌을 피하게 해주는 것도 포함된다.
전략 단계를 정확하게 적용하기 위해서는 높은 수준의 포용과 적응이 필수적으로 모든 팀들에 요구되는 사항이다.

#### Test Automation

Automated testing of each codebase helps in running more tests,  increases testing frequency, and saves time that is spent 
on manual QA. This process enables early bug detections, bug-fixing, and enhances overall software quality. There are several 
tools available which can integrate with DevOps tools like Selenium, RobotFramework, Appium, XCUITest, JUnit, etc. for test 
automation.

자동화 테스팅은 각 코드베이스를 더 많은 테스트를 거치게 해준다. 테스트 빈도수를 높여주고 수동으로 QA를 진행할 때의 시간을 절약해준다. 이러한 과정은 버그찾기, 버그 수정
전반적인 소프트웨어 품질을 향상 시키는데 많은 도움을 준다. 그리고 몇몇의 좋은 툴들이 있는데 이는  Selenium, RobotFramework, Appium, XCUITest, JUnit,등 이 있다.


#### Continuous Monitoring (CM)

Continuous Monitoring suggests to monitor all systems and infrastructure using several tools, dashboards, and alerts including 
real-time insights of different metrics impacting the software like system performance, number of tests, success and failure 
rates, deployment status, error logs, and all information in graphical, tabular and detailed report format. To accomplish 
such monitoring DevOps team can set up several tools like Prometheus, Grafana, Nagios, Appdynamics, NewRelic, Splunk, 
Logstash and many more are available in the market.

Continuous Monitoring은 시스템 성능, 테스트 횟수, 성공 및 실패율, 배포 상태, 오류 로그, 그래픽, 표 및 세부 구성등의 모든 정보 등 소프트웨어에 영향을 
미치는 다양한 메트릭에 대한 실시간 감시 또한 포함해서 여러 툴, 대시보드 및 경고를 사용하여 모든 시스템과 인프라를 모니터링할 것을 제안한다. 이러한 
모니터링을 위해 DevOps 팀은 Prometeus, Grafana, Nagios, Appdynamics, NewRelic, Splunk, Logstash 등과 같은 여러 도구를 사용할 수 있다.
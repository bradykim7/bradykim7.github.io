---
title: "What is Kubernetes?"
date: 2020-06-24
categories:
  - Kubernetes
  - DevOps
  - Docker
tags:
  - DevOps
---


### What is Kubernetes?

### Original from [HERE](https://dzone.com/articles/what-is-kubernetes-in-devops)

#### Introductions 

Kubernetes is an open-source container orchestration system or tool. In this article, we will explain the basics of kubernetes.

Kubernetes 는 오픈 소스 컨테이너 오케스트레이션 이다. 이번 시간엔 kubernetes의 기본적인 것을 알아보자.

Today in this article, we are going to discuss Kubernetes introduction. We will discuss the following topics in this article:

오늘 이 포스팅에서는 우리는 kubernetes 에 대해 말해보자. 다음을 알아갈 것이다.

1. What is Kubernetes?
2. What is the importance of Kubernetes?
3. Why does Every Company demand Kubernetes?

1. kubernetes란 ?
2. kubernetes의 중요한 점은 ?
3. 왜 모든 기업이 kubernetes 를 요구하지 ?

#### What Is Kubernetes?

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p17.jpg" alt="">

Kubernetes Is an Open-Source Container Orchestration System or Tool
“Orchestration” means to manage anything in a hidden way, so Kubernetes is the hidden way of managing your application.

Kubernetes 는 오픈 소스 컨테이너 오케스트레이션 시스템 혹은 툴이라고 불린다. 여기서 "Orchestration"의 의미는 모든 것을 비밀리에 관리한다는 의미이고, 
Kubernetes는 어플리케이션 몰래몰래 모든 것을 관리한다.

Let’s take a real-world example of our country, we have a lot of peoples living within your country and to manage such
 a huge population, “Politics” plays an important role. Politicians created different policies, rules, and regulations 
 to manage populations. The way by which politics manages a huge population. Kubernetes also manages our application 
 in the same way as politics manage the population.
 
조금 넓게 생각해보자. 수 많은 사람들이 우리나라에 살고 있는데, '정치'라는 것은 중요한 역할을 한다. 정치가들은 각각의 정책과 규칙, 규제들을 이 인구들을 관리하기 위해서
만들어낸다. 이러한 방식으로 정책은 수 많은사람들을 관리한다. Kubernetes 또한 우리의 어플리케이션에서 '정책'과 같은 역할을 한다.


#### What Is the Importance of Kubernetes?

Let’s talk about the example where we are not using the concept of containerization. Let’s recall the previous days
 when we have no container technology and cloud architecture.

컨테이너화 라는 컨샙을 사용하지않는 예를 들어 한번 살펴보자. 예전 방식의 컨테이너 기술과 클라우드 기술들이 존재 하지 않았던 시스템을 살펴보자는 뜻이다.

If any company wants to run the application like Netflix on-premises, then they had buy hardware to deploy their application.
 There was some configuration of that server hardware like 32 GB RAM, 500 HDD, 8 core, etc. They have installed one operating 
 system on the server and configure one IP to that server and bind this IP with the domain name via DNS, in this way their application 
 becomes live to everyone. The main problem arises when the number of visitors to this application increases as it requires
  more memory and storage to handle such huge traffic. The application is not responding after full utilization of the available 
  resources of the server.

만약 어떤 기업이 넷플릭스 와 같은 'on-premises' 어플리케이션을 구동시키고 싶어 한다면, 기업들은 어플리케이션 배포를 위한 하드웨어를 구입해야한다.
32 GB 램, 500HD, 8 core 등 과 같은 여러 서버 구성을 해야될 것이다. 이는 서버의 하나의 운영 시스템에 설치될 것이고, 하나의 IP를 구성해서 그 IP 에 도메인 네임까지 결합할 것이다.
이런 방식으로 우리는 해왔었다. 가장 큰 문제는 많은 수의 방문자가 어플리케이션에 생겼을 때, 많은 양의 저장공간과 메모리와 큰 트래픽을 어떠헥 처리해야하는 가이다. 어플리케이션은 
가동가능한 모든 자원을 쓰고 난후에는 반응하지 못할 것이다.

To handle this problem, they used to configure multiple servers and host their application on those servers. 
Now, there is a need to manage those multiple servers which help to run their application. To manage servers, 
some components are used such as load balancer, firewall, storage, etc. These all component works as orchestration 
in an on-premises deployment. Nowadays, companies use the concept of the container where they are deploying their 
application in multiple containers and all the containers are managed by orchestration tools such as Kubernetes, docker swarm, etc.

이러한 문제를 해결하기 위해, 우리는 다중 서버를 구성하고, 다중 서버로 어플리케이션을 호스팅한다. 이제 이 다중 서버로 구동되는 어플리케이션을 관리해야한다.
이 서버를 관리하기 위해 몇몇의 구성요소들, 로드 밸랜서, 방화벽, 저장소 등을 관리한다. 이러한 모든 구성 요소들은 orchestration로써 동작한다. 오늘날의 기업들은
컨테이너 컨셉을 사용한다. 이 컨테이너 컨샙이란, 기업의 어플리케이션을 멀티 컨테이너에 배포하고, 사용하고, 이 모든 컨테이너들을 orchestration 도구들, Kubernetes, docker swarm 등으로
관리한다.

#### Difference Between Docker Swarm and Kubernetes?

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p178.jpg" alt="">

The above diagram shows the difference between Docker swarm and Kubernetes.

위의 그림은 Docker swarm 과 Kubernetes의 차이점을 보여 주고 있다. 

Docker swarm|Kubernetes
:---|:---
Docker swarm is created and managed by the Docker community. It is not open-source, that is, we are unable to customize it. | Kubernetes is an open-source container orchestration tool that can be fully customizable. It was firstly developed by Google named as borg then, Google donated borg to Linux foundation.
In docker swarm, the components such as API server, controller, scheduler, etc are installed directly on the OS of a master node. | In Kubernetes, these components are not directly installed on the OS. They are installed on the containers which are surrounded by logical boundaries of POD.
Docker swarm은 Docker community에 의해 관리되고 만들어졌다. 오픈소스가 아님|  반면 Kubernetes는 높은 자유도를 지니고 있고 오픈소스이다. 
Docker Swarm의 구성요소들은  메인 마스터 노드에 설치된다. | Kubernetes 들은 OS에 직접 설치되지 않으며, POD에 의해 감싸진 컨테이너에 설치된다.
#### Why Does Every Company Demand Kubernetes?
Kubernetes are the most demanding technology among various company because of the following benefits:

Kubernetes는 아래와 같은 이유로 가장 많이 기업에서 요구되는 기술이다.

Speed of deployment
Ability to absorb change quickly
Ability to recover quickly
Hide infrastructure complexity in the cluster

빠른 배포
쉽고 빠른 흡수 능력
빠른 회복 능력
클러스터에서 복잡한 infrastructure를 숨김
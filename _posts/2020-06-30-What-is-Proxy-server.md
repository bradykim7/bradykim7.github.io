---
title: "What is Proxy Server?"
date: 2020-06-30
categories:
  - DevOps
  - Proxy Server
tags:
  - DevOps
  - Proxy Server
---

### What is Proxy Server?
### Original from [HERE](https://whatis.techtarget.com/definition/proxy-server) 

#### Introduction

A proxy server is a dedicated computer or a software system running on a computer that acts as an intermediary between an endpoint 
device, such as a computer, and another server from which a user or client is requesting a service. The proxy server may exist in 
the same machine as a firewall server or it may be on a separate server, which forwards requests through the firewall.

프록시 서버는 컴퓨터와 같은 엔드포인트 디바이스 혹은 사용자나 클라이언트가 서비스를 요청하는 다른 서버들 사이의 중재적인 역할을 하는 컴퓨터에서 동작하는 소프트웨어 시스템 혹은  컴퓨터를 말한다.
프로시 서버는 컴퓨터에 존재하는 방화벽 서버와 같이 존재하거나 분리된 서버로 존재한다.
 
An advantage of a proxy server is that its cache can serve all users. If one or more Internet sites are frequently requested, 
these are likely to be in the proxy's cache, which will improve user response time. A proxy can also log its interactions, 
which can be helpful for troubleshooting.

프록시서버의 장점은 모든 사용자에게 캐시를 제공할 수 있다는 것이다. 만약 하나 혹은 그 이상의 사이트들이 빈번하게 요청한다면, 이는 유저들에게 빠르게 서비스를 제공하기 위해서
 프록시의 캐시를 가져오는게 좋을 것이다. 또한 프록시 서버는 후에 트러블 슈팅에 도움이 되는 상호작용들에대한 로그들을 저장할 수 있다.

#### How proxy server works

When a proxy server receives a request for an Internet resource (such as a Web page), it looks in its local cache of previously pages. 
If it finds the page, it returns it to the user without needing to forward the request to the Internet. If the page is not in the cache,
 the proxy server, acting as a client on behalf of the user, uses one of its own IP addresses to request the page from the server out
 on the Internet. When the page is returned, the proxy server relates it to the original request and forwards it on to the user.

프록시 서버가 웹페이지와 같은 어떤 인터넷 자원에 관한 요청을 받았을 때, 프록시서버는 그전 페이지들에 대한 로컬 캐시들을 먼저 확인한다.
만약 페이지를 발견한다면, 유저에게 인터넷에 관한 어떠한 요청을 포워딩 하지 않아도 반환한다. 만약 페이지가 캐시에 존재 하지 않는다면, 사용자를 대신해 프록시 서버가 자신의 IP주소를 사용해서
인터넷 페이지를 요청하는 역할을 한다. 

Proxy servers are used for both legal and illegal purposes. In the enterprise, a proxy server is used to facilitate security, 
administrative control or caching services, among other purposes. In a personal computing context, proxy servers are used to 
enable user privacy and anonymous surfing. Proxy servers can also be used for the opposite purpose: To monitor traffic and undermine 
user privacy.

프록시 서버는 합법적인 목적 또는 불법적인 목적 2가지의 용돋로 사용될 수 있다. 만약 기업에서 사용한다면, 프록시 서버는 시설의 보안을 위해 사용하고, 관리자는 서비스를 컨트롤 하거나 캐싱하는
등의 목적을 가지고 사용한다. 개인적인 용도로 프록시 서버는 개인정보를 보호하거나 익명의 서핑을 가능하게 해준다. 프록시 서버는 반대의 목적으로 사용할 수 도 있다. 트래픽을 모니터하거나
개인 정보를 손상시키는 용도 등등. 

To the user, the proxy server is invisible; all Internet requests and returned responses appear to be directly with the addressed 
Internet server. (The proxy is not actually invisible; its IP address has to be specified as a configuration option to the browser 
or other protocol program.)

유저에게 있어서, 프록시 서버는 보이지 않는 서버이다. 모든 인터넷은 직접적으로 표시된 인터넷 서버의 어드레스에  request 와 responses를 반환한다. (사실 프록시서버가 아예 안보이는 것은 아니다
프록시 서버의 IP 주소는 브라우저나 프로토콜 프로그램에 구성 옵션으로 명시되어있다.)

Users can access web proxies online or configure web browsers to constantly use a proxy server. Browser settings include automatically 
detected and manual options for HTTP, SSL, FTP, and SOCKS proxies. Proxy servers may serve many users or just one per server. These
 options are called shared and dedicated proxies, respectively. There are a number of reasons for proxies and thus a number of types 
 of proxy servers, often in overlapping categories.

사용자는 온라인 웹 프록시 서버에 접근할 수 있고, 지속적으로 프록시서버를 사용하기 위해 웹 브라우저를 구성할 수 있다. 브라우저 설정은 자동적으로 혹은 수동적으로 
HTTP SSL, FTP 혹은 SOCKS 프록시 서버 옵션을 탐지 한다. 프록시 서버들은 많은 유저 혹은 오직 단 하나의 유저를 다룰 수도 있다. 각각 이는 공유 프록시, 전용 프록시 옵셥이라고 부른다.
프록시 서버를 쓰는 수 많은 이유가 존재하고, 즉 이에 따른 수 많은 종류의 프록시 서버 또한 존재한다.
 
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/qU0PVSJCKcs/0.jpg)](https://youtu.be/qU0PVSJCKcs)
 
#### Forward and reverse proxy servers

Forward proxies send the requests of a client onward to a web server. Users access forward proxies by directly surfing to a 
web proxy address or by configuring their Internet settings. Forward proxies allow circumvention of firewalls and increase 
the privacy and security for a user but may sometimes be used to download illegal materials such as copyrighted materials
 or child pornography.

포워드 프록시는 클라이언트의 request를 웹 서버 앞으로 보낸다. 사용자들은 포워드 프록시에 직접적으로 웹 프록시 어드레스를 통해 접근한거나 그들의 인터넷 설정을 
구성함으로써 접근한다. 포워드 프록시들은 방화벽을 우회적 접근을 가능하게하고, 보안과 개인정보의 보안을 유저들을 위해 높인다. 그러나 가끔 불법적으로 어떤매체를 다운로드를 할 때 사용되기도한다.

Reverse proxies transparently handle all requests for resources on destination servers without requiring any action on 
the part of the requester.

역 방향 프록시들은 요청자에게 어떠한 행위도 요구하지 않고, 모든 request들을 투명하게 처리한다.

Reverse proxies are used:

- To enable indirect access when a website disallows direct connections as a security measure.
- To allow for load balancing between severs.
- To stream internal content to Internet users.
- To disable access to a site, for example when an ISP or government wishes to block a website.

역 방향 프록시들은 아래와 같이 사용한다:

- 보안상의 이유로 직접 접근이 불간으한 웹사이트에 간접적인 접근을 가능하게 하려고할 
- 로드 밸런싱을 서버 사이에 가능하게 할 
- 인터넷 유저들에게 내부적 콘텐츠를 스트리밍 하려고 할 때
- 사이트에 접근을 불가능하게 할 때, 예를 들어 ISP 나 정부가 웹사이트를 막으려고할 때  

Sites might be blocked for more or less legitimate reasons. Reverse proxies may be used to prevent access to immoral, illegal or 
copyrighted content. Sometimes these reasons are justifiable and sometimes they are not. Reverse proxies sometimes prevent access 
to news sites where users could view leaked information. They can also prevent users from accessing sites where they can disclose 
information about government or industry actions. Blocking access to such websites may violate free speech rights.

사이트들이 블록되는 이유는 대부분 불법적인 이유로 블록될 것이다. 역방향 프록시는 부도덕, 불법 또는 저작권이 있는 콘텐츠에 대한 접근을 방지하기 위해 사용될 수 있다.
이와 같은 이유가 어떨 때는 정당하고, 어떤 때는 그렇지 못할 수도 있다. 역방향 프록시는 종종 사용자가 정보를 흘릴 수 있는 새로운 사이트로의 접근을 막는다. 
또한 사용자들이 정부나 산업 활동에 대한 정보를 공개할 수 있는 사이트에 접속하는 것을 막을 수 있다. 그러한 웹사이트에 대한 접근을 차단하는 것은 언론의 자유 권리를 침해일수도 있다. 


Watch a video introduction to reverse proxy servers (definition continues below):

[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/9rOU_P5YN_Q/0.jpg)](https://youtu.be/9rOU_P5YN_Q)


#### Other types of proxy servers

Transparent proxies are typically found near the exit of a corporate network. These proxies centralize network traffic. 
On corporate networks, a proxy server is associated with -- or is part of -- a gateway server that separates the network
 from external networks (typically the Internet) and a firewall that protects the network from outside intrusion and allows 
 data to be scanned for security purposes before delivery to a client on the network. These proxies help with monitoring 
 and administering network traffic as the computers in a corporate network are usually safe devices that do not need anonymity 
 for typically mundane tasks.

Transparent proxies는 일반적으로 우리가 기업 네트워크 끝에서 볼 수 있는 프록시 서버이다. 이 프록시 서버는 네트워크 트래픽을 중앙화 시킨다. 기업 네트워크에 프록시 서버는 
외부 네트워크(일반적으로 인터넷)과 분리하는 게이트웨이 서버와 연관되있거나 부분이다. 혹은 외부 침입으로부터 네트워크를 보호하고 네트워크의 클라이언트에 전달되기 전에 보안 목적을 
위해 데이터를 검색할 수 있는 방화벽의 부분을 포함된다. 이러한 프록시들은 일상적인 업무를 위해 익명성을 요구하지 않으면서  대체로 안전한 기기에 속해 있는 기업 네트워크의 
모니터링이나 네트워크 트래픽을 관리하는데 도움을 많이 준다. 

Anonymous proxies hide the IP address of the client using them allow to access to materials that are blocked by firewalls 
or to circumvent IP address bans. They may be used for enhanced privacy and / or protection from attack.

Anonymous proxies는 클라이언트의 IP 주소를 숨김으로써 방화벽에 의해 블록 되거나, IP 주소 우회 방식을 벤하는 것을 피해  접근하게 가능해준다.
 
Highly anonymous proxies hide even the fact that they are being used by clients and present a non-proxy public IP address. 
So not only do they hide the IP address of the client using them, they also allow access to sites that might block proxy servers.
 Examples of highly anonymous proxies include I2P and TOR.

Highly anonymous proxies 는 클라이언트가 쓰고 있다는 사실 조차 숨기면서 프록시가 아닌 공용의 IP 주소를 사용한다. 그래서 IP 주소를 사용하는 클라이언트를 숨기는 것 뿐만 아니라
그들은 프록시 서버로 부터의 접근을 차단하는 사이트의 접근도 가능하게 해준다. 이런 프록시의 예로는 I2P 와 TOR이 존재한다.

Socks 4 and 5 proxies provide proxy service for UDP data and DNS look up operations in addition to Web traffic. 
Some proxy servers offer both Socks protocols.

Sock 4, 5 프록시 서버는 UDP 데이터와 DNS look up 동작 및 웹 트래픽 를 위한 프록시 서비스를 제공한다. 몇몇의 프록시 서버는 4,5 두개의 소캣 프로토콜을 제공하기도 한다.

DNS proxies forward domain name service (DNS) requests from LANs to Internet DNS servers while caching for enhanced speed.

DNS 프록시 서버는 LANs 으로 부터의 DNS 요청들을 인터넷 DNS 서버로 전송한다.

#### Proxy hacking

In proxy hacking, an attacker attempts to steal hits from an authentic web page in a search engine's index and search results pages.
 The proxy hacker would have a either a fraudulent site emulating the original or whatever they felt like showing the clients 
 requesting the page.
 
프록시 해킹에서, 공격자는 검색앤진의 인덱스 혹은 검색 결과 페이지에서 인증된 웹페이지에서 히트를 훔치는 것을 시도한다. 또한 프록시 해커는 웹페이지의 원본이나 그들이 페이지를 요청하는 
 클라이언트에게 보여주고 싶은 어떤 가짜의 사이트를 가지고 있을 것이다.

Here's how it works: The attacker creates a copy of the targeted web page on a proxy server and uses methods such as keyword 
stuffing and linking to the copied page from external sites to artificially raise its search engine ranking. The authentic page will 
rank lower and may be seen as duplicated content, in which case a search engine may remove it from its index.

여기 어떻게 공격하는지 알아보자: 공격자는 타겟팅이 되는 웹페이지를 프록시서버에 만들어 놓는다. 그리고 검색 엔진 순위를 인위적으로 높이기 위해 키워드 삽입 및 외부 사이트의 복사된 페이지에 링크하는 등의 방법을 사용한다.
인증된 페이지들은 낮은 우선순위르 가지게 되고 이는 복재된 컨텐츠를 보게 될 것이다. 그리고 검색엔진은 아마 우선순위에서 제외시키게 될 것이다.

This form of hacking can be also be used to deliver pages with malicious intent. Proxy hacking can direct users to fake banking sites,
 for example, to steal account info which can then be sold or used to steal funds from the account. The attacker can also use the 
 hack to direct users to a malware-infected site to compromise their machines for a variety of nefarious purposes.

해킹의 형태는 악의적으로 페이지를 전달하는 형태이다. 예를 들어, 프록시 해킹은 직접적으로 가짜가의 은행 사이트를 개설하여, 계좌를 훔치고, 훔친 계좌로 마음대로 펀드를 사고 파는 
행위들을 할 것이다. 공격자들은 또한 유자들에 대한 직접적인 해킹을 통해 악성 코드를 사이트에 전염 시켜, 사용자들의 컴퓨터들을 사악한 목적으로 악화 시킬 것 이다.

Some means have been developed to compromise proxy abilities. Specially crafted Flash and Java apps, Javascript, Active X and 
some other browser plugins can be used to reveal a proxy user’s identity, so proxies should not be used on untrusted sites or 
anywhere that anonymity is important.

몇몇의 방법은 프록시 능력을 손상시키기 위해 개발되기도한다. 특수하게 조작된 Flash 및 Java 앱, Javascript, Active X 및 일부 다른 브라우저 플러그인은 프록시 사용자의 
신원을 노출하는 데 사용될 수 있으므로, 신뢰할 수 없는 사이트나 익명성이 중요한 장소에서는 프록시를 사용해서는 안 된다.

Website owners who suspect they have been the victim of a proxy hack can test the theory by searching for a phrase that would 
be almost uniquely identifying to the site. Their site should be prominent on the search engine results page (SERP). If a second 
site with the same content shows up, it may be a proxy page.

자신이 프록시 해킹의 피해자가 될 수 있다고 생각하는 웹사이트 소유자들은 사이트에 거의 독특하게 식별될 수 있는 문구를 검색함으로써 이 이론을 시험할 수 있다. 
그들의 사이트는 검색 엔진 결과 페이지(SERP)에서 두드러질 것이다. 콘텐츠가 같은 두 번째 사이트가 나타나면 프록시 페이지일 수 있다.


Eli the Computer Guy explains using proxies for hacking:

[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/-0nl5eEbNk8/0.jpg)](https://youtu.be/-0nl5eEbNk8)

#### Proxy server security

Proxy servers in many forms enhance security but like many things in computing may be vulnerable themselves. 
To prevent DoS attacks and network intrusion, administrators should keep software up to date, use load balancing, 
enforce secure authorization and authentication and block unsolicited traffic, malicious and open proxies.

많은 형태의 프록시 서버는 보안을 강화하지만 컴퓨팅의 많은 것들과 마찬가지로 그 자체도 취약할 수 있다.
DoS 공격과 네트워크 침입을 방지하려면 관리자는 소프트웨어를 최신 상태로 유지하고 로드 밸런싱을 사용하고 보안 권한 부여 및 인증을 적용하며 요청되지 않은 트래픽, 
악성 및 개방형 프록시를 차단해야 한다.

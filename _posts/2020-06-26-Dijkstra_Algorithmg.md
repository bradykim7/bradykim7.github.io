---
title: "Dijkstra Algorithm"
date: 2020-06-24
categories:
  - Algorithm
  - Python3
  - Dijkstra
tags:
  - Algorithm
  - Dijkstra
---


### Dijkstra Algorithm

### Original from [HERE](https://hsp1116.tistory.com/42)

#### Introduction

There's many ways to solve the shortest path problem in graphical Algorithms.

그래프에서 정점끼리의 최단 경로를 구하는 문제는 여러가지 방법이 있다.

1. 하나의 정점에서 다른 하나의 정점까지의 최단 경로를 구하는 문제(single source and single destination shortest path problem)
2. 하나의 정점에서 다른 모든 정점까지의 최단 경로를 구하는 문제(single source shortest path problem)
3. 하나의 목적지로가는 모든 최단 경로를 구하는 문제(single destination shortest path problem)
4. 마지막으로 모든 최단 경로를 구하는 문제(All pairs shortest path problem)이다.


1. First, single source and single destination shortest path problem
2. Secnod, single source shortest path problem
3. Third, single destination shortest path problem
4. And last, All pairs shortest path problem


Dijkstra Algorithm is the second, we can get all shortest path from a one node.And lines should be two ways line.

다익스트라 알고리즘은 여기서 두번째 방법으로, 하나의 정점에서 다른 모든 정점들의 최단 경로를 구한다.간선들은 모두 양의 간선들을 가져야 한다.

Simple logic of Dijkstra Algorithm is the first node is the startint point and  add the node to refresh the shortest path.
And before we add the node, node's value is has a infinite value.

다익스트라 알고리즘의 기본 로직은, 첫 정점을 기준으로 연결되어있는 정점들을 추가해가며, 최단 거리를 갱신하는 것이다.
정점을 잇기 전까지는 시작점을 재외한 정점들은 모두 무한대 값을 가진다.

정점 A에서 정점 B로 이어지면, 정점 B가 가지는 최단 거리는 시작점부터 정점 A까지의 최단 거리 + 점A와 점B 간선의 가중치와, 기존에 가지고 있던 정점 B의 최단 거리중 
작은 값이 B의 최단 거리가 된다.

#### Basic logic of Dijkstra Algorithm

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p19.jpg" alt="">

Let's start at node no.5, so the other node's value should be infinite.

다음과 같은 그래프가 있다. 여기서 시작점은 5번 정점이라고 해보자. 여기서 5번 노드를 제외한 나머지 정점들이 가지는 최단 경로는 아직 연결되지 않았으므로 무한대이다.

5 | 4 | 3 | 2 | 1 
:---:|:---:|:---:|:---:|:---:|
0 |  INFINITE | INFINITE | INFINITE | INFINITE

Let's choose the node that have the shortest distance from node No.5. We have two nodes that linked with node No.5. 
First, Look at teh node No.2. The shortest path would be selected the shortest distance one of those things, No.2 node,(INFINITE),  No.5 Node distance(0) + Distance between No.2 and No.5(4)

Thus, dist[2] = min(dist[2], dist[5] + adj[5][2]) so it means, min(INF,4) = 4.

Likewise, with node No.4:

dist[4] = min(dist[4], dist[5] + adj[5][4]) so, min(INF,2)=2

여기서 경로가 가장 짧은 정점을 고른다. 여기선 5번 노드이다. 5번 노드와 연결되어있는 노드는 2,4번 노드이다.
먼저 2번노드부터 보자. 2번 노드의 최단 거리를 가지고 있는 현재 최단거리(INF)와, 5번 노드의 최단거리(0) + 2번-5번의 가중치(4) 값 중 가장 작은 값으로 갱신한다.

즉, dist[2] = min(dist[2], dist[5] + adj[5][2])을 구한다 이는 min(INF,4)이므로 4가 된다.

4번 노드 또한 4번 노드의 최단 거리를 가지고있는 현재 최단거리(INF)와, 5번 노드의 최단거리(0) + 4번-5번의 가중치(2) 값 중 가장 작은 값으로 갱신한다.

즉, dist[4] = min(dist[4], dist[5] + adj[5][4])을 구한다. min(INF,2)이므로 2가 된다.


5 | 4 | 3 | 2 | 1 
:---:|:---:|:---:|:---:|:---:|
0 |  INFINITE | INFINITE | INFINITE | INFINITE
 -|  2 | - | 4 | -

Now we have to choose the shortest distance node. This time it is No.4 has a 2 so we choose it. Now, we have to see the node 
No.2 and No.3.
dist[2] = min(dist[2], dist[4] + adj[4][2])
dist[3] = min(dist[3], dist[4] + adj[4][3])

이제 나머지 정점 중에서 경로가 가장 짧은 정점을 고른다. 가장 짧은 거리를 가지고 있는 노드는 2의 길이를 가지고 있는 4번 노드이다. 
이제 4번 노드의 인접노드는 2,3번 노드이다.
2번 정점의 최단 거리를 가지고있는 현재 최단거리(4)와, 4번 정점의 최단거리(2) + 2번-4번의 가중치(1) 값 중 가장 작은 값으로 갱신한다.
즉, dist[2] = min(dist[2], dist[4] + adj[4][2])을 구한다
2번 정점의 기존 최단 거리 dist[2]는 4고, dist[4] + adj[4][2]는 3이므로 3으로 갱신된다.

또한 3번 정점은 의 최단 경로 dist[3]은 INF이므로, dist[4] + adj[4][3] = 3으로 갱신한다. 

5 | 4 | 3 | 2 | 1 
:---:|:---:|:---:|:---:|:---:|
0 |  INFINITE | INFINITE | INFINITE | INFINITE
-|  2 | - | 4 | -
-|  - | 3 | 3 | -

And we do this when we get to the final node.

5 | 4 | 3 | 2 | 1 
:---:|:---:|:---:|:---:|:---:|
0 (V)|  INFINITE | INFINITE | INFINITE | INFINITE
-|  2 (V) | - | 4 | -
-|  - | 3 (V)| 3 (V)| -
-|  - | - | - | 6 (V)

We visited all nodes. The path is the node with (V).

모든 정점을 방문했다. 완성한 테이블이 5번 정점부터 나머지 정점까지의 최단 경로이다.


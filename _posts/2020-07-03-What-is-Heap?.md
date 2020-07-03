---
title: "What is Heap?"
date: 2020-07-03
categories:
  - Algorithm
  - Heap
tags:
  - Algorithm
  - Heap
  - Python
---

### What is Heap ?
### Original from [HERE](https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html) 

#### Introduction

##### Priority Queue

Priority Queue is the data structure which has priority in queue.
Datas which is in the priority queues has the sequence when then come out from queues. Thus, higher priority datas come out first.

우선 순위의 개념을 큐에 도입한 자료구조
데이터들이 우선 순위를 가지고 있으며, 우선 순위가 높은 데이터가 먼저 나간다.

자료구조 | 삭제되는 요소
:---:|:---:
Stack | 가장 최근에 들어온 데이터 LIFO
Queue | 가장 먼저 들어온 데이터 FIFO
Priority Queue | 가장 우선순위가 높은 데이터

Data Structure | Delete Elements
:---:|:---:
Stack |  LIFO
Queue |  FIFO
Priority Queue | The highest priority dates

Priority Queue's Example:
- Simulation Systems
- Network Traffic Systems
- OS Scheduling
- Numerical interpretive calculation

우선순위 큐의 이용 사례
- 시뮬레이션 시스템
- 네트워크 트래픽 제어
- 운영 체제에서의 작업 스케쥴링
- 수치 해석적인 계산

In fact, there're many methods to implement the Priority Queue.

우선순위 큐는 배열, 연결리스트, 힙으로 구현이 가능

우선순위 큐 구현법 | 삽입 시간 | 삭제 시간
:---:|:---:|:---:
순서 없는 배열| O(1) | O(N)
순서 없는 연결 리스트| O(1) | O(N)
정렬된 배열 | O(n) | O(1)
정렬된 연결 리스트 | O(n) | O(1)
힙 | O(logN)| O(logN)

Methods | Insertion | Delete
:---:|:---:|:---:
UnOrdered Array | O(1) | O(N)
UnOrdered Linked List| O(1) | O(N)
Ordered Array | O(n) | O(1)
Ordered Linked List | O(n) | O(1)
Heap | O(logN)| O(logN)


##### Heap

- 완전 이진 트리의 일종으로 우선순위 큐를 위하여 만들어진 자료구조이다.
- 여러 개의 값들 중에서 최댓값이나 최솟값을 빠르게 찾아내도록 만들어진 자료구조이다.
- 힙은 일종의 반정렬 상태(느슨한 정렬 상태) 를 유지한다.
    + 큰 값이 상위 레벨에 있고 작은 값이 하위 레벨에 있다는 정도
    + 간단히 말하면 부모 노드의 키 값이 자식 노드의 키 값보다 항상 큰(작은) 이진 트리를 말한다.
- 힙 트리에서는 중복된 값을 허용한다. (이진 탐색 트리에서는 중복된 값을 허용하지 않는다.)

- Kind of Binary Tree,but for priority queue.
- It's good to find a max value or minimum value 
- Half orderd type data structure
    + Bigger existed in high level smaller existed in low level.
    + Thus, it is the binary tree that the parent node's key values is always higher(lower) than the child.
- Heap tree allow duplicated values.

##### Max Heap, Min Heap

Max Heap 
Parent node's key values has to be higher or same than child.
Key(Parent) >= Key(Child)

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p2.jpg" alt="">

Min Heap
Child node's key values has to be higher or same than parent.
Key(Parent) <= Key(Child)

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p3.jpg" alt="">

##### Implementation


<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p4.jpg" alt="">

Insertion 

```python
maxheap = ['-',9,7,6,5,4,3,2,2,1,3]

def insert_Max_Heap(item):
    maxheap.append(item)
    i = len(maxheap)-1
    
    while i >1:
        if maxheap[i//2] < maxheap[i]:
            maxheap[i//2] , maxheap[i] = maxheap[i], maxheap[i//2]
            i = i//2
        else:
            break
        
```

1. Insert node at the end of node (value : 8)

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p5.jpg" alt="">

2. parent node(4) < insert node(8) so ,exchange it

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p6.jpg" alt="">

3. parent node(7) < insert node(8) so ,exchange it again.

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p7.jpg" alt="">

4. parent node(9) < insert node(8) , nothing happen


Delete

In max heap, we have to delete the node which have the highest priority so, in this example, 
we delete key 1 ,value 9

```python
maxheap = ['-',9,7,6,5,4,3,2,2,1,3]

def insert_Max_Heap(item):
    maxheap.append(item)
    i = len(maxheap)-1
    
    while i >1:
        if maxheap[i//2] < maxheap[i]:
            maxheap[i//2] , maxheap[i] = maxheap[i], maxheap[i//2]
            i = i//2
        else:
            break
        
def delete_Max_Heap():
    if len(maxheap) == 0:
        return 0

    item = maxheap[1]
    maxheap[1], maxheap[len(maxheap)-1] = maxheap[len(maxheap)-1], maxheap[1]
    maxheap.pop(len(maxheap)-1)

    i = 1
    while i*2 <= len(maxheap):
        if maxheap[i] > maxheap[i*2] and maxheap[i] > maxheap[i*2+1]:
            break
        elif maxheap[i*2] > maxheap[i*2+1]:
            maxheap[i], maxheap[i*2] = maxheap[i*2] , maxheap[i]
            i = i*2
        else:
             maxheap[i], maxheap[i*2+1] = maxheap[i*2+1] , maxheap[i]
             i= i*2+1
           
    return item
```


1. 최대값인 루트를 삭제

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p8.jpg" alt="">

2. Parent node (3) < Child node (7) so , exchange

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p9.jpg" alt="">

3. Parent node (3) < Child node (5) so , exchange

<img src="{{ bradykim7.github.io }}/assets/images/2020/07/p10.jpg" alt="">

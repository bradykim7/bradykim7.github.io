---
title: "Loop Invariant"
date: 2020-06-28
categories:
  - Algorithm
  - Loop Invariant
tags:
  - Algorithm
  - Loop Invariant
  - Sorting
---

### Loop Invariant 루프의 불변

Sorting Algorithms를 공부하면서 접하게 된 알고리즘이다.

Hackerrank에서 나온 원문과 예제는 [이곳](https://www.hackerrank.com/challenges/correctness-invariant/problem)에서 참고하길 바란다.


#### Loop Invariant (ENG)

In computer science, you could prove it formally with a loop invariant, 
where you state that a desired property is maintained in your loop. 
Such a proof is broken down into the following parts:


Initialization: It is true (in a limited sense) before the loop runs.


Maintenance: If it's true before an iteration of a loop, it remains true before the next iteration.


Termination: It will terminate in a useful way once it is finished.

#### 루프의 불변성 (KOR)

컴퓨터 공학에서는 루프 안에서 어떤 특정한 값이 원하는 값을 가지고 있는 것을 증명하기 위해서 루프 불변식을 이용하여 주로 
증명한다. 그리고 그 증명은 다음의 3가지로 세분화 된다.

초기 : 루프가 돌기 전에 항상 참이 되는 값


유지 : 루프의 반복 이전에 항상 참이라면, 다음 반복이 실행 전에도 참으로써 남아있는다.


종료: 어떤 특정 상황을 만족한다면 종료가 될 것이다.


좀 더 내가 이해 한 내용을 쓰면 수학적 귀납법과 유사하. 즉, 초기에도 참 이고, 유지 단계에서의 값도
참이라면 마지막 종료에도 참? 이런말 인 것 같다. 
한국말로 쓴 나조차 무슨 말인지 이해가 안되고 이해하기가 어렵다. 이를 엔지니어 답게 코드로 해석을 해보자.

##### 코드로 이해하기
##### Loop invariant를 이야기하면서 가장 많이 예를 드는 Insertion Sorting을 예로 들겠다.

```python
    # l 은 List를 의미한다. E.g [7, 4, 3, 5, 6, 2]
    for i in range(1, len(l)):
        j = i-1
        key = l[i] 
        while (j > 0) and (l[j] > key): 
           l[j+1] = l[j] 
           j -= 1
        l[j+1] = key
```

위 코드에서의 초기, 유지 ,종료 단계를 나눠 본다면 


초기화 - 하위 배열은 배열 첫 번째 요소로 시작된다.


유지 - 루프의 각 반복은 서브배 확장하지만 정렬된 속성을 유지한다. 요소 V는 요소의 왼쪽보다 큰 경우에만 배에 삽입된다.배열
왼쪽의 요소는 이미 정렬되었기 때문에 V가 왼쪽의 모든 요소보다 크기 때문에 배열은 정렬된 상태로 유지됨을 의미한다.


종료 - 코드는 배열의 마지막 요소에 도달한 후 종료되며, 이는 정렬된 하위 배열이 전체 배열을 포함하도록 확장되었음을 의미한다. 배열이 이제 완전히 정리되었다.


루프 불변성은 시간이나 메모리에 관해 따지는 것이 아닌, 증명을 해냄에 있어서 중요한 것 같다...
나중에 제대로 알면 다시 정리해야겠다.
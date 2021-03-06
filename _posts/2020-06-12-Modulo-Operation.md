---
title: "Modulo Operation"
date: 2020-06-11
categories:
  - Algorithm
tags:
  - Algorithm
  - Modulo
---

### Modulo Operation
### Original from [HERE](https://opentutorials.org/course/1685/9532)


#### Modulo Circulation, 나머지의 순환

We can experss the 'n' likes below ( n >=0, a > b >=0)

n= ax +b

우리는 0이상의 양의 정수 n의 나머지 a와 몫 b에 대하여 아래와 같은 표현을 사용할 수 있습니다.

n = ax + b (단, a > b >=0)

We can call 'a' to quotient and 'b' is in the range of [0,a-1].
And when 'n' increase by one, b also increase by one and when 'b' over the range, b become zero and re-increase.
Thus, when 'n' increase step by step, remainder 'b' circulate the range of [0,a-1].

위와 같은 식에서 몫을 a라고 한다면, b는 [0, a-1]의 범위 안에 존재하게 됩니다. 
또한 n이 1씩 증가할수록 b는 차례로 1씩 증가하다가 0으로 돌아오고, 다시 증가하고를 반복합니다. 
즉, n이 차례로 증가할 때 마다 나머지 b는 [0, a-1]범위를 순환하게 됩니다.



#### Modulo's law, 나머지의 법칙

When you use a modulo operator, You always have to keep mind that the calculate sequence.
Because, basically modulo operation doesn't have commutative property, associative property and Distributive property.
But, modulo has a special one.

나머지 연산은 기본적으로 결합, 분배, 교환법칙이 모두 성립하지 않습니다. 그래서 사용할 때 항상 계산 순서와 위치에 주의해야합니다. 
단 나머지 연산에서 성립하는 독특한 성질들도 있습니다. 

We can express (a / b )'s remainder, a mod b  = a % b. And followings are always true.

a를 b로 나눈 나머지를 a mod b = a % b라고 표현하기로 합시다. 이 때 나머지는 다음과 같은 식들이 항상 성립합니다. 

( a + m ) % m = a % m

( (a % m) + ( b % m) ) % m = ( a + b ) % m 

( ( a % m) * ( b % m) ) % m = ( a * b) % m 




#### Modulo operation in Circular Queue, 나머지의 역방향 계산법 

This method is usually used in Circular Queue which has a index circulation structure.
주로 환형 큐(Circular Queue)와 같이 인덱스가 순환하는 구조에 자주 사용되는 방법입니다. 아래와 같은 원판을 상상 해 봅시다. 

<img src="{{ bradykim7.github.io }}/assets/images/2020/06/p6.jpg" alt="">

If we start at the A point and move forward B times, we can get the final place with a below function.

현재 우리가 a칸에 서 있다고 가정할 때에 b칸 만큼 앞으로 전진했을 때 서 있을 칸의 위치는 아래와 같이 간단하게 계산할 수 있습니다.

```python
# 길이가 len인 원형 판에서 
# now번 칸에 서 있을 때 count 칸 만큼 전진하면
# 서 있게 되는 칸의 번호 계산하기
def next_step(now, len, count):
    return ( now + count ) % len
```

However, how can we get the final place, if we start at the A pint and move backward distance B. If B <= A, then we can
know that final place is  (A-B)%M but, if B > A, then we get the negative values. So we do different way.
 
그렇다면 반대로 b칸 만큼 뒤로 간 경우 서 있게 될 인덱스는 어떻게 계산할 수 있을까요? b가 a보다 작거나 같다면 바로 (a-b)%m번 칸에 서 있다는 것을 알 수 있지만,
 b가 a보다 큰 경우 (a-b)가 음수가 되어 음수 나머지가 발생하게 됩니다. 위 처럼 환형으로 순환하는 인덱스를 계산하고 싶을때에는 아래와 같이 구현하면 됩니다.


```python
#길이가 len인 원형 판에서
#now번 칸에 서 있을 때 
#count칸 만큼 후진한 후 서 있는 칸 번호
def back_step(now, len, count):
    return (now - (count %len)+len) % len
```

위처럼 계산할 수 있는 이유는 , 어차피 원형판 위에 존재하는 칸의 개수 len번째마다 같은 위치에 서있게 되므로 결국 count칸 만큼 뒤로 간 결과는 (count % len)만큼 뒤로 간 결과와 같습니다.
 이 때 (count % len)은 len보다 작으므로 여기에 len을 더해주면 최종적으로 len으로 나눈 나머지를 구했을 때 결과는 같지만,  len - (count % len)이 항상 양수이므로 양수만으로 계산을 할 수 있게 됩니다.
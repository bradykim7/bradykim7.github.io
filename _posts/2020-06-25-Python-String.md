---
title: "Python String"
date: 2020-06-25
categories:
  - Python3
  - String
tags:
  - Python3
  - String
---


### Python String 

### Original from [HERE](https://www.datacamp.com/community/tutorials/python-string-replace) and [HERE](https://www.datacamp.com/community/tutorials/python-string-split)

#### Python String Replace
##### Learn to find and replace strings using regular expressions in Python.

In order to keep working with your prediction project, your next task is to figure out how to handle negations that occur 
in your dataset. Some algorithms for prediction do not work well with negations, so a good way to handle this is to remove 
either `not` or `n't`, and to replace the next word by its antonym.

미래의 프로젝트에서 너가 유지보수를 하기 위해서, 너가 다음과 같은 임무를 부여 받았다. 부정의 단어들을 다루는 것이다. 예측을 위한 어떤 알고리즘이 존재하는데 잘 작동하지 않는다고 한다.
그래서 `not`과 `n't`를 다른 단어로 대체하는 일로써 해결 할 수 있을 것이다.

Let's imagine that you have the string: `The movie isn't good`. You will need to remove `n't` and replace `good` for `bad`. 
This way, your string ends up being `The movie is bad`. You notice that in the first column of the dataset, you have a string 
that uses the word `isn't` followed by `important`.

`The movie isn't good` 라는 문장 가지고 있다고 상상해 보자. `n't`를 빼고 `good`를 `bad`로 교체해야 한다. 
너의 문장은 결국 'The movie is bad'가 된다. 데이터 집합의 첫 번째 열에는 `isn't`단어와 `important`  사용하는 문자열이 있다는 것을 알 수 있다.

The text of this column has been already saved in the variable `movies` so you start working with it. 
You can use `print(movies)` to view it in the IPython Shell.

이 열의 텍스트는 이미 `moives`라는 변수에 저장되어 있으므로, 당신은 이 칼럼으로 작업을 시작한다. 
`print(movies)` 이용하면 IPython Shell에서 볼 수 있다.

##### Exercise
TRY IT YOURSELF: Access the exercise in our Regular Expressions in Python course here.

Replace the substring `isn't` for the word `is`.
Replace the substring `important` for the word `insignificant`.
Print out the result contained in the variable `movies_antonym`.

```Python3
# Replace negations
movies_no_negation = movies.replace("isn't", "is")

# Replace important
movies_antonym = movies_no_negation.replace("important", "insignificant")
```


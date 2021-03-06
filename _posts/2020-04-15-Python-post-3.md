---
layout: post
title: "[Python3]파이썬 관계연산자와 조건문"
date: 2020-04-15
excerpt: "python posting-03. 파이썬의 조건문과 함께 관계연산자, 논리 연산자, is-elif-else 문에 대해 이해한다. "
tags: [sample post, readability, python, study]
comments: false
---
## 조건문
조건식이 참(True)이냐 거짓(False)냐에 따라 실행 경로가 달라지는 경우에 사용하는 것.

조건식에는 관계 연산자와 논리 연산자가 사용됩니다.
+ 관계 연산자 : 두 개의 피연산자를 비교하는데 사용하는 연산자들
    + `==` : 두 피연산자가 같은가?
    + `!=` : 두 피연산자가 다른가?
    + `>`, `>=`, `<`, `<=` : 두 피연산자의 크기 비교에 따른 참, 거짓

+ 논리 연산자 : 하나 또는 여러 개의 조건식을 조합하여 참인지 거짓인지 따질때 사용하는 연산자
    + `and` : 두 조건식이 참이면 참, 아니면 거짓
    + `or` : 두 조건식 중 하나가 참이면 참, 아니면 거짓
    + `not` : 조건식 하나가 참이면 거짓, 거짓이면 참

## if-else문
if 뒤에 오는 조건식이 참이면 해당 블록 내의 코드들을 실행하고, 거짓이면 else 블록 내의 코드들을 실행하는 대표적인 조건문 유형입니다.  
여기서 블록이란 콜론(:)아랫문장부터 동일 개수의 공백이 이어지는 부분까지를 의미합니다.
```python
age = 17
if age >= 19:
    #참일 경우 실행할 코드
    print("내 나이는 %s" % age)
    print("성인입니다.")
    #if 블록 끝
else:
    #거짓일 경우 실행할 코드
    print("미성년자입니다.")
    #else 블록 끝
print("코드 끝")
```
> 파이썬은 문법이 간결한 만큼 함수나 if문, for문 등 블록 단위로 엄격하게 검사하여 코드를 실행합니다. 따라서 문법 오류가 나지 않도록 일정한 공백 크기를 유지하여 코딩하는 것이 중요합니다. 위 if-else문 예제처럼 공백 4칸이 일정하게 띄어져 있는 것처럼 말이지요! 콜론을 깜빡해도 물론 에러가 나니 주의하세요!

## if-elif-else문
단 두가지의 조건문 말고도 연속으로 if문을 나열하는 방식이 있습니다. 바로 elif 키워드를 사용하는 거에요

```python
score = int(input("내 성적: ")) #사용자에게 입력받은 값을 int형으로 변환하여 score에 저장

if score >= 90:
    print("A")
elif score >= 80: #점수가 90점이 아니면 80점 이상인지 검사
    print("B")
elif score >= 70: #점수가 80점이 아니면 70점 이상인지 검사
    print("C")
else:
    print("D")

```

## 중첩 if-else문
위에서 블록이라는 단위는 동일한 개수의 공백을 가지며, 이것을 잘 따라야 문법 오류가 나지 않는다고 했습니다.

다음의 예제를 눈여겨봐주세요!
```python
age = 20
if age > 19:
    print("미성년자입니다.") 
    #1번
else:
    #2번
    if age > 16:
        print("고등학생입니다.")
    elif age > 13:
        #3번
        print("중학생입니다.")
    else:
        if age > 7:
            print("초등학생입니다.")
            #4번 
```
1번은 공백 4칸(=tab키 한 칸)을 가지며 if문 콜론 뒤에 위치하므로 `age > 19`조건이 참일 경우 실행됩니다.

2번은 공백 4칸(=tab키 한 칸)을 가지며 else문 콜론 뒤에 위치하므로 `age > 19`조건이 거짓일 경우에 실행됩니다.

3번은 공백 8칸(=tab키 두 칸)을 가지며 elif문 콜론 뒤에 위치하므로 `age > 13`조건 이 참인 경우 실행됩니다. 

4번은 공백 12칸(=tab키 세 칸)을 가지며 if문 콜론 뒤에 위치하므로 `age > 7`조건이 참일 경우 실행됩니다.

같은 크기의 공백이 주는 블록의 구분, 이해되실까요?

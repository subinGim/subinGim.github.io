---
layout: post
title: "[Python3]파이썬의 함수와 인수(argument)의 전달"
date: 2020-05-06
excerpt: "python posting-05. 함수의 작성법과 장점, 디폴트 인수와 키워드 인수 사용법, 매개변수가 전달되는 방식에 대해 알아보자 "
tags: [sample post, readability, python, study]
comments: false
---
## '함수'란
특정 작업을 수행하는 명령어들을 한 곳에 모아둔 것을 의미합니다. 함수를 사용하기 위해서는 `호출`이 필요하며, 이때 함수에게 넘겨주는 값을 `인수(argument)` 또는 `매개변수(parameter)`라고 합니다.  
함수는 넘겨 받아진 값들(정수, 문자열, 리스트, 등등 어떤 것이라도 될 수 있겠죠?)로 특정 작업을 수행하게 되고, 작업이 끝나면 결과물인 `반환값(return value)`을 보내오기도 합니다.

함수는 각자의 고유한 이름을 가지며, 호출은 `함수이름()`와 같이 해줍니다.

1. 동일한 작업을 계속 수행해야 할 경우(재사용)
2. 코드가 너무 길어서 가독성이 떨어지는 경우
3. 어떤 처리 결과값을 받아야 하는 경우  
등 함수를 사용하면 더욱 효율적이고 유지보수가 쉬운 코드를 작성할 수 있습니다.

또한 함수는 꼭 호출되는 시점에만 함수 내의 코드들이 실행됨에 주의합시다!  
그리고 함수에서 인수와 반환값은 사용자의 선택에 따라 써도 되고, 안써도 됩니다.

반환값의 경우 하나가 아닌, 여러 개를 반환할 수도 있는데요, 다음 예제를 참고해주세요. 

```python
def sub():
    return 1, 2, 3
a, b, c = sub() #함수 호출과 동시에 return된 값이 a, b, c 각각에 순서대로 저장
print(a, b, c)
#결과
1 2 3
```
## 디폴트 인수(Default argument)
위에서 함수에게 넘겨주는 값을 인수(argument)라고 했습니다.
사용자가 특정 값을 넘겨주는 것 말고, 함수의 인수가 갖는 기본값을 `디폴트 인수`라고 합니다.  
디폴트 인수를 써주고자 할 때는 다른 인수들보다 뒷쪽에 위치해야 하는 것에 주의하셔야 합니다. 다음 예제를 참고하세요

```python
#예제1
def greet(msg = "블라블라", hi):
    print(hi + msg)
greet('안녀엉')
#예제2
def greet(hi, msg="블라블라"):
    print(hi + msg) #안녀엉블라블라
greet('안녀엉') 
#예제3
def greet(hi, msg="블라블라"):
    print(hi, msg) #안녀엉 블라블라
greet('안녀엉') 
```
예제 1같은 경우 디폴트 인수는 msg인데 다른 인수보다 앞쪽에 위치합니다.  
이 경우 \*\*SyntaxError:non-defalut argument follows default argument\*\* 라는 에러가 발생합니다.  
따라서 예제 2와 같이 \*\*디폴트 인수를 써줄 때는 뒤에서부터!\*\* 기억해주세요   

그리고 예제2와 예제3의 차이를 한번 볼까요?  
두 예제의 차이는 print문에서 두 개의 인수 사이를 연결할 때 ` + `를 사용했는지, ` , `을 사용했는지 입니다.  
+를 사용할 경우 문자열을 합하는 것으로 공백없이 출력되지만, 반점을 사용할 경우 자동으로 띄어쓰기가 되어 출력되네요! ( ღ’ᴗ’ღ )


## 키워드 인수(Keyword argument)
위에 sub()함수를 쓰는 예제에서는 인수의 위치에 따라 세 개의 변수에 저장하는 방법을 살펴보았죠! 해당 인수들을 위치 인수(Positional argument)라고 부릅니다.  
이제는 인수의 위치가 아닌 키워드에 의해 함수로 전달되는 키워드 인수에 대해 알아봅시다. 

```python
def sub(a, b, c):
    return print(a,b,c)
sub(1, 2, 3) #결과: 6 인수 위치에 따라 a=1, b=2, c=3으로 받아진다.
sub(a=1, c=2, b=3) #결과: 6 인수의 위치와 상관없이 a=1, b=3, c=2으로 받아진다.
sub(1,c=2, a=3) #결과: 6 인수 a=1, b=2, c=3 으로 받아진다.

sub(4, b=2, 3) #SyntaxError: Positional argument follows keyword argument

sub(5, c=3, b=6) #결과: 14 인수 a=5, b=6, c=3 으로 받아진다.
sub(5, 3, b=6) #TypeError: sub() got multiple values for argument 'b'
```
키워드 인수를 사용시 주의할 점은 위 예제에서 볼 수 있는 syntaxError와 TypeError입니다.

+ SyntaxError: Positional argument follows keyword argument
즉, 디폴트 인수와 마찬가지로 키워드 인수는 위치 인수들보다 뒤에 위치해야 합니다. 뒤에서 부터 선언하는 것이 실수를 줄이는 방법이겠죠?

+ TypeError: sub() got multiple values for argument 'b'
파이썬이 sub에 들어온 값들에 대해 키워드가 없으면 자동으로 앞에서부터 매개변수를 읽습니다.  
예제를 보면 첫 인수인 5가 a에, 그 다음 인수인 3이 b에 대입될 것입니다. 그런데 뒤에서 `b=6`으로 넣겠다고 했으니 앞뒤가 모순적이죠?  
따라서 multiple values를 갖는다고 에러가 발생한 것입니다.  
키워드 인수를 쓸 때 논리적으로 잘 생각한 후 사용해야 할 것 같아요!

### 인수 전달 방식 두 가지
1. call-by-value
값에 의한 호출로, 함수의 \*\*매개변수에 변수값을 복사하여 넘겨줌\*\*으로써 전달되는 방식입니다.  
아래 예제는 modify함수 호출 시 id라는 문자열 변수를 복사하여 넘겨주고, 함수안에서 새로운 문자열을 만들어내는 예제입니다.

```python
def changing(s):
    s += "_g"
    print(s) #결과: soubii_g

id = "soubii"
print("id=", id) #결과: id= soubii
changing(id)
print("id=", id) #결과: id= soubii
```
print문 실행 결과, 함수 호출 전과 후의 결과가 다르지 않음을 알 수 있는데요, 이와 같이 call-by-value 방식은 변수값의 복사본을 함수에게 넘겨주기 때문에 기존 값이 변하지 않습니다.


2. call-by-reference
참조에 의한 호출, 함수의 매개변수에 \*\*참조값\*\*을 전달하는 방식입니다.  
여기서 참조값이란 어떤 자료가 저장되어있는 곳(리스트, 튜플 등등..)을 가리키는 `메모리 주소`값을 의미합니다.

```python
def changing2(li):
    li += [10, 20]
    print(s) #결과: [1, 2, 3, 4, 5, 10, 20]

list = [1, 2, 3, 4, 5]
print(list) #결과: [1, 2, 3, 4, 5]
changing2(list)
print(list) #결과: [1, 2, 3, 4, 5, 10, 20]
```
list라는 값이 [1, 2, 3, 4, 5]를 가리키고 있었고, changing2 함수에 list에 대한 참조값(주소)가 전달되면서 li라는 변수 또한 [1, 2, 3, 4, 5]를 가리키게 됩니다.  
이때 list와 li변수는 같은 값[1, 2, 3, 4, 5]를 가리키고 있겠죠?  

이 상태에서 [10, 20]이 추가되는데 두 변수는 같은 곳을 가리키고 있으므로 결국 list 또한 같이 수정됩니다.  
이렇듯 call-by-reference 방식은 참조값을 주고 받음에 따라 원본 값이 변경될 수 있습니다.  

## 무명함수
이름이 없고 몸체만 있는 함수를 무명함수라고 합니다. 무명 함수의 정의는 `lambda` 키워드를 사용하며 형식은 다음과 같아요.
```python
lambda arg1, arg2:수식 
```
호출 시에는 함수 이름 대신에 `변수명 = lambda ... `와 같이 사용할 수 있습니다.  
다음은 두 정수를 인수로 받아 합을 계산하여 출력하는 예제입니다.

```python
sum = lambda x, y: x+y
print( "정수의 합 : ", sum( 10, 20 ))
print( "정수의 합 : ", sum( 20, 20 ))
```
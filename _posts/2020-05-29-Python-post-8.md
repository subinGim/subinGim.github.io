---
layout: post
title: "[Python3]클래스와 객체, 그리고 상속"
date: 2020-05-29
excerpt: "python posting-08. 객체 지향 프로그래밍에서 중요한 개념인 '객체'와 '상속' 그리고 '다형성'.
파이썬에서는 어떻게 다뤄야 할까?"
tags: [python, study]
comments: false
---
객체, 클래스의 개념을 설명하기 위해서는 먼저 객체 지향 프로그래밍과 객체의 개념에 대한 이해가 필요합니다.

## 객체의 개념
`객체 지향 프로그래밍(Object-Oriented Programming)`이란 현실에서 존재하는 사물들을 컴퓨터상에서 데이터로 추상화시켜 `객체`라는 단위로 표현하고 
각 객체마다의 유기적인 상호작용을 통해 데이터를 처리하는 컴퓨터 프로그래밍 패러다임 입니다.  

이때 각 객체는 \*\*독립적\*\*이며, \*\*메세지\*\*를 주고받고 \*\*상태(state)와 행위(behavior)\*\*를 갖습니다. 

여기 하나의 TV객체가 있다고 가정합시다.  


객체의 상태란 객체의 '속성'을 의미하며 TV객체가 가지는 속성으로는  
+ 채널번호, 볼륨, 전원상태, 해상도, 크기 등 
을 가질 수 있을 것입니다.  


TV객체가 가지는 동작(기능)은  
+ 전원끄기, 전원켜기, 볼륨 변경하기, 해상도 변경하기 등  
을 가질 수 있습니다.  

이처럼 객체는 각자의 상태와 동작을 가지는데, 코드적으로 표현할 때 상태(또는 속성)는 `필드` 또는 `인스턴스 변수`, 동작(또는 기능)을 `메소드(method)`라는 이름을 가집니다.  

이러한 개념은 파이썬 뿐만아니라 다른 객체 지향 언어들과 같습니다.

위 TV객체의 속성과 메소드를 파이썬 코드로 한번 표현해볼까요?
```python
channel = 38 #채널 번호
volume = 12 #볼륨 크기
isPowerOn = True #전원 상태
light = 'UHD' #해상도
size = '64inch' #화면 크기(inch)

def turnOn():
    #...

def turnOff():
    #...

def volumeUp():
    #...

def changeLight():
    #...
```

## 클래스의 개념
객체는 사용자가 어떻게 정의하느냐에 따라 다양하게 생성될 수 있습니다.  

마치 호빵안에 단팥을 넣는냐, 야채를 넣는냐, 단팥+크림을 넣는냐 선택하는 것 처럼요! ~저는 팥 극호...~  
하지만 단팥빵을 매번 손으로 빚는 것보다는 틀에 반죽을 넣어 만드는 것이 더 빠르고 일정하게 많이 만들 수 있지 않겠어요?  


설명이 좀 진부했지만.. 
단팥빵을 객체라고 생각한다면 틀의 역할을 해주는 것이  
바로 `클래스(class)`입니다.  
그리고 클래스로부터 만들어진 객체들을 `인스턴스(instance)`라고 부릅니다.  각각의 인스턴스는 또 각자의 이름을 가진답니다!  

클래스로 특정 객체를 여러 개 생성해보는 것을 코드로 표현해볼게요
```python
class Phone: 
    def __init__(self, name1, brand1):
        self.name = name1
        self.__brand = brand1 #접근지정자를 private으로 설정
        self.isPowerOn = False

    def turnOn(self):
        self.isPowerOn = True

    def turnOff(self):
        self.isPowerOn = False

#클래스를 이용하여 인스턴스 세 개 생성
p1 = Phone('갤럭시s20', 'samsung')
p2 = Phone('아이폰11', 'apple')
p3 = Phone('아이폰11_PROMAX', 'apple')
#생성된 인스턴스 객체를 통해 메소드 호출
p1.turnOn()

```
class 내부에 메소드를 정의할 때는 꼭 첫번째 인자에 `self`키워드가 붙어야 함을 참고하세요.  
self는 class 안에서 자기 자신을 의미하는 지칭할 때 사용하며, `self.name`, `self.isPowerOn`에서와 같이 클래스 내부에서 변수나 메소드를 호출할 때 사용합니다.  

또한 메소드에 다른 파라미터(인자)를 넘겨받고자 할 때는 ` , `으로 연결하여 파라미터명을 적어주면 됩니다! `__init__`메소드 처럼요~

### __init__() : 생성자
생성자(constructor)는 클래스가 \*\*최초\*\*에 생성될 때 원하는 값으로 초기화시키기 위해 사용하는 특수한 메소드 입니다.  
위 예제처럼 매개변수를 받아오 그 값으로 초기화시킬 수도 있고, `클래스명()`형식과 같이 매개변수 없이 객체를 생성할 수도 있습니다.

생성자는 필요에 따라 적어주면 되는 선택 사항입니다만 '메소드'이기 때문에 `self` 를 꼭 붙여줘야 함은 잊지 마세요! 

만약 메소드에서 self를 써주지 않으면 다음과 같은 TypeError가 발생해요.
```python
TypeError: turnOn() takes 0 positional arguments but 1 was given
TypeError: __init__() takes 2 positional arguments but 3 were given

#해석: y개의 파라미터가 필요한데 x개의 파라미터 밖에 없다. y-x의 차수가 1이라면, 인수 하나가 빠졌다면 self가 넣어져있는지 확인하자.
TypeError: 메소드명() takes x positional arguments but y were given
```

## 정보은닉과 캡슐화
캡슐화(encapsulation)란 데이터와 알고리즘을 하나로 묶음으로써 외부에서 해당 기능에 대해, 데이터가 어떻게 처리되는지를 알 수 없도록 숨기는 것을 의미합니다.

비슷한 개념으로 정보은닉(information hiding)이 있습니다.  
클래스 안에 정의된 변수를 외부에서 직접적으로 접근할 수 없도록 접근지정자(public, private, default 등)를 설정, 외부에서는 메소드만 접근하여 사용할 수 있게 합니다.  

위 코드 예제에서처럼 접근지정자를 private으로 설정하는 파이썬 문법은  
변수명 앞에 `__`를 붙이는 것입니다.  
```python
self.__brand #접근지정자를 private으로 설정
```
그럼 이제 의문이 생길거에요.  

"외부에서 변수를 직접 접근할 수 없다면 인스턴스를 만들어도 어떻게 변수값을 변경하지?"  

정답은 __메소드__ 입니다.

변수에 직접 접근 없이 메소드를 사용하여 변수값을 불러오고, 수정하는 역할을 해주는 메소드를 각각 `접근자(getter)`, `설정자(setter)`라고 부릅니다.  

이 메소드들의 정의 또한 개발자의 선택사항이지만 캡슐화를 지양하는 객체 지향 프로그래밍에서는 이들을 사용하는 것이 추천됩니다.

사용 형식은 다음과 같습니다.
```python
class Phone: 
    def __init__(self, name1, brand1):
        self.name = name1
        self.__brand = brand1 #접근지정자를 private으로 설정
        self.isPowerOn = False

    #접근자: 이름을 'get+변수명'으로 짓는 것이 일반적
    def getBrand(self):
        return self.__brand
    #설정자: 이름을 'set+변수명'으로 짓는 것이 일반적
    def setBrand(self, b):
        self.__brand = b

#클래스를 이용하여 인스턴스 생성
p1 = Phone('갤럭시s20', 'apple')
print(p1.getBrand()) #apple 출력

#생성된 인스턴스 객체를 통해 getter, setter 호출
p1.setBrand('samsung')
print(p1.getBrand()) #samsung 출력
```
---
layout: post
title: "JavaScript의 자료형"
date: 2020-04-22
excerpt: "js 포스팅-01"
tags: [sample post, readability, javascript]
comments: false
---
## JavaScript는
인터프리터 방식의 프로그래밍 언어로서, 소스코드를 실행파을로 변환하지 않고 한줄씩 읽으며 실행된다.
js인터프리터는 웹브라우저에 내장되어 있다.

> node.js는 js를 서버에서 실행하기 위한 플랫폼이다. 당연히 node.js에도 js인터프리터가 내장되어 있다. 
> 여기서 플랫폼이란 실행 엔진(인터프리터), 라이브러리, 개발도구를 합한 것이다.
> 예를 들어 안드로이드는 자바 vm과 라이브러리, sdk가 합쳐진 플랫폼이다.


비쥬얼코드 단축키
새 터미널 ctrl+shift+`
터미널 창 열고 닫기 (종료되는 것은 아님) ctrl+`

자바 스크립트 명령어
프린트 console.log("");
변수선언은 let 또는 var 변수타입은 쓰지 않는다. let은 지역변수를 의미한다.
문장 끝의 ; 을 생략할 수 있다.

js소스코드 파일의 실행은 main함수에서 시작하지 않는다. 각 소스코드 파일에서 코드 순서대로 실행된다.

## JavaScript의 자료형
js는 약타입 언어라서 변수의 자료형을 엄격하게 구분하지 않음. 자바는 강타입 언어.
따라서 js는 변수 선언없이도, 변수 자료형을 언급하지 않아도 실행에 문제가 없다.

비교연산자 ===, !==를 쓰면 타입까지 비교해주는 연산자다.
==는 타입을 비교하지는 않음
자매품으로 typeof가 있는데 해당 변수의 타입을 알수 있음
js에서 숫자는 무조건 number 타입이다. 즉, 정수와 실수를 구분하지 않음

-js의 기본자료형은 number/string/boolean/undefined이다. 
-js의 복합자료형은 function/object 이다. function이 자료형이라함은 함수 자체가 값이고, 때문에 이 함수를 다른 변수에 대입할 수 있음을 의미한다. 


js에서 undefined라는 키워드는 어떤 변수가 선언된 후에 아직 값이 대입되지 않은 값임을 의미한다.
null키워드와 비교를 하자면 null도 값 자체를 의미하기 때문에 undefined는 null이라는 값 자체도 없는 것이고, null은 null이라는 비어있는 "값"이 되어있음을 의미한다.

형변환 명령
문자열 -> 숫자 parseInt( ) /parseFloat( )/Number( )
숫자 -> 문자열 toString( ) / String()

Math클래스
Math.PI
Math.rount() 반올림
Math.pow(2, 4) 거듭제곱
Math.sqrt( ) 제곱근
Math.abs(-3) 절대값
Math.floor() 내림
Math.ceil() 올림
Math.max(1,2,3) 목록에서 최대값 리턴
Math.min(4,3) 목록에서 최소값 리턴
Math.random() 난수 메소드 

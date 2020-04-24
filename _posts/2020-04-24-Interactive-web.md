---
layout: post
title: "Interactive web 기초"
date: 2020-04-24
excerpt: "interactive web-01"
tags: [sample post, readability, javascript, jQuery]
comments: false
---
### HTML과 CSS로만 구성한 페이지를 Js코드로 간단하게 
onclick="document.getElementById('').src='이미지경로';" 
### JavaScript 코드로 바꾸기

html태그 사이에 들어가는 js코드는 최대한 간결할수록 좋다.
js문법을 간단하게 사용할 수 있는 라이브러리인 jquery.
를 사용하기 위해서는 환경설정이 필요하다.
google에서 jquery cdn을 검색해서 사이트를 들어가 원하는 버전을 선택하여
<script>코드를 html태그 안 head부분에 붙여넣는다.

설치방법은 이처럼 cdn을 사용하는 방법, jquery코드를 직접 다운 받는 방법 두가지가 있다.
코드를 직접 다운받는 경우에는 프로젝트 안에 원하는 위치에 두고, <script>태그에 해당 코드(확장자는 .js)파일에 대한 경로를 적어준다. 


$('#사과') : id가 '사과'인 특정 요소를 선택하는 것. 이 표시가 있다면 jquery를 사용했다는 것을 알 수 있음.
attr : 해당 요소의 속성을 바꾸는 역할
css : 해당 요소의 css속성을 바꾸는 역할
### HTML 이벤트 요소
* 사용자가 요소 클릭
* 요소 위나 바깥으로 마우스가 올라오고 나감
* 페이지 로딩 끝
* 키보드 누름

위처럼 이벤트가 발생했을 때 특정 코드를 실행시키는 것을 '이벤트 핸들링'이라고 한다.
그리고 이러한 이벤트를 처리하는 함수를 '이벤트 핸들러' 라고 한다. 
이때 사용할 수 있는 것이 .on인데 
특정 jquery요소에 이벤트를 추가하는 것을 의미함.

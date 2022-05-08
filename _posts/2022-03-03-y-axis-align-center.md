---
layout: post
title: "[CSS]세로 방향으로 가운데 정렬하기"
subtitle: "line-height와 vertical-align"
date: 2022-03-03 02:43:00 +0900
background:
categories: css
---

<h1>[CSS]세로 방향으로 가운데 정렬하기</h1>

내 블로그의 navbar에서 문제가 생겼다.

"category"에 마우스를 올렸을 때, 여러 카테고리가 잘 정렬되어 나타나야 하는데,

글자가 네모 칸 위에 딱 달라붙어 이상했다.

그래서 구글에 검색해서 세로 방향으로 텍스트 가운데 정렬을 시도해보았다.

시도 1)

    vertical-align : middle;

그런데 이게 안되는 경우,

시도 2)

    display: table;    

그런데 시도 2를 할 때, 다른 스타일에 영향을 주는 경우가 생긴다.

이런 경우, 

시도 3)

    line-heigt: <text가 속해있는 태그의 height>;


CSS는 Cascading Style Sheets인 것을 명심하자.

여기서 Cascading의 의미는 스타일 시트에서 우선순위가 위에서 아래로 계단식으로 적용된다는 의미이다. 

즉, 우선순위가 높은 것을 적용하고 나머지는 덮어쓴다는 말이다.

따라서 , CSS의 스타일 우선순위를 잘 파악하여 적용하는 것이 중요하다.
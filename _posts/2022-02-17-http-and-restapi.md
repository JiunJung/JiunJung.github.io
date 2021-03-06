---
layout: post
title: "HTTP와 REST API"
keywords: "REST API, HTTP, HTTP와 REST API"
date: 2022-02-17 17:46:00 +0900
background: '/img/posts/2022-02-17-plastic-cup.jpg'
categories: etc
---

<h1>REST API란? | HTTP와 REST API</h1>
<p>사이드 프로젝트를 구상하다가 공공 API를 사용하고자 <a href="https://www.data.go.kr/" target="_blank">공공 데이터 포털</a>에 들어갔다.</p>
<p>여기서 다양한 OPEN API를 구경할 수 있었는데, 내가 사용하려는 API에 "API 유형 : REST"라는 말이 있었다.</p>
<p>언젠가 REST API에 대해서 설명하는 동영상을 본 적이 있는데 기억이 가물가물해 다시 찾아보았다.</p>
<p><a href="https://www.youtube.com/watch?v=PmY3dWcCxXI" target="_blank">REST API (생활코딩)</a>과 <a href="https://ko.wikipedia.org/wiki/REST" target="_blank">REST API - 위키백과</a>를 참고해 REST API가 뭔지 대략 알 수 있었다.</p>
<p>이번 포스트는 이렇게 찾아본 "REST API"에 대한 내용을 간략히 정리한 것이다.</p>
<p>REST API는 어떤 기술이나 도구가 아니라 일종의 지침 또는 약속이다.</p>
<p>그리고 REST API는 HTTP를 최대한 활용하는 통신 지침이라고 할 수 있다.</p>
<p>REST API에서 데이터를 resouce라고 한다.<small>(resource는 collection(데이터 묶음)과 element(데이터 하나)로 이루어져 있다.)</small></p>
<p>이 resouce를 CRUD할 때 HTTP method를 각각 post, get, put/patch, delete로 함으로써 HTTP의 의미를 명확이 하자는 것이 REST API에서 말하는 지침이다.</p>
<p>또한 resouce식별 시 URI로 하고, <small>(예를 들어 "http://example.com/collection/elementID")</small></p>
<p>결과는 status code로 표현하자는 것이다.<small>(예를 들어 "200 ok", "404 page not found")</small></p>
<P>이렇게 REST API는 HTTP가 원래 가지고 있는 의미를 잘 활용하자는 권고안이라고 할 수 있다.</P>

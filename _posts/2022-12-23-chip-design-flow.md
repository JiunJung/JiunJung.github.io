---
layout: post
title: "Chip Design Flow"
keywords: "Chip Design Flow, 칩 설계 과정, digital design, verilog"
date: 2022-12-23 13:00:00 +0900
background: '/img/posts/2022-02-15-blog.jpg'
categories: semiconductor-talk
---

# Chip Design Flow

-----------------------------------

<br/>

팹리스 회사에서 반도체 칩이 만들어지는 과정을 Chip Design Flow 라고 한다.


<br/>

## 1. Collect Requirements
------------------------------------
<br/>
우선, 시장의 수요를 조사하여 어떠한 스펙을 가진 반도체 칩을 만들지 정해야 한다.

<br/>

## 2. Product Requirement/Specipication
---------------------------------------
<br/>
반도체 칩의 구체적인 스펙을 결정한다. 예를 들어, 동작 주파수는 몇 Hz로 할 것인지, 그래픽 카드는 어떤 것을 쓸 것인지 등 어느 정도의 성능과 기능을 가질 것인지 정한다.

<br/>

## 3. Architecture Specification
---------------------------------------
<br/>
칩의 구조를 구상하는 단계이다. 위에서 결정한 스펙을 충족하는 칩을 만들기 위해서 어떠한 구성요소를 어떻게 연결해야 하는 지 결정한다.

<img src="/img/in_post/chip-require.jpg" width = "500" height = "500">

(출처 : chipverify.com)

<br/>


## 4. Digital Design(RTL)
-------------------------------------

<br/>

베릴로그와 같은 하드웨어 기술 언어로 코딩을 하여 칩을 설계한다. 이 단계를 RTL 설계라고 한다. 참고로 RTL은 Resistor Transfer Level의 준말.

보통 이 때, 칩을 처음부터 끝까지 모두 코딩해서 설계하는 것은 아니다. 물론 회사에서 이미 만들어 놓은 IP(베릴로그 코드)만으로 칩을 만들 수도 있겠지만 대부분의 경우에는 여러 IP Vendor에서 IP 코드를 구매하고 그 것들을 잘 연결하여 설계한다. 

베릴로그 코딩을 할 때에는, 회로의 동작을 기술하는 Behavior방식으로 코딩을 한다. Behavior 방식의 Verilog 코드는 C코드와 비슷하다.

<img src="/img/in_post/verilog.jpg" width = "300" height = "450" >

[베릴로그 코드 (출처 : chipverify.com)]

<br/>


## 5. Verification
------------------------------------
<br/>

우리가 RTL 단계에서 설계한 것에 문제가 없고 잘 동작하는 지 테스트하는 단계이다. 칩이 물리적으로 제작되기 이전에 검증하는 단계이기 때문에 pre-silicon verification이라고도 한다.

이 단계에서는 테스트를 만들어서 이전 단계의 RTL 디자인을 검증한다. 다양한 stimulus를 DUT(Design Under Test)에 넣어주면서 설계한 것이 원하는 대로 잘 동작하는 지 시뮬레이션한다. 에러가 있으면 다시 이전 단계로 돌아가 RTL 디자인을 수정하고 다시 검증 작업을 하는 방식으로 진행된다.

검증을 하는 방식에는 크게 (1) 베릴로그(시스템 베릴로그)로 테스트 벤치 코드를 만드는 방법, (2) C 코드를 만들어 가상의 CPU를 통해 디자인을 테스트 하는 방법, (3) UVM을 사용하는 방법이 있다.

<br/>

## 6. Logic Synthesis 
-------------------------------------
<br/>

RTL 코드를 게이트 수준의 netlist로 변환하는 작업이다. EDA tool이 Behavior 코드를 해석하여 게이트 수준의 코드로 바꿔준다. 이 단계가 있기 때문에 앞서 RTL 코딩 시 게이트 수준의 코딩이 아닌 Behavior 코딩을 통해 쉽게 디자인하는 것이 가능했던 것이다.

<img src="/img/in_post/netlist.jpg" width="700" heigth="300">

[게이트 수준 코드 (출처 : chipverify.com)]

<br/>

## 7. Logic Equivalence 
--------------------------------------
<br/>

Synthesis의 결과물인 netlist를 검증하는 단계이다. 굉장히 많은 논리 게이트와 플립플롭이 있기 때문에 검증을 하는 시간은 굉장히 오래걸린다. 앞서 pre-silicon verification을 이미 수행했는데도 이 단계를 진행하는 이유는 RTL 디자인에 맞게 netlist가 잘 생성되었는지 검증하기 위함이다.

<br/>

## 8. Placement and Routing
------------------------------------
<br/>

앞서 생성된 netlist를 통해 물리적인 디자인을 하게 되는 단계이다. 흔히, PnR이라고 불리는 작업이며 보통 EDA tool을 통해 이루어진다. 이 때, 물리적 디자인을 레이아웃이라고도 한다.

<img src="/img/in_post/layout.jpg" width="400" height="400">

[레이아웃 (출처 : chipverify.com)]

레이아웃 작업 시에는 CTS가 매우 중요하다. CTS는 Clock Tree Synthesis의 준말이며, 칩 내부에서 clock skew를 줄이기 위해 버퍼를 효율적으로 배치하는 작업이다. clock skew란 병렬 통신 시, 출발한 신호가 도착점에 동시에 도착하지 못해 늦게 도착하는 신호에 의해 동작이 지연되거나 오류가 발생하는 현상을 말한다. 따라서, 병렬적인 신호가 동시에 도달할 수 있도록 버퍼를 설계하여 clock skew를 예방해주어야 한다.

<br/>

## 9. Validation
----------------------------------
<br/>

마지막으로, 파운드리에서 Fab-out된 샘플 반도체 칩을 테스트하는 작업이다. 시뮬레이션이 아닌 실제 칩을 테스트하는 작업이다보니 아무래도 이전 검증작업에 비해서 훨씬 많은 시간이 걸리게 된다. 여러 온도에서 칩을 동작시켜 보기도 하는 등의 다양한 테스트를 진행하게 된다.

<br/>


실제로는 각 단계에서 세분화되기도 하고 변형이 이루어지기도 하지만 전반적으로 위 내용대로 반도체 칩이 디자인된다.

여기까지가 Chip Design Flow!
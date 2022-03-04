---
layout: post
title: "Behavioral coding in verilog"
date: 2022-03-04 01:59:00 +0900
background:
categories: ComputerArchitecture
---

컴퓨터 구조 강의를 듣기 전 지난 논리회로설계 강의를 복습하면서 중요하다고 생각하는 부분을 좀 적어보았다.

# 1. verilog와 behavioral coding

verilog는 HDL로서 HDL은 Hardware description language의 약자이다.
C언어로 하드웨어의 특정부분을 표현하기에는 한계가 있어 등장하게 되었다.
다음은 베릴로그 코드의 예시이다.
        
    module example(a,b,c,f,e);
        input a,b,c;
        output f,e;

        and g1(d,a,b);
        not g2(e,c);
        or g3(f,d,e);
    endmodule

a,b,c,f,e 는 port라고 부르며 input port, output port로 나뉜다.
d와 같이 회로의 node에도 labeling을 해주어야한다.
위와 같은 코드는 structural code라고 할 수 있는데, 말 그대로 회로의 구조 그대로, 즉, 게이트를 그냥 코드로 옮겨 놓은 것이다.
이러한 코딩 방식의 문제점은 VLSI와 같은 규모가 큰 회로를 설계할 때 상당히 복잡해진다는 것이다.
behavioral coding을 통해 이러한 문제를 해결할 수 있다. 다음은 behavioral coding 예시이다.

        
    assign d = a & b;
    assign e = ~ c;
    assign f = d | e;
        
assign은 조합논리회로(combination circuit)임을 명시해주는 예약어이다.
이처럼 behavioral coding이란 회로의 구조가 아닌, 구현할 기능을 명시하는 코딩 방식이다.

Synthesis라는 툴(시놉시스 회사 참고)을 이용하면 behavior code를 sturctural code로 바꿀 수 있다. 즉, 회로를 디자인 할 때에는 굳이 복잡한 structural coding을 할 필요없이 behavior coding을 한 후 설계를 위해서 Synthesis 툴로 structural code로 바꿔주기만 하면 된다.

참고 : "In computer engineering, logic synthesis is a process by which an abstract specification of desired circuit behavior, typically at register transfer level (RTL), is turned into a design implementation" <https://en.wikipedia.org/wiki/Logic_synthesis>

그래서 structural code는 디자인이 아닌 모델링이라고 말한다. 

# 2. DUT와 TestBench
Testbench란 회로가 동작을 하는 지 테스트 하는 것을 말한다.
DUT란 Device Under Test의 약자로 테스트 대상 장비를 일컫는 말이다.
회로 검증 시, Testbench 모듈 내에서 DUT모듈을 테스트하는 식으로 코드가 짜여지게된다.
예를 들어 다음과 같다.

    module tb_examble();
        reg x,y,z;
        wire m,n;

        <some DUT>

        <some test>

    endmodule

# 3. 기타 verilog 용어
- initial 이란 0ns에 초기화 할 것을 말함. 여러개를 병렬적으로 initilaize할 수 있음.
- #20 이란 20ns만큼 딜레이 시킨 후 다음 명령을 수행할 것이라는 의미.
- $finish 란 시뮬레이션을 종료한다는 뜻.
- 4'b0100 이란 크기가 4인 binary 0100 (십진수로는 4)이라는 뜻.
  
다음 예시는 module을 만들고 쓰는 예시임.
        
    module mydesign(input x, y, z
                    output o);
        ...
    endmodule
    
    module tb_top();
        wire[1:0] a;
        wire b,c;
        mydesign d0(a[0],b,a[1],c);

    endmodule
        
참고로 [1:0] 은 0부터 1까지 2칸의 array라고 생각할 수 있음. 여기선 bus 라고 함.
mydesign d0와 같이 모듈과 그 모듈의 새로운 이름을 주면서 모듈 사용.

-----
추천사이트 : <https://www.chipverify.com/verilog/verilog-tutorial>
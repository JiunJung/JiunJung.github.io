---
layout: post
title: "[c++]배열을 사용해서 최솟값 최댓값 찾기"
date: 2022-03-17 01:45:00 +0900
background:
categories: cpp
---

# [C++]배열을 사용해서 최솟값 최댓값 찾기

새학기가 시작되고 바빠져서 포스트를 올리는 것이 늦어졌다.

학교 수업과 개인 공부를 병행하는 일이 쉽지 않은 것 같다...

C++ 공부를 하면서 백준에서 문제를 풀어보았다.

10818 문제는 배열을 사용하여 최댓값 최솟값을 골라내는 것이다.

입력 : 
    
    5
    20 10 35 30 7

출력 :

    7 35

코드

    #include <iostream>
    #include <algorithm>
  
    int main()
    {
        std::cin.tie(NULL);
        std::ios_base::sync_with_stdio(false);
        int* a = new int[1000000];
        int n;
        std::cin >> n;
        for (int i = 0; i < n; i++) std::cin >> a[i];
        std::sort(a, a + n);
        std::cout << *a <<" " << *(a+n-1);
        delete[] a;
        return 0;
    }

코드해설
- using namespace std; 는 일반적으로 권장되지 않는다. (namespace 충돌 문제 방지 위함.)
- C++에서는 algorithm이라는 STL(표준 템플릿 라이브러리)를 제공하고 있고, 이 라이브러리 안에 sort를 사용하여 퀵정렬 알고리즘 기반의 정렬을 할 수 있다.
- 배열은 힙영역에 동적할당하기위해 new와 delete를 사용했다.
---
layout: post
title: "c++ 에서 배열을 사용해서 최솟값 최댓값 나타내기"
date: 2022-03-17 01:45:00 +0900
background:
categories: DevJiun
---

# C++에서 최솟값 최댓값 찾기

새학기가 시작되고 바빠져서 포스트를 올리는 것이 늦어졌다.

최근에 C++공부를 시작하면서 백준이라는 사이트를 알게되었고, 문제 푸는 것에 맛 들려 3일째 매일 접속해서 문제를 풀고 있다. 랭킹 올리는 재미가 있다.

아래는 내가 생각한 백준 10818 문제의 답이다.

10818 문제는 배열을 사용하여 최댓값 최솟값을 골라내는 것이다.

    #include <iostream>
    #include <algorithm>
    using std::cin;
    using std::cout;

    int main()
    {
        cin.tie(NULL);
        std::ios_base::sync_with_stdio(false);
        int* a = new int[1000000];
        int n;
        cin >> n;
        for (int i = 0; i < n; i++) cin >> a[i];
        std::sort(a, a + n);
        cout << *a <<" " << *(a+n-1);
        delete[] a;
        return 0;
    }

코드해설
- C++에서는 algorithm이라는 STL(표준 템플릿 라이브러리)를 제공하고 있고, 이 라이브러리 안에 sort를 사용하여 퀵정렬 알고리즘 기반의 정렬을 할 수 있다.
- 배열은 힙영역에 동적할당하기위해 new와 delete를 사용했다.
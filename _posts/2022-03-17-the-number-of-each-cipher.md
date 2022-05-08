---
layout: post
title: "[c++]백준 2577번"
date: 2022-03-17 01:45:00 +0900
background:
categories: cpp
---

# [C++]백준 2577번

1차원 배열을 사용해보라는 취지의 문제이다.

세 개의 자연수 A, B, C가 주어질 때 A × B × C를 계산한 결과에 0부터 9까지 각각의 숫자가 몇 번씩 쓰였는지를 구하는 프로그램을 작성하시오.

예를 들어 A = 150, B = 266, C = 427 이라면 A × B × C = 150 × 266 × 427 = 17037300 이 되고, 계산한 결과 17037300 에는 0이 3번, 1이 1번, 3이 2번, 7이 2번 쓰인 것이다.

입력

    150
    266
    427

출력

    3
    1
    0
    2
    0
    0
    0
    2
    0
    0

코드

    #include <iostream>

    int main()
    {
        std::cin.tie(NULL);
        std::ios_base::sync_with_stdio(false);
        int a, b, c;
        std::cin >> a >> b >> c;
        int mul = a * b * c;
        int num[100];
        int i = 0;
        while (mul != 0) {
            num[i] = mul % 10;
            mul /= 10;
            i++;
        }
        for (int j = 0; j < 10; j++) {
            int output = 0;
            for (int k = 0; k < i; k++) {
                if (num[k] == j) output++;
            }
            std::cout << output<<"\n";
        }
        return 0;
    }


코드 해설 

- while문은 계산결과의 각 자릿수를 배열에 저장한다.
- 이중 for문은 0부터 9까지 각 숫자가 각 자릿수에 몇 개가 있는 지 센다.
- std::endl 대신에 "\n"을 쓰면 속도를 향상 시킬 수 있다.
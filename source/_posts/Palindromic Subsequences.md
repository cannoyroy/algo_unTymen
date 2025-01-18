---
title: Palindromic Subsequences
category:
  - CodeForces
tags:
  - math
  - constructive algorithms
  - brute force
date: 2025-01-17
updated: 2025-01-18
mathjax: true
---

[Problem - C - Codeforces](https://codeforces.com/contest/2056/problem/C)

## SOLUTION

本质上：需要找到一种构造规律

案例分析如下：

- 对于 1 1 2 3 1 2 有回文子序列:

  - 1,1,1

  - 1,2,1
    1,3,1

  - 2,3,2
    2,1,2

其实5个回文子序列可以分为以上三类。中间的2\3\……的数量，决定了总的回文数量；且 $f(a) \equiv 3$ 。

## CODE

```c++
#include<bits/stdc++.h>
using namespace std;

void resolution();

int main(){
    ios::sync_with_stdio(0);
    int T;
    cin >> T;
    while(T--){
        resolution();
    }
    return 0;
}

void resolution(){
    int n;
    cin >> n;
    cout << "1 1 ";
    for(int i = 1; i <= n-4; i++){
        cout << i + 1 << " ";
    }
    cout << "1 2\n";
    return ;
}
```


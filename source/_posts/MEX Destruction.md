---
title: MEX Destruction
category:
  - CodeForces
tags:
  - greedy
  - implementation
  - '*800'
date: 2025-01-11
updated: 2025-01-18
mathjax: true
---

[Problem - A - Codeforces](https://codeforces.com/contest/2049/problem/A)

## QUESTION

对于一个给定的序列而言，将其中的连续子序列b用数 mex(b) 来替换

mex(b)：最小的不出现在序列b中的非负整数

问，需要多少次操作才能把当前序列中的数全部变成0

## RESOLUTION

- 如果全部由0构成，则无需操作。

 - 如果全部由正数构成，则操作一次。

 - 如果0与正数在序列中是分开的（即，000XXXXX），则操作一次。

 - 如果0会穿插在整数中（即，XX0X00），则操作两次。

也可以通过找连续正数块的数量来判定：

 - 没有正数块：0

 - 1个正数块：1

  - 多于1个：2

## CODE

```c++
#include<iostream>
using namespace std;

void resolution(){
    int n, x, t = 0;
    cin >> n;
    bool flag = 0;
    cin >> x;
    if(x){
        flag = 1;
        t++;
    }
    for(int i = 2; i <= n; i++){ // 寻找连续的正数子序列数量
        cin >> x;
        if(flag && !x){
            t++;
            flag = 0;
        }
        if(!flag && x){
            t++;
            flag = 1;
        }
        if(i == n  && x)    t++;
    }
    t /= 2;
    if(!flag && t == 0) cout << 0 << endl;
    else if(t >= 2) cout << 2 << endl;
    else    cout << 1 << endl;
    return ;
}

int main(){
    ios::sync_with_stdio(0);
    int T;
    cin >> T;
    while(T--){
        resolution();
    }
    return 0;
}
```
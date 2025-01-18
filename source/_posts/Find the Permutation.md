---
title: Find the Permutation
category:
  - CodeForces
tags:
  - brute force
  - implementation
  - sortings
date: 2025-01-17
updated: 2025-01-18
mathjax: true
---

[Problem - B - Codeforces](https://codeforces.com/contest/2056/problem/B)

## SOLUTION

其实直接用`sort`进行排序，

考虑两个元素 $x<y$ 。假设它们在 $p$ 中的位置分别是 $i$ 和 $j$ 。

如果 $g_{x,y}=1$，我们知道 $i<j$，否则 $i>j$ 。

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

string g[1001];

bool cmp(int u, int v) {
    if(u < v){
        return g[u][v] == '1';
    }
    return g[v][u] == '0';
}

void resolution(){
    int n;
    cin >> n;
    for (int i = 0; i < n; i++){
        cin >> g[i];
    }
    int perm[1001];
    for (int i = 0; i < n; ++i){ //初始化
        perm[i] = i;
    }
    // 由于输入的字符串从下标0开始，所以对0~n-1进行排序
    sort(perm, perm + n, cmp);
    for (int i = 0; i < n; ++i){
        cout << perm[i] + 1 << " ";
    }
    cout << endl;
    return ;
}
```


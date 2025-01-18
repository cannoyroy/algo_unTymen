---
title: Shape Perimeter
category:
  - CodeForces
tags:
  - math
  - constructive algorithms
date: 2025-01-17
updated: 2025-01-18
mathjax: true
---

[Problem - A - Codeforces](https://codeforces.com/contest/2056/problem/A)

## SOLUTION

由于只需要计算周长，所以，对于任意一个构建出来的不规则图形，总存在一个长方形与其周长相同。

即构建出的图形周长，等于 $2*(x_{right}-x_{left} + y_{top} - y_{bottom})$ 。

由于题中所给的数据为每次往x\y轴移动的单位，所以：
$$
x_{right}-x_{left}=\sum_{i=2}^{n}{x_i} + m
$$

$$
y_{top}-x_{bottom}=\sum_{i=2}^{n}{y_i} + m
$$

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
    int n, m;
    cin >> n >> m;
	int ans = 2 * m;
	for(int i = 1; i <=n; i++){
	    int x, y;
	    cin >> x >> y;
	    if(i == 1)    continue;
	    ans += x + y;
	}
	cout << ans * 2<< endl;
    return ;
}
```


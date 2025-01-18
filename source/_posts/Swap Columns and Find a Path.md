---
title: Swap Columns and Find a Path
category:
  - CodeForces
tags:
  - greedy
  - sortings
  - '*1200'
date: 2025-01-12
updated: 2025-01-18
mathjax: true
---

### 题意

给定一个由2行n列组成的矩阵，矩阵的行从上到下编号为1到2，列从左到右编号为1到n。矩阵中的每个单元格 (i, j) 包含一个整数，初始时单元格 (i, j) 中的整数为 $a_{i,j}$ 。

可以进行任意次数的列交换操作（包括0次）：选择两列x和y（1 ≤ x < y ≤ n），然后交换第一行的 $a_{1,x}$ 与 $a_{1,y}$ ，以及第二行的 $a_{2,x}$ 与 $a_{2,y}$ 。

操作完成后，需要从单元格(1, 1)选择一条路径到单元格(2, n)。路径上的每个单元格(i, j)（除了最后一个）的下一个单元格可以是(i + 1, j)或(i, j + 1)。路径不能超出矩阵边界。

路径的成本是路径上所有(n + 1)个单元格中的整数之和。目标是通过执行操作和选择路径，使得路径的成本尽可能大。



### 题解

在所有n*2个格子中，需要绕开 $n-1$ 个格子，使用贪心，肯定是绕开数值最小的格子。

又因为不可能同时绕开处在一列的两个格子，故此处需要维护。


### CODE

```c++
#include<iostream>
#include<algorithm>
using namespace std;
const int N = 5000 + 10;

struct Cell{
    int value, column;
}a[N * 2];

bool cmp(Cell a, Cell b){
    return a.value < b.value;
}
void resolution(){
    int n, sum = 0;
    bool flg[N];
    cin >> n;
    for(int i = 1; i <= n * 2; i++){
        cin >> a[i].value;
        a[i].column = (i % n != 0 ? i%n : n);
        sum += a[i].value;
        flg[a[i].column] = 1;
    }
    sort(a + 1, a + n*2 + 1, cmp);
    int cnt = n - 1, t = 1;
    while(cnt){
        if(flg[a[t].column]){
            flg[a[t].column] = 0;
            sum -= a[t].value;
            t++;
            cnt--;
            // cout << a[t].value << " ";
        }else{
            t++;
        }
    }
    cout << sum << endl;
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
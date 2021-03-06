---
title:  ZJUTOJ-1347-最大公约数
tags:
- ZJUTOJ
- 算法
date:   2020-03-08 20:00:00
categories: 数据结构与算法
---

根据读入的两个正整数，计算他们的最大公约数，数据有多组。

## Input:

第一行是一个正整数 `n` (1<=n<=50),接下来n行每行包括两个正整数 `a` 和 `b` (1<=a,b<=10000);

## Output:

每行输出形式为 `Case t: x` ，其中 `t` 从 `1` 到 `n` ，`x` 为运算答案，共 `n` 行。

## Sample Input:

```
5
20 494
2172 5298
3789 54
3065 7899
3294 5967
```

## Sample Output:

```
Case 1: 2
Case 2: 6
Case 3: 9
Case 4: 1
Case 5: 27
```

## Solve:

```c++
#include <iostream>
using namespace std;
int main() {
    int n;
    while(cin >> n) {
        int matrix[n][2];
        int res[n];
        for(int i = 0; i < n; i++) {
            int min = 0;
            cin >> matrix[i][0] >> matrix[i][1];
            int a = matrix[i][0];
            int b = matrix[i][1];
            if(a < b) {
                min = a;
            } else {
                min = b;
            }
            for(int k = 1; k < min; k++) { // 枚举法
                int ret;
                if(a % k == 0) {
                    if(b % k == 0) {
                        ret = k;
                    }
                }
                res[i] = ret;
            }
        }
        for(int j = 0; j <  n; j++) {
            cout << "Case " << j+1 << ": " << res[j] << endl;
        }
    }
    return 0;
}

/*
// 辗转相除法
while( b!=0 ) {
        t = a%b;
        a = b;
        b = t;
    }
    printf("gcd=%d\n", a);
*/
```

<div align="center">
    <hr style="height:1px;"/>
    <br>
    <img width="200px" src="https://runcoderhang.github.io/thumbnails/wxgzh-hang.png">
</div>
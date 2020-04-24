# 階乗計算の再帰解

Created: Apr 24, 2020 4:23 PM
Property: ape iria
Property 2: No
Tags: recursive

```c
#include <stdio.h>

long kaijo(int);
void main() {
    int n;
    for (n = 0; n < 13; ++n) {
        printf("%2d!=%10ld\n", n, kaijo(n));
    }
}
    long kaijo(int n){
        if(n==0)
            return 1L;
        else
            return n*kaijo(n-1);
}
```

実行結果

```c
0!= 1
1!= 1
2!= 2
3!= 6
4!= 24
5!= 120
6!= 720
7!= 5040
8!= 40320
9!= 362880
10!= 3628800
11!= 39916800
12!= 479001600
```
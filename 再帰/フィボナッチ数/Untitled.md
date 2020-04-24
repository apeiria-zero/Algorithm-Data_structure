# フィボナッチ数

Created: Apr 24, 2020 4:32 PM
Property: ape iria
Property 2: No
Tags: recursive

```c
#include <stdio.h>

long fib(long);

void main(){
    long n;
    for (n = 1;  n<=20 ; n++)
        printf("%3ld: %ld\n",n,fib(n));
}
long fib(long n){
    if(n==1 || n==2)
        return 1L;
    else
        return fib(n-1)+fib(n-2);
}
```

```c
1: 1
2: 1
3: 2
4: 3
5: 5
6: 8
7: 13
8: 21
9: 34
10: 55
11: 89
12: 144
13: 233
14: 377
15: 610
16: 987
17: 1597
18: 2584
19: 4181
20: 6765
```
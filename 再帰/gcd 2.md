# gcd(2)練習問題有

Created: Apr 24, 2020 4:46 PM
Property: ape iria
Property 2: No
Tags: recursive

```c
#include <stdio.h>

int gcd(int,int);

void main(){
    int a,b;

    printf("data-->");
    scanf("%d %d",&a,&b);

    printf("gcd = %d\n",gcd(a,b));
}
int gcd(int m,int n){
    if(n==0)
     return m;
    else
        return gcd(n,m%n);
}
```

```c
data-->128 72
gcd = 8
```

練習問題

[C - Sum of gcd of Tuples (Easy)](https://atcoder.jp/contests/abc162/tasks/abc162_c)
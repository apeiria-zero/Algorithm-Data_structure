# 素数判定

Created: Apr 30, 2020 10:16 PM
Property: ape iria
Property 2: No
Tags: 競プロライブラリ

ｎがｎ以下の整数で割り切れるか否かを２まで繰り返し、割り切れるものがあった場合は、素数でないとしてループから抜ける。

調べる開始の値はｎではなく√ｎからでよいことが数学的に分かっている。

```c
#include<stdio.h>
#include <math.h>

void main(void) {
    int i, n, Limit;
    while (printf("data->"), scanf("%d", &n) != EOF) {
        if (n >= 2) {
            Limit = (int)sqrt((double)n);　//キャスト
            for (i = Limit; 1 <i ; i--){

                if (n % i == 0)
                    break;
            }
            if (i == 1)
                printf("prime number\n");
            else
                printf("not prime number\n");
        }
    }
}
```

２－Nまでのすべての素数

```c
#include<stdio.h>
#include <math.h>

#define NUM 1000

void main(void) {
    int prime[NUM / 2];
    int i, n,m=0, Limit;

    for (n=2; n <= NUM; n++)
    {
        Limit = (int)sqrt((double)n);
        for ( i = Limit; i > 1; i--)
        {
            if (n % i == 0)
                break;
        }
        if (i == 1)
            prime[m++] = n;
    }
    printf("\nprime number\n");
    for ( i = 0; i < m; i++)
    {
        printf("%5d", prime[i]);
    }
    printf("\n");
}
```

練習問題

[https://atcoder.jp/contests/abc149/tasks/abc149_c](https://atcoder.jp/contests/abc149/tasks/abc149_c)
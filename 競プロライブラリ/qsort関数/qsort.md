# qsort関数

Created: May 01, 2020 3:48 PM
Property: ape iria
Property 2: No
Tags: 競プロライブラリ

[C言語関数辞典](http://www.c-tipsref.com/reference/stdlib/qsort.html)

```c
#include <stdio.h>
#include <stdlib.h>

int comp(const void *a, const void *b){
    return *(int*)a-*(int*)b;
}

int main(void)
{
    int i, n, a[200001];
    scanf("%d", &n);

    for( i = 0; i < n; i++ ){
        scanf("%d", &a[i]);
    }

    qsort(a, n, sizeof(int), comp);

    for( i = 0; i < n-1; i++ ){
        if( a[i] == a[i+1] ){
            printf("NO\n");
            return 0;
        }
    }
    printf("YES\n");
    return 0;
}

```
# distributio_counting_sort(分布数え上げソート)

Date Created: Aug 16, 2020 12:45 PM
Status: sort

```c
#include <stdio.h>
#include <stdlib.h>
typedef struct {
    int key; 
    int other; 
}DATA;

#define M 100 //keyの上限

int count[M+1];

void dist_count_sort(DATA a[],DATA b[],int n){
    int i;

    for (i = 0;  i<=M ; ++i) {
        count[i]=0;
    }
    for (i = 0;  i<n ; ++i) {
        count[a[i].key]++;
    }
    for (i = 0;  i<M ; ++i) {
        count[i+1] += count[i];
    }
    for (i = n-1;  i>=0 ; i--) {
        b[--count[a[i].key]]=a[i];
    }
}

void main(void){
    DATA b[M];
    DATA a[7]=
            {
                    {7,NULL},
                    {1,NULL},
                    {4,NULL},
                    {2,NULL},
                    {7,NULL},
                    {8,NULL},
                    {2,NULL},
            };
    dist_count_sort(a,b,7);

    for (int i = 0; i <7 ; ++i) {
        printf("%d ",b[i].key);
    }
}
```
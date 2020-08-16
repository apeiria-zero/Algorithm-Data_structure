# bin_sort

Date Created: Aug 16, 2020 12:05 PM
Status: sort

```c
#include <stdio.h>
#include <stdlib.h>
typedef struct {
    int key;
    int other;
}DATA;

#define M 100

DATA bin[M+1];

void bin_sort(DATA a[],int n){
    int i,j;
    for (i = 0;  i<=M ; ++i) {
        bin[i].key=-1;
    }
    for (i = 0;  i<n ; ++i) {
        bin[a[i].key]=a[i];
    }
    j=0;
    for (i = 0;  i<=M ; ++i) {
        if(bin[i].key!=-1)
            a[j++]=bin[i];
    }
}

void main(void){
    DATA a[3]=
            {
                    {4,NULL},
                    {3,NULL},
                    {1,NULL},
            };
    bin_sort(a,3);
    for (int i = 0; i <3 ; ++i) {
        printf("%d ",a[i].key);
    }
}
```
# quicksort

Date Created: Jul 11, 2020 12:06 AM
Status: Algorithm

```c
#include <stdio.h>

void quick(int *,int,int);

#define N 10

void main(void){
    static int a[]={41,24,76,11,45,64,21,69,19,36};
    int k;

    quick(a,0,N-1);

    for (k = 0;  k<N ; k++)
        printf("%4d",a[k]);
    printf("\n");
}
void quick(int a[],int left,int right){
    int s,t,i,j; //sが軸を表す

    if(left<right){
        s=a[left]; //一番最左の項を軸に設定(最初はa[0]=41が軸)
        i=left;j=right+1;
        while(1){
            while(a[++i]<s); //軸より大きい(a[i]がsより大きくなるまで繰り返す.a[++i]なので、iをインクリメントしてから比較する)
            while(a[--j]>s); //軸より小さい(a[j]がsより小さくなるまで繰り返す)
            if(i>=j) break; //i=jとなったらループ抜ける.
            t=a[i];a[i]=a[j];a[j]=t; //入れ替え
        }
        a[left]=a[j];a[j]=s; //軸を正しい位置に入れる. 軸(a[left])とa[j]を入れ替える.a[j]の位置を軸とする.

        quick(a,left,j-1); //左部分列
        quick(a,j+1,right); //右部分列
    }
}
```
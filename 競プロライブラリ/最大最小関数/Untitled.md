# 最大最小関数

Created: Apr 30, 2020 1:08 PM
Property: ape iria
Property 2: No
Tags: 競プロライブラリ

[C - Rally](https://atcoder.jp/contests/abc156/tasks/abc156_c)

```c
#include <stdio.h>

int min(int x,int y);
int max(int x,int y);
const int inf =100000000;

int main(){
    int n;
    scanf("%d",&n);
    int x[n];
    for (int i = 0; i <n ; ++i) {
        scanf("%d",&x[i]);
    }
   int L=x[0];int R=x[0];
    for (int i = 0; i <n ; ++i) {
        L=min(L,x[i]);
        R=max(R,x[i]);
    }
    int ans=inf;
    for (int i = L; i <=R ; ++i) {
        int cost=0;
        for (int j = 0; j <n ; ++j)
            cost+=(x[j]-i)*(x[j]-i);
            ans=min(ans,cost);
        }
    printf("%d",ans);
    return 0;
}

int min(int x,int y){
    if(x<y)
        return x;
    else
        return y;
}
int max(int x,int y){
    if(x>y)
        return x;
    else
        return y;
}
```
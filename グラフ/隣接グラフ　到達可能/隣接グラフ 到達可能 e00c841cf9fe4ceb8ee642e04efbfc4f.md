# 隣接グラフ　到達可能

Date Created: Aug 26, 2020 1:05 PM
Status: Data structure

```c
#include <stdio.h>

#define N 8 //点の数

int a[N+1][N+1]={{0,0,0,0,0,0,0,0,0},
                 {0,0,1,0,0,0,0,0,0},
                 {0,1,0,1,1,1,0,0,0},
                 {0,0,1,0,0,0,0,1,0},
                 {0,0,1,0,0,0,0,0,0},
                 {0,0,1,0,0,0,1,0,0},
                 {0,0,0,0,0,1,0,1,1},
                 {0,0,0,1,0,0,1,0,1},
                 {0,0,0,0,0,0,1,1,0}};
int v[N+1];

int queue[100];
int head=0,tail=0;
int is_reachble1(int,int);
int is_reachble(int,int);

void main(){
    if(is_reachble(1,2))
        printf("success");
    else
        printf("error");
}

int is_reachble1(int s,int g){
    int i;
    if(s==g)
        return 1;
    if(v[s])
        return 0;
    v[s]=1;
    for (i = 1; i <=N ; ++i){
            if (a[s][i] && is_reachble1(i,g)) return 1;
    }
    return 0;
}

int is_reachble(int s,int g){
    int i;
    for (i = 1;  i<=N ; i++)
        v[i]=0;
    return is_reachble1(s,g);
}
```
# モンテカルロ法を用いた楕円面積計算

Created: May 01, 2020 11:20 PM
Property: ape iria
Property 2: No
Tags: 数値計算

```c
#include <stdio.h>
#include <stdlib.h>

#define NUM 1000

double rnd(void);

void main(){
    double x,y,s;
    int i,in=0;
    for (i = 0; i <NUM ; ++i) {
        x=2*rnd();
        y=rnd();
        if(x*x/4+y*y<=1)
            in++;
    }
    s=4.0*(2.0*in/NUM);
    printf("area of an ellipse=%f\n",s);
}
double rnd(void){
    return (double)rand()/(RAND_MAX+0.1);
}
```

実行結果

```c
area of an ellipse=6.224000
```
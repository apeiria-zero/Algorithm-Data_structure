# gcd(1)

Created: Apr 24, 2020 4:43 PM
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
    if(m==n)
        return m;
    if(m>n)
        return gcd(m-n,n);
    if(m<n)
        return gcd(m,n-m);
}
```

```c
data-->128 72
gcd = 8
```
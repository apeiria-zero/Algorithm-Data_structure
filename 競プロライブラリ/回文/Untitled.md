# 回文

Created: May 01, 2020 9:13 PM
Property: ape iria
Property 2: No
Tags: 競プロライブラリ

```c
#include<stdio.h>
#include<string.h>

int main(void)
{
    char s[100];
    scanf("%s",s);
    int n = strlen(s);
    for(int i=0;i<n/2;i++){
        if(s[i]!=s[n/2+i+1]){
            printf("No\n");
            return 0;
        }
        else if(s[i]!=s[n-i-1]){
            printf("No\n");
            return 0;
        }
    }
    printf("Yes\n");
    return 0;
}
```
# 二分探索木

Created: Apr 17, 2020 5:33 PM
Property: ape iria
Property 2: No
Tags: tree

a[p].leftは左の子へのポインタ。a[p].rightは右の子へのポインタ。

このポインタの値は配列の要素番号を用いる。

nilはポインタが指し示すものが無いという意味で、具体的にはー１などの値を用いる。

keyがノードのデータより小さければ左の木へ、大きければ右側の木へと探索を進める。

ポインタがnilになても見つからなければデータは無いということになる。

    #include <stdio.h>
    #include <string.h>
    
    #define nil -1
    #define MaxSize 100
    
    struct tnode{
        int left;
        char name[20];
        int right;
    };
    void main(){
        struct tnode a[MaxSize]={{1,"Machilda",2},
                                 {3,"Candy",4},
                                 {5,"Rolla",nil},
                                 {nil,"Ann",nil},
                                 {6,"Emy",7},
                                 {nil,"Nancy",nil},
                                 {nil,"Eluza",nil},
                                 {nil,"Lisa",nil}};
        char key[12];
        int p;
    
        printf("Search name-->"); scanf("%s",key);
        p=0;
        while(p!=nil){
            if(strcmp(key,a[p].name)==0){
                printf("found\n");
                break;
            }
            else if (strcmp(key,a[p].name)<0)
                p=a[p].left;
            else
                p=a[p].right;
        }
    }

実行結果

    Search name-->Emy
    found

    Search name-->Apeiria
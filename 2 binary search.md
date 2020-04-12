# 2分探索(binary search)

Created: Apr 10, 2020 2:20 PM
Property: ape iria
Tags: sort

二分探索は、データが*ソートされて小さい順（または大きい順）に並んでいるときに有効*な探索法

探索範囲の下限を low ,上限をupperとしx=(low+upper)/2 の位置のデータとkey（探すデータ）

を比較する。

もしkeyのほうが大きければ、キーの位置はxより上にあるはずなので、lowをx+1にする。

逆に、keyのほうが大きければ、keyの位置はxより下にあるはずなので、upperを-1にする。

これをlow≤upperの間繰り返す。

つまり、２部探索では、探索するデータ範囲を半分に分け、keyがどちらの半分にあるかを調べることを繰り返し、調べる範囲をkeyに向かって絞っていく。

もし、keyが見つからなければ、lowとhighが逆転してlow>highになったときに終了する。

たとえば、次のようなデータからデータの50を２分探索する場合を考えてみる。


    #include <stdio.h>
    
    #define N 10
    
    void main(void){
        int a[]={2,3,7,11,31,50,55,70,77,80};
        int key,low,high,mid,flag=0;
    
        printf("search data >");scanf("%d",&key);
        low=0;high=N-1;
        while(low<=high){
            mid=(low+high)/2;
            if(a[mid]==key){
                printf("%d is at %d",a[mid],mid);
                flag=1;
                break;
            }
            if(a[mid]<key)
                low=mid+1;
            else
                high=mid-1;
        }
        if(flag!=1)
            printf("NOT FOUND");
    }

実行結果

    search data >70
    70 is at 7

    search data >1
    NOT FOUND

**※参考 break文を使わずに書く場合**

Pascalなどではbreakなどで強制脱出ができない。そこでbreakを使わない書き方を示す。

keyが見つかったときに、low=mid+1 と low=mid-1 の２つを行うことにすると

low-high =(mid+1)-(mid-1)=2　∴low=high+2となり、low≤highという条件を満たさなくなるから

探索ループから抜け出すことができる。

ループを終了したときにlow=high+2ならデータが見つかったときで、mid位置にデータあること

になる。low=high+1ならデータが見つからなかったことを示す。

    #include <stdio.h>
    
    #define N 10
    
    void main(void){
        int a[]={2,3,7,11,31,50,55,70,77,80};
        int key,low,high,mid;
    
        printf("search data >");scanf("%d",&key);
        low=0;high=N-1;      //high=Nとしないように注意（添字は0から始まるため）
        while(low<=high){
            mid=(low+high)/2;
            if(a[mid]<=key)
                low=mid+1;
            if(a[mid]>=key)
                high=mid-1;
        }
        if(low==high+2)
            printf("%d is at %d. \n",a[mid],mid);
        else
            printf("NOT FOUND");
    }

実行結果

    search data >55
    55 is at 6.

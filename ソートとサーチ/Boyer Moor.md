# Boyer-Moor法

Created: Apr 13, 2020 12:20 PM
Property: ape iria
Tags: Algorithm

Boyer-Moor法は、テキスト中の文字列とkey文字列との照合を右端を基準にして行い、一致しなかった場合次の照合位置をテキスト中の照合文字の右端文字で決まるある値分だけ先に進めるもの。

パターンを末尾から先頭に向かって逆向きにチェックします。

不一致になった文字によって、パターンを何文字ずらすかという情報は、探索処理に入る前に、前処理によってテーブルに格納します。この表は、不一致になった文字の文字コードを添え字としてパターンをずらす量を入れた配列skipとして実現します。1バイトの文字は0~255までの値をとるので、配列の大きさは256としておきます。

最悪の計算量はO(n)ですが、O(n/m)となるときもあります。

力まかせ方やKMP法よりも高速なアルゴリズムです。

    #include <stdio.h>
    #include <string.h>
    
    char *search(char *,char *);
    void table(char *);
    
    int skip[256];
    
    int main(void){
        static char text[]="This is a pen. That is a pencil.";
        char *p,*key="pen";
    
        table(key);
        p=search(text,key);
        while(p!=NULL){
            printf("%s\n",p);
            p=search(p+strlen(key),key);
        }
    }
    void table(char *key){
        int n;
        n=strlen(key);
        for (int k = 0; k <=255 ; ++k)　//配列skipの内容を計算
            skip[k]=n;
        for (int k = 0; k <n-1 ; ++k)
            skip[key[k]]=n-1-k;   //key[k]は文字コード
    }
    char *search(char *text,char *key){
        int m,n;
        char *p;
    
        m=strlen(text);
        n=strlen(key);
    
    	  p=text+n-1;　//注目点
        while(p<text+m){
            if(*p==key[n-1]){
                if(strncmp(p-n+1,key,n)==0)
                    return p-n+1;　//一致した点のポインタを返す
            }
            p=p+skip[*p]; //配列skipに基づいてポインタを進める
        }
        return NULL;
    }

実行結果

    pen. That is a pencil.
    pencil.
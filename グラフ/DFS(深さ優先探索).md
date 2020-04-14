# DFS(深さ優先探索)

Created: Apr 13, 2020 4:12 PM
Property: ape iria
Tags: graph

・始点を出発し、番号の若い順に進む位置を調べ、いけるところまで進む

・行き場所がなくなったら、行き場所があるところまで戻り、再び行けるところまで進む

・行き場所がすべてなくなったら終わり（来た道を戻る）

プログラムにおいてi点からj点まで進めるかは、隣接行列a[i][j]が１でかつ訪問フラグv[j]が0のときである。訪問フラグはi点への訪問が行われればv[j]=1とする。

    #include <stdio.h>
    
    #define N 8　　　　　　　　　　//点の数
    
    int a[N+1][N+1]={{0,0,0,0,0,0,0,0,0},   //隣接行列
                     {0,0,1,0,0,0,0,0,0},
                     {0,1,0,1,1,0,0,0,0},
                     {0,0,1,0,0,0,0,1,0},
                     {0,0,1,0,0,1,0,0,0},
                     {0,0,0,0,1,0,1,0,0},
                     {0,0,0,0,0,1,0,1,1},
                     {0,0,0,1,0,0,1,0,1},
                     {0,0,0,0,0,0,1,1,0}};
    int v[N+1];                          //訪問フラグ
    
    void visit(int);
    
    void main(){
        for (int i = 1; i <=N ; ++i)
            v[i]=0;
        visit(1); //始点を１とする
    		printf("\n");
    }
    void visit(int i){
        v[i]=1;       
        for (int j = 1; j <=N ; ++j) {
            if(a[i][j]==1 && v[j]==0){
                printf("%d->%d ",i,j);
                visit(j);
            }
        }
    

実行結果

    1->2 2->3 3->7 7->6 6->5 5->4 6->8

例題

[A - 深さ優先探索](https://atcoder.jp/contests/atc001/tasks/dfs_a)

再帰関数による解答例

    #include <stdio.h>
    
    //trueを1 falseを0に
    int Y, X;
    int reached[501][501];
    char meiro[501][501];
    
    void search(int x, int y) {
        if (x < 0 || x >= X || y < 0 || y >= Y || meiro[x][y] == '#') return;
        if (reached[x][y] != 0) return;
        reached[x][y] = 1;
        search(x + 1, y);
        search(x - 1, y);
        search(x, y + 1);
        search(x, y - 1);
    }
    
    int main() {
        int sx = 0, sy = 0, gx = 0, gy = 0;
        scanf("%d%d\n", &Y, &X);
        for (int i = 0; i < Y; i++) {
            for (int j = 0; j < X; j++) {
                if (j == X - 1 && i != Y - 1) {
                    scanf("%c\n", &meiro[j][i]); //端だから区切る必要あり
                    if (meiro[j][i] == 's')sx = j, sy = i;
                    if (meiro[j][i] == 'g')gx = j, gy = i;
                }
                else {
                    scanf("%c", &meiro[j][i]);
                    if (meiro[j][i] == 's')sx = j, sy = i;
                    if (meiro[j][i] == 'g')gx = j, gy = i;
                }
            }
        }
        for (int i = 0; i < Y; i++) for (int j = 0; j < X; j++) reached[j][i] = 0; //reached[j][i]を初期化
        search(sx, sy);
        if (reached[gx][gy] == 1) printf("Yes");
        else printf("No");
        return 0;
    }

実行例

    4 5
    s####
    ....#
    #...g
    Yes
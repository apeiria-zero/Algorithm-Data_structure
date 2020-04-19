# 二分探索木のトラバーサル(再帰)

Created: Apr 19, 2020 1:44 PM
Property: ape iria
Property 2: No
Tags: tree

一定の手順で、気のすべてのノードを訪れることを木の走査（トラバーサル）といいます。

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct tnode {
        struct tnode* left;
        char name[20];
        struct tnode* right;
    };
    
    struct tnode* talloc(void);
    struct tnode* gentree(struct tnode*, char*);
    void treewalk(struct tnode*);
    
    void main() {
        char dat[12];
        struct tnode* root;
    
        root = NULL;
        while (scanf("%s", dat) != EOF) {
            root = gentree(root, dat);
        }
        treewalk(root);
    }
    void treewalk(struct tnode* p) { //木のトラバーサル
        if (p != NULL) {
            treewalk(p->left);
            printf("%s\n", p->name);
            treewalk(p->right);
        }
    }
    struct tnode* gentree(struct tnode* p, char* w) { //木の作成の再帰手続き
        if (p == NULL) {
            p = talloc();
            strcpy(p->name, w);
            p->left = p->right = NULL;
        }
        else if (strcmp(w, p->name) < 0) //辞書順で w の方が小さければ（前に来れば） 0 より小さい値が、w の方が大きければ（後に来れば） 0 より大きい値が、w と p->name が同じであれば 0 が返される。
            p->left = gentree(p->left, w);
        else
            p->right = gentree(p->right, w);
        return p;
    }
    struct tnode* talloc(void) {
        return (struct tnode*)malloc(sizeof(struct tnode));
    }
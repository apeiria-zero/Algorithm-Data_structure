# 自己再編成探索(一つ前に移す)

Date Created: Aug 22, 2020 11:19 PM
Status: Data structure

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct tfield {
    char name[20];
    char tel[20];
    struct tfield* pointer;
}*head;

struct tfield* talloc(void);
void displist(void);

void main() {
    char key[20];
    struct tfield* p, * old1, * old2, * q;

    head = NULL;
    while (p = talloc(), scanf("%s %s", p->name, p->tel) != EOF) {
        p->pointer = head;
        head = p;
    }
    p = talloc();
    p->pointer = head;
    head = p;

    while (printf("\nKey Name-->\n"), scanf("%s", key) != EOF) {
        p = head->pointer;
        old1 = old2 = head;
        while (p != NULL) {
            if (strcmp(p->name, key) == 0) {
                printf("%15s%15s\n", p->name, p->tel);
                if (p != head->pointer) {
                    q = old1->pointer;
                    old1->pointer = p;
                    old2->pointer = p->pointer;
                    p->pointer = q;
                }
                break;
            }
            old1 = old2;
            old2 = p;
            p = p->pointer;
        }
    }
    displist();
}

void displist(void) {
    struct tfield* p;
    p = head->pointer;
    while (p != NULL) {
        printf("%15s%15s\n", p->name, p->tel);
        p = p->pointer;
    }
}

struct tfield* talloc(void) {
    return (struct tfield*)malloc(sizeof(struct tfield));
}
```
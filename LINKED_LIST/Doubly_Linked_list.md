# DOUBLY LINKED LIST

## Structure 
```cpp
struct Node{
    int data;
    struct Node *next;
    struct Node *prev;
};
struct Node *head;
```

## create a Doubly Node
```cpp
Node* createNode(int value) {
    Node *newNode = (Node *)malloc(sizeof(Node));
    newNode->data = value;
    newNode->next = NULL;
    newNode->prev = NULL;
    return newNode;
}
```



## Implementation of DLL
```cpp
#include <stdio.h>
#include <stdlib.h>

typedef struct Node{
    int data;
    struct Node *next;
    struct Node *prev;
}Node;
Node *head=NULL;
Node *temp=NULL;
void create(){
    int choice=1;
    while(choice){
        Node *newNode=(Node *)malloc(sizeof(Node));
        printf("\nEnter Data: ");
        scanf("%d",&newNode->data);
        newNode->prev=NULL;
        newNode->next=NULL;
        if(head==NULL){
            head=temp=newNode;
        }else{
            temp->next=newNode;
            newNode->prev=temp;
            temp=newNode;
        }
        printf("\nDo you want to insert Node(0 for No/1 for yes): ");
        scanf("%d",&choice);
    }
}
void printList(){
    temp=head;
    while(temp != NULL){
        printf("%d->",temp->data);
        temp=temp->next;
    }
    printf("NULL");
}

int main(){
    create();
    printList();
    return 0;
}
```
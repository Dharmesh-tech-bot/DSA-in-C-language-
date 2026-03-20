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
Node *head,*temp;
void create(){
    head=temp=NULL;
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

## OPERATIONS on DLL

| Operation                     | Description                                                                 | Time Complexity |
|------------------------------|-----------------------------------------------------------------------------|-----------------|
| Traversal (Forward)          | Visit nodes from head to last using `next` pointer                          | O(n)            |
| Traversal (Backward)         | Visit nodes from last to head using `prev` pointer                          | O(n)            |
| Insertion at Beginning       | Add a new node before the head and update pointers                          | O(1)            |
| Insertion at End             | Add node at the last position (requires traversal if no tail pointer)       | O(n)            |
| Insertion at End (with tail) | Insert node directly using tail pointer                                     | O(1)            |
| Insertion at Position        | Insert node at a specific index (requires traversal)                        | O(n)            |
| Deletion at Beginning        | Remove the head node and update the new head                                | O(1)            |
| Deletion at End              | Remove last node (requires traversal if no tail pointer)                    | O(n)            |
| Deletion at End (with tail)  | Remove last node directly using tail pointer                                | O(1)            |
| Deletion at Position         | Delete node at a given position                                             | O(n)            |
| Search                       | Find a node with a given value                                              | O(n)            |
| Update                       | Modify the value of a node after locating it                                | O(n)            |



### INSERTION OPERATION 

```cpp
#include <stdio.h>
#include <stdlib.h>

typedef struct Node{
    int data;
    struct Node *next;
    struct Node *prev;
}Node;

Node *head,*tail,*newNode; //global declaration 

Node *createNode(int value){
    newNode=(Node *)malloc(sizeof(Node));
    newNode->data=value;
    newNode->prev=NULL;
    newNode->next=NULL;
    return newNode;
}

void insertAtEnd(int value){  //no asterisk due to no return type 
    newNode=createNode(value);
    if(head==NULL){
        head=tail=newNode;
        return;
    }
    //Transversing not required 
    tail->next=newNode;
    newNode->prev=tail;
    tail=newNode;
}

void printList(){
    Node *temp=head;
    while(temp != NULL){
        printf("%d->",temp->data);
        temp=temp->next;
    }
    printf("NULL");
}

int main(){
    head=tail=newNode=NULL;
    insertAtEnd(10);
    insertAtEnd(20);
    insertAtEnd(30);
    printList();
    return 0;
}
```






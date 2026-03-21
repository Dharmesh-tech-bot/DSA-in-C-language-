# SINGLY LINKED LIST

A Singly Linked List is a linear data structure where each element (node) contains two parts:

 **Data** – the value stored

 **Next pointer** – the address of the next node in the list.

*Unlike arrays, elements are not stored in continuous memory locations.*

## Real-life Example

Think of a treasure hunt game 🗺️.

Each clue paper contains:

•Some information (data)

•The location of the next clue (pointer).

```
Head
 ↓
[Clue1 | • ] → [Clue2 | • ] → [Clue3 | • ] → [Clue4 | NULL]

```
You start from the first clue (Head).

•Each clue tells you where the next clue is.

•The last clue points to NULL, meaning the game ends.


This is exactly how a singly linked list works.

## Defining a Node

```cpp
struct Node{
    int data;
    struct Node* next;
};
```
### using alias name
```cpp
typedef struct Node{
    int data;
    struct Node *next;
}Node;
```
## Creating a Node

```cpp
struct Node* createNode(int value)
{
//remember to allocate memory 
    struct Node *temp=(struct Node*)malloc(sizeof(struct Node));
    temp->data=value;
    temp->next=NULL;
    return temp;
}
```
# INSERTION operation 
## Inserting newNode at last of the Linkedlist's Node 
### Using Return Head pointer
```cpp
Node* insertNodeAtEnd(int value, Node *head){
    Node *newNode = createNode(value);
    
    if(head == NULL)
        return newNode;

    Node *temp = head;
    while(temp->next != NULL){
        temp = temp->next;
    }

    temp->next = newNode;
    return head;
}

/* 
int main(){
    Node *head = NULL;
    head = insertNodeAtEnd(10, head);
    head = insertNodeAtEnd(20, head);
    head = insertNodeAtEnd(30, head);
    printList(head);
    return 0;
}
*/
```
### Using Pointer to Pointer 
```cpp
void insertNodeAtEnd(int value, Node **head){
    Node *newNode = createNode(value);

    if(*head == NULL){
        *head = newNode;
        return;
    }

    Node *temp = *head;

    while(temp->next != NULL){
        temp = temp->next;
    }

    temp->next = newNode;
}

/*
int main(){
    Node *head = NULL;
    insertNodeAtEnd(10, &head);
    insertNodeAtEnd(20, &head);
    insertNodeAtEnd(30, &head);
    printList(head);
    return 0;
}
*/
```
### Using Recursion 
```cpp
Node* insertNodeAtEnd(Node *head, int value){
    
    if(head == NULL){
        return createNode(value);
    }

    head->next = insertNodeAtEnd(head->next, value);
    return head;
}

/*
int main(){
    Node *head = NULL;
    head = insertNodeAtEnd(head, 10);
    head = insertNodeAtEnd(head, 20);
    head = insertNodeAtEnd(head, 30);
    printList(head);
    return 0;
}
*/

/*
void insertNodeAtEnd(Node **head, int value){

    if(*head == NULL){
        *head = createNode(value);
        return;
    }

    insertNodeAtEnd(&((*head)->next), value);
}

int main(){
    Node *head = NULL;
    insertNodeAtEnd(&head, 10);
    insertNodeAtEnd(&head, 20);
    insertNodeAtEnd(&head, 30);
    printList(head);
    return 0;
}
*/
```
## Traversing a list

```cpp
void printList(struct Node *head){
    struct Node *current=head;
    while(current != NULL){
        printf("%d->", current->data);
        current=current->next;
    }
    printf("NULL\n");
}
```

## Finding Length of the list

```cpp
void lengthOfList(struct Node *head){
    int count = 0;
    struct Node *current=head;
    while(current != NULL){
        count++;
        current=current->next;
    }
    printf("\nLength of the Linkedlist is %d.",count);
}
```
#Implementation of SLL by taking User Input
```cpp
#include <stdio.h>
#include <stdlib.h>

struct Node{
    int data;
    struct Node *next;
};
struct Node *head,*tail;

void createSLL(){
    head=tail=NULL;
    int choice=1;
    while(choice){
        struct Node *newNode=(struct Node *)malloc(sizeof(struct Node));
        if(newNode==NULL){
            printf("Memory allocation failed\n");
            exit(1);
        }
        printf("\nEnter data: ");
        scanf("%d",&newNode->data);
        newNode->next=NULL;   //optional
        
        if(head==NULL){
            head=tail=newNode;
        }else{
            tail->next=newNode;
            tail=newNode;
        }
        
        printf("Do you want to add Node(0/1): ");
        scanf("%d",&choice);
        
    }
}

void printList(){
    struct Node *temp=head;
    while(temp != NULL){
        printf("Node Address: %p | Data: %d | Next: %p\n", temp, temp->data, temp->next);
        temp=temp->next;
    }
}

int main(){
    createSLL();
    
    printf("\nLinked List Details:\n");
    printList();

    printf("\nHead Address: %p", head);
    printf("\nTail Address: %p\n", tail);
    printf("%p",tail->next);
    return 0;
}

```

# Implementation of SLL by message passing

```cpp
#include <stdio.h>
#include <stdlib.h>

struct Node{
    int data;
    struct Node* next;
};

struct Node* createNode(int value)
{
    struct Node *temp=(struct Node*)malloc(sizeof(struct Node));
    temp->data=value;
    temp->next=NULL;
    return temp;
}

void printList(struct Node *head){
    struct Node *current=head;
    while(current != NULL){
        printf("%d->", current->data);
        current=current->next;
    }
    printf("NULL\n");
}

void lengthOfList(struct Node *head){
    int count = 0;
    struct Node *current=head;
    while(current != NULL){
        count++;
        current=current->next;
    }
    printf("\nLength of the Linkedlist is %d.",count);
}
int main(){
    struct Node *head=createNode(10);
    struct Node *second=createNode(20);
    struct Node *third=createNode(30);
    
    head->next=second;
    second->next=third;
    
    printList(head);
    lengthOfList(head);
    
    return 0;
}
```

## Reverse the Linked List

There are two ways:

1.save the data into an array and set back that data in list in reverse order

2.Reverse the Node with the help of three pointer: 
***previousNode** , ***currentNode** and ***nextNode**

```cpp
//Reversing the Node
struct Node* reverseList(struct Node *head)
{
    struct Node *prevNode,*currNode,*nextNode;
    
    currNode=head;
    prevNode=nextNode=NULL;
    
    while(currNode != NULL){
        nextNode=currNode->next;
        currNode->next=prevNode;
        prevNode=currNode;
        currNode=nextNode;
    }
    
    return prevNode; //currNode = NULL
}
```

## key Advantage of singly Linked list 

1.Dynamic Size – Can grow or shrink at runtime.

2.Efficient Insertion/Deletion –No shifting of elements like arrays.

3.Non-contiguous Memory – Nodes can be stored anywhere in memory.

4.Better Memory Utilization – Memory is allocated only when needed.

5.Flexible Structure – Easy to rearrange nodes.

## Disadvantage of Singly Linked list

•It is unidirectional means we can only move forward.

•**O(n) Deletions/Insertions**: If we are given a pointer to a specific node to delete (or insert before), we still have to traverse the list from the head to find the previous node. This takes O(n) time.

•**No reverse traversal**: we cannot easily step backward, which makes operations like reversing the list more complex.

## Reason to need doubly Linked list

•It enables bidirectional traversal and to optimize specific insertion and deletion operations.

•**O(1) Deletions/Insertions**: Because each node has a prev pointer, we instantly know the previous node. This drops the time complexity of deleting that node (or inserting before it) from O(n) to O(1).

•**Two-way movement**: we can seamlessly traverse backward, which is ideal for real-world applications like LRU caches, browser histories, or undo/redo functions.




























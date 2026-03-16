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
# Implementation of singly LL

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

## key Advantage of singly Linked list 

1.Dynamic Size – Can grow or shrink at runtime.

2.Efficient Insertion/Deletion –No shifting of elements like arrays.

3.Non-contiguous Memory – Nodes can be stored anywhere in memory.

4.Better Memory Utilization – Memory is allocated only when needed.

5.Flexible Structure – Easy to rearrange nodes.

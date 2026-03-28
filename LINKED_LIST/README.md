# LINKED LIST

A **Linked List** is a linear data structure where elements are stored in nodes and connected using pointers.

### Key Points:
- A linked list is a **linear data structure**.
- It consists of multiple elements called **nodes**.

- Each node has two parts:

  - **Data** – stores the value or information.

  - **Pointer (Address)** – stores the address of the next node.

- Nodes are **not stored in contiguous memory**.

- Nodes are connected through **pointers**.

- The first node is called the **head**.

- The last node points to **NULL**.

### Interview:

“A linked list is a linear data structure made up of nodes, where each node contains data and a pointer to the next node, and nodes are connected using addresses rather than stored contiguously.”

### Representation

---

## Types of Linked List
Linked lists can be classified into different types based on how nodes are connected.

&emsp; 1. &emsp; Singly Linked List

&emsp; 2. &emsp; Doubly Linked List

&emsp; 3. &emsp; Circular Linked List

&emsp; 4. &emsp; Doubly Circular Linked List

### 1. Singly Linked List
- Each node contains **data** and a **pointer to the next node**.
- Traversal is possible in **one direction only**.
- The last node points to **NULL**.

**Representation:**

---

### 2. Doubly Linked List
- Each node contains **data**, a **pointer to the previous node**, and a **pointer to the next node**.
- Traversal is possible in **both directions** (forward and backward).
- Requires extra memory for the previous pointer.

**Representation:**


---

### 3. Circular Linked List
- Similar to a singly linked list, but the **last node points back to the first node**.
- There is **no NULL pointer**.
- Forms a **loop (circle)**.

**Representation:**



---

### 4. Doubly Circular Linked List
- Combination of **doubly** and **circular** linked lists.
- Each node has **previous and next pointers**.
- The **last node points to the first**, and the **first node points to the last**.

**Representation:**


---

### Quick Summary

| Type                     | Direction       | Last Node Points To |
|--------------------------|----------------|---------------------|
| Singly Linked List       | One direction  | NULL                |
| Doubly Linked List       | Two directions | NULL                |
| Circular Linked List     | One direction  | First Node          |
| Doubly Circular List     | Two directions | First Node          |



---
## Structure of Various Linked list

### Structure of Singly LL
```cpp
struct Node{
	int data;
	struct Node *next;
};
```
### Structure of Doubly LL
```cpp
struct Node{
	int data;
	struct Node *next;
	struct Node *prev;
};
```
### Structure of Circular LL
```cpp
struct Node{
	int data;
	struct Node *next;	//last node point to first node
};
```
### Structure of Doubly Circular LL
```cpp
struct Node{
	int data;
	struct Node *next;
	struct Node *prev;	//last node next point to first node prev
};
```

## Implementation 
There are various way to implement linked list like using functions,by passing array as argument,head to head pointer,recursion.

But, here we implement linked list by taking input from user.

### Implementation of SLL

```cpp
#include<stdio.h>
#include<stdlib.h>

struct Node{
	int data;
	struct Node *next;
};
struct Node *head;

void createSLL(){
	head=NULL;
	int choice=1;
	while(choice){
		struct Node *newNode=(struct Node*)malloc(sizeof(struct Node));
		if(newNode==NULL){
			printf("\nMemory Allocation Failed.");
			return;
		}
		printf("\nEnter data: ");
		scanf("%d",&newNode->data);
		newNode->next=NULL;

		if(head=NULL){
			head=NULL;
		}else{
			struct Node *temp=head;
			while(temp != NULL){
				temp=temp->next;
			}
			temp->next=newNode;
			temp=newNode;
		}
		printf("Do you want to add Node(0/1): ");
		scanf("%d",&choice);
	}
}

void display(){
	struct Node *temp=head;
	while(temp != NULL){
		printf("%d",temp->data);
		temp=temp->next;
	}
	printf("NULL");
}
int main(){
	createSLL();
	display();

	return 0;
}
```







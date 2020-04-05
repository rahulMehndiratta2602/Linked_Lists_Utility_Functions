# Linked_Lists_Utility_Functions
//Contains Linked lists utility functions in C language

#include <stdlib.h>
#include <stdio.h>
struct Node
{
	int data;
	struct Node* next;
};struct Node* head;
void Reverse_using_recursion(struct Node* p)
{
	if(p->next==NULL)
	{
		head=p;
		return;
	}
	Reverse_using_recursion(p->next);
	struct Node* q=p->next;
	q->next=p;
	p->next=NULL;
}

void Reverse()
{
	struct Node* current,* prev,* next;
	current=head;
	prev=NULL;
	while(current!=NULL)
	{
		next=current->next;
		current->next=prev;
		prev=current;
		current=next;
	}
	head=prev;
}
void Delete(int n)
{
	int i;
	struct Node* temp2;
	struct Node* temp1=head;

	if(n==1)
	{
	head=temp1->next;
	free(temp1);
	}
	else
	{
	for(i=1;i<=n-2;i++)
	{
	temp1=temp1->next;
	}
	temp2=temp1->next;
	temp1->next=temp1->next->next;
	free(temp2);
	}
}
void Insert(int x,int n)Inserting a node at nth position
{
	int i;
	struct Node* temp=(struct Node*)malloc(sizeof (struct Node));
	struct Node* temp1=head;
	temp->data=x;
	if(n==1)
	{
	temp->next=head;
	head=temp;
	}
	else {
	for(i=1;i<=n-2;i++)
	{
	temp1=temp1->next;
	}
	temp->next=temp1->next;
	temp1->next=temp;}
	return;
}
void Insert_at_head(int x)
{
	struct Node* temp=(struct Node*)malloc(sizeof (struct Node));
	temp->data=x;
	temp->next=head;
	head=temp;


}
void Insert_at_tail(int x)
{
	struct Node* temp=(struct Node*)malloc(sizeof (struct Node));
	struct Node* temp1;
	temp->data=x;
	temp->next=NULL;
	if(head==NULL)
	{
		head=temp;
	}
    else
    {
        temp1=head;
	while(temp1->next!=NULL)
	{
		temp1=temp1->next;
	}
	temp1->next=temp;
	}
	return;
}
void Print()
{
	struct Node* temp=head;
	while(temp!=NULL)
	{
		printf("%d ",temp->data);
		temp=temp->next;
	}
	printf("\n");
	return;
}
 void Print_using_recursion(struct Node* p)
 {
 	if(p==NULL)
 	{
 		printf("\n");
 		return;
 	}
 	printf("%d",p->data);
 	Print_using_recursion(p->next);
 }
void Print_reverse_using_recursion(struct Node* p)
{
	if(p==NULL) return;
	Print_reverse_using_recursion(p->next);
	printf("%d",p->data);
}
int main()
{
	head = NULL;
	int y,i,n,x;
	printf("How many numbers?\n");
	scanf("%d",&n);
	for(i=1;i<=n;i++)
	{
		printf("Enter a number\n");
		scanf("%d",&x);
		Insert_at_tail(x);
	}
	Print_using_recursion(head);
	Print_reverse_using_recursion(head);
	Print();
	Insert(19,1);
	Print();
	Insert(40,2);
	Print();556
	Insert(50,5);
	Print();
	Insert(90,4);
	Print();
	printf("Which node do you want to delete?");
	scanf("%d",&y);
	Delete(y);
	Print();
	printf("The reversed linked list is:\n");
	Reverse();
 	Reverse_using_recursion(head);
 	printf("\n");
	Print_using_recursion(head);
	return 0;
}

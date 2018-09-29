# Linked-list
//*there are program of linked list for insertion,deletion and diaplay.*//
#include<stdio.h>
#include<conio.h>
struct node
{
	int data;
	struct node * link;
};
struct node * head;
int loc,n,i,count;
void insert();
void insertbeg();
void insertspe();
void insertend();
void display();
void deletebeg();
void deletespe();
void deleteend();
void main()
{
	int choice,k;
	clrscr();
	do
	{
	printf("\nenter your choice");
	printf("\n1.create list\n2.insert at beggining\n3.insert at specific location\n4.insert at end\n5.delete at beginning\n6.delete at specific location\n7.delete at end\n8.exit ");
	scanf("%d",&choice);
	switch(choice)
	{
		case 1:
			printf("\nhow many element you want to print?");
			scanf("%d",&n);
			count=n;
			for(i=0;i<n;i++)
			insert();
			display();
			break;
		case 2:
			abc:
			insertbeg();
			display();
			break;
		case 3:
			insertspe();
			display();
			break;
		case 4:
			if(count==0)
				goto abc;
			insertend();
			display();
			break;
		case 5:
			def:
			deletebeg();
			display();
			break;
		case 6:
			deletespe();
			display();
			break;
		case 7:
			if(count==1)
			goto def;
			deleteend();
			display();
			break;
		case 8:
			exit (0);
		default:
			printf("\nwrong choice");
			break;
	}
	}while(k!=0);
	getch();
}
void insert()
{
	if(i==0)
	{
		head=(struct node*)malloc(sizeof(struct node));
		printf("enter element");
		scanf("%d",&head->data);
		head->link=NULL;
	}
	else
	{
		struct node * temp;
		struct node * temp1;
		temp1=(struct node*)malloc(sizeof(struct node));
		temp=head;
		while(temp->link!=NULL)
		{
			temp=temp->link;
		}
		printf("\nenter element");
		scanf("%d",&temp1->data);
		temp1->link=NULL;
		temp->link=temp1;
	}
}
void insertbeg()
{
		struct node * temp2;
		temp2=(struct node*)malloc(sizeof(struct node));
		printf("\nenter element");
		scanf("%d",&temp2->data);
		temp2->link=head;
		head=temp2;
		count++;
}
void insertspe()
{
	printf("enter location");
	scanf("%d",&loc);
	if(loc==1)
	{
		insertbeg();
		goto abc;
	}
	else if(loc==n)
	{
		insertend();
		goto abc;
	}
	else
	{
		struct node * temp2;
		struct node * temp1;
		struct node * new1;
		temp1=head;
		temp2=head;
		for(i=0;i<loc-1;i++)
		{
			temp1=temp2;
			temp2=temp2->link;
		}
		new1=(struct node *)malloc(sizeof(struct node));
		printf("\nenter element");
		scanf("%d",&new1->data);
		temp1->link=new1;
		new1->link=temp2;
		count++;
	}
	abc:
}
void insertend()
{
		struct node * temp3;
		struct node * temp4;
		temp3=head;
		while(temp3->link!=NULL)
		{
			temp3=temp3->link;
		}
		temp4=(struct node*)malloc(sizeof(struct node));
		printf("\nenter element");
		scanf("%d",&temp4->data);
		temp3->link=temp4;
		temp4->link=NULL;
		count++;
}
void display()
{
	struct node * temp;
	temp=head;
	printf("\nlist:");
		while(temp!=NULL)
		{
			printf("%d",temp->data);
			temp=temp->link;
		}

}
void deletebeg()
{
	struct node * temp;
	struct node * temp1;
	temp=head;
	temp1=temp->link;
	head=temp1;
	free(temp);
	count--;
}
void deleteend()
{
	struct node * temp;
	struct node * temp1;
	temp=head;
	while(temp->link!=NULL)
	{
		temp1=temp;
		temp=temp->link;
	}
	temp1->link=NULL;
	free(temp);
	count--;
}
void deletespe()
{
	printf("\nenter location");
	scanf("%d",&loc);
	if(loc==1)
	{
		deletebeg();
		goto abc;
	}
	else if(loc==count)
	{
		deleteend();
		goto abc;
	}
	else
	{
		struct node * temp;
		struct node * temp1;
		struct node * temp2;
		temp=head;
		temp1=head;
		for(i=0;i<loc-1;i++)
		{
			temp=temp1;
			temp1=temp1->link;
		}
		temp2=temp1;
		temp2=temp2->link;
		temp->link=temp2;
		free(temp1);
		count--;
	}
	abc:
}













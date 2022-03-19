# circular-list
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int data;
    struct node*next;
}*newnode,*temp;
struct node* head=NULL;
struct node* tail=NULL;
void create()
{
    int value,ch;
    do{
        newnode=(struct node*)malloc(sizeof(struct node*));
        printf("enter the value");
        scanf("%d",&value);
        newnode->data=value;
        newnode->next=NULL;
        if(head==NULL)
        {
            head=newnode;
            tail=newnode;
            newnode->next=head;
        }
        else
        {
            tail->next=newnode;
            tail=newnode;
            tail->next=head;
        }
        printf("1-continue,0-exit\n");
        fflush(stdin);
        scanf("%d",&ch);
    }
    while(ch==1);
}
void display()
{
    temp=head;
    while(temp->next!=head)
    {
        printf("%d",temp->data);
        temp=temp->next;
    }
}
void insert_beg()
{
    int value;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("enter the value\n");
    scanf("%d",&value);
    newnode->data=value;
    newnode->next=head;
    tail->next=newnode;
    head=newnode;
}
void insert_end()
{
    int value;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("enter the value\n");
    scanf("%d",&value);
    newnode->data=value;
    newnode->next=head;
    tail->next=newnode;
    tail=newnode;
}
void insert_pos()
{
    int i,pos,value;
    temp=head;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("enter the value\n");
    scanf("%d",&value);
    printf("enter the position\n");
    scanf("%d",&pos);
    for(i=0;i<pos-1;i++)
    {
        newnode->data=value;
        newnode->next=temp->next;
        temp->next=newnode;
    }
}
void delete_beg()
{
    temp=head;
    while(temp->next!=head)
    {
        temp=temp->next;
    }
    temp->next=head;
    tail=temp;
}
void delete_end()
{
    temp=head;
    while(temp->next!=head)
    {
        temp=temp->next;
    }
    temp->next=head;
    tail=temp;
}
void delete_pos()
{
    int pos,i,value;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("enter the value");
    scanf("%d",&value);
    printf("enter teh position");
    scanf("%d",&pos);
    for(i=0;i<pos-1;i++)
    {
        temp=temp->next;
    }
    temp->next=temp->next->next;
}
int main()
{
     int choice=0;
        while(choice<9)
        {
            printf("Operations on circular linked list are:\n");
            printf("1.Creation\n");
            printf("2.Display\n");
            printf("3.Insertion at beginning\n");
            printf("4.Insertion at ending\n");
            printf("5.Insertion at specified position\n");
            printf("6.Deletion at beginning\n");
            printf("7.Deletion at ending\n");
            printf("8.Deletion at specified position\n");
            printf("Others:Exit()\n");
            printf("Enter your choice:\n");
            scanf("%d",&choice);
            switch(choice)
            {
                case 1:
                        create();
                        break;
                case 2:
                        display();
                        break;
                case 3:
                        insert_beg();
                        break;
                case 4:
                        insert_end();
                        break;
                case 5:
                        insert_pos();
                        break;
                case 6:
                        delete_beg();
                        break;
                case 7:
                        delete_end();
                        break;
                case 8:
                        delete_pos();
                        break;
                default:
                        break;
            }
        }
}

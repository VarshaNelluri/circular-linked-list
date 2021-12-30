# circular-linked-list
#include<stdio.h>
#include<stdlib.h>
struct circularlist
{
    int data;
    struct circularlist *next;
};
typedef struct circularlist node;
node *create(node *first)
{
    node *new,*prev;
    int x;
    printf("enter a value(enter -1 to stop)\n");
    scanf("%d",&x);
    while(x!=-1)
    {
        new=(node *)malloc(sizeof(node));
        new->data=x;
        new->next=NULL;
        if(first==NULL)
        {
            first=new;
            prev=new;
        }
        else
        {
            prev->next=new;
            prev=new;
        }
        printf("enter a value(enter -1 to stop)\n");
        scanf("%d",&x);
        prev->next=first;
    }
    return first;
}
void display (node *first)
{
    node *temp=first;
    node *k=first;
    if(first==NULL)
    {
        printf("No list is found\n");
    }
    else
    {
        printf("%d->",temp->data);
        while (temp->next!=k)
        {
            temp=temp->next;
            printf("%d->",temp->data);
        }
    }
}
int count(node *first)
{
    int c=0;
    node *temp=first;
    node *k=first;
    while(temp->next!=k)
    {
        c++;
        temp=temp->next;
    }
    return c+1;
}
void search(node *first,int f)
{
    node *temp=first;
    node *k=first;
    int flag=0;
    while(temp->next!=k)
    {
        if(temp->data==f)
        {
            flag=1;
            break;
        }
        temp=temp->next;
    }
    if(flag==1)
        printf("%d Element is found\n",f);
    else
        printf("%d Element is not found\n",f);
}
node *insert_at_begin(node *first,int x)
{
    node *new,*k,*temp;
    temp=first;
    k=first;
    new=(node *)malloc(sizeof(node));
    new->data=x;
    new->next=NULL;
    if(first==NULL)
    {
        first=new;
    }
    else
    {
        while(temp->next!=k)
        {
           temp=temp->next; 
        }
        temp->next=new;
        new->next=first;
        first=new;
    }
    return first;
}
node *insert_at_end(node *first,int x)
{
    node *temp=first,*new;
    node *k=first;
    new=(node *)malloc(sizeof(node));
    new->data=x;
    new->next=NULL;
    if(first==NULL)
    {
        first=new;
    }
    else
    {
        while(temp->next!=k)
        {
            temp=temp->next;
        }
        temp->next=new;
        new->next=first;
    }
    return first;
}
node *insert_at_pos(node *first,int x,int pos)
{
    node *new,*temp=first;
    new=(node *)malloc(sizeof(node));
    new->data=x;
    new->next=NULL;
    for(int i=1;i<pos-1;i++)
    {
        temp=temp->next;
    }
    new->next=temp->next;
    temp->next=new;
    return first;
}
node *begin_delete(node *first)
{
    node *temp,*k;
    temp=first;
    k=first;
...

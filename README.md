# llappend
#include<iostream>
using namespace std;


class Node
{
    public:
    int data;
    Node* next;
    Node(int data)
    {
        this->data=data;
        next=NULL;
    }
};
Node* insert()
{
    int data;
    cin>>data;
    Node* head=NULL;
    Node* tail=NULL;
    while(data!=-1)
    {
        Node* newNode=new Node(data);
        if(head==NULL)
        {
            head=newNode;
            tail=newNode;
        }
        else
        {
            tail->next=newNode;
            tail=tail->next;
        }
        cin>>data;
    }
    return head;
}
void print(Node* head)
{
    Node* temp=head;
    while(temp!=NULL)
    {
        cout<<temp->data<<" ";
        temp=temp->next;
    }
}

Node* append(Node* head,int pos)
{
    Node* temp=head;
    int count =0;
    int len=0;
    while(temp!=NULL)
    {
        len++;
        temp=temp->next;
    }
    temp=head;
    count=len-pos;
    for(int i=0;i<count-1;i++)
    {
        temp=temp->next;
    }
    Node* h1=temp;
    cout<<h1->data<<endl;
   
    temp=head;
    for(int i=0;i<count;i++)
    {
        temp=temp->next;
    }
    Node* h2=temp;//
    cout<<h2->data<<endl;
     h1->next=NULL;
    Node* last;
    while(temp!=NULL)//here temp starts from h2 address
    {
        last=temp;
        temp=temp->next;
    }
    cout<<last->data<<endl;
    last->next=head;

    return h2;

}
int length(Node* head)
{
    Node* temp=head;
    int len=0;
    while(temp!=NULL)
    {
        len++;
        temp=temp->next;
    }
    return len;
}

int main()
{
    Node* head=insert();
   head=append(head,3);
   //cout<<length(head)<<endl;
    print(head);
}

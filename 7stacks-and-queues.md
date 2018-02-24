Brackets

StoneWall

Fish

Nesting




#include <stdio.h>
#include <stdlib.h>

struct node
{
    char *val;
    struct node *next;

};
struct node *head;

void push(char *A)
{
    struct node *newNode=malloc(sizeof(struct node));
    struct node *tmp;

    newNode->val=A;
    tmp=head;
    head=newNode;
    newNode->next=tmp;
}
char pop()
{
    struct node *tmp;
    char val;
    tmp=head;
    val=tmp-val;
    head=head->next;
    free(tmp);
    return val;
}
int isEmpty()
{

    if(head==NULL)
    {

        return 1;
    }
    else
        return 0;
}

int isLeftBracket(char A)
{

    switch(A)
    {
    case '{':
    case '[':
    case '(':
        return 1;
    default:
        return 0;
    }
}

int isRightBracket(char A)
{

    switch(A)
    {
    case '}':
    case ']':
    case ')':
        return 1;
    default:
        return 0;
    }
}
int isPaired(char a,char b)
{

    if(a=='(' && b ==')')
        return 1;
    if(a=='{' && b =='}')
        return 1;
    if(a=='[' && b ==']')
        return 1;
    return 0;

}
int solution(char *S)
{
    int i=0;
    struct node *head;
    char val;
    if(S==NULL)
    {
        return 1;
    }
    else
    {
        while(S[i]!='\0')
        {
            if(isLeftBracket(S[i]))
            {
                push(S[i]);
            }
            else
            {
                if(isRightBracket(S[i]))
                {
                    val=pop();
                    if(!isPaired(val,S[i]))
                        return 0;
                }
                else
                {
                    return 0;//contain a character that not any of {[( )]}
                }
            }
        }
    }
    if(!isEmpty())
        return 0;
    return 1;
}

int main()
{
    printf("Hello world! %d\n",solution('[]'));
    printf("Hello world! %d\n",solution('{}'));
    return 0;
}

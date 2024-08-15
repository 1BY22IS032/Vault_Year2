    # Stack using Array

```c
#include<stdio.h>
#include<stdlib.h>
#define Max 3
void push(int s[],int* top, int item){
    if(*top == Max-1){
        printf("Reached Top of stack, overflow\n");
        return;
    }

    s[++(*top)] = item;
    printf("%d has been added to stack\n",item);

}
 
void pop(int s[],int *top){
    if(*top == -1){
        printf("Stack Empty / Stack Overflow\n");
        return;
    }
    int item;
    item =s[(*top)--];
    printf("%d has been delted\n", item);
}

void display(int s[],int* top){
    printf("Displaying the stack:\n");
    for(int i=*top;i>-1;i--){
        printf("%d \n",s[i]);
    }
}

int main(){
    int top = -1;
    int stack[Max];
    int ele;
    int ch;

    while (1)
    {
        printf("1.push\n2.pop\n3.display\n4.exit\n");
        printf("Enter your choice\n");
        scanf("%d",&ch);

        switch(ch){
            case 1: {
                printf("Enter the element to be inserted\n");
                scanf("%d",&ele);
                push(stack,&top,ele);
                break;
            }
            case 2: {
                pop(stack,&top);
                break;
            }
            case 3: {
                display(stack,&top);
                break;
            }
            case 4:{
                exit(0);
                break;
            }
        }
    }
    
}
```
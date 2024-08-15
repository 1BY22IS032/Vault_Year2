```java
package com.bmsit_programs.program2;
public class program2 {
    public int Max = 5;
    public int[] our_stack = new int[Max];
    public int top = -1;
    int item;

    public void push(int item){
        if(top==Max-1){
            System.out.println("S Over");
        }
        else{
            our_stack[++top]= item;
        }
    }

    public void pop(){
        if(top==-1){
            System.out.println("Underflow");
        }
        else{
            int temp;
            temp = our_stack[top--];
            System.out.println(temp+" is deleted");
        }
    }

    public void display(){
        for(int i=top;i>-1;i--){
            System.out.println(our_stack[i]);
        }
    }

    public static void main(String[] args){
        program2 stack_object = new program2();
        stack_object.push(12);
        stack_object.push(13);
        stack_object.push(14);
        stack_object.display();
        stack_object.push(15);
        stack_object.push(16);
        stack_object.push(17); // should be stack overflow
        stack_object.pop();
        stack_object.pop();
        stack_object.pop();
        stack_object.pop();
        stack_object.pop();
        stack_object.pop();// should be underflow

    }
}

```
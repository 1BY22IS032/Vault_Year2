# Recursion and Queues

## Recursion

Recursion

```c
a(parameters){
    a(arguments);
}
```

### Factorial Function

![Factorial Definition](https://cdn.imgchest.com/files/g4z9cxrbr37.png)

Factorial Code:

```c
Factorial(n){
    if(n=0){
        return 1;
    }
    else{
        Factorial(n-1);
    }
}
```

### Fibbonachi Sequence

The next element is the sum of the preceding 2 elements

Fibbonachi code

```c
Fibbonachi(n){
    if(n==1){
        return 0;
    }
    else if(n==2){
        return 1;
    }
    else{
        for(int i=0;i<n;i++){
                printf("%d",Fibbonachi(n-1)+Fibbonachi(n-2));
        }
    }
}   
```

### Greatest Common Divisor

To find the greatest common divisor or gcd

Code:

```c
int GCD(m,n){
    if(m==n){
        return m;
    }
    else if(m>n){
        return GCD(m-n,n);
    }
    else if(m<n){
        return GCD(m,n-m);
    }
}
```

### Tower Of Hanoi Problem

### Ackerrman's Function

![Ackermman's](https://cdn.imgchest.com/files/my8xc8mb6r4.png)

## Queues

Runs on **First Come First Serve (FCFS)**

In a Linear Queue we

1. Insert Rear
2. Delte Front
3. Display

These three functions are used

In a **linear queue**, when there are no elements, front = 0 and rear = -1.

If front>rear, that implies there are no elements in the queue.

if f == r, then there is only one element in the queue.

[Linear Queue](.\ProgramCodes\Linear_Queues.md)

Disadvantages of Ordinary Queues

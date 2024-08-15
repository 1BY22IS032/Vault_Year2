<!--markdownlint-disable MD046-->
# Module 1

## What are data structures

Data structes are the models for organizing the data so that accessing memory becomes easy.
They deal with the study of how data is organized in memory, how it can be manipulated, how it can be retrieved or interacted with.

### Classification

                Primitive                                           Non Primitive
    Int     Float       Char        Bool                      Linear           Non-Linear 
                                                        Arrays                             Trees
                                                        linked lists                       Graphs

Primitive Data Structures: can be manipulated directly by machine instructions

Non Primitive DS : cannot be directly manipulated

Linear: Structures where the data is stored either physically adjacent or logically adjacent in a linear fashion

Non Linear: Do not exhibit any linear behaviour but are logically related

## Dynamic Memory Allocation

- Is the process of allocating memory during runtime
- Used in programs where memory usage is unpredictable
- There are 4 functions used for memory allocation

### Malloc

- Used to allocate one single block of memory of specified size
- returns a pointer of the first block of memory allocated
- Syntax `<pointerName> = (<castType>*)malloc(<sizeOfMemory>);`
  
### Calloc

- Allocated multiple blocks of the same datatype and size
- initializes all of the blocks to 0
- returns a pointer to the first byte of allocated memory
- Syntax : `<pointerName> = (<castType>*)calloc(<number>,<size>);`
  
### Realloc

- Reallocates or modifies size of allocated block/ blocks of memory
- Syntax : `<pointerName> = (<castType>*)realloc(<pointerName>,<size>);`

### Free

- Deallocated allocated memory
- Syntax : `free(<pointerName>);`

### Problems with Dynamic Memory allocation

1. Memory leakage
   1. A problem where memory is reserved but not accessible to any of the applications.
   2. In the below example, a is being reallocated as 20 and the memory allocated as 10 is inaccessible.

```C
int* a;
a=(int*)malloc(sizeof(int));
*a = 10;
a =(int*)malloc(sizeof(int));
*a=20;
```

1. Dangling Pointer
   1. Any pointer to a destroyed object or which doesn't contain a valid address is called a dangling pointer

```C
        int*a;
        a = (int*)malloc(sizeof(int));
        *a= 10;
        free(a);
```

   2. In the above example a is being deallocated and the pointer nolonger points to any valid address

### Static vs Dynamic Memory allocation

|Static Memory Allocation | Dynamic Memory Allocation|
|:-----------------------:|:------------------------:|
|Memory is allocated during compile time| Memory is allocated during Runtime|
|Size is fixed and can't be altered|Size is variable and can also be changed|
|Execution is faster cuz memory is already allocated|Execution is slower comparitivly|
|Part of memey allocated is stack memory or global memory|Memory is allocated from Heap|
|Ex arrays| Ex Dynamic arrays or Linked Lists|

## Arrays

Arrays are group of similar type elements grouped together next to one another in memory.
a diagram of memory allocation of an array is as follows.

![ArrayMemoryAllocation](https://cdn.imgchest.com/files/k46acew8gw7.png)

The upper bound Or UB is the largest index in the array and the lower bound LB is the lowest index in the array

### Binary Search

Here is the code for the binary search of an element in an array

```C
#include<stdio.h>
int main(){
    int a[10] = {1,3,5,7,9,12,13,16,17,18};
    int ele;
    scanf("%d",&ele);

    low = 0;
    high = n-1;
    while(low<=high){
        mid = (low+high)/2;
        if(ele==a[mid]){
            printf("found");
            exit(0);
        }
        else if(ele<a[mid]){
            high = mid -1;
        }
        else if(ele>a[mid]){
            low = mid+1;
        }
    }
}
```

### Dynamic Arrays

Dynamic arrays is an array whose size can be determined at runtime.

#### Dynamic MXN matrix

```C
    int main() {
    int m, n;
    
    // Input the dimensions of the array
    printf("Enter the number of rows (m): ");
    scanf("%d", &m);
    printf("Enter the number of columns (n): ");
    scanf("%d", &n);

    // Dynamically allocate memory for the array
    int **array = (int **)malloc(m * sizeof(int *));
    if (array == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }
    for (int i = 0; i < m; i++) {
        array[i] = (int *)malloc(n * sizeof(int));
        if (array[i] == NULL) {
            printf("Memory allocation failed.\n");
            // Free previously allocated memory before returning
            for (int j = 0; j < i; j++) {
                free(array[j]);
            }
            free(array);
            return 1;
        }
    }
}
```

## Structures

if we want to store the informati0n which is a collectioi1 of ite11.1s cif dissimilar datatype, we
carmot use an·ays. This is where we use structures.

Definition of a structure:

```c
    struct <name>{
        <datatype> member1;
        <datatype> member2;
        ..
        ..
    }
```

### Typedef

The "typedef' is a keyword that allows the programmer to create a new datatype name for an
existing datatype.

Syntax:

```c
        typedef <datatype> <newName>;
```

### Different ways to declare structures

Format 1:

```c
        struct student{
            /*
            all of the stuff
            */
        };
        struct student a,b,c;
```

Format 2:

```c
        struct student {
            /*
            all of the stuff
            */
        } a,b,c;
```

Format 3 : using typedef

```c
       typedef struct {
            /*
            all of the stuff
            */
        } STD;
        STD a,b,c;
```

## Self Referential Structures

A structure which contains a reference to itself is called a self referential structure.

General Format:

```c
struct <name>{
    <datatype> member1;
    <datatype> member2;
    ..
    ..
    ..
    struct <name>* <pointerName>;
}
```

## Stacks

Stacks using Arrays:

[Stack Using Arrays](./ProgramCodes/Stack_Array.md)

Stack using Dynamic Arrays:

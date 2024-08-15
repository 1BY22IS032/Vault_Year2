# Introduction to JAVA MODULE 1

## Imp points

### Parameters used in Java program

- class : used to declare a class
- public : access specifier, allows the method to be visible to all
- static : static methods need not be called
- void : return type
- main : starting keyword
- String[] args : cli arguments

## Identifier Rules

1. Should start with a letter or underscore or dollar sign
2. shouldn't start with a number or other special chars
3. can contain any set combination of chars
4. THEY ARE CASE SENSITIVE

## Types of variables

1. Local :
   1. Placed inside method of class
   2. specific to method
2. Class variable (Static variable)
   1. Placed inside class but outside method
   2. made with `static` keyword
   3. constant for all instances of class
   4. used specifically for constants
3. Instance Variable (non static variable)
   1. Placed inside the class but outside method
   2. made without `static` keyword
   3. is unique for each and every instance of a class

## Data types

### Primitive Datatypes

![PrimitiveDataTypes](https://cdn.imgchest.com/files/w7pjcdwa8d7.png)

### Non Primitive Datatypes

![NonPDT](https://cdn.imgchest.com/files/345xcq9zde7.png)

## Operators in JAVA

### Unary Operator

They work on a single operand
Types:

1. Increment/Decrement:
   1. ++ --
   2. specify prefix and postfix
   3. example
2. Negetion Operator:
   1. Inverts the posititve or negetive values
   2. also inverses boolean values
   3. example
3. Logical not operator
   1. ! operator
   2. used to inverse boolean values
4. Bitwise complement operator
   1. ~ operator
   2. used to invert indivisual binaries in the value
   3. example 1001 becomes 0110

### Terenery Operator

is a replacement for if-then-else statements
`condition ? expression_true : expression_false`

## Java Switch Statement

- used to replace if-else-if ladders
- pivots against multiple conditions and appropriate results

```java
switch (expression) {
  case value1:
    // code to execute if expression == value1
    break;
  case value2:
    // code to execute if expression == value2
    break;
  // ... more cases
  default:
    // code to execute if expression doesn't match any case
}
```

## Loops

![Loops](https://cdn.imgchest.com/files/j7kzcwbvjg7.png)

## Arrays

- An array is a group of similar data typed variables that shares a common name
- The elements of the array are accessed by the array index
- The array index should be a positive integer value. An array may be one-dimensional or multidimensional
- Syntax `type array-name[ ] = new type[size];`
- Every Array is an object, so we can create new arrays using the new operator
- Array input: `int a[5]={1,2,3,4,5}`
- can be accessed via `arrayName[index]`
  
Java program to sort an array of numbers

```java
package com.random;
class sort{
    int[] array;
    sort(int[] a){
        this.array =a;
        int temp;
        int i,j;
        for( i=0;i<a.length;i++){
            for( j=0;j<a.length;j++){
                if (a[i]<a[j]){
                    temp = a[j];
                    a[j]=a[i];
                    a[i]=temp;
                }
            }
        }
    }
    void print(){
        for (int i : array){
            System.out.println(i+"\n");
        }
    }
}
public class Sorting {
    public static void main(String[] args){
        int[] array = new int[]{10, 11, 94, 3, -4};
        sort arra = new sort(array);
        arra.print();
    }
}

```

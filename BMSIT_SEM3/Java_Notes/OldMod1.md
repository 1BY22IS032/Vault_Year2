# Java Module 1 & 2

## Features of java

### Simple

- simple to learn
- first to introduce Automatic garbage collection

### Object Oriented Programming

- Supports OOPS,
- supports Polymorphism,Inheritance,Abstraction,Encapsulation

### Platform independent

- uses JVM or Java Virtual Machine
- has two components, JVM and JAPI
- Write Once and run anywhere

### Secure language

- Removes the need of Explicit pointers
- runs all programs in a sandbox called JVM separating the OS/System from itself.
- The Class Loader dynamically allocates the classes defined in the program to the Java Runtime environment by separating the
classes that are local to the machine and those that are imported from other network sources.
- prevents malicious code access to objects above its permission domain
  
### Robustness

- Java can handle unexpected events without crashing or causing harm
- Uses strong memory allocation so improper allocation doesn't harm the system
- Java implements the concept of Error handling and allowed users to execute and do custom actions

### Architechture Neutral

- Can run on any machine using JVM and JRE

### High Performance

- Lot faster due to its use of bytecode.
- but is slower than C/C++

### MultiThreaded Programming

- Supports multiple operations running at the same time.

### Dynamic Nature

- Classes are not loaded in all at once, they jump into action only when an invoke exp  or some data about the class is necessary

## Lexical Issues

### Comments

- Single line `//`
- Multi line `/**/`

### Identifieres

- Names for classes, functions and variables etc are called identifiers
- key words used by the language can't be identifiers
- should begin with an Alphabet,$ or _
- Identifiers are case sensitive

### Modifiers

- Access Modifiers
  - Public: accesssible from outside the class
  - Private: accessible only from inside the class
  - Protected: can be accessed by child classes

## Data Types

![DataTypes](https://cdn.imgchest.com/files/84apcov2984.png)
![DataTypes](https://cdn.imgchest.com/files/b49zcov82my.png)

## Variables

- Syntax `datatype variable_name = value;`
- naming cannot contain white spaces
- name can begin with special characters such as $ and _
- CamelCase naming convention

### Types of variables

- Local
- Static
- Instance

## Random

### Java Literal

- Literal = fixed value
- Types
  - Integer
  - Real
  - Character
  - String
  - Backslash
- Decimal Literal : 0->9 
- Octal: 0->7 ; must have `0` as prefix
- HexaDecimal: 0-9,A-Z; must have prefix of `Ox`

- long must be suffixed with L
- floats should be suffixed with f
- string must be in doubleQuotes

## Type Conversions

![TypeConversion](https://cdn.imgchest.com/files/p7bwco2naj7.png)

```java
double d = 120.04;
long l = (long)d;
float i = (float)l;
```

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

<!--markdownlint-disable MD025-->
<!--markdownlint-disable MD033-->
# Questions

1. Define Algorithm,what are the criteria that an algo must satisfy (8) [DONE]
2. Write an algo to find the maximum element in an array of n elements, give the mathematical analysis of this non recursive algorithm (8) [DONE]
3. Explain general plan for analysing efficiency of a recursive algorithm, and write the algo to find the factorial of a given number. Derive its efficacy (8) [Done]
4. Explain with an example of how a new variable count introduced in a program that can be used to find the no of steps needed by a program to solve a problem instance (4) [L8R]
5. Define Space and Time complexity of an algorithm and Compute the time complexity of a fibbonachi number (5) [DONE]
6. What are the basic asymptotic efficiency classes and explain Big O, Omega and Theta classes with examples (10) [DONE]
7. Give the Mathematical Analysis of a non recursive Matrix multiplication algorithm
8. Give the general plan for analyzing the time effciency of a recursive algo and also analyse TOWER OF HANOI recursive algo. if m in the no of times a disc has been moved, calculate the reccurance relation and solve it.
9. Design an algo that performs Sequential Search and computes best, worst and avg case efficiency (10)
10. Recursive and Non Recursive implementation of Factorial (6)
11. Order of Growth (4)
12. Combination of Time Complexity Questions (10)
13. Algorithm analysis (Read From paper)
14. Explain Best, Worst, Avg case efficiencies of an algo with examples for each case

# Answers

## Define Algorithm,what are the criteria that an algo must satisfy

An algorithm is a finite set of well defined instructions or rules designed to perform a specific task or solve a particular problem. It takes an input, processes it and produces an output

The Criteria for an algorithm are:
                        {F.D.I.O.E.G}

- Finiteness
- Definiteness
- Input
- Output
- Effectiveness
- Generality

1. Finiteness:
   - an algorithm cannot go on indefinetly
   - An algorithm must terminate after a finite no of steps
   - Ensuring finiteness guarantees that an algo reaches a conclusion
   - eg, a sorting algorithm musn't sort endlessly
2. Definiteness
    - Each step of the algorithm must be precicely and unambiguiously defined
    - each instruction and operation must be simple
    - This is to ensure consistency in execution
3. Input:
    - An algo must have 0 or more inputs
    - inputs are the starting point for an algo, they are the data that is to be processed
4. Output:
    - An algo must have 0 or more outputs
    - An algorithm produces an output based on the procees and calculations processed on the input
5. Effectiveness:
    - Steps are simple and basic and must be easy to comprehend

## Write an algo to find the maximum element in an array of n elements, give the mathematical analysis of this non recursive algorithm

```algorithm
function maxElement(A[0->n-1])
    maxval <- A[0]
    for i <- 1 to n-1
        if maxval < A[i]
            maxval := A[i]
    return maxval
```

### Mathematical Analysis of Non Recursive functions

1. Identify the input paramenter that indicates input size
2. Identify the basic operation of the algorithm
3. Verify whether the no of steps is dependent upon the input size alone and if not, calculate the Best, worst and avg case scenarios
4. Create a sum of the no of steps of the algorithm executed
5. Using sum manipulation find the closed form formula or the order of growth

![Analysis](https://cdn.imgchest.com/files/myd5c8gz564.png)

## Explain general plan for analysing efficiency of a recursive algorithm, and write the algo to find the factorial of a given number. Derive its efficacy

```algo
function factorial(n)
    if n <= 1
        return 1
    else
        return n * factorial(n)k
```

### Mathematical Analysis

1. Identify the input paramenter that indicates input size
2. Identify the basic operation of the algorithm
3. Verify whether the no of steps is dependent upon the input size alone and if not, calculate the Best, worst and avg case scenarios
4. Setup a recurrance relation for the number of times a basic step has been executed
5. Solve the recurrance relation

![Factorial](https://cdn.imgchest.com/files/b49zcq9g6dy.jpg)\

## Define Space and Time complexity of an algorithm and Compute the time complexity of a fibbonachi number

Time complexity measures how the runnign time of an algorithm matches upto the size of the input given.
It is usually described in BIG O notation. BIG O notation is the upper bound of the time taken or the time taken in the worst case scenario of the algorithm

Space complexity is the amount of space taken by the algorithm during its execution and to check if it is dependednt upon the size of the input
It is also depicted by the Big O notation which is the worst case scenario for the space taken

### Fibbonachi series recursive

```algo
function fibbo(n){
    if n =0
        return 0
    if n = 1 
        return 1
    else
        return fibbo(n-1)+fibbo(n-2)
}
```

The time complexity of Recursive fibbo is
> T(n) = T(n-1) + T(n-2) + O(1)

the number of function calls grows exponentially and when you add them together, you get

> T(n) = $2^n$O(1)
> <br>
> T(n) = O($2^n$)

## Asymptotic Notations

### BIG O ($O$)

A function $t(n)$ is said to be in $O(g(n))$, denoted by $t(n)$ $\epsilon$ $O(g(n))$ if $t(n)$ is bounded above by some constant multiple of $g(n)$

$$   t(n) \leq C * g(n) ,\hspace{5mm} \forall \: n > n_0 $$

The value $g(n)$ is the upper bound for $f(n)$. It is the measure of the longest time the function $f(n)$ can take.

![Big O](https://cdn.imgchest.com/files/k739c2gblx7.png)

### Big Omega ($\Omega$)

A function $t(n)$ is said to be in $\Omega(g(n))$,
if $t(n)$ is bounded below by some positive constant multiple of $g(n)$.
if there exists soem positive constant c and some non negetive constant $n_0$ such that

$$ t(n) \geq c*g(n), \hspace{5mm} \forall \, n > n_0 $$

![Big omega](https://cdn.imgchest.com/files/e4gdc6owae4.png)

### Big Theta ($\Theta$)

A function $t(n)$ is said to be in $\Theta(g(n))$,
if $t(n)$ is bounded by both above and below by soem positive constant multiples of $g(n)$ for all large n,
such that,

$$ c_2 \, g(n) \leq t(n) \leq c_1 \, g(n) , \hspace{3mm} \forall n > n_0$$

![Big Theta](https://cdn.imgchest.com/files/l7lxcqrwea7.png)

## Give the Mathematical Analysis of a non recursive Matrix multiplication algorithm

```algo
for i <- 0 to n-1 do 
    for j <- 0 to n -1 do
        C[i,j] <- 0.0
        for k <- 0 to n-1 do
            C[i,j] <- C[i,j] + A[i,k] * B[k,j]
return C
```


<!--markdownlint-disable MD033-->
<!--markdownlint-disable MD025-->

# Questions Set A

1. Explain the general concept of divide and conquer method. Give the general algorithm DAndC(P) [ Where P is the problem to solve] to illustrate this technique. Discuss general divide and conquer technique with control abstraction and recurrence relation.
2. List the advantages and disadvantages of Divide and Conquer.
3. Find the upper bound of recurrences given by below by the substitution method
   - $T(n) = 2*T(n) + n$
   - $T(n) = T(n/2) + 1$
4. Explain the general method of substitutuion method to solve recurrence equation
5. State and explain master's theorem to solve recurrence equation
6. Consider TOH puzzle. Derive the recurrence relation for the total movement of disk. Solve the recurrence relation using substitutuion method

# Answers Set A

## Explain the general concept of divide and conquer method

- Given a function to compute on 'n' inputs,  the DAC strat suggests splitting the problem into sub problems
- The sub problems must be solved and then combined into a whole solution
- If the sub problems are large themselves, they must be recursivly divided and solved

### General Algorithm of DAC

Algorithm:

```algo
Algorithm DAndC(P){
    if Small(P) then return S(P);
    else{
        divide P into smaller instances p1,p2,p3...p(k). k>=1;
        Apply DAndC to each of the sub problems;
        return Combine(DAndC(P1),DAndC(P2)....DAndC(P3))
    }
}
```

- Initially DAndC(P) is invoked where P is the problem to be solved
- Small(P) is a boolean that determines if the problem needs to be divided into sub problems and be solved
- Combine is a function that determines the solution to P by combining the results of the subproblems

### Recurrance relation for Divide and conquer

For Problem P, size n and sizes of the k sub problems be n1,n2...nk then,

$$
T(n) =
    \begin{cases}
    g(n) & \text{n small} \\
    T(n_1) + T(n_2) + \cdots + T(n_k) + f(n) & \text{otherwise}
    \end{cases}
$$

Where,

$T(n)$ is the time for d&c method on any input of size n

$g(n)$ is the time to compute answer for small/simple inputs

$f(n)$ is the time taken to divide and combine all the subproblems

### Recurrance Equation

- Instance of size n
- divided into b parts
**HERE WE ASSUME $n = b^k$**


$$
T(n) =
    \begin{cases}
    T(1) & \text{n=1} \\
    aT(n/b)+f(n) &\text{n>1}
    \end{cases}
$$

### Master Theorem

$$T(n) = aT(n/b) + f(n) \rightarrow \hspace{3mm} f(n) \,\epsilon \, \Theta(n^d)$$

**PLEASE CONCENTRATE ON THE** $n^d$

$$
T(n) =
    \begin{cases}
    \Theta (n^d) & \text{if} & a < b^d \\
    \Theta (n^{d}\log(n)) & \text{if} & a=b^d\\
    \Theta (n^{\log_b(a)}) & \text{if} & a>b^d
    \end{cases}
$$

## Advantages and disadvantages

### Advantages

1. **Simplicity**: D&C algorithms often simplify complex problems by breaking them down into smaller, more manageable subproblems. This can make the algorithm easier to understand and implement.

2. **Efficiency**: Many problems that are hard to solve with direct methods can be efficiently solved using D&C. For example, merge sort and quicksort are both efficient sorting algorithms that use D&C.

3. **Optimal Substructure**: D&C algorithms often exploit the optimal substructure of problems, meaning that optimal solutions to subproblems can be combined to form an optimal solution to the original problem.

4. **Parallelism**: D&C algorithms naturally lend themselves to parallel processing because different subproblems can be solved concurrently. This can lead to significant performance improvements on multi-core or distributed systems.

5. **Improved Performance for Certain Problems**: For many problems, D&C algorithms provide significant improvements over naive approaches. For example, D&C methods for matrix multiplication or finding the closest pair of points are more efficient than straightforward approaches.

### Disadvantages

1. **Overhead**: The process of dividing the problem and combining the results can introduce significant overhead, especially if the overhead of dividing and combining is high relative to the time spent solving the subproblems.

2. **Complexity of Recursion**: For some problems, the recursive nature of D&C algorithms can lead to complex code and difficulties in managing recursion depth, stack space, and function calls.

3. **Memory Usage**: D&C algorithms often require additional space for recursion stacks or temporary arrays (e.g., merge sort requires additional space for the merge operation), which can be a disadvantage for memory-constrained environments.

4. **Not Always Optimal**: For some problems, D&C might not be the most efficient approach. For example, problems with overlapping subproblems may be better suited to dynamic programming.

5. **Difficulty in Analyzing Performance**: For certain algorithms, analyzing the time complexity can be challenging. Although there are well-established methods (e.g., the Master Theorem), not all D&C algorithms fit neatly into these methods, making performance analysis more difficult.

Overall, the effectiveness of the D&C approach depends on the specific problem and the characteristics of the algorithm being used.

## Design an algo to find the max and the min element in a given list of n number using divide and conquer method

```algo
StraightMaxMin(a,n,max,min){
    max:=min:=a[1];
    for i:= 2 to n do{
        if(a[i] > max) then max:= a[i];
        if(a[i]< min) then min:=a[i];
    }
}
```

- This algorithm requires 2(n-1) element comparisons in the best average, and worst cases.
- Now the Best case occurs when the elements are in increasing order The number of element comparisons is 2(n-1).
- The worst case occurs when the element are in decreasing order. In this case number of comparisons is 2(n-1)


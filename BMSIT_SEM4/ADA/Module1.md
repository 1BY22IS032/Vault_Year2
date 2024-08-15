# Introduction to Algorithms

What is an algorithm : `An algorithm is a sequence of unambiguous outputs given to legitimete inputs in a given period of time`

## Cases

### WorstCase

The worst case efficiency is the efficiency for the worst case input of size n for which the algorithm has to run the longest through all inputs.

### BestCase

Best case; efficiency ; best case input ; for which; runs fastest;

### AvgCase

Time taken by algorithm; avged over all possible inputs

### SequentialSearchAlgorithm

```algo
i <- 0
while i<n and A[i]!= K
    i <- i+1
if i<n
return i
else return -1
```

take counter i,our search array A and search element K

## Space Complexity

- The total space taken up by an algorithm during its execution
- 2 parts ; fixed and variable
- fixed : consists of variables, constants etc
- variable : consists of input / output to function and recursion

formula is  S = c + Sp

## Time Complexity

Sum of the time taken to execute all instructions of the program

### Counter method 

1. use a counter variable
2. at each variable/constant definition, increase count
3. increase count for every loop and statement within the loop
4. increase count for last iteration of loop and return statements

### Steps per execution

![Alttext](https://cdn.imgchest.com/files/j7kzcw2e267.png)

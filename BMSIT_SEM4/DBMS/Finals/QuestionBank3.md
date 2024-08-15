<!--markdownlint-disable MD025-->
<!--markdownlint-disable MD029-->
<!--markdownlint-disable MD032-->

# Normal Forms

## Functional Dependencies

For a table `[x,y]` y is functionally dependent on x if,
when $t_1(x) = t_2(x)$ , $t_1(y) = t_2(y)$

Here, $x$ is called `determinant` and $y$ is called `dependent`

## First Normal Form 1NF

1. Each attribute must be atomic (ie should not be divisible any further )
   1. Composite attributes get separated to their own distinct attributes
   2. Multi Valued attributes get their own tuple or row
2. A attribute should contain values of the same type
3. attributes must have unique names
4. No order towards the rows should affect the database

- By default if a ER diagram is converted into a relational schema, it is in 1NF

## Second Normal Form 2NF

1. Should be in 1NF
2. No Partial Dependency must be present in the table

### Partial Dependency

- Partial Dependency is when A proper subset of the candidate key will determine a non prime attribute
- Prime attributes are ones that are part of Candidate key

![2NF](https://cdn.imgchest.com/files/pyvdc52qdey.jpg)

## Third Normal Form 3NF

1. Should be in 2NF
2. There shouldn't be any Transitive Dependency for Non Prime Attributes

> A table is in 3NF if and only if for each of its non trivial functional dependencies, atleast one of the following conditions holds
> 1. LHS is Super Key
> 2. RHS is Prime Attribute

## Boyce Codd Normal Form BCNF

1. Should be in 3NF
2. For each Non trivial Functional dependency, the Determinant must be a super key

## Rules of Inference

1. Reflexivity Rule
   1. If $Y \subseteq X$, then $X \rightarrow Y$
   2. If Y is a subset of X , X functionally determines Y
   3. Ex : $X = {A,B}$ then ${A,B} \rightarrow {A}$ and ${AB} \rightarrow {B}$
2. Augmentation Rule
   1. If $X \rightarrow Y$ then $XZ \rightarrow YZ$ for every $Z$
   2. If X determines Y, then X combined with any other attribute Z will determine Y combined with Z
3. Transitivity Rule
   1. $X \rightarrow Y$ and $Y \rightarrow Z$ then $X \rightarrow Z$
   2. If X determines Y and Y Determines Z, then X will Determine Z
4. Union Rule
   1. if $X \rightarrow Y$ and $X \rightarrow Z$ then, $X \rightarrow YZ$
   2. Allows you to combine the results of separate FDs with the same Determinant
5. Decomposition Rule
   1. if $X \rightarrow YZ$, then $X \rightarrow Y$ and $X \rightarrow Z$
   2. If X Determines a composite set of Attributes YZ, it indivisually Determines Both or all subsets of the Composite Set
6. Psudo Transitivity Rule
   1. if $X \rightarrow Y$ and $WY \rightarrow Z$, then $WX \rightarrow Z$
   2. If X determines Y and WY determines Z, then combining X with W will determine Z
7. Identity Rule
   1. $X \rightarrow X$
   2. Any set of attributes are functionally dependent on itself

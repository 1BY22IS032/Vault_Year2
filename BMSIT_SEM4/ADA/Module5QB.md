# Module 5

## Sum of Subsets

### Algorithm

**STUDY ONCE AGAIN**->

```plaintext
function sumOfSubsets(set, subset, n, subsetSize, total, sum, node):
    if total == sum:
        printSubset(subset, subsetSize)
        return

    if node >= n or total > sum:
        return

   
    subset[subsetSize] = set[node]
    sumOfSubsets(set, subset, n, subsetSize + 1, total + set[node], sum, node + 1)

    sumOfSubsets(set, subset, n, subsetSize, total, sum, node + 1)
```

## General Solution Backtracking

```text
Algorithm Backtrack(node):
    if isSolution(node) then
        processSolution(node)
    else
        candidates = generateCandidates(node)
        for each candidate in candidates do
            if isValid(candidate) then
                makeMove(candidate)
                Backtrack(candidate)
                unmakeMove(candidate)
```

## N Queens

```text
function solveNQueens(n):
    board = empty n x n board
    if placeQueen(board, 0) is true:
        print board
    else:
        print "No solution exists"

function placeQueen(board, col):
    if col >= n:
        return true
    
    for row from 0 to n-1:
        if isSafe(board, row, col):
            place queen at board[row][col]
            if placeQueen(board, col + 1) is true:
                return true
            remove queen from board[row][col]
    
    return false

function isSafe(board, row, col):
    check if no queen in the same row
    check if no queen in the upper left diagonal
    check if no queen in the lower left diagonal
    if all checks pass, return true
    else return false

main:
    call solveNQueens(8)
```
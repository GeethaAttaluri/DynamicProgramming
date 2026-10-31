# Fibonacci DP Notes

## Problem Analysis

### Problem
- Given n, return the nth Fibonacci number.
- Sequence: 0, 1, 1, 2, 3, 5, 8, ...

### Recognition
- The current answer depends on the previous two answers.

### State
- dp[i] = Fibonacci number at position i.

### Choices
- Calculate F(n-1)
- Calculate F(n-2)

### Recurrence
- F(n) = F(n-1) + F(n-2)

### Recursion Tree
- F(5) → F(4) + F(3)
- F(4) → F(3) + F(2)

### Overlapping Subproblems
- F(3) and F(2) are calculated multiple times.

### Base Case
- F(0) = 0
- F(1) = 1

## Time and Space Complexity
- Recursion Time: O(2^n)
- Recursion Space: O(n)
- Memoization Time: O(n)
- Memoization Space: O(n)
- Tabulation Time: O(n)
- Tabulation Space: O(n)

## Python Recursion

```python
def fib(n):
    if n <= 1:
        return n

    return fib(n - 1) + fib(n - 2)
```

## Python Tabulation

```python
def fib(n):
    if n <= 1:
        return n

    dp = [0] * (n + 1)
    dp[0] = 0
    dp[1] = 1

    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]

    return dp[n]
```

## One-Dimensional DP
- One changing variable: n
- Two previous states are used
- Repeated calculations are avoided
- Bottom-up table filling is used

## Python Memoization

```python
def fib(n):
    memo = {}

    def helper(n):
        if n <= 1:
            return n

        if n in memo:
            return memo[n]

        memo[n] = helper(n - 1) + helper(n - 2)
        return memo[n]

    return helper(n)
```

# Climbing Stairs DP Notes

## Problem Analysis

### Problem
Count the number of ways to reach step n.

### Recognition
At each step, you can move either 1 step or 2 steps.
Count all possible paths to reach the target.

### State
dp[i] = number of ways to reach step i.

### Choices
Take 1 step.
Take 2 steps.

### Recurrence
dp[i] = dp[i-1] + dp[i-2]

### Overlapping Subproblems
The same smaller states, such as dp[2] and dp[1], are reached repeatedly.

### Base Case
dp[0] = 1
dp[1] = 1

## Time and Space Complexity

### Recursion
Time: O(2^n)
Space: O(n)

### Memoization
Time: O(n)
Space: O(n)

### Tabulation
Time: O(n)
Space: O(n)

## Recursion Tree

For n = 4:
ways(4)
 / \
ways(3) ways(2)
 / \ / \
ways(2) ways(1) ways(1) ways(0)
 / \
ways(1) ways(0)

### Observation
ways(2) and ways(1) are calculated more than once.

## Tabulation Dry Run

For n = 5:
Step i: 0 1 2 3 4 5
Ways: 1 1 2 3 5 8

### Explanation
dp[0] = 1
dp[1] = 1
dp[2] = dp[1] + dp[0] = 2
dp[3] = dp[2] + dp[1] = 3
dp[4] = dp[3] + dp[2] = 5
dp[5] = dp[4] + dp[3] = 8

## Python Programs

### 1. Recursion

```python
def climb_stairs(n):
    if n == 0 or n == 1:
        return 1
    return climb_stairs(n - 1) + climb_stairs(n - 2)

print(climb_stairs(5))
```

### 2. Memoization (Top-Down DP)

```python
def climb_stairs(n):
    memo = {}

    def helper(n):
        if n == 0 or n == 1:
            return 1
        if n in memo:
            return memo[n]
        memo[n] = helper(n - 1) + helper(n - 2)
        return memo[n]

    return helper(n)

print(climb_stairs(5))
```

### 3. Tabulation (Bottom-Up DP)

```python
def climb_stairs(n):
    if n <= 1:
        return 1

    dp = [0] * (n + 1)
    dp[0] = 1
    dp[1] = 1

    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]

    return dp[n]

print(climb_stairs(5))
```

## Key Interview Takeaway

### 1D DP — Counting ways
State: Current stair number i.
Choices: Move 1 step or 2 steps.
Recurrence: Add the ways from both previous positions.
Base Case: One way to stand at step 0, and one way to reach step 1.

## Important Distinction from Fibonacci
The recurrence looks the same.
But the meaning of the state and the base case is different.
For Fibonacci, the sequence starts from 0 and 1.
For Climbing Stairs, the value at step 0 is 1 because there is one way to stay at the starting position.

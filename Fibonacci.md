PROBLEM	Given n, return the nth Fibonacci number. Sequence: 0, 1, 1, 2, 3, 5, 8...
RECOGNITION	Current answer depends on the previous two answers.
STATE	dp[i] = Fibonacci number at position i.
CHOICES	Calculate F(n-1) and F(n-2).
RECURRENCE	F(n) = F(n-1) + F(n-2)
RECURSION TREE	F(5) → F(4) + F(3); F(4) → F(3) + F(2)
OVERLAPPING	F(3) and F(2) are calculated multiple times.
BASE CASE	F(0) = 0, F(1) = 1.
RECURSION TIME	O(2ⁿ)
RECURSION SPACE	O(n)
MEMOIZATION TIME	O(n)
MEMOIZATION SPACE	O(n)
TABULATION TIME	O(n)
TABULATION SPACE	O(n)


**Python recusruion**

def fib(n):
    if n <= 1:
        return n

    return fib(n - 1) + fib(n - 2)

**Python Tabulation**

def fib(n):
    if n <= 1:
        return n

    dp = [0] * (n + 1)

    dp[0] = 0
    dp[1] = 1

    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]

    return dp[n]

**    One-dimensional DP: One changing variable (n), two previous states, repeated calculations, and bottom-up table filling.
**Python Memoization**

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

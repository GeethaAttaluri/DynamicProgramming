Cheat Sheet
Step	Explanation
PROBLEM	Count the number of ways to reach step n.
RECOGNITION	At each step, you can move either 1 or 2 steps. Count all possible paths.
STATE	dp[i] = number of ways to reach step i.
CHOICES	Take 1 step or take 2 steps.
RECURRENCE	dp[i] = dp[i-1] + dp[i-2]
OVERLAPPING	The same smaller states, such as dp[2] and dp[1], are reached repeatedly.
BASE CASE	dp[0] = 1, dp[1] = 1.
RECURSION TIME	O(2ⁿ)
RECURSION SPACE	O(n)
MEMOIZATION TIME	O(n)
MEMOIZATION SPACE	O(n)
TABULATION TIME	O(n)
TABULATION SPACE	O(n)

Recursion tree
For n = 4:
                  ways(4)
                 /       \
             ways(3)    ways(2)
             /    \      /   \
         ways(2) ways(1) ways(1) ways(0)
          /   \
      ways(1) ways(0)


Notice ways(2) and ways(1) are calculated more than once.
Tabulation dry run
For n = 5:
Step i	0	1	2	3	4	5
Ways	1	1	2	3	5	8

Explanation:
dp[0] = 1
dp[1] = 1

dp[2] = dp[1] + dp[0] = 2
dp[3] = dp[2] + dp[1] = 3
dp[4] = dp[3] + dp[2] = 5
dp[5] = dp[4] + dp[3] = 8


Python programs
1. Recursion
def climb_stairs(n):    if n == 0 or n == 1:        return 1    return climb_stairs(n - 1) + climb_stairs(n - 2)print(climb_stairs(5))  # 8



2. Memoization (Top-Down DP)
def climb_stairs(n):    memo = {}    def helper(n):        if n == 0 or n == 1:            return 1        if n in memo:            return memo[n]        memo[n] = helper(n - 1) + helper(n - 2)        return memo[n]    return helper(n)print(climb_stairs(5))  # 8



3. Tabulation (Bottom-Up DP)
def climb_stairs(n):    if n <= 1:        return 1    dp = [0] * (n + 1)    dp[0] = 1    dp[1] = 1    for i in range(2, n + 1):        dp[i] = dp[i - 1] + dp[i - 2]    return dp[n]print(climb_stairs(5))  # 8



Key interview takeaway
1D DP — Counting ways
- State: Current stair number i.
- Choices: Move 1 step or 2 steps.
- Recurrence: Add the ways from both previous positions.
- Base case: One way to stand at step 0 (do nothing), and one way to reach step 1.
Important distinction from Fibonacci: The recurrence looks the same, but the meaning of the state and

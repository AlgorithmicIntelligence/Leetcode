# 115. Distance Subsequences
----------------------
*__BFS solution__*

Input: S = "babgbag", T = "bag"

We can search the first char of __T__ whether it's exist in chars of __S__, and focus on possible solution.
```
          b   a   b   g   b   a   g
     
  b       |       |       |\
     a b g b a g gbag     ag\
  a  |       |     |      |\
   bgbag     g     g      g \
  g O  O     O     O      O\
```
<img src="https://github.com/AlgorithmicIntelligence/Leetcode/blob/main/115.DistanceSubsequences/leetcode115.jpg" width="900">

[**Cite**](https://leetcode.com/problems/distinct-subsequences/discuss/932043/DFS-greater-DP-Progression-with-Explanation-987)

*__BP solution__*

But we will find there are too many redundant computation, hence we can utilize BP solution.

__(1) First Aspect__
S = "rabbbit", T = "rabbit"
```
    T->
S   r a b b i t max 
  1 1 0 0 0 0 0  1
r 1 1 0 0 0 0 0  1
a 1 1 1 0 0 0 0  1
b 1 1 1 1 0 0 0  1
b 1 1 1 2 1 0 0  2
b 1 1 1 3 3 0 0  3
i 1 1 1 3 3 3 0  3
t 1 1 1 3 3 3 3  3
```
```
if S[i] == T[j]:
    // If the chars of S(0 ~ i-1) are matched with T(0 ~ j-1), the num of solution is dp[i-1][j-1], hence S[i] and T[j] make a pair. (dp[i][j] = dp[i-1][j-1])
    // If S(0 ~ i-1) are already matched with T(0 ~ j), the num of solution is dp[i-1][j], hence S[i] can be omitted. (dp[i][j] = dp[i-1][j])
    dp[i][j] =dp[i-1][j]+dp[i-1][j-1]
else:
    // If S(0 ~ i-1) are already matched with T(0 ~ j), the num of solution is dp[i-1][j], hence S[i] can be omitted. (dp[i][j] = dp[i-1][j])
    dp[i][j]=dp[i-1][j]
```

__(2) First Aspect__
```
  Ø r a b b b i t
Ø 1 1 1 1 1 1 1 1
r 0 1 1 1 1 1 1 1
a 0 0 1 1 1 1 1 1
b 0 0 0 1 2 3 3 3
b 0 0 0 0 1 3 3 3
i 0 0 0 0 0 0 3 3
t 0 0 0 0 0 0 0 3 
```

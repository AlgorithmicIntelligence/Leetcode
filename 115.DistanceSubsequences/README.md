# 115. Distance Subsequences
----------------------
*__BFS solution__

Input: S = "babgbag", T = "bag"

We can search the first char of __T__ whether it's exist in chars of __S__, and focus on possible solution.
'''
          b   a   b   g   b   a   g
     
  b       |       |       |\
     a b g b a g gbag     ag\
  a  |       |     |      |\
   bgbag     g     g      g \
  g O  O     O     O      O\
'''
<img src="https://github.com/AlgorithmicIntelligence/Leetcode/blob/main/115.DistanceSubsequences/leetcode115.jpg" width="900">


*__BP solution__

But we will find there are too many redundant computation. 

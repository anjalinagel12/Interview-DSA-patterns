# 🧠  Dynamic Programming Cheatsheet

This guide covers the most **frequently asked DP problems**, **core patterns**, and **must-know concepts** for interviews.

---

## 🔁 Core DP Patterns & Problems

| Core Concept                  | Must Know Keywords / Patterns                          | Top Problems (LeetCode)                          |
|------------------------------|---------------------------------------------------------|--------------------------------------------------|
| **1. 1D DP (Classic)**        | Recurrence, memoization, bottom-up                     | [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/), [746. Min Cost Climbing](https://leetcode.com/problems/min-cost-climbing-stairs/), [198. House Robber](https://leetcode.com/problems/house-robber/), [213. House Robber II](https://leetcode.com/problems/house-robber-ii/), [91. Decode Ways](https://leetcode.com/problems/decode-ways/) |
| **2. 2D DP / Grid DP**        | Matrix, directions, prefix sums                        | [64. Min Path Sum](https://leetcode.com/problems/minimum-path-sum/), [62. Unique Paths](https://leetcode.com/problems/unique-paths/), [63. Unique Paths II](https://leetcode.com/problems/unique-paths-ii/), [221. Maximal Square](https://leetcode.com/problems/maximal-square/), [72. Edit Distance](https://leetcode.com/problems/edit-distance/) |
| **3. DP on Subsequences**     | LCS, LIS, subsequence patterns                         | [1143. LCS](https://leetcode.com/problems/longest-common-subsequence/), [516. Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/), [300. LIS](https://leetcode.com/problems/longest-increasing-subsequence/), [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/) |
| **4. DP on Strings**          | Palindrome, partition, substring                       | [131. Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/), [647. Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/), [5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/), [10. Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/) |
| **5. DP on Trees**            | Postorder, subtree info return                         | [337. House Robber III](https://leetcode.com/problems/house-robber-iii/), [124. Max Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/), [543. Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/) |
| **6. Knapsack Variants**      | Weights, capacity, subset sum                         | [416. Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/), [494. Target Sum](https://leetcode.com/problems/target-sum/), [518. Coin Change II](https://leetcode.com/problems/coin-change-ii/), [322. Coin Change](https://leetcode.com/problems/coin-change/) |
| **7. Bitmask DP**             | Bitmask state, subset optimization                    | [847. Shortest Path Visiting All Nodes](https://leetcode.com/problems/shortest-path-visiting-all-nodes/), [688. Knight Probability](https://leetcode.com/problems/knight-probability-in-chessboard/), [1125. Smallest Sufficient Team](https://leetcode.com/problems/smallest-sufficient-team/) |
| **8. State Compression**      | Optimize dimensions                                    | [877. Stone Game](https://leetcode.com/problems/stone-game/), [188. Buy & Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/), [123. Best Time III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/), [309. Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/) |
| **9. Partition DP**           | k partitions, min/max cuts                            | [132. Palindrome Partitioning II](https://leetcode.com/problems/palindrome-partitioning-ii/), [312. Burst Balloons](https://leetcode.com/problems/burst-balloons/), [1000. Merge Stones](https://leetcode.com/problems/minimum-cost-to-merge-stones/), [1547. Min Cost to Cut a Stick](https://leetcode.com/problems/minimum-cost-to-cut-a-stick/) |
| **10. DP + Greedy Hybrid**    | Jump game, task scheduling                            | [55. Jump Game](https://leetcode.com/problems/jump-game/), [45. Jump Game II](https://leetcode.com/problems/jump-game-ii/), [134. Gas Station](https://leetcode.com/problems/gas-station/), [621. Task Scheduler](https://leetcode.com/problems/task-scheduler/) |

---

## 🔑 Core Concepts to Master

| Concept                    | Explanation |
|---------------------------|-------------|
| **Recurrence Relation**   | How current state depends on subproblems. Eg: `dp[i] = dp[i-1] + dp[i-2]` |
| **Memoization**           | Top-down recursion + cache using `lru_cache` or `dict`. |
| **Tabulation**            | Bottom-up DP using arrays, avoids recursion stack overflow. |
| **State Definition**      | Clearly define what each `dp[i]` or `dp[i][j]` represents. |
| **Base Case**             | Define and initialize correctly for all problems. |
| **Transition**            | Derive logic for how to go from previous states to current. |
| **Space Optimization**    | Convert 2D → 1D DP when only previous row/state is needed. |
| **Bitmasking in DP**      | Use bits to represent used/unavailable states in subsets. |
| **Prefix Sum / Difference**| Use to speed up range queries in DP. |

---

## 🧪 Practice Pack

| Difficulty      | Recommended Problems                                   |
|-----------------|--------------------------------------------------------|
| 🟢 **Warmup**    | [70](https://leetcode.com/problems/climbing-stairs/), [746](https://leetcode.com/problems/min-cost-climbing-stairs/), [198](https://leetcode.com/problems/house-robber/), [213](https://leetcode.com/problems/house-robber-ii/), [121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) |
| 🟡 **Intermediate** | [62](https://leetcode.com/problems/unique-paths/), [64](https://leetcode.com/problems/minimum-path-sum/), [91](https://leetcode.com/problems/decode-ways/), [1143](https://leetcode.com/problems/longest-common-subsequence/), [131](https://leetcode.com/problems/palindrome-partitioning/), [300](https://leetcode.com/problems/longest-increasing-subsequence/) |
| 🔴 **Advanced**  | [10](https://leetcode.com/problems/regular-expression-matching/), [132](https://leetcode.com/problems/palindrome-partitioning-ii/), [312](https://leetcode.com/problems/burst-balloons/), [1000](https://leetcode.com/problems/minimum-cost-to-merge-stones/), [688](https://leetcode.com/problems/knight-probability-in-chessboard/), [847](https://leetcode.com/problems/shortest-path-visiting-all-nodes/) |
| 🚨 **Google Repeats** | [198](https://leetcode.com/problems/house-robber/), [213](https://leetcode.com/problems/house-robber-ii/), [300](https://leetcode.com/problems/longest-increasing-subsequence/), [1143](https://leetcode.com/problems/longest-common-subsequence/), [221](https://leetcode.com/problems/maximal-square/), [322](https://leetcode.com/problems/coin-change/), [124](https://leetcode.com/problems/binary-tree-maximum-path-sum/), [309](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/), [1000](https://leetcode.com/problems/minimum-cost-to-merge-stones/) |

---

## 🧰 Debugging Tools

- ✍️ Draw the DP table (especially for 2D).
- 🔎 Dry-run transitions on small input.
- 🖨️ Add print statements to debug values.
- 🧠 Use `@lru_cache(maxsize=None)` for top-down memoization.

---

## ✅ Final Tips for  DP Interviews

- Clarify input constraints (length, values).
- Start with brute-force → optimize to DP.
- Explain **state**, **base case**, **transition**, and **space/time complexity** clearly.
- Code correctness is more important than premature optimization.
- Discuss follow-ups (space optimized, tabulation, etc.).

---

> ✨ **Pro Tip**: Practice writing clean, bug-free code within 20–30 minutes per DP problem. Time yourself like a real interview!

---

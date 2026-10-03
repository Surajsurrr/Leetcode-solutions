# 02. 3Sum

- **Platform:** [LeetCode](https://leetcode.com/problems/3sum/)
- **Difficulty:** Medium
- **Topics:** Array, Two Pointers, Sorting

---

## Problem Statement

Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

---

### Examples

**Example 1:**
- **Input:** `nums = [-1,0,1,2,-1,-4]`
- **Output:** `[[-1,-1,2],[-1,0,1]]`
- **Explanation:** 
  - `nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0`.
  - `nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0`.
  - `nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0`.
  - The distinct triplets are `[-1,0,1]` and `[-1,-1,2]`.
  - Notice that the order of the output and the order of the triplets does not matter.

**Example 2:**
- **Input:** `nums = [0,1,1]`
- **Output:** `[]`
- **Explanation:** The only possible triplet does not sum up to 0.

**Example 3:**
- **Input:** `nums = [0,0,0]`
- **Output:** `[[0,0,0]]`
- **Explanation:** The only possible triplet sums up to 0.

---

### Constraints

- $3 \le \text{nums.length} \le 3000$
- $-10^5 \le \text{nums}[i] \le 10^5$

---

## Approach (Used in `solution2.java`): Sorting + Two Pointers + HashSet

1. **Sort the Array:**
   - Sorting simplifies the problem and allows using the two-pointer technique to find pairs that sum to $-nums[i]$.
2. **Fix the First Element:**
   - Loop `i` from index `0` up to `nums.length - 3`.
   - Set two pointers: `left = i + 1` and `right = nums.length - 1`.
3. **Two-Pointer Search:**
   - Compute `sum = nums[i] + nums[left] + nums[right]`.
   - If `sum == 0`, add `[nums[i], nums[left], nums[right]]` to a `HashSet` (which automatically handles duplicate triplets).
   - If `sum < 0`, increment `left` to increase the total sum.
   - If `sum > 0` (or after checking `sum < 0`), decrement `right` to reduce the total sum.
4. **Return Result:**
   - Convert the `HashSet<List<Integer>>` into an `ArrayList<List<Integer>>` and return.

### Complexity Analysis

- **Time Complexity:** $O(n^2)$
  - Sorting takes $O(n \log n)$.
  - The outer loop runs $n$ times, and for each iteration, the two-pointer inner scan takes $O(n)$ time.
  - Overall time complexity is dominated by $O(n^2)$.
- **Space Complexity:** $O(k)$ (excluding output list, where $k$ is the number of unique triplets stored in the `HashSet`) + $O(\log n)$ to $O(n)$ auxiliary space used by sorting depending on the language implementation.

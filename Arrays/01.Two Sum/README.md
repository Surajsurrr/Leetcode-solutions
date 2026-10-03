# 01. Two Sum

- **Platform:** [LeetCode](https://leetcode.com/problems/two-sum/)
- **Difficulty:** Easy
- **Topics:** Array, Hash Table

---

## Problem Statement

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have ***exactly* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

---

### Examples

**Example 1:**
- **Input:** `nums = [2,7,11,15]`, `target = 9`
- **Output:** `[0,1]`
- **Explanation:** Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

**Example 2:**
- **Input:** `nums = [3,2,4]`, `target = 6`
- **Output:** `[1,2]`

**Example 3:**
- **Input:** `nums = [3,3]`, `target = 6`
- **Output:** `[0,1]`

---

### Constraints

- $2 \le \text{nums.length} \le 10^4$
- $-10^9 \le \text{nums}[i] \le 10^9$
- $-10^9 \le \text{target} \le 10^9$
- **Only one valid answer exists.**

---

## Approach: One-Pass Hash Table

1. Use a Hash Map to store elements visited so far along with their indices (`number -> index`).
2. Iterate through the array. For each element `nums[i]`:
   - Calculate its complement: `complement = target - nums[i]`.
   - Check if `complement` exists in the map:
     - If yes, return `[map.get(complement), i]`.
     - If no, add `nums[i]` and its index `i` into the map.
3. This guarantees finding the pair in a single pass.

### Complexity Analysis

- **Time Complexity:** $O(n)$ — We traverse the list containing $n$ elements only once. Each lookup in the hash table takes $O(1)$ on average.
- **Space Complexity:** $O(n)$ — The extra space required depends on the number of items stored in the hash table, which stores at most $n$ elements.

## 01. Count Subsets with Sum

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/perfect-sum-problem5633/1)

### Problem Description

**Task:** Given an array arr[] of non-negative integers and an integer target, the task is to count all subsets of the array whose sum is equal to the given target.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [5, 2, 3, 10, 6, 8], target = 10
```
- **Output:**
```text
3
```
- **Explanation:** The subsets {5, 2, 3}, {2, 8}, and {10} sum up to the target 10.

##### Example 2

- **Input:**
```text
arr[] = [2, 5, 1, 4, 3], target = 10
```
- **Output:**
```text
3
```
- **Explanation:** The subsets {2, 1, 4, 3}, {5, 1, 4}, and {2, 5, 3} sum up to the target 10.

##### Example 3

- **Input:**
```text
arr[] = [5, 7, 8], target = 3Output: 0
```
- **Explanation:** There are no subsets of the array that sum up to the target 3.

##### Example 4

- **Input:**
```text
arr[] = [35, 2, 8, 22], target = 0Output: 1
```
- **Explanation:** The empty subset is the only subset with a sum of 0.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n*target)
- **Expected Auxiliary Space Complexity:** O(n*target)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-10-07 19:34:16
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def perfectSum(self, arr, target):
        n = len(arr)
        # Memoization dictionary TLE se bachne ke liye
        memo = {}

        def backtrack(index, current_sum):
            if index == n:
                return 1 if current_sum == target else 0

            state = (index, current_sum)
            if state in memo:
                return memo[state]

            # 1. Element ko include karna
            pick = 0
            if current_sum + arr[index] <= target:
                pick = backtrack(index + 1, current_sum + arr[index])

            # 2. Element ko exclude karna
            not_pick = backtrack(index + 1, current_sum)

            memo[state] = pick + not_pick
            return memo[state]

        return backtrack(0, 0)
```

#### Solution 2 (Python)

- **Submitted:** 2026-10-07 19:31:48
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def perfectSum(self, arr, target):
        n = len(arr)
        # Memoization dictionary TLE se bachne ke liye
        memo = {}

        def backtrack(index, current_sum):
            if index == n:
                return 1 if current_sum == target else 0

            state = (index, current_sum)
            if state in memo:
                return memo[state]

            # 1. Element ko include karna
            pick = 0
            if current_sum + arr[index] <= target:
                pick = backtrack(index + 1, current_sum + arr[index])

            # 2. Element ko exclude karna
            not_pick = backtrack(index + 1, current_sum)

            memo[state] = pick + not_pick
            return memo[state]

        return backtrack(0, 0)
```

*Generated on: 10/7/2026, 7:34:33 PM*
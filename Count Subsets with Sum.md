class Solution:
    def perfectSum(self, arr, target):
        n = len(arr)
        memo = {}

        def backtrack(index, current_sum):
            if index == n:
                return 1 if current_sum == target else 0

            state = (index, current_sum)
            if state in memo:
                return memo[state]

            pick = 0
            if current_sum + arr[index] <= target:
                pick = backtrack(index + 1, current_sum + arr[index])

            not_pick = backtrack(index + 1, current_sum)

            memo[state] = pick + not_pick
            return memo[state]

        return backtrack(0, 0)

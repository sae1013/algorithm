```python
# dp 에 각 구간까지의 합을 저장한다.
class Solution:
    def findMaxAverage(self, nums: List[int], k: int) -> float:
        dp = [0] # dp : 각 구간 까지의 합. [0,5]
        sum = 0
        for num in nums :
            sum+=num
            dp.append(sum)
        ans = -10**8
        for i in range(len(dp)):
            if i+k < len(dp):
                diff = (dp[i+k]-dp[i])/k
                print(diff)
                ans = max(ans,diff)
        return ans
```
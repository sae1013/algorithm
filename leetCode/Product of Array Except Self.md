O(N)으로 풀이하는 방법
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        left = [0]*n
        total = 1
        for i in range(len(nums)):
            left[i] = total*nums[i]
            total = left[i]
        right = [0]*n
        total = 1
        for i in range(len(nums)-1,-1,-1):
            right[i] = total*nums[i]
            total = right[i]

        for i in range(len(left)):
            temp = 1
            if i-1 >=0 :
                temp*=left[i-1]
            if i+1 <= n-1 :
                temp*=right[i+1]
            nums[i] = temp
        return nums


```
O(N)
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        water = 0
        le = 0
        ri = len(height) - 1  # 8

        while le != ri:
            common_height = min(height[le], height[ri])
            water = max(water, common_height * (ri - le))

            if common_height == height[le]:
                le += 1
            else:
                ri -= 1
        return water

# 양끝에서 조여오면서, 최대값 높이 2개를 구한다. 그중 작은 높이값이 height가 된다.
# 작은높이를 한칸 씩 당긴다. le,ri 두개의 지표가 필요함.
```
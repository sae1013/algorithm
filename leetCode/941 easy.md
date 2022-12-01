O(N)
```python
class Solution:
    def validMountainArray(self, arr: List[int]) -> bool:
        max_val = max(arr)  # 이과정을 축약할 수 있음.
        max_idx = 0
        for i in range(len(arr)):
            if max_val == arr[i]:
                max_idx = i
                break

        if len(arr) < 3:
            return False
        if max_idx == len(arr) - 1 or max_idx == 0:
            return False

        ll, rr = max_idx, max_idx

        while ll > 0:
            if arr[ll - 1] >= arr[ll]:
                return False
            ll -= 1

        while rr < len(arr) - 1:
            if arr[rr] <= arr[rr + 1]:
                return False
            rr += 1
        return True
```
더 간결해진 코드
```python
class Solution:
    def validMountainArray(self, arr: List[int]) -> bool:
        i = 0
        N = len(arr)

        if len(arr) < 3 :
            return False

        while i+1 < N and arr[i] < arr[i+1] :
            i+=1
        if i == N-1 or i == 0 :
            return False

        while i+1 < N and arr[i] > arr[i+1]:
            i+=1

        return i == N-1
```
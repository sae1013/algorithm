### 문제접근

힙을 이용한다.
여기서 공간복잡도를 최소화하기위해, 힙의 노드수는 K개로 유지할 수 있다.

```python
import heapq
from collections import deque

class Solution(object):
    def topKFrequent(self, nums, k):
      heap = []
      hash_map = {}
      answer = deque()

      for num in nums:
        try:
          hash_map[num]+=1
        except:
          hash_map[num] = 1 

      for key,v in hash_map.items(): #
        heapq.heappush(heap,[v,key])
        if len(heap) > k:
          heapq.heappop(heap)

      while heap:
        v,k = heapq.heappop(heap)
        answer.appendleft(k)
      return list(answer)
```

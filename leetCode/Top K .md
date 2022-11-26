```phthon
import heapq
class Solution:
    def topKFrequent(self, nums: List[int], l: int) -> List[int]:
        hashmap= {}
        for num in nums :
            if num in hashmap :
                hashmap[num] +=1
            else:
                hashmap[num] = 1
        q = []
        ans = []
        for k,v in hashmap.items():
            heapq.heappush(q,[-v,k])

        for _ in range(l):
             v,k= heapq.heappop(q)
             ans.append(k)
        return ans
```
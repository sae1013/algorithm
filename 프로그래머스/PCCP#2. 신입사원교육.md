단순히 최소힙을 사용해서, 계산하면 되는 문제
```python
import heapq
def solution(ability, number):
    heapq.heapify(ability)
    for _ in range(number):
        a = heapq.heappop(ability)
        b = heapq.heappop(ability)
        heapq.heappush(ability,a+b)
        heapq.heappush(ability,a+b)
    return sum(ability)
```
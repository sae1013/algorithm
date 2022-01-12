### 접근방법
파라매트릭서치를 통해서 최적화 하는 문제였다.
O(logN)으로 풀어야하는 문제이므로 사실 보자마자 이분탐색이 떠올랐다.

```python
def leftBound(n,times): # target 60분 이라면, times 를 다 더해서, 
    start = 1
    end = times[len(times)-1] * n
    answer = 0
    while start <= end : 
        mid =(start+end) // 2 
        temp = 0
        for time in times:
            temp+= mid//time
        if temp >= n: # 왼쪽 탐색하기
            end = mid-1
            answer = mid
        else:
            start = mid+1 # 오른쪽 탐색하기
    return answer
        
        
def solution(n, times):
    times.sort() # max_time
    return leftBound(n,times)
```

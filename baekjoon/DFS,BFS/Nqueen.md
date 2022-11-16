```python
import math
import sys
sys.setrecursionlimit(5000)
# 대각선 유무 확인.
def check(q_col,q_row):
    for i in range(q_col):
        dx = abs(q_col-i)
        dy = abs(q_row-col[i])
        if dx == dy :
            return False
    return True

def dfs(cnt): # 처음엔 0 이들어온다.
    global ans
    if cnt == n: # 모두 선택되었을때
        ans+=1
        return

    for i in range(n): # 0행 ~ 7행
        if visit[i] == 0 and check(cnt,i): # 행, 열
            visit[i] = 1  # 행 방문처리
            col[cnt] = i
            dfs(cnt+1)
            visit[i] = 0

n = int(input())
col = [-1]*n
visit = [0]*n
ans = 0
dfs(0)
print(ans)
```

시간 복잡도를 N^N 에서 -> N! 으로 줄일수 있다. 즉, 순열문제로 바뀐다.


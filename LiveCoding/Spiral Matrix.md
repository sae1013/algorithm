 1
2 3

```python
from collections import deque
# 시간복잡도 : N^2
# 공간복잡도 : N^2
def bfs(y,x):
    q = deque()
    q.append((y, x))
    answer = []
    visit[y][x] = 1
    d = 0
    while q :
        y,x = q.popleft()
        ny,nx = y+dy[d],x+dx[d]
        answer.append(arr[y][x])
        if 0 > ny or ny >=3 or 0 > nx or nx >= 3 or visit[ny][nx]:
            d = (d+1)%4
            ny, nx = y + dy[d], x + dx[d]
        if visit[ny][nx] == 0:
            q.append((ny,nx))
            visit[ny][nx] = 1
    return answer

arr = [[1,2,3],[4,5,6],[7,8,9]]
# 동 , 남, 서 , 북
dy = [0,1,0,-1]
dx = [1,0,-1,0]

visit = [ [0]* len(arr[0]) for _ in range(len(arr)) ]

print(bfs(0,0))

```

```python
# 1 2 3
# 4 5 6
# 7 8 9
# 시간복잡도 : O(N^2) 공간복잡도 O(1)
arr = [[1,2,3],[4,5,6],[7,8,9]]

top = 0
left = 0
bottom = len(arr)-1
right = len(arr[0])-1
ret = []
cnt = 0
while left <= right and top <= bottom :
    #좌측탑 -> 우측탑

    for i in range(left,right+1):
        ret.append(arr[top][i])
    top+=1

    #우측탑 -> 우측바텀
    for i in range(top,bottom+1):
        ret.append(arr[i][right])
    right-=1

    # 우측 바텀 -> 좌측 바텀
    for i in range(right,left-1,-1):
        ret.append(arr[bottom][i])
    bottom-=1

    # 좌측바텀 -> 좌측 탑
    for i in range(bottom,top-1,-1):
        ret.append(arr[i][left])
    left+=1

print(ret)
```

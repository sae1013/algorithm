백준 벽부수고 이동하기 문제랑 유사함
N = 1000 ,M =1000 이므로
BFS로 O(NM)으로 풀어야함 DFS로 풀면 최적화를 엄청 잘해야함
그리고 최종 도달하는 지점이 최솟값인지 보장하지않기때문에,
매번 끝 노드에 도달할 때마다 값을 갱신해줘야함

```python
from collections import deque

def bfs(y,x,z,n,m,board,visit,dp):
    dy = [0,-1,0,1]
    dx = [-1,0,1,0]
    q= deque()
    q.append([y,x,z])
    visit[z][y][x] = 1
    while q:
        y,x,z = q.popleft()
        for i in range(4):
            ny = dy[i]+y
            nx = dx[i]+x
            ny2 = dy[i]*2+y
            nx2 = dx[i]*2+x
            if z == 0 :
                if 0<=ny< n and 0<=nx<m and board[ny][nx] and visit[z][ny][nx] == 0:
                    q.append([ny,nx,z])
                    visit[z][ny][nx] = 1
                    dp[z][ny][nx] = dp[z][y][x] + 1

                elif 0<=ny2< n and 0<=nx2<m and board[ny2][nx2] and visit[z+1][ny2][nx2] == 0:
                    #ny,nx가 2배가된다.
                    q.append([ny2,nx2,z+1])
                    visit[z+1][ny2][nx2] = 1
                    dp[z+1][ny2][nx2] = dp[z][y][x] + 1

            elif z == 1:
                if 0<=ny< n and 0<=nx<m and board[ny][nx] and visit[z][ny][nx] == 0:
                    q.append([ny,nx,z])
                    visit[z][ny][nx] = 1
                    dp[z][ny][nx] = dp[z][y][x] + 1


def solution(m, n, hole):
    board = [[1]*m for _ in range(n)]
    visit = [ [[0]*m for _ in range(n)] for _ in range(2)]
    dp = [ [[-1]*m for _ in range(n)] for _ in range(2)]
    dp[0][0][0] = 0
    for x,y in hole:
        board[y-1][x-1] = 0

    bfs(0,0,0,n,m,board,visit,dp)
    ans = min(dp[0][n-1][m-1],dp[1][n-1][m-1])
    if ans == -1:
        return max(dp[0][n-1][m-1],dp[1][n-1][m-1])
    else:
        return min(dp[0][n-1][m-1],dp[1][n-1][m-1])
print(solution(5,4,[[1, 4], [2, 1], [2, 2], [2, 3], [2, 4], [3, 3], [4, 1], [4, 3], [5, 3]]))
```
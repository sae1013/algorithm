내리막길
백트래킹 만 쓰면 안되고 DP 랑 같이 써야하는데, 자주 응용되는 내용일것같다
```python
import sys
sys.setrecursionlimit(10**7)
def dfs(y,x):
    global dp

    if y == n-1 and x == m-1 :
        return 1
    if dp[y][x] != -1 :
        return dp[y][x]
        # 이미 갯수 가 담겨있는경우
    dp[y][x] = 0
    for i in range(4):
        ny,nx = y+dy[i],x+dx[i]
        if(0<=ny<n and 0<=nx<m and board[y][x]> board[ny][nx]):
            dp[y][x]+=dfs(ny,nx)
    return dp[y][x]



dy = [0,-1,0,1]
dx = [-1,0,1,0]
n, m = map(int,input().split())
board = []

dp = [[-1]*m for _ in range(n)]
cnt = 0
for i in range(n):
    board.append(list(map(int,input().split())))
dfs(0,0)
print(dp[0][0])
```
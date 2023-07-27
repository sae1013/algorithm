```python
# 여러번 방문횟수에 제한은 없으나, G에 딱 도착한것을 어떻게 수치화해야하나? 
# 예를들어 현재가 . 이고 다음 
# 어렵다. 쭉 미끄러져야하고, 탐색하다가 다음이 D 혹은 벽이고, 자신이 G이면 자기 방문 누적횟수를 출력.G는중복 방문을 허용해야함.
# 나머지는 중복방문 허용 X
from collections import deque
def bfs(y,x,visit,board):
    dy = [0,0,-1,1]
    dx = [1,-1,0,0]
    q = deque()
    q.append([y,x])
    visit[y][x] = 1
    
    while q:
        y,x = q.popleft()
        for i in range(4):
            ny = y+dy[i]
            nx = x+dx[i]
            while 0<=ny<len(board) and 0<=nx<len(board[0]) and board[ny][nx] != 'D':
                ny +=dy[i]
                nx +=dx[i]
            ny = ny-dy[i]
            nx = nx-dx[i]
            
            if visit[ny][nx] == 0 :
                visit[ny][nx] = visit[y][x] + 1
                q.append([ny,nx])
                
def solution(board):
    visit = [[0]*len(board[0]) for _ in range(len(board))]
    ty,tx = 0,0
    for i in range(len(board)):
        for j in range(len(board[0])):
            if board[i][j] == 'R':
                bfs(i,j,visit,board)
            if board[i][j] == 'G':
                ty,tx = i,j 
    if visit[ty][tx] == 0 :
        return -1
    else:
        return visit[ty][tx]-1
```

### 접근방법
DFS 이지만, 노드를 어떻게 잡을까 잠시 생각했다
입력이 	[[1, 1, 0], [1, 1, 0], [0, 0, 1]] 와 같을때, 
[1,1,0] -> 0번노드, [1, 1, 0] -> 1번노드 ... 와 같이 통째로 잡으면 된다.
그 외에는 일반적인 완전탐색 이었다.

```python
def dfs(node,visit,computers):

    if visit[node]:
        return
    
    visit[node] = 1
    for i in range(len(computers)):
        if computers[node][i]:
            dfs(i,visit,computers)
    
def solution(n, computers):
    
    global visit
    cnt = 0
    visit = [0]*n
    for i in range(n):
        if not visit[i]:
            dfs(i,visit,computers)
            cnt+=1
    return cnt
```


```python
from collections import deque
def bfs(graph,visit,node):
    q = deque()
    visit[node] = 1
    q.append(node)
    while q :
        node = q.popleft()
        for next_node in graph[node]:
            if not visit[next_node]:
                visit[next_node] = visit[node] + 1
                q.append(next_node)
    
def solution(n, roads, sources, destination):
    graph = [[] for _ in range(n+1)]
    for a,b in roads :
        graph[a].append(b)
        graph[b].append(a)
    
    ans = []
    visit = [0]*(n+1)
    bfs(graph,visit,destination)
    for x in sources:
        ans.append(visit[x]-1)
    return ans
 # destination에서 각 source로 가는 최단거리를 구한다
 # O(V)
```

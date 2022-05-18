```python
import sys
import copy
from collections import deque
input = sys.stdin.readline

def poly():
    global N,K,graph,depth,time,cache
    q = deque()

    for i in range(1,N+1):
        if depth[i] == 0:
            q.append(i)

    while q:
        curnode = q.popleft()
        for i in graph[curnode]:
            depth[i]-=1
            cache[i]= max(cache[curnode]+time[i], cache[i])
            if depth[i] == 0:
                q.append(i)

T = int(input())

for _ in range(T):
    N,K = map(int,input().split())
    graph = [[] for _ in range(N+1)]
    depth = [0]*(N+1)
    time = [0]+list(map(int,input().split()))
    cache= copy.copy(time)

    for i in range(K):
        a,b = map(int,input().split())
        graph[a].append(b)
        depth[b]+=1
    target = int(input())

    poly()
    print(cache[target])

```
import sys
from collections import deque
import copy
input = sys.stdin.readline
def typology():
    while q : # 처리되어야할 노드들이 먼저 들어온다. depth가 0 인놈들이 먼저 들어옴
        cur = q.popleft()
        for next in graph[cur] :
            depth[next]-=1
            cache[next] = max(cache[next], time[next]+cache[cur])
            if depth[next] == 0 :
                q.append(next) # 다음 노드를 삽입한다.

t = int(input())

for _ in range(t):
    n,m = map(int,input().split())
    depth = [0]*(n+1)
    graph = [[] for _ in range(n+1)]
    q = deque()
    time = [0]+list(map(int,input().split()))
    cache = copy.copy(time)

    for _ in range(m):
        a,b = map(int,input().split())
        depth[b] += 1
        graph[a].append(b)
    k = int(input())
    for i in range(1,n+1):
        if depth[i] == 0 :
          q.append(i)
    typology()
    print(cache[k])




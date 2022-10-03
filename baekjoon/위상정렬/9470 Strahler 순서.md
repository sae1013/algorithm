```python
import sys
from collections import deque
import copy
input = sys.stdin.readline

def typology():
    while q:
        cur = q.popleft()
        # 자신의 노드 누적값을 판단하여 뎁스를 정한다.
        max_dp = 1
        if len(dp[cur]) != 0 :
            max_dp = max(dp[cur])

        cnt = 0
        for i in range(len(dp[cur])) :
            if dp[cur][i] == max_dp:
               cnt+=1
        if cnt > 1:
            node_depth[cur] = max_dp+1
        else:
            node_depth[cur] = max_dp

        for next in graph[cur] :
            depth[next]-=1
            dp[next].append(node_depth[cur]) # 자신의 누적값을 추가한다.
            if depth[next] == 0 :
                q.append(next)

t= int(input())

for tc in range(t):
    k, n, m = map(int, input().split())
    graph = [[] for _ in range(n + 1)]
    depth = [0] * (n + 1)

    dp = [[] for _ in range(n + 1)]
    node_depth = [1] * (n + 1)

    for _ in range(m):
        a,b = map(int,input().split())
        graph[a].append(b)
        depth[b]+=1
    q = deque()
    for i in range(1,n+1):
        if depth[i] == 0:
            q.append(i) # 해당노드 삽입

    typology()
    print(tc+1, max(node_depth))
```
#노드별로 해당지점까지 도달하는 depth를 저장하는 배열이 필요하다.
# 이전 노드에서, 해당지점에 depth 배열에 삽입한다.
# 이전 노드에서, 가장 큰값과 갯수를 찾고 자신의 depth를 결정한다.
### 접근방법
DFS 깊이탐색을 해야하는 문제이다.
깊이탐색을하면, 경로를 추적할 수 있는데, 이때 중요한점은 백트래킹을 사용해야한다.
왜냐하면, 방문하는 순서에따라 전체순회가 불가능한 경우가 생기기 때문이다.
따라서, 방문을 하다가 전체방문이 이뤄지지않은상태에서 다음 방문지를 찾을 수 없는경우는 , 백트래킹으로 경로를 빼주어야하고 방문처리도 취소해주어야한다.

```python
import copy

answer = []
def dfs(target_node,tickets,visit,temp):
    global answer
    
    for i in range(len(tickets)):
        if tickets[i][0] == target_node: #타겟노드를 찾는다.
            if not visit[i]:
                visit[i] = True
                temp.append(target_node) # 현재 타겟노드 방문처리
    
                dfs(tickets[i][1],tickets,visit,temp)
        
                visit[i] = False 
                temp.pop()

    if sum(visit) == len(visit) and len(answer)==0: # 처음으로 정답이 나온경우 출력.
        temp.append(target_node)
        answer = copy.copy(temp)
        
def solution(tickets):
    global answer
    temp = []
    visit = [0]*len(tickets)
    tickets.sort(key = lambda x : (x[0],x[1]) )
    dfs('ICN',tickets,visit,temp)
    return answer
```

### 문제
이진트리인지 아닌지를 확인하는 문제.

입력이 다음과 같다. ["(1,2)", "(2,4)", "(5,7)", "(7,2)", "(9,5)"] 

ex) "(1,2)" 요소인 경우는, 1이 자식노드, 2가 부모노드를 의미한다.

따라서 정규식을써서 파싱을 먼저 진행했다. 그리고, 노드가 총 몇개인지, 노드번호가 몇인지 정해지지 않았기때문에 해시-맵을 이용하여 노드간의 간선관계를 저장하였다.

```python
import re
# 노드셋 필요.
isCycle = False

def dfs(node,visit_set,graph_map):
  global isCycle
  if node in visit_set: # 중복방문인경우 
    isCycle = True
    return
  
  visit_set.add(node)
  for next_node in graph_map[node]:
    # 다음 노드가 있을 때만 깊이 탐색.
    if next_node in graph_map:
      dfs(next_node,visit_set,graph_map)
    else:
      visit_set.add(next_node) # 다음 노드 방문 처리

def ArrayChallenge(strArr):
  
  node_set = set()
  child_set = set()
  visit_set = set()
  graph_map = {}
  
  input_arr = [] 
  for string in strArr:
    numbers = list(map(int,re.findall(r'\d+',string)))
    input_arr.append(numbers)
  
  for ele in input_arr:
    child = ele[0]
    parent = ele[1]
    node_set.add(child)
    node_set.add(parent)
    child_set.add(child)

    if parent in graph_map:
      graph_map[parent].append(child)
    else:
      graph_map[parent] = [child]

  for v in graph_map.values():
    if len(v)> 2 :
      return 'false'
      
  root_set = node_set.difference(child_set)
  if len(root_set) > 1:
    return 'false'

  root_node = root_set.pop()
  
  dfs(root_node,visit_set,graph_map)

  if isCycle:
    return 'false'
  if len(visit_set) == len(node_set):
    return 'true'

print(ArrayChallenge(["(1,2)", "(2,4)", "(5,7)", "(7,2)", "(9,5)"]))


```

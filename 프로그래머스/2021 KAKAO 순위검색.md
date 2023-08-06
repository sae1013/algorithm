```python
import itertools
import bisect
import collections

def solution(info, queries):
    query_map = dict()
    for infomation in info :
        condition = infomation.split()[:-1]
        score = int(infomation.split()[-1])
        for i in range(5): # 조합의 갯수. 
            indices_combi = list(itertools.combinations([0,1,2,3],i))
            for indices in indices_combi :
                copy_condition = condition.copy()
                for idx in indices:
                    copy_condition[idx] = '-' #     
                key = "".join(copy_condition)
                if key in query_map :
                    query_map[key].append(score)
                else:
                    query_map[key] = [score]
    
    for k,v in query_map.items() :
        query_map[k] = sorted(v)
    
    # bisect        
    ans = []
    for query in queries :
        query = query.split(' and ')
        score = int((query[-1].split())[-1])
        query[-1] = (query[-1].split())[0]
        query_key = "".join(query)
        info_list = []
        if query_key in query_map:
            info_list = query_map[query_key]
        idx = bisect.bisect_left(info_list,score)
        ans.append(len(info_list) - idx)
    return ans 
        
```

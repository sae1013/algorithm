선분으로 구체화 할 수 있다.
그다음 겹치는 구간의 최대갯수를 세어주면 되는데 , 이부분이 병목지점이 되지않도록 해야한다 .
백준 최대 클리크 문제와 유사
```python
from collections import deque
def solution(menu, order, k):
    st = []

    for i in range(len(order)):
        if not st:
            st.append([i*k,i*k + menu[order[i]]])
            continue
        if st[-1][1] >= i*k: # 바로 다음주문을 실행
            st.append([i*k,st[-1][1]+menu[order[i]] ])
        else: # 기다렸다가 다음주문을 실행.
            st.append([i*k,i*k+menu[order[i]]])

    q = []
    cnt = 0
    ans = 0
    for x in st: # st = [10,20]
        q.append([x[0],1]) # 1 열림
        q.append([x[1],0]) # 0 닫음 .
    q = sorted(q,key = lambda x:(x[0],x[1] ))

    while q :
        t,o = q.pop(0)
        if o == 1:
            cnt+=1
        else:
            cnt-=1
        ans = max(ans,cnt)
    return ans


```
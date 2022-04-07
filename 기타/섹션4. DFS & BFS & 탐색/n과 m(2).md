```python
import sys

def dfs(i) :
    if i == m:
        for i in range(len(ans)):
            if ans[i] :
                print(ans[i],end=" ")
        print()
        return
    for num in range(1,n+1):
        if ch[num] == 0 and num > ans[i-1]:
            ans[i] = num
            ch[num] = 1  # 해당 숫자 방문
            dfs(i + 1)
            ch[num] = 0

n,m = map(int,input().split()) # n 은 자연수 , m 은 뽑으려는 갯수
ch = [0] * (n+1)
ans = [0]*(n)

dfs(0)
```
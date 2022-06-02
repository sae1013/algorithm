```python
import sys

sys.setrecursionlimit(5000)


def check(cur_col):
    global N
    global arr

    for i in range(0, cur_col):  # 이전에 놓은 말들과 비교.
        if arr[i] == arr[cur_col] or abs(arr[i] - arr[cur_col]) == abs(i - cur_col):
            return False
    return True


def dfs(cur_col):
    global arr
    global N
    global ans

    if cur_col == N:
        ans += 1
        return

    for i in range(N):  # 전체 행을 순회
        arr[cur_col] = i  # 일단 퀸을 배치하고 놓을 수 있는지 확인.
        if check(cur_col):
            dfs(cur_col + 1)

arr = [0] * 15
ans = 0
N = int(input())

dfs(0)
print(ans)

```
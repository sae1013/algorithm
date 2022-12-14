```python
# 각 라인에서 가장 작ㅇ느수를 더해가면서 내려간다. 바로아래, 대각선 위치로만 내려갈 수있다.
# 점화식 dp[i][j] = max(dp[i-1][j],dp[i-1][j-1],dp[i-1][j+1])
class Solution:
    def minFallingPathSum(self, matrix: List[List[int]]) -> int:
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                if i > 0 and j >0 and j != len(matrix[0])-1: # i가 2번째 줄 이상이고, j도 2번째줄 이상일때 맨마지막요소가 아닐때
                    matrix[i][j] = min(matrix[i-1][j-1],matrix[i-1][j],matrix[i-1][j+1]) + matrix[i][j]
                    continue
                if i > 0 and j == 0: # 첫번째 요소일때
                    matrix[i][j] = min(matrix[i-1][j],matrix[i-1][j+1]) + matrix[i][j]
                    continue
                if i>0 and j == len(matrix[0])-1 :
                    matrix[i][j] = min(matrix[i-1][j-1],matrix[i-1][j])+ matrix[i][j]
        return(min(matrix[-1]))
```
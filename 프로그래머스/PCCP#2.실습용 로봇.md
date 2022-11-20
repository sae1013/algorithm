단순 시뮬레이션 문제
```python

def solution(command):
    dy = [1,0,-1,0] #북 동 남 서
    dx = [0,1,0,-1]

    cur_d = 0 # 초기위치 북 오른쪽회전 -> +1 왼쪽회전 -> -1
    y,x = 0,0
    for com in command :
        if com =='R':
            cur_d = (cur_d+1)%4
        elif com =='L':
            cur_d = (cur_d-1)%4
        elif com =="G":
            y = dy[cur_d]+y
            x = dx[cur_d]+x
        elif com =="B":
            y = -dy[cur_d]+y
            x = -dx[cur_d]+x
    return [x,y]


solution("GRGLGRG")
```
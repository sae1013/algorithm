문해력이 부족한가... 문제가 이해가 되지않을때가 있네.  
TC: O(N^2) N: 로그배열 길이


```python
def trans_hms_sec(hms):
    hms = hms.split(':')
    h_sec = int(float(hms[0])*3600*1000)
    m_sec = int(float(hms[1]) * 60 * 1000)
    s_sec = int(float(hms[2])*1000)
    return h_sec+m_sec+s_sec

def trans_start_end(time_str):
    split_arr = time_str.split(" ")
    time_str = split_arr[1]
    delta_sec = int(float(split_arr[2][:-1])*1000)
    end_sec = trans_hms_sec(time_str)
    return [end_sec-delta_sec+1,end_sec]

def get_request_cnt(time,timeline):
    start = time
    end = time+999
    cnt = 0
    for i in range(len(timeline)):
        if timeline[i][0] <= end and timeline[i][1] >=start :
            cnt+=1
    return cnt

def solution(lines):
    timeline = []
    for line in lines :
        timeline.append(trans_start_end(line))
    ans = 0
    for start,end in timeline : # 기준
        ans = max(ans,get_request_cnt(start,timeline))
        ans = max(ans,get_request_cnt(end,timeline))
            
    return ans
```

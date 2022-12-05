coder byte
```python
from collections import Counter
def MinWindowSubstring(strArr):
  str = strArr[0]

  hashmap = Counter(strArr[1])
  hashmap_input = {}
  for char in str :
    hashmap_input[char] = 0

  ll = 0
  rr = 0
  min_len = 10**8 # substring의 길이.
  ans = ""
  cnt = len(hashmap) # answer 단어의 갯수
  cur_cnt = 0

  while ll <= rr and rr < len(strArr[0]): # 서브스트링을 포함하지않으면 rr 증가, 서브스트링을 포함하면 ll 증가
    if cur_cnt < cnt :
      hashmap_input[str[rr]] +=1
      if str[rr] in hashmap and hashmap_input[str[rr]] == hashmap[str[rr]] :
        cur_cnt+=1
    rr+=1

    # 갯수가 같으면, 왼쪽 인덱스를 감소 시켜 갑니다. abcde
    while cur_cnt == cnt : # 정답을 체크해준다,
      # substring 저장
      if rr-ll < min_len :
        min_len = rr-ll
        ans = str[ll:rr]

      hashmap_input[str[ll]]-=1
      if str[ll] in hashmap and hashmap_input[str[ll]] < hashmap[str[ll]] :
        cur_cnt-=1
      ll+=1
  return ans



# keep this function call here
print(MinWindowSubstring(input()))
```
시간복잡도 : O(N*K) N: 배열의 길이 , K : 요소의 문자열 길이 (정렬)
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        hashMap = {}
        for str in strs:
            temp = "".join(sorted(str))
            if temp in hashMap :
                hashMap[temp].append(str)
            else:
                hashMap[temp] = [str]
        ans = []
        for k,v in hashMap.items() :
            ans.append(v)
        return ans
```
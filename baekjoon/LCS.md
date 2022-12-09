```python
# # prev = text
# # 공백은
# # def isUnique(str): # 양 문자열 끝 은 공백으로 치지안흔ㄴ다.
# #     ret = ""
# #     space = 0
# #     for i in range(len(str)):
# #        if str[i] == " ":
# #            space+=1
# #        else:
# #            # add Space,
# #            if ret == "":
# #                space = 0
# #            for j in range(space): # 이 과정을 거치지 않도록.
# #                ret+="%20"
# #            space = 0
# #            ret+=str[i]
# #     return ret
# #
# # print(isUnique("Mr John Smith"))
# # print(isUnique("Mr John Smith    "))
# # print(isUnique("   abc "))
# print('a'.lower.is('a'))

def makeCommonSubsequence(arr,text1,text2):
    col = len(arr[0])
    row = len(arr)
    i,j= row-1,col-1
    answer= ""
    while 0<= i < row and 0<=j < col and arr[i][j] !=0 :
        if arr[i-1][j-1]+1 == arr[i][j] and text1[i-1] == text2[j-1] : # 대각선 수가 같고, 해당 글자가 같을때
            answer= text1[i-1]+answer

        if arr[i - 1][j] >= arr[i][j - 1]:
            i -= 1
        else:
            j -= 1
    return answer

def longestCommonSubsequence(text1, text2) : # 대각선으로 올라가되, 문자열이 같은경우만 더한다.
    dp = [[0] * (len(text2) + 1) for _ in range(len(text1) + 1)]
    for i in range(1, len(text1) + 1):
        for j in range(1, len(text2) + 1):
            if text1[i - 1] == text2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
    for i in range(len(dp)):
        for j in range(len(dp[0])):
            print(dp[i][j],end=" ")
        print()
    return dp

text1,text2 = "abcde","ace"
dp = longestCommonSubsequence(text1,text2)

longest_common_string = makeCommonSubsequence(dp,text1,text2)
print(longest_common_string)


```
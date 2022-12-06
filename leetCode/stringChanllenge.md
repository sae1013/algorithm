# 베어로보틱스
1번문제
```python
def StringChallenge(strParam):
    key1 = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine']
    key2 = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']
    numberMap = dict(zip(key1, key2))
    numberToStrMap = dict(zip(key2, key1))

    temp = ""  # 문자열 임시저장
    num_str = ""  # 숫자문자 합치는 문자열
    num_st = []  # 문자열 스택
    oper_st = []  # 연산자 스택

    for char in strParam:
        temp += char
        if temp in numberMap:
            num_str += numberMap[temp]
            temp = ""
        elif temp == "plus":
            num_st.append(int(num_str))
            oper_st.append('+')
            num_str = ""
            temp = ""

        elif temp == "minus":
            num_st.append(int(num_str))
            oper_st.append('-')
            num_str = ""
            temp = ""
    num_st.append(int(num_str))

    # Calculate
    oper_st = oper_st[::-1]
    num_st = num_st[::-1]
    print(oper_st,num_st)
    while oper_st:
        oper = oper_st.pop()
        num1 = num_st.pop()
        num2 = num_st.pop()
        if oper == "+":
            num_st.append(num1 + num2)
        else:
            num_st.append(num1 - num2)

    total = num_st.pop()  # total 은 number형

    answer = ""
    for char in str(total):
        if char == '-':
            answer += 'negative'
        else:
            answer += numberToStrMap[char]

    return answer


# keep this function call here
print(StringChallenge(input()))
```

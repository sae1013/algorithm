```python
def MathChallenge(strParam):
  st = []
  str_arr = strParam.split()
  for char in str_arr:
    if char == '+' or char =='-' or char == '*' or char =='/':
      a = st.pop()
      b = st.pop()
      if char =='+':
        st.append(a+b)
      elif char =='-':
        st.append(a-b)
      elif char =='*':
        st.append(a*b)
      elif char =='/':
        st.append(b//a)
    else:
      st.append(int(char))
  
  return st.pop()

print(MathChallenge(input()))

```

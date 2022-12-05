```python
class MinStack:

    def __init__(self):
        self.st = []
        self.minst = []

    def push(self, val: int) -> None:
        if len(self.st) == 0 :
            self.st.append(val)
            self.minst.append(val)
        else:
            minval = min(self.minst[-1],val)
            self.st.append(val)
            self.minst.append(minval)


    def pop(self) -> None:
        if self.st:
            self.minst.pop()
            return self.st.pop()

    def top(self) -> int:
        if self.st:
            return self.st[-1]

    def getMin(self) -> int:
        if self.minst:
            return self.minst[-1]
```
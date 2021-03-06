# **스택으로 큐 구현**

## 작성자
[![tdm1223](https://avatars1.githubusercontent.com/u/21440957?s=100&v=4)](https://github.com/tdm1223)

## 스택으로 큐 구현하기
- 2개의 스택을 이용하여 구현한다.
![stackToQueue](https://user-images.githubusercontent.com/21440957/63852102-84cf3d00-c9d2-11e9-91ae-d232fc9a53f1.png)

### 1. Enqueue(삽입)
1) 첫 번째 스택인 a에 추가만 하면 된다.

### 2. Dequeue(제거)
1) 두 번째 스택인 b가 비어있지 않다면 b에 있는 값을 제거(반환) 하면 된다.
2) 두 번째 스택인 b가 비었다면 첫 번째 스택인 a가 빌 때까지 a를 pop(제거)하면서 두 번째 스택인 b에 push(추가) 한다.

### Cpp Version
```cpp
#include<stack>
using namespace std;
class StackQueue
{
public:
    stack<int> a;
    stack<int> b;
    void enqueue(int data)
    {
        a.push(data);
    }
    int dequeue()
    {
        if (b.empty())
        {
            while (!a.empty())
            {
                b.push(a.top());
                a.pop();
            }
        }
        int data = b.top();
        b.pop();
        return data;
    }
};
```

### Java Version
```java
class StackQueue{
    Stack<Integer> a;
    Stack<Integer> b;

    public StackQueue() {
        this.a = new Stack<>();
        this.b = new Stack<>();
    }

    public void enqueue(int data) {
        a.push(data);
    }
    
    public int dequeue() {
        if (b.isEmpty()) {
            while (!a.isEmpty()) {
                b.push(a.pop());
            }
        }
        int data = b.pop();
        return data;
    }
}
```

### Javascript Version
```javascript
class StackQueue {
    constructor() {
        this.a = [];
        this.b = [];
    }
    
    enqueue(data) {
        this.a.push(data);
    }

    dequeue() {
        if (this.b.length == 0) {
            while (this.a.length > 0) {
                this.b.push(this.a.pop());
            }
        }
        return this.b.pop();
    }
}
```

### Python3 Version
```python3
class MyQueue:
    def __init__(self):
        self.a = list()
        self.b = list()

    def enQueue(self, number):
        self.a.append(number)

    def deQueue(self):
        if len(self.b) == 0:
            for i in range(len(self.a)):
                self.b.append(self.a.pop())

        if len(self.b) == 0:
            return -1
        else:
            return self.b.pop()
```

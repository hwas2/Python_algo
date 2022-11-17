7/19 (화) 10828번 스택 (실버4)
https://www.acmicpc.net/problem/10828  
- push X: 정수 X를 스택에 넣는 연산이다.  
- pop: 스택에서 가장 위에 있는 정수를 빼고, 그 수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
- size: 스택에 들어있는 정수의 개수를 출력한다.  
- empty: 스택이 비어있으면 1, 아니면 0을 출력한다.  
- top: 스택의 가장 위에 있는 정수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.
```python
#remove 대신 pop 쓰기
# push 숫자 에서 입력 숫자가 반드시 한 자리수라는 보장이 없다 (https://www.acmicpc.net/board/view/23969)
import sys
input=sys.stdin.readline
stack=[]
for i in range(int(input())):
  a=input().split()
  if a[0]=='push':
    stack.append(int(a[1]))
  elif a[0]=='pop':
    if len(stack)==0:
      print(-1)
    else:
      print(stack[-1])
      stack.pop()
  elif a[0]=='size':
    print(len(stack))
  elif a[0]=='empty':
    if len(stack)==0:
      print(1)
    else:
      print(0)
  elif a[0]=='top':
    if len(stack)==0:
      print(-1)
    else:
      print(stack[-1])
```



7/20 (수) 10845번 큐 (실버4)
https://www.acmicpc.net/problem/10845  
- push X: 정수 X를 큐에 넣는 연산이다.  
- pop: 큐에서 가장 앞에 있는 정수를 빼고, 그 수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
- size: 큐에 들어있는 정수의 개수를 출력한다.  
- empty: 큐가 비어있으면 1, 아니면 0을 출력한다.  
- front: 큐의 가장 앞에 있는 정수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
- back: 큐의 가장 뒤에 있는 정수를 출력한다. 만약 큐에 들어있는 정수가 없는 경우에는 -1을 출력한다.
```
pop(인덱스 번호)를 이용하면 인덱스 번호에 맞는 변수가 꺼내져
pop(0)를 통해 마지막 정수가 아닌 가장 앞에 있는 정수를 출력할 수 있다.
```
```python
import sys
input=sys.stdin.readline
que=[]
for i in range(int(input())):
  a=input().split()
  if a[0]=='push':
    que.append(int(a[1]))
  elif a[0]=='pop':
    if len(que)==0:
      print(-1)
    else:
      print(que[0])
      que.pop(0) #pop(인덱스 번호) : 인덱스 번호에 맞는 변수 꺼내짐
  elif a[0]=='size':
    print(len(que))
  elif a[0]=='empty':
    if len(que)==0:
      print(1)
    else:
      print(0)
  elif a[0]=='front':
    if len(que)==0:
      print(-1)
    else:
      print(que[0])
  elif a[0]=='back':
    if len(que)==0:
      print(-1)
    else:
      print(que[-1])
```



7/21 (목) 10866번 덱 (실버4)
https://www.acmicpc.net/problem/10866  
- push_front X: 정수 X를 덱의 앞에 넣는다.  
- push_back X: 정수 X를 덱의 뒤에 넣는다.  
- pop_front: 덱의 가장 앞에 있는 수를 빼고, 그 수를 출력한다. 만약, 덱에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
- pop_back: 덱의 가장 뒤에 있는 수를 빼고, 그 수를 출력한다. 만약, 덱에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
- size: 덱에 들어있는 정수의 개수를 출력한다.  
- empty: 덱이 비어있으면 1을, 아니면 0을 출력한다.  
- front: 덱의 가장 앞에 있는 정수를 출력한다. 만약 덱에 들어있는 정수가 없는 경우에는 -1을 출력한다.  
- back: 덱의 가장 뒤에 있는 정수를 출력한다. 만약 덱에 들어있는 정수가 없는 경우에는 -1을 출력한다.
```
list의 append() 함수는 리스트의 맨 뒤에 데이터를 추가한다. 만약 리스트의 맨 앞에 데이터를 추가하려면?
insert(index, item) : 인자로 전달된 index에 아이템을 추가한다.
따라서 리스트의 맨 앞에 아이템을 추가하려면 insert(0, item)을 사용하면 된다.
```
```python
import sys
input=sys.stdin.readline
daque=[]
for i in range(int(input())):
  a=input().split()
  if a[0]=='push_front':
    daque.insert(0,int(a[1]))
  elif a[0]=='push_back':
    daque.append(int(a[1]))
  elif a[0]=='pop_front':
    if len(daque)==0:
      print(-1)
    else:
      print(daque[0])
      daque.pop(0)
  elif a[0]=='pop_back':
    if len(daque)==0:
      print(-1)
    else:
      print(daque[-1])
      daque.pop(-1)
  elif a[0]=='size':
    print(len(daque))
  elif a[0]=='empty':
    if len(daque)==0:
      print(1)
    else:
      print(0)
  elif a[0]=='front':
    if len(daque)==0:
      print(-1)
    else:
      print(daque[0])
  elif a[0]=='back':
    if len(daque)==0:
      print(-1)
    else:
      print(daque[-1])
```



```python

```



```python

```



```python

```



```python

```



```python

```
10773번 제로 (실버4) - 구현, 자료 구조, 스택
https://www.acmicpc.net/problem/10773
```
" su.remove(su[-1])은 su의 마지막 원소를 제거하라는 뜻이 아닙니다.
su[-1]이란 원소를 앞에서부터 찾아서, 지우는 겁니다. "
 => remove 대신 pop으로 쓰기
```
```python
K=int(input())
num=[]
for i in range(K):
  new=int(input())
  if new != 0:
    num.append(new)
  else:
    num.pop()
print(sum(num))
```



10828번 스택 (실버4) - 자료 구조, 스택  
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



10845번 큐 (실버4) - 자료 구조, 큐  
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



10866번 덱 (실버4) - 자료 구조, 덱  
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



9012번 괄호 (실버4) - 자료 구조, 문자열, 스택  
https://www.acmicpc.net/problem/9012
```
리스트는 .remove로 제거
문자열은 .replace('제거하고싶은문자열','')
```
```python
T=int(input())
for i in range(T):
  PS=input()
  if len(PS)%2 == 1:
    print("NO")
  else:
    for j in range(int(len(PS)/2)):
      PS = PS.replace('()','')
    if len(PS)==0:
      print("YES")
    else:
      print("NO")
```



4949번 균형잡힌 세상 (실버4) - 자료 구조, 문자열, 스택  
https://www.acmicpc.net/problem/4949
```python
while True:
  N=input()
  if N == '.':
    break
  else:
    bracket=[]
    for i in range(len(N)):
      if N[i] in ['(',')','[',']']:
        bracket.append(N[i])
    bstr="".join(bracket)
    for j in range(int(len(bstr)/2)):
      bstr = bstr.replace('()','')
      bstr = bstr.replace('[]','')
    if len(bstr)==0:
      print("yes")
    else:
      print("no")
```



11866번 요세푸스 문제0 (실버5) - 구현, 자료 구조, 큐  
https://www.acmicpc.net/problem/11866
```python
N,K = map(int, input().split())
circle=[i for i in range(1,N+1)] #[1, 2, 3, 4, 5, 6, 7]
osps=[]
newK = 0
for i in range(N):
  newK = (newK + K -1) % len(circle)
  #반복문 대신 나머지로 쓸 수 있다, 인덱스라 -1 붙여줌
  #원래 N보다 클 때 while 문 돌려서 N을 빼주려고 했는데 나머지가 더 좋은 방법!
  osps.append(circle.pop(newK))
  print(circle)
  print(osps)
print("<",", ".join(map(str,osps)),">", sep="")
```



2164번 카드2 (실버4) - 자료 구조, 큐 
https://www.acmicpc.net/problem/2164
```
list의 pop과 append : 시간 초과 -> deque 사용 
popleft()
- 큐의 맨 왼쪽의 element를 삭제하고 반환
- element가 없으면, IndexError가 발생한다
```
```python
from collections import deque
N=int(input())
card = deque(i for i in range(1,N+1))
while len(card) > 1:
    card.popleft()
    card.append(card.popleft())
    #print(card)
print(card[0])
```
```
6 
deque([3, 4, 5, 6, 2]) 
deque([5, 6, 2, 4]) 
deque([2, 4, 6]) 
deque([6, 4]) 
deque([4]) 
4
```



10815번 숫자 카드 (실버5) - 자료 구조, 정렬, 이분 탐색  
https://www.acmicpc.net/problem/10815
```
- 순서와 중복에 대한 특성을 사용하지 않는다면 list보다 set이 시간 복잡도가 적음
 - list는 O(n), set은 O(1)
```
```python
import sys
input = sys.stdin.readline
N = int(input())
Nlist = set(map(int, input().split()))
M = int(input())
Mlist = list(map(int, input().split()))
for i in Mlist:
  if i in Nlist:
    print(1, end=" ")
  else:
    print(0, end=" ")
```
```python
#이분 탐색 풀이
import sys

n = int(input())
card = list(map(int, sys.stdin.readline().split()))
m = int(input())
check = list(map(int, sys.stdin.readline().split()))

card.sort()

def binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2

        if array[mid] == target:
            return mid
        elif array[mid] > target:
            end = mid - 1
        else:
            start = mid + 1
    return None


for i in range(m):
    if binary_search(card, check[i], 0, n - 1) is not None:
        print(1, end=' ')
    else:
        print(0, end=' ')
```



1920번 수 찾기 (실버4) - 자료 구조, 정렬, 이분 탐색  
https://www.acmicpc.net/problem/1920
```
def binary_search(array, target, start, end):
def binary_search(탐색하려는 배열, 찾고자 하는 수, 시작점, 끝점):
```
```python
import sys
input = sys.stdin.readline
N=int(input())
Nlist=list(map(int,input().split()))
Nlist.sort()
M=int(input())
Mlist=list(map(int,input().split()))

def binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2
        if array[mid] == target: # 찾은 경우 중간점 인덱스 반환
            return 1
        elif array[mid] > target: # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
            end = mid - 1
        else:
            start = mid + 1 # 중간점의 값보다 찾고자 하는 값이 작은 경우 오른쪽 확인
    return 0
    
for i in Mlist:
  print(binary_search(Nlist,i, 0, N-1))
```



```python

```



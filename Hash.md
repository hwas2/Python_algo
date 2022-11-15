
1764번 듣보잡 (실버4)
https://www.acmicpc.net/problem/1764
```python
N,M = map(int, input().split())
lis = []
see = []
for i in range(N):
  lis.append(input())
for j in range(M):
  see.append(input())
lisee = list(set(lis) & set(see)) #중복 찾기
#리스트 [i for i in see if i in lis] = 집합 set(lis) & set(see)
print(len(lisee))
for i in sorted(lisee):
  print(i)
```



17219번 비밀번호 찾기 (실버4)
https://www.acmicpc.net/problem/17219  
딕셔너리{key:value} 이용  
제공되는 입력 예시 오른쪽에 공백 함께 들어감 -> input().rstrip()에서 rstrip 없으면 런타임 에러(KeyError) 발생
```python
import sys
input=sys.stdin.readline
N,M=map(int,input().split())
password={}
for i in range(N):
  url, pw = input().split()
  password[url] = pw
for j in range(M):
  print(password[input().rstrip()])
```



1620번 나는야 포켓몬 마스터 이다솜 (실버4)
https://www.acmicpc.net/problem/1620
```python
import sys
input = sys.stdin.readline

N,M = map(int, input().split())
pk = {}
for i in range(1, N+1):
  name = input().rstrip()
  pk[i] = name
  pk[name] = i

for j in range(M):
  ans = input().rstrip()
  if ans.isdigit():
    print(pk[int(ans)])
  else:
    print(pk[ans])
```



1302번 베스트셀러 (실버4)
https://www.acmicpc.net/problem/1302  
첫째 줄에 가장 많이 팔린 책의 제목을 출력한다. 만약 가장 많이 팔린 책이 여러 개일 경우에는 사전 순으로 가장 앞서는 제목을 출력한다.  
key 기준으로 정렬  
  - sorted(a.key()) : key만 정렬된 값 반환  ['a', 'c', 'e']  
  - sorted(a.items()): 키를 기준으로 정렬하고 key와 value를 튜플로 묶어서 정렬된 값 반환  [('a',2), ('c',4), ('e'.2)]   
  - sorted(a.items(), key=lambda x: x[0])  
value를 기준으로 정렬  
  - sorted(a.value())  
  - sorted(a.items(), key=lambda x: x[1])
```python
import sys
input = sys.stdin.readline

N = int(input())
book = {}
for i in range(N):
  btitle = input().rstrip()
  if btitle in book:
    book[btitle] += 1
  else:
    book[btitle] = 1

maxbook = []
for j in book.keys(): #여기선 딕셔너리 key가 책 제목, value가 책 수
  if book[j] == max(book.values()):
    maxbook.append(j)
print(sorted(maxbook)[0])
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
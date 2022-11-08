5585번 거스름돈 (브론즈2)
https://www.acmicpc.net/problem/5585
```python
money = 1000 - int(input())
list=[500,100,50,10,5,1]
count = 0
for i in list:
  if money >= i:
    count += money//i #같은 동전을 차감해야 할 때 "몫"이 필요하다
    money -= i*(money//i)
  else:
    pass
print(count)
```



2839번 설탕 배달 (실버4)
https://www.acmicpc.net/problem/2839
```python
N=int(input())
count = 0
while N>=0:
  if N%5==0:    #5로 나누어떨어지면 몫만큼 count
    count+=N//5
    print(count)
    break
  N-=3   #아니면 3을 뺀다음 5를 나누어주는 과정 반복
  count+=1
  
else: 
  print(-1) #위에 해당 사항이 없다면 -1 출력
```
  


9009번 피보나치 (실버1)
https://www.acmicpc.net/problem/9009
```python
n = int(input())
d = [0,1]
#d(44) = 701,408,733
#d(45) = 1,134,903,170
#이므로 1 ≤ n ≤ 1,000,000,000. 에 따라 d를 45까지 만들어준다
for i in range(2, 46):
  d.append(d[i-1] + d[i-2])

for i in range(n):
  T = int(input())
  answer = []
  for j in range(45,0,-1):
    if d[j] <= T:
      T -= d[j]
      answer.append(d[j])
  answer.sort()
  for i in answer:
    print(i, end=" ")
  print()
```



1049번 기타줄 (실버4)
https://www.acmicpc.net/problem/1049
```python
import sys
input = sys.stdin.readline

N, M = map(int, input().split()) #기타줄 개수N, 브랜드 개수M
sixl = []
onel = []
for i in range(M):
  s, o = map(int,input().split()) #6개 가격, 1개 가격
  sixl.append(s)
  onel.append(o)
  
money = 0
if 6*min(onel) > min(sixl): #패키지가 쌀 때
  money = min(sixl) * (N // 6)
  if min(onel) * (N % 6) > min(sixl) : #남은 개수*금액보다 패키지 한 묶음이 쌀 때
    money += min(sixl)
  else:
    money += min(onel) * (N % 6) #남은 개수*금액이 쌀 때
else: #개별 구매가 쌀 때
  money = min(onel) * N

print(money)
```
  


13305번 주유소 (실버3)
https://www.acmicpc.net/problem/13305
```python
N = int(input()) #도시의 개수
road = list(map(int, input().split())) #도로의 길이
price = list(map(int, input().split())) #주유소의 리터당 가격

total = 0
cost = price[0]
for i in range(N-1):
  if price[i] < cost:
    cost = price[i]
  total += road[i] * cost

print(total)
```
  


1541번 잃어버린 괄호 (실버2)
https://www.acmicpc.net/problem/1541
```python
S = list(input().split('-'))
total = sum(map(int,S[0].split('+')))
#양수를 가지고 만든 식이라 첫번째 항은 무조건 양수이다. 따라서 첫 항은 더해준다 
for i in range(1, len(S)):
  total -= sum(map(int,S[i].split('+'))) #=마다 끊긴 것이므로 total에서 빼준다
print(total)
```
  


1026번 보물 (실버4)
https://www.acmicpc.net/problem/1026
```python
N = int(input())
A = list(map(int, input().split()))
A = sorted(A)
B = list(map(int, input().split()))
B = sorted(B, reverse=True)
sum=0
for i in range(N):
  sum+=A[i]*B[i]
print(sum)
```
  


11399번 ATM (실버4)
https://www.acmicpc.net/problem/11399
```python
N = int(input())
Nlist = list(map(int, input().split()))
Nlist.sort() #[1, 2, 3, 3, 4]
for i in range(len(Nlist)):
  if i>=1:
    Nlist[i]+=Nlist[i-1]
print(sum(Nlist)) #[1, 3, 6, 9, 13] 합 32
```
  


11047번 동전 0 (실버4)
https://www.acmicpc.net/problem/11047

```python
import sys
input=sys.stdin.readline
N,K=map(int, input().split())
money=[]
for i in range(N):
  money.append(int(input()))
money = sorted(money, reverse=True)
cnt=0
for j in money:
  if K>=j:
    cnt+=K//j #몫(개수)
    K=K%j #남은 금액
print(cnt)
```
  


1439번 뒤집기 (실버5)
https://www.acmicpc.net/problem/1439  
입력 0001100 출력 (2번 바뀜) 1  
입력 11111 출력 (0번 바뀜) 0  
입력 00000001 출력 (1번 바뀜) 1  
입력 11001100110011000001 출력 (8번 바뀜) 4  
"0->1 또는 1->0 으로 바뀌는 횟수를 찾는다"
```python
S=list(map(int,input()))
cntz=0
cnto=0
for i in range(len(S)-1):
  if S[i]==0 and S[i]!=S[i+1]:
    cntz+=1
  elif S[i]==1 and S[i+1]==0:
    cnto+=1
if S[-1]==0:
  cntz+=1
if S[-1]==1:
  cnto+=1
#print(cntz,cnto)
print(min(cntz,cnto))
```
  


1789번 수들의 합 (실버5)
https://www.acmicpc.net/problem/1789
```python
S = int(input())
num=0
total=0
while total<S:
  num+=1
  total+=num
  if total>S:
    num-=1
    break
print(num)
```
  


2217번 로프 (실버4)
https://www.acmicpc.net/problem/2217  
"모두 고르게 중량이 걸리게 되면 사용되는 로프 중 가장 적은 중량 * 사용되는 로프 개수만큼 총 중량을 들어올릴 수 있다."   
따라서 내림차순 정렬을 한 뒤, rope[i]*(i+1) 로 계산하면
최소 중량 * 로프 개수 를 구할 수 있다.
```python
N = int(input())
rope=[]
for i in range(N):
  rope.append(int(input()))
rope = sorted(rope, reverse=True)
for j in range(len(rope)):
  rope[j]=(j+1)*rope[j]
print(max(rope))
```
  


10610번 30 (실버4)
https://www.acmicpc.net/problem/10610
```python
N=list(map(int,str(input()))) #리스트에 정수형으로 담는다
N=sorted(N,reverse=True) #내림차순 정렬
if N[-1] != 0: #10의 배수가 아니면
  print(-1)
elif sum(N)%3 !=0: #3의 배수가 아니면
  print(-1)
else:
  print("".join(map(str,N))) #int형 리스트를 .join으로 꺼내기
```



1931번 회의실 배정 (실버1)
https://www.acmicpc.net/problem/1931
```python
N = int(input())
room = []
for i in range(N):
  start, end = map(int, input().split())
  room.append([start, end])

room.sort(key = lambda x : (x[1], x[0]))
#시작 시간이 먼저여도 회의 시간이 길다면 먼저 끝나는 것을 선택해야 하기 때문에
# 끝나는 시간을 먼저 오름차순 정리하고, 시작 시간을 오름차순 정리해주었다.
# room.sort(key = lambda x : (x[0], x[1]))로 진행시 답이 3으로 출력되었다.

cnt = 0
last = 0
for i,j in room:
  if i >= last:
    cnt += 1
    last = j

print(cnt)
```
  


2864번 5와 6의 차이 (브론즈2)
https://www.acmicpc.net/problem/2864
```python
A, B = input().split()
minab = int(A.replace('6','5')) + int(B.replace('6','5')) #6을 5로 바꾸면 최소
maxab = int(A.replace('5','6')) + int(B.replace('5','6')) #5를 6으로 바꾸면 최대
print(minab, maxab)
```



10162번 전자레인지 (브론즈3)
https://www.acmicpc.net/problem/10162
```python
T = int(input())
cnta = 0
cntb = 0
cntc = 0

if T % 10 != 0:
  print(-1)
else:
  while T > 0:
    if T >= 300:
      cnta += T//300
      T = T % 300
    elif T >= 60:
      cntb += T//60
      T = T % 60
    else:
      cntc += T//10
      T = T % 10
  print(cnta, cntb, cntc)
```
  


4796번 캠핑 (브론즈1)
https://www.acmicpc.net/problem/4796
```python
i = 0
while True:
  L, P, V = map(int, input().split()) #연속하는 P일 중, L일동안만 사용, V일짜리 휴가 시작
  i += 1
  if L == 0 and P == 0 and V ==0:
    break
  day = V//P * L
  day += min(V%P, L)
  print('Case %d: %d' %(i, day))
```
  


1946번 신입 사원 (실버1)
https://www.acmicpc.net/problem/1946
```python
import sys
input = sys.stdin.readline

T = int(input())
for i in range(T):
  N = int(input())
  people = []
  for j in range(N):
    text, interview = map(int, input().split())
    people.append((text, interview))
  
  people.sort(key = lambda x : x[0]) #서류 성적 정렬
  answer = 1 #서류 1등인 사람은 무조건 포함해야 한다
  mininterview = people[0][1]
  for k in range(1,N):
    if people[k][1] < mininterview: #등수가 낮으면 포함한다
      mininterview = people[k][1]
      answer += 1
  print(answer) 
```
  


```python

```

```python

```

```python

```
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
  


11053번 가장 긴 증가하는 부분 수열 (실버2) 
https://www.acmicpc.net/problem/11053
```python
Al = int(input())
A = list(map(int, input().split())) #10 20 10 30 20 50
cnt = [1 for i in range(Al)]
for i in range(1,Al):
  for j in range(i):
    if A[i] > A[j]:
      cnt[i] = max(cnt[i], cnt[j]+1)
print(max(cnt)) #[1, 2, 1, 3, 2, 4]
```



1932번 정수 삼각형 (실버1)
https://www.acmicpc.net/problem/1932  
d[0][0]=7  
d[1][0]=3+7     d[1][1]=8+7  
d[2][0]=8+d[1][0]     d[2][1]=1+max(d[1][0],d[1][1])     d[2][2]=0+d[1][1]  
d[3][0]=2+d[2][0]     d[3][1]=7+max(d[2][0],d[2][1])     d[3][2]=4+max(d[2][1],d[2][2])     d[3][3]=4+d[2][2]
```python
import sys
input=sys.stdin.readline

N = int(input())
tri = []
for i in range(N):
  tri.append(list(map(int, input().split())))

for i in range(1,N):
  for j in range(len(tri[i])):
    if j == 0:
      tri[i][j] = tri[i][j] + tri[i-1][j] #맨 왼쪽의 경우
    elif i == j:
      tri[i][j] = tri[i][j] + tri[i-1][j-1] #맨 오른쪽의 경우
    else:
      tri[i][j] = tri[i][j] + max(tri[i-1][j-1], tri[i-1][j]) #그 외의 경우 (가운데 숫자들)
print(max(tri[i]))
```



1149번 RGB거리 (실버1)
https://www.acmicpc.net/problem/1149
```python
import sys
input=sys.stdin.readline

N = int(input())
h = []
for i in range(N):
  h.append(list(map(int, input().split())))
for i in range(1,N):
  h[i][0] = min(h[i-1][1], h[i-1][2]) + h[i][0] #빨강 선택
  h[i][1] = min(h[i-1][0], h[i-1][2]) + h[i][1] #초록 선택
  h[i][2] = min(h[i-1][0], h[i-1][1]) + h[i][2] #파랑 선택
print(min(h[-1]))
```



2156번 포도주 시식 (실버1)
https://www.acmicpc.net/problem/2156  
2579번 계단 오르기와 유사한 문제인데 마지막을 선택하지 않아도 된다는 점이 다르다.  
마지막을 선택하지 않는 경우, 한 가지만 더 고려해주면 된다.
```python
import sys
input=sys.stdin.readline

N = int(input())
g = [0 for i in range(10001)] #런타임 에러 : g = [0 for i in range(N+1)]
d = [0 for i in range(10001)]
for i in range(N):
  g[i] = (int(input()))

d[0] = g[0]
d[1] = g[0]+g[1]
d[2] = max(d[0]+g[2], g[1]+g[2], d[1])
for i in range(3,N):
  d[i] = max(d[i-3]+g[i-1]+g[i], d[i-2]+g[i], d[i-1])
  #d[i-3]+g[i-1]+g[i] : 3개의 계단은 연속으로 밟을 수 없다
  #d[i-1] : 마지막 잔은 먹지 않아도 된다.
print(max(d))
# print(g) [6, 10, 13, 9, 8, 1, 0]
# print(d) [6, 16, 23, 28, 33, 33, 0]
```



2748번 피보나치 수2 (브론즈1)
https://www.acmicpc.net/problem/2748
```python
#메모이제이션 동작 분석 - 실제로 호출되는 함수에 대해서만 방문, 시간 복잡도 = O(N)
n = int(input())
d = [0] * 91
d[0] = 0
d[1] = 1
for i in range(2, n+1):
  d[i] = d[i-1] + d[i-2]
print(d[n])
```



10826번 피보나치 수4 (실버5) 
https://www.acmicpc.net/problem/10826
```python
n = int(input())
d = [0,1]
for i in range(2, n+1):
  d.append(d[i-1] + d[i-2])
print(d[n])
```



14495번 피보나치 비스무리한 수열 (실버4)
https://www.acmicpc.net/problem/14495
```python
n = int(input())
d = [0,1,1,1]
for i in range(4, n+1):
  d.append(d[i-1] + d[i-3])
print(d[n])
```



1788번 피보나치 수의 확장 (실버3)
https://www.acmicpc.net/problem/1788  
- n>0 : 1 1 2 3 5 8 13 ...  
- n=0 : 0  
- n<0 : 1 -1 2 -3 5 -8 13 ...
```python
n = int(input())
d = [0,1]
for i in range(2, abs(n)+1):
  d.append((d[i-1] + d[i-2])%1000000000)
if n<0 and n%2==0:
  print(-1) #n이 음수이면서, 2로 나누어떨어질 땐 음수값을 갖는다
elif n==0:
  print(0) #n = 0일때
else:
  print(1) #양수일때
print(d[abs(n)])
```



14916번 거스름돈 (실버5)
https://www.acmicpc.net/problem/14916
```python
N = int(input())
dp = [-1] * (N+8)
dp[2] = 1
dp[4] = 2
dp[5] = 1
dp[6] = 3
dp[7] = 2
dp[8] = 4
for i in range(9,N+1):
  dp[i] = min(dp[i-2],dp[i-5])+1
print(dp[N])
```



9625번 BABBA (실버5)
https://www.acmicpc.net/problem/9625  
A -> BA -> BAB -> BABBA -> BABBABAB 상근이는 화면의 모든 B는 BA로 바뀌고, A는 B로 바뀐다는 사실을 알게되었다.  
B가 BA, A가 B로 바뀌므로 B[i-1] = A[i] 임을 알 수 있다. 따라서 B의 개수만 dp로 구하면 A의 개수도 찾을 수 있다.
```python
K = int(input())
dp = [0] * (K+1)
dp[1] = 1
for i in range(2, K+1):
  dp[i] = dp[i-1] + dp[i-2]
print(dp[K-1], dp[K])
```



1904번 01타일 (실버3)
https://www.acmicpc.net/problem/1904  
d[1] = 1  
d[2] = 2  
d[3] = 3  
d[4] = 5
```python
N =int(input())
d = [0] * 1000001
d[1] = 1
d[2] = 2
for i in range(3,N+1):
  d[i] = (d[i-1] + d[i-2])%15746
print(d[N])
```



2193번 이친수 (실버3)
https://www.acmicpc.net/problem/2193  
d[1] = 1  
d[2] = 1  
d[3] = 2  
d[4] = 3  
d[5] = 5
```python
N =int(input())
d = [0] * 91
d[1] = 1
d[2] = 1
for i in range(3,N+1):
  d[i] = d[i-1] + d[i-2]
print(d[N])
```



1003번 피보나치 함수 (실버3)
https://www.acmicpc.net/problem/1003  
fibonacci(3)을 호출하면 다음과 같은 일이 일어난다.  
- fibonacci(3)은 fibonacci(2)와 fibonacci(1) (첫 번째 호출)을 호출한다.  
- fibonacci(2)는 fibonacci(1) (두 번째 호출)과 fibonacci(0)을 호출한다.  
- 두 번째 호출한 fibonacci(1)은 1을 출력하고 1을 리턴한다.  
- fibonacci(0)은 0을 출력하고, 0을 리턴한다.  
- fibonacci(2)는 fibonacci(1)과 fibonacci(0)의 결과를 얻고, 1을 리턴한다.  
- 첫 번째 호출한 fibonacci(1)은 1을 출력하고, 1을 리턴한다.  
- fibonacci(3)은 fibonacci(2)와 fibonacci(1)의 결과를 얻고, 2를 리턴한다.  
1은 2번 출력되고, 0은 1번 출력된다. N이 주어졌을 때, fibonacci(N)을 호출했을 때, 0과 1이 각각 몇 번 출력되는지 구하는 프로그램을 작성하시오.
```python
import sys
input = sys.stdin.readline

T = int(input())
for i in range(T):
  N = int(input())
  dp0 = [1, 0]
  dp1 = [0, 1]
  for i in range(2,N+1):
    dp0.append(dp1[i-1]) #0의 갯수 = 이전 1의 갯수
    dp1.append(dp0[i-1] + dp1[i-1]) #1의 갯수 = 이전 0+이전1 갯수
  print(dp0[N], dp1[N])
```



11722번 가장 긴 감소하는 부분 수열 (실버2)
https://www.acmicpc.net/problem/11722
```python
Al = int(input())
A = list(map(int, input().split())) #10 30 10 20 20 10
cnt = [1 for i in range(Al)]
for i in range(1,Al):
  for j in range(i):
    if A[i] < A[j]:
      cnt[i] = max(cnt[i], cnt[j]+1)
print(max(cnt)) #[1, 1, 2, 2, 2, 3]
```



11052번 카드 구매하기 (실버1)
https://www.acmicpc.net/problem/11052
```python
N = int(input())
P = [0] + list(map(int, input().split()))
dp = [0] * (N+1)
dp[1] = P[1]

for i in range(1, N+1):
  for j in range(1, i+1):
    dp[i] = max(dp[i], dp[i-j]+P[j])
print(dp[N])
```
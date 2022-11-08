2775번 부녀회장이 될테야 (브론즈1)
https://www.acmicpc.net/problem/2775  
2층[1 4 10 20 35 56 84]  
1층[1 3 6  10 15 21 28]  
0층[1 2 3  4  5  6  7 ]
```python
T=int(input())
for i in range(T):
  floor=int(input()) #층
  num=int(input()) #호
  people=[j for j in range(1,num+1)] #0층의 호실마다 사람 수
  for f in range(0,floor):
    for n in range(1,num):
      people[n] += people[n-1] #people[f][n]=people[f-1][n]+people[f][n-1]
  print(people[-1])
```



9095번 1,2,3 더하기 (실버3)
https://www.acmicpc.net/problem/9095  
- n= 1일때 1 : 1  
- n=2일때 2 : 1+1, 2  
- n=3일때 4 : 1+1+1, 2+1, 1+2, 3  
- n=4일때 7: 1+1+1+1, 2+1+1, 1+2+1, 1+1+2, 3+1, 1+3, 2+2  
- n=5일때 13: 1+1+1+1+1, 2+1+1+1(4개), 3+1+1(3개), 2+2+1(3개), 3+2(2개)  
- n=6일때 24: 1+1+1+1+1+1, 2+1+1+1+1(5개), 3+1+1+1(4개), 2+2+1+1(6개), 2+2+2, 3+3, 3+2+1(6개)  
여기서 d(n)=d(n-1)+d(n-2)+d(n-3)임을 알 수 있다.
```python
T=int(input())

def d(n):
  if n==1:
    return 1
  elif n==2:
    return 2
  elif n==3:
    return 4
  else:
    return d(n-1)+d(n-2)+d(n-3)

for i in range(T):
  n=int(input())
  print(d(n))
```



1463번 1로 만들기 (실버3) 
https://www.acmicpc.net/problem/1463  
연산 최솟값이면 수가 크게 감소하는 %3, %2, -1 순으로 연산을 진행한다...?  
하지만 10의 경우 10->5->4->3->1 보다 10->9->3->1의 횟수가 더 적다...!  
f(10) - f(9), f(5)  
f(9) - f(8), f(3)  
       f(8) - f(7), f(4)
       f(3) - f(2), f(1)  
f(5) - f(4)  
       f(4) - f(3), f(2)
```python
N=int(input())
d = [0] * (N+1) #DP 테이블 초기화

for i in range(2, N+1):
  # 1을 빼는 경우
  d[i] = d[i-1] + 1
  # 3으로 나누어지는 경우
  if i%3 == 0:
    d[i] = min(d[i], d[i//3]+1)
  # 2로 나누어지는 경우
  if i%2 == 0:
    d[i] = min(d[i], d[i//2]+1)
print(d[N])
```



9461번 파도반 수열 (실버3)
https://www.acmicpc.net/problem/9461  
1, 1, 1, 2, 2, 3, 4, 5, 7, 9  
- P[4] = P[1] + P[2]  
- P[5] = P[2] + P[3]  
- P[6] = P[3] + P[4]  
- P[7] = P[4] + P[5]  
- P[8] = P[5] + P[6]
```python
P = [0] * (101) #DP 테이블 초기화
P[1] = 1
P[2] = 1
P[3] = 1
for i in range(4, 101):
  P[i] = P[i-3] + P[i-2]

T = int(input())
for i in range(T):
  N = int(input())
  print(P[N])
```



2579번 계단 오르기 (실버3)
https://www.acmicpc.net/problem/2579
```python
import sys
input=sys.stdin.readline

N = int(input())
s = [0 for i in range(N+1)]
d = [0 for i in range(N+1)]
for i in range(N):
  s[i] = (int(input()))

d[0] = s[0]
d[1] = s[0] + s[1]
for i in range(2,N+1):
  d[i] = max(d[i-3]+s[i-1]+s[i], d[i-2]+s[i])
  #s[i-3]+s[i-1]+s[i] : 3개의 계단은 연속으로 밟을 수 없다
print(d[N-1])
```



9655번 돌 게임 (실버5)
https://www.acmicpc.net/problem/9655  
탁자 위에 돌 N개가 있다. 상근이와 창영이는 턴을 번갈아가면서 돌을 가져가며, 돌은 1개 또는 3개 가져갈 수 있다. 마지막 돌을 가져가는 사람이 게임을 이기게 된다.  
두 사람이 완벽하게 게임을 했을 때, 이기는 사람을 구하는 프로그램을 작성하시오. 게임은 상근이가 먼저 시작한다.  
돌이 3개 또는 1개가 남는 순간 승패가 결정된다. 돌은 짝수개씩 줄어든다. (1+1, 1+3, 3+1, 3+3)의 경우가 존재한다.
```python
N = int(input())
if N % 2 == 0:
    print("CY")
else:
    print("SK")
```



9656번 돌 게임 2 (실버5)
https://www.acmicpc.net/problem/9656  
9655번 돌 게임과 결과값만 바꾸면 된다.  
탁자 위에 돌 N개가 있다. 상근이와 창영이는 턴을 번갈아가면서 돌을 가져가며, 돌은 1개 또는 3개 가져갈 수 있다. 마지막 돌을 가져가는 사람이 게임을 지게 된다.  
두 사람이 완벽하게 게임을 했을 때, 이기는 사람을 구하는 프로그램을 작성하시오. 게임은 상근이가 먼저 시작한다.
```python
N = int(input())
if N % 2 == 0:
    print("SK")
else:
    print("CY")
```



1912번 연속합 (실버2)
https://www.acmicpc.net/problem/1912  
이 중 연속된 몇 개의 수를 선택해서 구할 수 있는 합 중 가장 큰 합을 구하려고 한다.  
-> 앞의 수를 더한 것과 본인 수를 비교하여 큰 것으로 한다
```python
N = int(input())
Nlist = list(map(int, input().split())) #2 1 -4 3 4 -4 6 5 -5 1
cnt = Nlist
for i in range(1,N):
  cnt[i] = max(cnt[i]+cnt[i-1], cnt[i])
print(max(cnt)) #[2, 3, -1, 3, 7, 3, 9, 14, 9, 10]
```



11726번 2×n 타일링 (실버3)
https://www.acmicpc.net/problem/11726  
d[1] = 1  
d[2] = 1 + 1  
d[3] = 1 + 2 = 3  
d[4] = 1 + 3 + 1 = 5 (모두 세로, 세로2,가로2, 가로4)  
d[5] = 1 + 4 + 3 = 8  
d[6] = 1 + 5 + 6 + 1 = 13
```python
N = int(input())
d = [0]*1001 #런타임 에러 : d = [0 for i in range(N+1)]
d[1] = 1
d[2] = 2
for i in range(3, N+1):
  d[i] = d[i-2] + d[i-1]
print(d[N]%10007)
```



11727번 2×n 타일링 2 (실버3)
https://www.acmicpc.net/problem/11727  
d[1] = 1  
d[2] = 1 + 1*2 = 3  
d[3] = 1 + 2*2 = 5  
d[4] = 1 + 3*2 + 1*4 = 11  
d[5] = 1 + 4*2 + 3*4 = 21
```python
N = int(input())
d = [0]*1001
d[1] = 1
d[2] = 3
for i in range(3, N+1):
  d[i] = 2 * d[i-2] + d[i-1]
print(d[N]%10007)
```



2133번 타일 채우기 (골드4)
https://www.acmicpc.net/problem/2133
```python
N = int(input())
#런타임에러 d = [0 for i in range(N+1)]
d = [0 for i in range(31)]
d[2] = 3
if N % 2 == 1:
  print(0)
else:
  for i in range(4, N+1, 2):
    d[i] = d[i-2] * d[2]
    for j in range(4, i, 2):
      d[i] += d[i-j]*2
    d[i] += 2
  print(d[N])
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



```python

```

```python

```

```python

```
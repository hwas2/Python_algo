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

```python

```

```python

```

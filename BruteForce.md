2231번 분해합 (브론즈2)
https://www.acmicpc.net/problem/2231
```python
N=int(input())
for i in range(N):
  M=list(map(int,str(i)))
  if N==i+sum(M):
    print(i)
    break
else:
  print(0) #생성자가 없는 경우에는 0을 출력한다.
```



2798번 블랙잭 (브론즈2)
https://www.acmicpc.net/problem/2798
```python
N, M = map(int, input().split())
Nlist = list(map(int, input().split()))
Nlist.sort()
cardsum=0
for i in range(N):
  for j in range(i+1, N):
    for k in range(j+1,N):
      if Nlist[i]+Nlist[j]+Nlist[k] > M  or Nlist[i]+Nlist[j]+Nlist[k] < cardsum:
        continue
      cardsum = Nlist[i]+Nlist[j]+Nlist[k]
print(cardsum)
```



7568번 덩치 (실버5)
https://www.acmicpc.net/problem/7568
```python
people=[]
for i in range(int(input())):
  x,y=map(int,input().split())
  people.append((x,y))

for i in people:
  rank = 1
  for j in people:
    if i[0] < j[0] and i[1] < j[1]:
      rank += 1
  print(rank, end=" ")
```



1436번 영화감독 숌 (실버5)
https://www.acmicpc.net/problem/1436  
종말의 숫자란 어떤 수에 6이 적어도 3개이상 연속으로 들어가는 수를 말한다. 제일 작은 종말의 숫자는 666이고, 그 다음으로 큰 수는 1666, 2666, 3666, .... 과 같다. 일반화해서 생각하면, N번째 영화의 제목은 세상의 종말 (N번째로 작은 종말의 숫자) 와 같다. 숌이 만든 N번째 영화의 제목에 들어간 숫자를 출력하는 프로그램을 작성하시오.  
- 입력 2 출력 1666  
- 입력 3 출력 2666  
- 입력 6 출력 5666  
- 입력 187 출력 66666  
- 입력 500 출력 166699
```python
N = int(input())
cnt=0
sixs=666
while True:
  if '666' in str(sixs):
    cnt+=1
  if cnt==N:
    print(sixs)
    break
  sixs+=1
```



1476번 날짜 계산 (실버5)
https://www.acmicpc.net/problem/1476  
지구를 나타내는 수를 E, 태양을 나타내는 수를 S, 달을 나타내는 수를 M이라고 했을 때, 이 세 수는 서로 다른 범위를 가진다. (1 ≤ E ≤ 15, 1 ≤ S ≤ 28, 1 ≤ M ≤ 19)  
첫째 줄에 E S M으로 표시되는 가장 빠른 연도를 출력한다. 1 1 1은 항상 1이기 때문에, 정답이 음수가 나오는 경우는 없다.  
- 1 16 16 출력 16  
- 1 1 1 출력 1  
- 1 2 3 출력 5266 (15*351+1 = 28*188+2 = 19*277+3)  
- 15 28 19 출력 7980
```python
E,S,M=map(int,input().split())
i=1
while True:
  if (i-E)%15==0 and (i-S)%28==0 and (i-M)%19==0:
    print(i)
    break
  i+=1
```



2309번 일곱 난쟁이 (브론즈1)
https://www.acmicpc.net/problem/2309
```python
#아홉 난쟁이의 합에서 100을 빼서 해당하는 키의 2명의 난쟁이를 삭제한다.
import sys
input=sys.stdin.readline
total=[]
for i in range(9):
  total.append(int(input()))
total.sort()
for i in range(9):
  for j in range(i+1,9):
    if total[i]+total[j] == sum(total)-100:
      first=total[i]
      second=total[j]
      total.remove(first)
      total.remove(second)
      break
  if len(total)==7:
    break
for _ in total:
  print(_)
```



1065번 한수 (실버4)
https://www.acmicpc.net/problem/1065  
어떤 양의 정수 X의 각 자리가 등차수열을 이룬다면, 그 수를 한수라고 한다. N이 주어졌을 때, 1보다 크거나 같고, N보다 작거나 같은 한수의 개수를 출력하는 프로그램을 작성하시오.  
입력 : 첫째 줄에 1,000보다 작거나 같은 자연수 N이 주어진다. => 입력은 세 자리 수이다.  
- 110 출력 99  
- 1 출력 1  
- 210 출력 105  
- 1000 출력 144  
- 500 출력 119  
"한자리수, 두자리수는 모두 한수이다. 세 자리수만 각 자리의 등차수열을 확인하면 된다."
```python
X = int(input())
cnt = 0
for i in range(1,X+1):
  if i <= 99:
    cnt+=1
  else:
    Xlist = list(map(int,str(i)))
    if Xlist[2]-Xlist[1] == Xlist[1] - Xlist[0]:
      cnt+=1
print(cnt)
```



4673번 셀프 넘버 (실버5)
https://www.acmicpc.net/problem/4673  
생성자가 없는 숫자를 셀프 넘버라고 한다. 100보다 작은 셀프 넘버는 총 13개가 있다.  
1, 3, 5, 7, 9, 20, 31, 42, 53, 64, 75, 86, 97
```python
num = [i for i in range(1,10_000)]
gen = []
for i in num:
  ilist=list(map(int,str(i)))
  isum = sum(ilist) + i
  if isum in num:
    gen.append(isum)
for _ in num:
  if _ not in gen:
    print(_)
```



1977번 완전제곱수 (브론즈2)
https://www.acmicpc.net/problem/1977
```python
M = int(input())
N = int(input())
two = []
for i in range(M, N+1):
  if i**(1/2) == int(i**(1/2)):
    two.append(i)
if len(two)>0:
  print(sum(two))
  print(min(two))
else:
  print(-1)
  ```



1057번 토너먼트 (실버4)
https://www.acmicpc.net/problem/1057  
16 8 9  
8 -> 4 -> 2 -> 1 -> 1  
9 -> 5 -> 3 -> 2 -> 1  
출력 : 4
```python
N, kim, lim = map(int, input().split())
cnt = 1
while (kim//2 + kim%2) != (lim//2 + lim%2):
  kim = kim//2 + kim%2
  lim = lim//2 + lim%2
  cnt += 1
print(cnt)
```



1543번 문서 검색 (실버4)
https://www.acmicpc.net/problem/1543  
문서와 단어는 알파벳 소문자와 공백으로 이루어져 있다. => 공백 고려  
세준이는 문서와 검색하려는 단어가 주어졌을 때, 그 단어가 최대 몇 번 중복되지 않게 등장하는지 구하는 프로그램을 작성하시오. => 중복 안 됨
```python
#중복이 안 되야 하므로 해당 단어가 등장하면 인덱스를 단어의 길이만큼 증가시켜 준다.
text = list(input())
searchword = list(input())
cnt = 0
i = 0
while i <= len(text)-len(searchword):
  if text[i:i+len(searchword)] == searchword:
    cnt += 1
    i+=len(searchword)
  else:
    i+=1
print(cnt)
```



1120번 문자열 (실버4)
https://www.acmicpc.net/problem/1120  
adaabc aababbc -> 2  
a a b a b b c  | a a b a b b c  
a d a a b c    |   a d a a b c  
 3개 다름      |   2개 다름  
hello xello -> 1  
koder topcoder -> 1  
abc topabcoder -> 0  
giorgi igroig -> 6  
```python
A, B = input().split()
answer = []
for i in range(len(B)-len(A)+1): #두 문자열 길이가 같을 때도 동작해야 하므로 1을 더해준다
  cnt = 0
  for j in range(len(A)):
    if A[j] != B[i+j]:
      cnt += 1
  answer.append(cnt)
print(min(answer))
```



2003번 수들의 합2 (실버4)
https://www.acmicpc.net/problem/2003
```python
N, M = map(int, input().split()) # M: 연속된 숫자의 합
Nlist = list(map(int, input().split()))

left,right = 0, 1
cnt = 0

while left <= right and right <= N:
  if sum(Nlist[left:right]) < M:
    right += 1
  elif sum(Nlist[left:right]) == M:
    cnt += 1
    right += 1
  else:
    left += 1
print(cnt)
```
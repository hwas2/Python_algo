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



9009번 피보나치 (실버1) - 그리디 알고리즘
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
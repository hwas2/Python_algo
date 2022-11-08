2839번 설탕 배달 (실버4)
https://www.acmicpc.net/problem/2839

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
# 2512 : 예산
## 😎solved code
### 💻code
```python
import sys

n = int(sys.stdin.readline().rstrip())
budget_list = list(map(int,sys.stdin.readline().rstrip().split()))
total_budget = int(sys.stdin.readline().rstrip())

left = 0
right = max(budget_list)
mid = 0
result = 0

while(left <= right):

  mid = (left+right) // 2
  count = 0

  for budget in budget_list:
    if(budget >= mid):
      count += mid
    else:
      count += budget
  
  if(count > total_budget):
    right = mid -1

  elif(count <= total_budget):
    if(mid > result):
      result = mid

    left = mid + 1

print(result)
  ```
## ❗️결과
성공
## 💡접근
M이 10억이하의 숫자이기 때문에 완전탐색을 하게되면 무조건 시간초과가 발생하게 된다. 따라서 이진탐색을 통해서 예산 배정을 하기로 하였다.
1. 배정받고자하는 예산안 리스트 중 가장 큰 값을 right 값으로 두고, 문제의 조건대로 예산안을 모두 더한다.
2. 합쳐진 예산안(count)가 총 예산안보다 적다면, 배정된 예산을 늘려주고 크다면, 배정된 예산안을 이분탐색에 맞게 줄여준다.
3. 총 예산안의 범위내에서 가장 많은 예산을 줄 수 있는 값을 출력한다.

## 🧐문제 회고
문제의 입력조건을 보고 무조건 이분탐색임을 확인할 수 있었다.
이분탐색의 대상이 어떤 값인지를 잘 선정하는 능력을 기르자!

# 1234 : ABCD
## 😎solved code
## 🥺unsolved code
### 💻code
```python

  ```
## ❗️결과

## 💡접근

## 🧐문제 회고

# 43238 : 입국심사
## 🥺unsolved code
### 💻code
```python
def solution(n, times):
    times.sort()
    answer = float("inf")
    left = 0
    right = (n+1) * max(times)
    mid = 0
    
    while(left <= right):
        mid = (left + right) // 2
        total = n
        people = mid // times[0]
        total -= people
        flag = 0
        for i in range(1,len(times)):
            add_time = total * times[i]
            if(add_time > mid):
                left = mid + 1
                flag = 1
                break
        
        if(flag != 1):
            right = mid - 1
            if(mid < answer):
                answer = mid
            
    return answer
  ```
## ❗️결과
테스트 케이스 통과 후 실패
## 💡접근
이 문제 역시 입력 조건이 10억이하라 이분탐색을 생각했다.
1. 가장 입국심사시간이 적은 심사관에서 많은 사람이 갔을 때 모든 사람이 심사를 받는데 걸리는 시간이 가장 작을 것으로 생각했다.\
2. 그래서 총 입국심사 시간을 이분탐색의 대상으로 선정하고, 선정된 총 입국심사 내에 입국심사시간이 가장 적은 심사관에게 가장 많은 수의 인원을 할당하였다.
3. 이후 남은 사람들을 그 이후의 사람들에게 할당하여 총 입국심사시간을 초과하면 입국심사시간을 증가시키고, 적다면 가장 적은 입국심사시간을 출력하였다.

위의 로직으로 테스트 케이스는 통과하였지만 심사관이 3명인 경우 남은 인원을 상황에 따라 재 분배해주어야하는 예외사항이 발생하였다.
그래서 로직을 수정하여 문제풀이를 진행하여야했다.

## 😎solved code
### 💻code
```python
def solution(n, times):
    answer = float("inf")
    
    left = 0
    right = (n+1) * max(times)
    mid = 0
    
    while(left <= right):
        mid = (left + right) // 2
        count = 0
        for time in times:
            accept_people = mid // time
            count += accept_people
            
        if(count < n):
            left = mid + 1
        elif(count >= n):
            right = mid - 1
            if(mid < answer):
                answer = mid
                
    return answer
  ```
## ❗️결과
성공
## 💡접근
1. 순서에 상관없이 각각의 심사관이 총 심사시간동안 심사할 수 있는 인원을 각각 구했다.
2. 각각의 인원들을 모두 더해서 총 심사인원보다 작다면 총 입국심사시간을 이분탐색 로직에 맞게 증가시키고, 총 심사인원보다 많다면 총 입국심사시간을 줄여주었다.

## 🧐문제 회고
심사관들의 심사시간에 맞춰 인원을 할당해야한다는 생각에 초반에 많이 헤맸다.
그러나 결국 심사관들의 심사 순서에 상관없이 주어진 시간에 얼마만큼의 인원을 심사할 수 있느냐를 생각하는 것이 문제풀이의 핵심이였다.
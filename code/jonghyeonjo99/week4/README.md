# 10814 : 나이순 정렬
## 😎solved code
### 💻code
```python
import sys

n = int(sys.stdin.readline().rstrip())

people = []

for i in range(n):
  age,name = sys.stdin.readline().rstrip().split()
  people.append([int(age),name,i])

#나이순, 나이가 같으면 입장순(i)으로 정렬  
people.sort(key= lambda x : (x[0],x[2]))

for age, name, ticket in people:
  print(age, name)
  ```
## ❗️결과
성공
## 💡접근
1. 입력값에 int와 문자열이 섞여있기 때문에 자료형 구분없이 입력값을 받는다.
2. 이후 리스트에 나이, 이름을 저장해줄 때 나이는 int형으로 구분해주고 입장 순서 (i)를 추가로 append한다.
3. 리스트를 lambda를 이용하여 나이순, 나이가 같다면 입장순(i)로 정렬해주고 순서대로 출력해준다.
## 🧐문제 회고
나이의 자료형을 int로 구분해주지않으면 정렬과정에서 의도와 다르게 순서가 뒤로 밀릴 수 있다.
따라서 자료형 구분을 확실하게 해주는게 중요하다!

# 18870 : 좌표 압축
## 🥺unsolved code
### 💻code
```python
import sys

n = int(sys.stdin.readline().rstrip())
num = list(map(int,sys.stdin.readline().rstrip().split()))

num_set = set(num)
num_set = list(num_set)
num_set.sort()

for i in num:
  print(num_set.index(i), end=" ")
  ```
## 😎solved code 
### 💻code
```python
import sys

n = int(sys.stdin.readline().rstrip())
num = list(map(int,sys.stdin.readline().rstrip().split()))

num_set = set(num)
num_set = list(num_set)
num_set.sort()

dic = {}
for i in range(len(num_set)):
  dic[num_set[i]] = i

for i in num:
  print(dic[i], end=" ")
  ```
## ❗️결과
시간초과 후 참조
## 💡접근
1. 리스트의 순서가 출력값 순서와 상관이 있기 때문에 기존의 리스트와 크기를 비교할 수 있는 정렬된 리스트를 하나 더 만들어준다.
2. 중복을 없애기 위해 집합 자료형으로 중복을 제거해준다.
3. 그렇게 생성된 리스트의 인덱스 값과 value값을 딕셔너리에 추가해준다.
4. 딕셔너리의 key, value로 치환된 값을 출력해준다.
## 🧐문제 회고
n의 범위가 1,000,000인 것을 확인하고 이중 for문은 시간초과가 발생할 것으로 예상하였지만, for문을 하나만 사용하였는데도 시간초과가 발생하였다.
원인에 대한 생각을 하다가 구글을 참조하였는데, list의 index값을 가져오는 과정의 시간복잡도가 O(N)임을 새로 배웠다.
그래서 순서가 정해지지않은 key, value를 갖고, O(1)의 시간복잡도를 갖는 딕셔너리 구조를 사용하여 시간복잡도를 개선 시킬 수 있었다.

# 1234 : ABCD
## 😎solved code
## 🥺unsolved code
### 💻code
```python

  ```
## ❗️결과

## 💡접근

## 🧐문제 회고
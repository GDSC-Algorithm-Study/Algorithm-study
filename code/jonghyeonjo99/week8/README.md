# 1647 : 도시분할계획
## 😎solved code
### 💻code
```python
import sys
import heapq

n,m = map(int,sys.stdin.readline().rstrip().split())
billiage = []
queue = []
size = 0
parent = [0] * (n+1)

def find(k):
  if parent[k] != k:
    return find(parent[k])
  return k

def union(a,b):
  a = find(a)
  b = find(b)
  if a < b:
    parent[b] = a
  else:
    parent[a] = b

for i in range(1,n+1):
  parent[i] = i

for i in range(m):
  a,b,c = map(int,sys.stdin.readline().rstrip().split())
  billiage.append((c,a,b))

#유지비가 적은 순으로 정렬
billiage.sort()

for i in range(m):
  if(find(billiage[i][1]) != find(billiage[i][2])):
    union(billiage[i][1], billiage[i][2])
    # 숫자에 '-'를 붙여 최대 힙 구현
    heapq.heappush(queue,(-billiage[i][0], billiage[i][0]))
    size += billiage[i][0]

max_road = heapq.heappop(queue)[1]

print(size - max_road)
  ```
## ❗️결과
성공
## 💡접근
모든 집들이 길로 연결되어있어야한다. 이를 힌트삼아 유니온 파인드 알고리즘을 채택하였다.
유니온 파인드 알고리즘은 각각의 노드들의 부모노드가 다를 때, 같은 부모노드를 바라보게 만들어 하나의 집합으로 연결되게 하는 알고리즘이다.
집을 연결시키는 것을 유니온으로 보고 집이 연결되어있는지는 파인드를 통해 찾고자 하였다.
이때, 길의 유지비가 최소가 되야하기 때문에 서로다른 A와 B 집을 연결하는 길이 2개 이상 있을 때, 유지비가 적은 길을 선택하여 연결시켜야 한다.
그러기위해서는 유지비가 적은 길을 먼저 바라보고 집을 연결시켜야하기 때문에 유지비가 적은 순으로 정렬해주었다.
이후 두 집이 연결되어있지않다면 연결(Union)시켜주고, 유지비를 size에 담았다.
그렇게 모든 집들이 연결되고나서 그 중 유지비가 가장 큰 길 하나를 없애주면 최소 유지비를 갖는 두 마을이 형성된다.

## 🧐문제 회고
오랜만에 보는 유니온파인드 유형이라 문제를보고 알고리즘을 떠올리는데 시간이 꽤 걸렸다.
개념과 구현이 쉬운만큼 잊지않도록 노력하자!

# 1234 : ABCD
## 😎solved code
## 🥺unsolved code
### 💻code
```python

  ```
## ❗️결과

## 💡접근

## 🧐문제 회고

# 1234 : ABCD
## 😎solved code
## 🥺unsolved code
### 💻code
```python

  ```
## ❗️결과

## 💡접근

## 🧐문제 회고
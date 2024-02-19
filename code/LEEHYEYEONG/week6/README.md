# 백준 12865번

## 접근

이런 문제는 냅색 알고리즘으로 풀 수 있다고 한다.

### 냅색 알고리즘

한 배낭에 담을 수 있는 무게의 최댓값이 정해져있고, 일정 가치와 무게가 있는 짐들을 배낭에 넣을 때, 가치의 합이 최대가 되도록 짐을 고르는 방법을 찾는 문제

**냅색 알고리즘을 나누는 기준**

`담을 수 있는 물건이 나뉠 수 있는가, 없는가?`

- 담을 수 있는 물건이 나누어질 때
  - 분할 가능한 배낭 문제(Fractional Knapsack Problem)
- 담을 수 있는 물건이 나누어질 수 없을 때
  - 0-1 배낭 문제(0-1 Knapsack Problem)

냅색 알고리즘의 핵심은 `특정 물건을 담지 않았을 때가 오히려 최선의 선택일 수 있음을 고려`

DP를 이용한 냅색 알고리즘 풀이

가방에 최대 Nkg까지 담을 수 있을 때, dp[i][j]는 다음과 같다.

dp[i][j] → j개의 무게를 가방에 담을 수 있을 때, i개의 물건 중 담을 수 있는 최대 가치

1. j (현재 가방에 담을 수 있는 무게)가 현재 물건의 무게 w보다 작을 때

   1. 현재 물건을 담을 수 없으므로, 이전 물건에서의 i에 해당하던 값 (i - 1)을 넣어준다.

   $$
   dp[i][j] = dp[i-1][j]
   $$

2. j가 현재 물건의 무게 w와 같거나 클 때

   1. 현재 물건을 담을 수 있음
   2. 물건을 담았을 때와 담지 않았을 때의 가치를 비교해준 뒤, 더 큰 값을 할당해줌
   3. 현재 물건의 가치는 v

   $$
   dp[i][j] = max(dp[i-1][j], dp[i-1][j-w] + v)
   $$

물건의 최대 가치는 dp[가방 크기][물건의 개수]로 구할 수 있다.

위 냅색 알고리즘을 이용하여 현재 문제를 풀어보았다.

```python
for i in range(1, n+1):
    for j in range(1, k+1):
        weight = bag[i][0]
        value = bag[i][1]

        if j < weight:
            dp[i][j] = dp[i-1][j]
        else:
            dp[i][j] = max(dp[i-1][j], dp[i-1][j-weight] + value)


print(dp[n][k])
```

## 참고

[[Python] 냅색 알고리즘(Knapsack Problem) - Dynamic Programming(DP)](https://inni-iii.tistory.com/74)

<br>

# 백준 2225번

## 접근

입력받기

```python
import sys
n, k = map(int, sys.stdin.readline().split())

dp = [[0 for _ in range(k+1)] for _ in range(n+1)]
```

예제에서 20 2 → [0 + 20을 1개로 나눈 것] + [1 + 19을 1개로 나눈 것] + … + [19 + 1을 1개로 나눈 것] + [20 + 0을 1개로 나눈 것]

0~20 → 21

이렇게 나타낼 수 있으므로

`dp[n][k] = dp[0][k-1] + dp[1][k-1] + … + dp[n][k-1]`

`dp[n-1][k] = dp[0][k-1] + dp[1][k-1] + … + dp[n-1][k-1]`

따라서 `dp[n][k] = dp[n-1][k] + dp[n][k-1]` 이렇게 된다.

dp[0][0]은 0 하나이기 때문에 1

```python
dp[0][0] = 1

for i in range(0, n+1):
    for j in range(1, k+1):
        dp[i][j] = dp[i-1][j] + dp[i][j-1]

print(dp[n][k] % 1000000000)
```

피보나치처럼 점화식을 이용해서 간단히 풀 수 있는 문제였다.

0 + 20, 1+19… 이런 식으로 하는 방식은 생각해보았는데 어떻게 표현해야할지 고민하면서 참고했다.

잘모르면 하나씩 써보면서 코드를 작성해가면 될 것 같다.

## 참고

[[Python] 백준 2225번: 합분해 풀이](https://jyeonnyang2.tistory.com/54)

<br>

# 프로그래머스 N으로표현

## 접근

예시를 보면 그냥 일의자리 5만쓰는게 아니라 55, 555도 사용가능이라 어떻게 풀어야 할지 짐작이 잘 안간다.

일단 8번을 넘어가면 -1을 반환하기에 시간복잡도를 크게 고려하지 않아도 될 것 같았다.

N을 1개 사용해서 표현 → 5

N을 2개 사용해서 표현 → 55, 5+5, 5-5, 5\*5, 5/5

N이 i개인 경우

→ N을 1번 사용한 수 **사칙연산** N을 i-1번 사용한 수 … N을 i-1번 사용한 수 **사칙연산** N을 1번 사용한 수

`dp[i] 의 원소 = dp [i - j]의 원소 사칙연산 dp[j]`

```python
# N이 i번 사용한 경우
for i in range(1, 9):
    dp[i].append(int(str(N)*(i))) # N, NN, NNN...삽입
```

일단은 사칙연산 말고 N을 i번 반복한 경우를 dp에 넣어준다.

그리고 N이 j번 쓰인 경우의 수와 N이 i-j번 쓰인 경우의 사칙연산을 dp에 넣는다.

```python
for j in range(1, i):
		for x in dp[j]:
				for y in dp[i-j]:
						dp[i].append(x+y)
						dp[i].append(x-y)
						dp[i].append(x*y)
								if y != 0: # 0으로 나누지 않기 위해
										dp[i].append(x//y)
```

궁금한게 코드에서 따로 괄호를 고려하지 않았는 것 같은데 이건 어떻게 되는건지 잘모르겠다.

어차피 dp [i - j]의 원소와 dp[j]의 사칙연산을 고려하기 때문에 따로 고려하지 않아도 되는 것 같기도 하다.

## 참고

[[프로그래머스] N으로 표현](https://yensr.tistory.com/61)
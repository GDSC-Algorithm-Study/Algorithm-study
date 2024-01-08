# 1주차 README
## 수리공 항승 문제 [백준_1449]
- 문제 풀이 방법 O and 코드 구현 O and 채점결과 O

### 문제 파악
- 물이 새는 곳은 신기하게도 가장 왼쪽에서 정수만큼 떨어진 거리만 물이 샌다.
- 길이가 L인 테이프를 무한개 가지고 있다.
- 물을 막을 때, 적어도 그 위치의 좌우 0.5만큼 간격을 줘야 물이 다시는 안 샌다고 생각
- 항승이가 필요한 테이프의 최소 개수를 구하는 프로그램을 작성
- 테이프를 자를 수 없고, 테이프를 겹쳐서 붙이는 것도 가능

### 입력형식
첫째 줄에 물이 새는 곳의 개수 N과 테이프의 길이 L이 주어진다. 둘째 줄에는 물이 새는 곳의 위치가 주어진다. N과 L은 1,000보다 작거나 같은 자연수이고, 물이 새는 곳의 위치는 1,000보다 작거나 같은 자연수이다.
### 출력형식
항승이가 필요한 테이프의 개수를 출력

### 문제풀이
- 입력받는 부분 -> map함수를 이용해서 한꺼번에 입력받도록 
- 알고리즘 부분 -> 문제에서 물이 새는 곳 앞뒤로 0.5cm 간격을 준다고 함 이걸 고려해서 문제에 접근. 테이프 끝 위치를 고려하였다. tape_end가 새는 위치보다 작을 경우 tape_end값을 해당 위치 + 테이프 길이 - 1 (0.5*2)로 갱신, 그리고 사용한 테이프 개수 증가시킴
- if tape_end < li[i]:: 현재 테이프의 끝 위치보다 현재 물이 새는 위치가 더 크다면, 새로운 테이프가 필요한 경우
tape_end = li[i] + L - 1: 테이프의 끝 위치를 갱신, 테이프의 길이 L만큼을 현재 물이 새는 위치에 더하고, 앞뒤로 0.5씩 테이프를 써야하기 때문에 1을 빼준다.



## 강의실 배정 [백준_11000]
- 문제 풀이 방법 O and 코드 구현 O and 채점결과 X

#### 문제 파악
- Si에 시작해서 Ti에 끝나는 N개의 수업이 주어지는데, 최소의 강의실을 사용해서 모든 수업을 가능하게 해야 한다. 
- 수업이 끝난 직후에 다음 수업을 시작할 수 있다. (즉, Ti ≤ Sj 일 경우 i 수업과 j 수업은 같이 들을 수 있다.)

#### 입력
첫 번째 줄에 N이 주어진다. (1 ≤ N ≤ 200,000)
N개의 줄에 Si, Ti가 주어진다. (0 ≤ Si < Ti ≤ 109)

#### 출력
강의실의 개수를 출력

### 문제접근한 방법
강의 시작 시간을 기준으로 정렬한 후 첫번째 강의 끝난 시간을 저장해두고 이걸 업데이트하는 방식으로 문제를 풀거다. 만약 현재 수업시작시간이 last_end_time다 작으면 새로운 방을 사용해야한다. 만약 크거나 같다면 last_end_time이 끝난 강의실을 사용하면 되기에 다른 방은 필요하지 않다.

### 문제회고
시간초과가 많이 발생하였다. headq를 사용하는 방법으로 시도해봐야할 듯하다.
문제에 잘못 접근하였는지 채점결과 틀렸다고 뜬다. 


## 메뉴 리뉴얼 [프로그래머스_72411]
- 문제 풀이 방법 O and 코드 구현 O and 채점결과 O

#### 문제 파악
- 기존에는 단품으로만 제공하던 메뉴를 조합해서 코스요리 형태로 재구성해서 새로운 메뉴를 제공하기로 결정
- 한 단품메뉴들을 코스요리 메뉴로 구성하기로함

#### 조건
- 단, 코스요리 메뉴는 최소 2가지 이상의 단품메뉴로 구성
- 최소 2명 이상의 손님으로부터 주문된 단품메뉴 조합에 대해서만 코스요리 메뉴 후보에 포함
- 각 단품메뉴는 A ~ Z의 알파벳 대문자로 표기

#### 문제
- 각 손님들이 주문한 단품메뉴들이 문자열 형식으로 담긴 배열 orders, "스카피"가 추가하고 싶어하는 코스요리를 구성하는 단품메뉴들의 갯수가 담긴 배열 course가 매개변수로 주어질 때, "스카피"가 새로 추가하게 될 코스요리의 메뉴 구성을 문자열 형태로 배열에 담아 return 하도록 solution 함수를 완성

#### 제한상황
- orders 배열의 크기는 2 이상 20 이하입니다.
- orders 배열의 각 원소는 크기가 2 이상 10 이하인 문자열입니다.
- 각 문자열은 알파벳 대문자로만 이루어져 있습니다.
- 각 문자열에는 같은 알파벳이 중복해서 들어있지 않습니다.
- course 배열의 크기는 1 이상 10 이하입니다.
- course 배열의 각 원소는 2 이상 10 이하인 자연수가 오름차순으로 정렬되어 있습니다.
- course 배열에는 같은 값이 중복해서 들어있지 않습니다.
- 정답은 각 코스요리 메뉴의 구성을 문자열 형식으로 배열에 담아 사전 순으로 오름차순 정렬해서 return 해주세요.
- 배열의 각 원소에 저장된 문자열 또한 알파벳 오름차순으로 정렬되어야 합니다.
- 만약 가장 많이 함께 주문된 메뉴 구성이 여러 개라면, 모두 배열에 담아 return 하면 됩니다.
- orders와 course 매개변수는 return 하는 배열의 길이가 1 이상이 되도록 주어집니다.

### 문제풀이 
입력받은 값으로 모든 가능한 조합을 만든 후, 해당 조합의 문자열의 등장 횟수를 세어보고 
2번이상 나온 것과 course의 횟수에 해당한 것만을 answer로 고려하도록한다.

### 라이브러리
from itertools import combinations
from collections import Counter
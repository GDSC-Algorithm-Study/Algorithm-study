## 1449 수리공 항승

- 접근 방법
  <br/>

  1. 벡터에 구멍 위치를 저장
  2. 오름차순으로 벡터 정렬
  3. 벡터를 순차 탐색하며 구멍 위치부터 테이프로 막을 수 있는 최대 길이 계산.
  4. 이중 반복문으로 최대길이를 넘어갈 때 까지 인덱스 밀기
  5. 최대길이를 넘어갔으면 테이프 사용 갯수 증가
  6. i가 n보다 커질 때 까지 3번으로 돌아가 반복문 탐
     <br/>
     <br/>

- 회고
  <br/>

  알고리즘 문제를 처음 풀어봐서 하루 종일 항승이만 팼다..<br /><br />
  이중 포문 안에서 j를 밀고, 반복문 탈출 시 i = j - 1을 해줘야 i <= n이 됐을 때, 마지막 테이프까지 카운트가 됐었다..<br /><br />
  문제는 알았지만 어떻게 식으로 세워야 할 지 몰라 현재 코드와 같은 이상한 코드가 나왔다..
  <br />
  <br />

---

## 11000 강의실 배정

- 접근 방법
  <br/>

  어떻게 풀어야 될 지 몰라서 주위 분들의 풀이 방법을 참고했다..

  1. 벡터에 강의 시작 시간, 종료 시간을 저장
  2. 벡터 오름차순으로 정렬
  3. 벡터 순차탐색
  4. 우선순위 큐 ( 오름차순 ) 에 "강의 마지막 시간" 을 push
  5. 우선순위 큐의 top ( min ) 과 현재 벡터의 "강의 시작 시간" 을 비교
  6. 큐의 top이 벡터의 시작시간보다 작거나 같으면 동일 강의실을 사용할 수 있으니 top을 pop
  7. 벡터의 끝까지 3번으로 돌아가 반복
  8. 반복문 탈출 후 우선순위 큐의 크기가 강의실 갯수가 됨
     <br/>
     <br/>

- 회고
  <br/>

  우선순위 큐 처음써봣는데 나중에 js로 풀 때, 어캐 구현해야할지 막막하다..<br /><br />
  코드가 너무 간단해서 허탈하다...

  <br />
  <br />

---

## 72411 메뉴 리뉴얼

- 접근 방법
  <br/>

  어떻게 풀어야 될 지 몰라서 주위 분들의 풀이 방법을 또 참고했다..

  1.  combinations 함수를 만들어서 orders에 들어있는 문자열에서 주어진 course의 갯수에 맞는 문자열 조합을 생성한다.
  2.  map = { [ 문자열 조합 ]: count, ... } <- 이런 객체를 만들어서 키가 겹치면 count를 증가시킨다.
  3.  map으로 반복문을 돌면서 max < count ? max = count : max 로 갱신시킨다.
  4.  반복문 탈출 후 max를 값으로 가지는 key를 정답 배열에 푸시한다.
  5.  주어진 course 갯수에 따라 1번으로 돌아가 반복한다...
      <br/>
      <br/>

- 회고
  <br/>

  문제 이해도 안갔다<br /><br />
  이번엔 코드가 너무 복잡해서 힘들다...<br /><br />
  다른 언어는 combination함수 다 있던데 왜 js는 없는지 모르겠다..
  이건 못풀었다고 친다.. 내가 푼 게 아니니까......
## 2512 예산

- 접근 방법
  <br/>

  1. 입력받은 예산을 오름차순으로 정렬
  2. 이진탐색을 인덱스가 아닌 밸류값으로 설정
  3. lower_bound를 사용하여 중앙값을 가진 인덱스를 찾고, 그 인덱스를 기준으로 더 작은값은 기존 값을, 큰 값은 중앙값을 더해 정해진 예산에 초과하는지 확인
  4. 초과한다면 다시 이진탐색을 하여 더 작은 중앙값 설정
  5. 초과하지 않는다면 중앙값을 저장하고, 더 큰 값을 설정할 수 있는지 이진탐색으로 확인
     <br/>
     <br/>

- 회고
  <br/>

  왜 이 문제를 이진탐색으로 풀어야 하는지 한참 고민했다.
  나머지 문제들도.. 이진탐색으로 어떻게 풀어야하는지 고민했지만 답이 안보여서 첫번째 문제만 풀엇다..
  <br />
  <br />

---
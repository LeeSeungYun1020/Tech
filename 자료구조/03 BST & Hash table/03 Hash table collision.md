# Hash table collision
## 충돌이 발생한 경우 어떻게 하나요?
- open addressing
    - 미리 정한 규칙에 따라 빈 슬롯을 찾음
    - Linear probing, Quadratic probing, Double hashing
- separate chaining
  - linked list 이용
  - 충돌이 발생하면 linked list에 노드 추가하여 데이터 저장

## TIP
- 매우 자주 나오고 중요
- open addressing과 separate chaining 방식의 매커니즘과 차이점 알아야
- separate chaining의 worst case 시간복잡도(O(n)) 설명


## Open addressing
- 충돌이 발생하면 미리 정한 규칙에 따라 해시 테이블의 빈 슬롯을 찾음
- 추가적인 메모리 사용이 없으므로 separate chaining에 비해 메모리 적게 사용
- 빈 슬롯을 찾는 방법에 따라 Linear probing, Quadratic probing, Double hashing으로 나뉨
- Linear probing(선형 조사법)과 Quadratic probing(이차 조사법)
  - 충돌이 발생한 해시 값으로 부터 일정한 만큼(+1, +2, +3, ... 또는 +1, +4, +9, ...) 떨어진 빈 슬롯을 찾음
  - 충돌이 여러 번 발생하면 여러 번 건너 뛰어 빈 slot 찾음
  - 충돌 횟수가 많아지면 데이터가 특정 영역에 몰리는 클러스터링 현상 발생 가능 -> 평균 탐색 시간 증가
- Double Hashing(이중 해시)
  - 클러스터링 문제가 발생하지 않도록 2개의 해시 함수 사용
  - 최초 해시값 얻을 때 하나를 사용하고 다른 하나는 해시 충돌이 발생할 때 이동 폭을 얻기 위해 사용

## Separate chaining
- 연결 리스트로 충돌 해결
- 충돌 발생하면 연결 리스트에 노드 추가하여 데이터 저장
- 삽입: 충돌시 연결 리스트에 노드 추가 -> O(1)
- 검색: 기본적으로 O(1), 최악의 경우 O(n)
- 삭제: 삭제를 위해 검색이 필요 -> O(1), 최악의 경우 O(n)
- 최악의 경우는 모든 key가 동일 해시 값 가지는 경우

## 문답
Q. Worst case 시간복잡도는 O(n)이라고 했는데 어떤 상황인가요?
- 모든 key가 동일한 해시값을 가지면 길이 n의 연결 리스트가 생성
- 특정 key를 찾기 위해서는 linked list 검색하는 O(n)의 시간복잡도와 동일

Q. 이중 해싱(double hashing)은 무엇인가요?
- 이중 해싱은 open addressing 방식 이용하여 충돌 해결할 때 probing 하는 방식 중 하나
- linear probing과 quadratic probing에서는 탐사 이동폭이 같아 클러스터링 문제 발생 가능
- 2개의 해시 함수를 이용하여 충돌시 키에 따라 탐사 이동폭이 달라지게 함





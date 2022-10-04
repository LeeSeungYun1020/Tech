# Queue 2개로 Stack 구현

## TIP
- Queue 2개로 stack의 push, pop 구현에 초점
- 해결 과정 어필

## 구현
- q1, q2를 정의
- push는 q1에 enqueue
- pop
  - q1에서 dequeue하여 마지막 항목을 제외하고 q2에 enqueue
  - 마지막 항목이 pop해야 할 data
  - q1, q2 swap

## 시간복잡도
- push: O(1), enqueue만 하면 됨
- pop: O(n), n-1개를 옮겨야(dequeue하여 enqueue하여야) 함
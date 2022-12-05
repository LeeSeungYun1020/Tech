# Stack 2개로 Queue 구현

## TIP
- 현장에서 바로 떠오르기 힘든 아이디어
- stack 2개로 enqueue, dequeue 구현에 초점
- 과정에 초점

## 구현
- instack, outstack을 정의
- enqueue시 instack에 push
- dequeue시
  - outstack이 비어있지 않으면 outstack에서 pop
  - outstack이 비어있으면 instack을 pop하여 outstack에 push 후 outstack에서 pop

## 시간복잡도
- enqueue: O(1), push 한 번만 하면 됨
- dequeue
  - outstack이 비어있지 않으면 O(1), pop 한 번만 하면 됨
  - outstack이 비어있으면 O(n), instack을 pop하여(n번) outstack에 push(n번) 후 outstack에서 pop(1번)
  - 따라서 amortized O(1)의 시간복잡도를 가진다.

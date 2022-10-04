# Queue

## Queue는 어떤 자료구조인가요?
- 큐는 먼저 들어간 항목이 먼저 나오는(FIFO) 자료구조입니다.
- 시간복잡도는 enqueue, dequeue 모두 O(1)입니다.
- 캐시 구현, 프로세스 구현, 너비우선탐색(BFS)에 사용 가능합니다.

## TIP
- 나중에 들어간 항목이 먼저 나오는(LIFO) 스택과 비교
- Circular Queue

## 용어
- FIFO: First In First Out, 먼저 들어간 데이터가 먼저 나온다. 선입선출
- enqueue: 큐에 데이터를 추가
- dequeue: 큐에서 데이터를 꺼냄
- enqueue는 맨 뒤에 데이터 추가하면 되므로 O(1), dequeue는 맨 앞에 데이터 삭제하면 되므로 O(1)

## 구현
- Array-Based Queue: enqueue, dequeue 과정에서 남는 메모리 생김 -> circular queue로 구현
- List-Based Queue: 재할당이나 메모리 낭비 걱정 무

## 확장과 활용
- Deque: 양쪽 끝에서 삽입, 삭제가 가능한 자료구조
- Priority Queue: 우선순위가 높은 데이터가 먼저 나오는 자료구조
- 자원을 공유하는 프린터, CPU task scheduling, 캐시 구현, 너비우선탐색(BFS)

## 문답
Q. Array-base와 List-base의 차이점은 무엇인가요?
- Array-base
  - circular queue로 구현하여 메모리를 효율적으로 사용
  - enqueue가 계속 발생시 고정 size 넘어가므로 dynamic array로 size 확장
  - enqueue이 시간복잡도는 amortized O(1)을 유지
  - 전반적으로 나은 performance이나 size 조정시 느릴 수 있음
- (Linked) List-base
  - singly-linked list로 구현
  - enqueue는 단순히 append하는 것으로 구현되고 deuqeue는 맨 앞 원소를 삭제하고 head를 변경하면 되기 떄문에 O(1)
  - enqueue마다 메모리 할당 필요하여 전반적인 runtime이 느릴 수 있음
- 어떤 자료 구조를 사용하여 구현해도 enqueue, dequeue 모두 O(1)

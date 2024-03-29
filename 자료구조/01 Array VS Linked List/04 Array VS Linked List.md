# Array VS Linked List

## 정의
- Array는 메모리 상에서 연속적으로 데이터 저장하는 자료구조
- Linked List는 메모리상에서 연속적이지 않지만, 각각의 원소가 다음 원소의 주소 값을 저장하여 논리적 연속성 유지

## 시간복잡도
- Array는 조회에 O(1) 랜덤 액세스, 삽입/삭제에 O(n) (맨 마지막 O(1))
- Linked List는 조회에 O(n) 순차 액세스, 삽입/삭제에 O(1) (추가, 삭제하려는 index 도달에 O(n)이 걸리므로 실질적으로 O(n)이 소요되기도 함)

## 사용
- 저장할 데이터 크기를 알고 조회가 많다면 Array
- 데이터 크기가 확실치 않고 삽입, 삭제가 잦다면 Linked List

## 메모리
- Array는 fixed size이든 dynamic size이든 데이터가 저장되어 있지 않아도 메모리를 차지하기 때문에 메모리 낭비 발생
- Linked List는 런타임 중에 사이즈 조절이 가능, 처음 size를 고민할 필요가 없고 필요한 만큼 메모리 할당하여 낭비가 적음


## 문답

Q. 언제 Linked List가 더 유리한가요?
- 얼마만큼의 데이터가 들어올지 예측할 수 없을 때
- 조회 작업이 적고 삽입 삭제가 많은 경우

Q. 언제 Array가 더 유리한가요?
- 데이터 사이즈가 정해져 있는 경우
- 조회 작업을 자주 해야 하는 경우
- 반복문을 통해 빠르게 순회할 때
- 메모리를 적게 서용하는 것이 중요한 경우, 들어올 데이터 양을 알고 있다면 array가 더 효율적(연결 리스트는 다음 주소를 저장해야 함)

Q. Array와 Linked List의 memory allocation은 언제 일어나며, 메모리의 어느 영역을 할당받나요?
- Array는 컴파일 단계에서 메모리 할당(static memory allocation), 스택 영역에 할당됨
- Linked List는 런타임 시간에 새로운 노드 추가시마다 메모리 할당(dynamic memory allocation), 힙 영역에 할당됨
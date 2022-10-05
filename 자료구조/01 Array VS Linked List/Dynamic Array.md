# Dynamic Array

배열은 사이즈가 고정되어 선언시에 설정한 크기보다 많은 데이터를 추가할 수 없음  
Dynamic array는 저장공간이 가득차면 **resize하여** 유동적으로 크기를 조절할 수 있음

TIP  
1. resize 방식
2. append 시간복잡도

## resize 방식
원래 배열보다 큰 사이즈 배열 선언하고 옮김. 기본 배열은 메모리에서 삭제  
doubling: 기존 사이즈보다 두배 더 큰 배열 선언하여 데이터를 옮김

## append 시간복잡도
데이터를 추가할 때에는 O(1), 사이즈를 키울 때는 배열을 옮기는 것이 필요하므로 O(n)
분할상환 시간복잡도(Amortized time complexity): O(1) -> 주로 O(1)이고 가끔 resize가 필요한 경우 O(n)이 발생  

Q. Dynamic Array(동적 배열)와 Linked List(연결 리스트) 비교  
Dynamic Array의 장점
- 데이터 접근이 O(1)으로 빠름 (random access, 주소값 + offset으로 바로 접근 가능)
- 맨 뒤에 데이터 추가 삭제가 O(1)으로 빠름

Dynamic Array의 단점
- 중간에 데이터 추가, 삭제시 느린 편(연속적으로 데이터 저장되어 있어 shift 필요)
- resize시 낮은 performance(O(n)) 발생
- 사용하지 않고 남는 메모리 공간 발생 (resize 통해 필요한 것 이상으로 메모리 공간 할당함)
# 멀티 프로세스와 멀티 스레드
## TIP
- 동시에 여러 작업을 수행한다는 점에서 유사한 측면이 있음
- 적용할 시스템에 따라 두 방법의 장단점을 고려하여 적합한 방법 선택
  - 하나의 프로그램을 설계할 때, 멀티 프로세스 방식을 취할 것인지, 멀티 스레드 방식을 취할 것인지를 물어보는 것
  - 안정성 관점에서 멀티 프로세스가 유리
  - Context switching이 자주 일어나고 데이터 공유가 빈번하여 자원을 효율적으로 사용해야 하는 경우 멀티 스레드가 유리

## 멀티 스레드 관점
- 멀티 스레드로 구현할 경우 메모리 공간과 시스템 자원 소모가 줄어듬
- 프로세스 생성하고 자원 할당하는 것과 같은 system call 생략 가능 -> 효율적인 자원 관리
- 프로세스간 통신(IPC)보다 스레드 간의 통신 비용이 적기 때문에 통신으로 인한 오버헤드가 적음
- Context switching 시 캐시 메모리를 초기화할 필요가 없어 스위칭 속도가 빠름
- 스레드간 자원을 공유하기 때문에 동기화 문제가 발생 가능
- 하나의 스레드의 문제로 전체 스레드가 종료될 수 있음(프로세스는 하나가 종료되더라도 다른 프로세스에 영향 주지 않음)

|         | 메모리 공간 | CPU 시간 | Context switching | 안정성 |
|---------|--------|--------|-------------------|-----|
| 멀티 프로세스 | 많이 필요  | 많이 차지  | 느림                | 높음  |
| 멀티 스레드  | 적게 필요  | 적게 차지  | 빠름                | 낮음  |

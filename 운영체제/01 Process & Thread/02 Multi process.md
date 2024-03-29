# 멀티 프로세스

## 멀티 프로세스에 대해 설명
- 2개 이상의 프로세스가 동시에 실행되는 것
- 동시성과 병렬성
- 동시성: 여러 프로세스를 짧은 시간 동안 번갈아 가면서 연산하게 되는 시분할 시스템으로 실행
- 병렬성: CPU 코어가 여러 개일 때, 각각의 코어가 각각의 프로세스를 연산하여 실제로 프로새스가 동시에 실행되는 것

## TIP
- 병렬성 보다 동시성 개념이 중요
- 동시성을 통해 하나의 코어가 동시에 여러 프로세스를 처리
- 면접에서는 시분할 시스템, context, PCB, context switching, process의 메모리 영역을 설명해야

## 멀티 프로세스
- 2개 이상의 프로세스가 동시에 실행되는 것
- 프로세스들은 CPU와 메모리를 공유
- 메모리의 경우 여러 프로세스들이 각자 메모리 영역 차지하며 동시에 적재
- CPU는 매순간 하나의 연산만 가능하지만 처리 속도가 매우 빨라 짧은 시간 간격에 
여러 프로세스들이 CPU에서 번갈아 실행되므로 여러 프로그램이 동시에 실행되는 것처럼 보인다.
- CPU 작업 시간을 여러 프로세스들이 나누어 쓰는 시스템을 시분할 시스템이라고 부름

## 메모리 관리
- 운영체제가 서로 다른 프로세스의 영역을 침범하지 않도록 관리(자신의 메모리 영역에만 접근하도록)

## CPU 연산과 PC 레지스터
- CPU는 프로그램 카운터 레지스터가 가리키고 있는 명령어를 읽어들여 연산 진행
- 멀티 프로세스에서는 프로세스1의 코드 영역을 가리키다가 프로세스2가 진행되면 프로세스2의 코드 영역을 가리키게 됨
- 프로그램 카운터 레지스터가 가리키는 곳에 따라 프로세스를 변경해 가면서 명령어를 읽어들이고 연산

## Context
- 프로세스가 현재 어떤 상태로 수행되고 있는지에 대한 정보
- PCB(Procsee Control Block)에 저장

## PCB
- 프로세스의 상태 정보를 저장하는 운영체제의 자료구조
- 중요한 정보이므로 일반 사용자가 접근하지 못하도록 보호된 메모리 영역 안에 저장됨
- 프로세스 상태, 프로세스 번호, 프로그램 카운터, 레지스터, CPU 스케줄링 정보, 우선순위, 메모리 정보 등 저장

## Context Switch
- 한 프로세스에서 다른 프로세스로 CPU 제어권을 넘겨주는 것
- 이전 프로세스의 상태를 PCB에 저장하여 보관
- 새로운 프로세스의 PCB를 읽어서 보관된 상태를 복구

## Process의 state
- 실행: 프로세스가 CPU를 점유하고 명령을 수행 중인 상태
- 준비: CPU가 할당되면 즉시 명령을 수행할 수 있도록 준비된 상태
- 봉쇄: CPU를 할당받아도 명령을 실행할 수 없는 상태
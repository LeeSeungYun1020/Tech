# TCP/IP와 OSI

## 개요
- OSI 7계층은 네트워크 통신을 표준화한 모델로 통신 시스템을 7단계로 나누어 설명한 것
- OSI 모델을 실무넉으로 이용하기 복잡한 탓에 실제 인터넷에서는 이를 단순화한 TCP/IP 4계층을 사용

## TIP
- 네트워크를 이해하기 위해 필요한 기본적인 내용
- OSI 7계층 각 단계에서 어떤 동작이 일어나는지를 중점적으로 공부
- TCP/IP 4계층과의 차이점은 무엇인지 비교하며 공부

## OSI 7계층과 TCP/IP 4계층

|    OSI 7 layer     |     TCP/IP 4 layer      |             Protocols             |
|:------------------:|:-----------------------:|:---------------------------------:|
| Application layer  |    Application layer    | HTTP, FTP, DNS, Telnet, SMTP, SSH |
| Presentation layer |            〃            |                 〃                 |
|   Session layer    |            〃            |                 〃                 |
|  Transport layer   |     Transport layer     |             TCP, UDP              |
|   Network layer    |     Internet layer      |           IP, ICMP, AR            |
|  Data link layer   | Network interface layer |             Ethernet              |
|   Physical layer   |            〃            |                 〃                 |

- 각 계층은 하위 계층의 기능을 이용하고 상위 계층에 기능을 제공
- 예를 들어 HTTP 프로토콜은 TCP 프로토콜과 IP 프로토콜을 이용해서 작동
- 일반적으로 상위 계층 프로토콜은 소프트웨어로, 하위 계층 프로토콜은 하드웨어로 구현

## 캡슐화와 역캡슐화
- 캡슐화: 통신 프로토콜의 특성을 포함한 정보를 헤더에 포함시켜서 하위 계층에 전송하는 것
- 역캡슐화: 통신 상대측에서 헤더를 역순으로 제거하여 원래의 데이터를 얻는 과정
- Ex: 사용자가 최상위 계층인 응용 계층에서 입터넷 접속(HTTP), 메일 전송(SMTP), 파일 전송(FTP), 원격 로그인(Telnet) 작업 수행
  - 사용자 입장에서는 데이터가 바로 전송되는 것처럼 보임
  - OSI 7계층 관점에서 캡슐화, 역캡슐화 과정까지 살펴보면
  - 사용자가 전송하고자 하는 데이터가 하위 계층에 전달될 때, 각 프로토콜의 정보를 헤더에 포함시켜서 전달(캡슐화)
  - 수신자는 이러한 헤더를 역순으로 하나씩 제거하면서 상위 계층으로 데이터를 전달하고 최종적으로 원본 데이터를 수신(역캡슐화)

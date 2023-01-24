# 3-way handshake

## 개요
- 3-way handshake는 TCP/IP 프로토콜로 통신하기 전, 정확한 정보 전송을 위해 상대와 세션을 수립하는 과정
- 클라이언트가 서버에게 접속을 요청하는 SYN 패킷을 보내면 서버는 요청을 수락하는 ACK를 포함하여 SYN과 ACK 패킷을 클라이언트에 발송
- 클라이언트가 이를 수신하면 다시 ACK 패킷을 서버에게 보내고, 서버가 이를 수신하여 세션을 수립하여 데이터를 주고받을 수 있게 됨

## TIP
- 전공자라면 꼭 알아야 하는 내용 - 기본을 잘 알고 있는지 확인하는 용도
- 기초적인 네트워크 지식
- HTTP 1.1, 2.0 버전 모두 TCP 프로토콜 사용 -> 특정 사이트에 접속할 때 서버와 내 컴퓨터가 3-way handshake로 서로를 확인
- 3-way handshake의 목적, 각 단계별 절차를 중점적으로
- 4-way handshake도 알고 있으면 좋음

## 3-way handshake
- TCP 통신은 3단계의 과정을 거치며, connection setup 단계에서 3-way handshake가 이루어짐
  - connection setup - tcp 연결 초기화, 3-way handshake
  - data transfer - 데이터 전송
  - connection termination - tcp 연결 종료, 4-way handshake

| Client |                         | Server |
|--------|:-----------------------:|--------|
| 접속 요청  |      ---- SYN --->      |        |
|        |   <--- SYN + ACK ----   | 요청 수락  |
| 응답     |      ---- ACK --->      |        |
|        | <--- data transfer ---> |        |

## 4-way handshake
- TCP 연결을 종료하는 connection termination 단계에서 4-way handshake가 이루어짐
- 양방향으로 2개의 연결이 독립적으로 닫히기 때문에 4-way로 구성
  - 클라이언트 프로세스에서 active close하면 클라이언트 TCP에서 FIN 세그먼트를 전송
  - 서버는 FIN에 대한 ACK 전송, 서버 내의 프로세스에 EOF를 보냄(아직 프로세스는 close되지 않을 수 있음)
  - 서버 프로세스에서 passive close를 받으면 서버 TCP에서 FIN 세그먼트를 전송
  - 클라이언트는 FIN에 대한 ACK 전송, 서버 TCP가 ACK를 받으면 연결 종료

| Client                       |                         | Server                        |
|------------------------------|:-----------------------:|-------------------------------|
|                              | <--- data transfer ---> |                               |
| client process의 active close |      ---- FIN --->      | server process에 EOF 전송        |
|                              |      <--- ACK ----      | FIN에 대한 응답                    |
|                              |      <--- FIN ----      | server process의 passive close |
| FIN에 대한 응답                   |      ---- ACK --->      |                               |


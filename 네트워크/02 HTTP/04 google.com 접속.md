# google.com 접속 과정을 네트워크 관점에서 설명
## 개요
- www.google.com을 주소 창에 입력했을 때 화면이 나오기까지의 과정을 네트워크 관점에서 설명

1. 사용자가 브라우저에 URL 입력
2. 브라우저는 DNS를 통해 서버의 IP 주소 찾음
3. 클라이언트에서 HTTP request 메시지 -> TCP/IP 패킷 생성 -> 서버로 전송
4. 서버에서 요청에 대한 HTTP response 메시지 -> TCP/IP 패킷 생성 -> 클라이언트로 전송
5. 도착한 HTTP response message는 웹 브라우저에 의해 랜더링

## TIP
- 매우 자주 나옴
- 웹 개발의 전반적인 프로세스를 잘 이해하고 있는지 다각적으로 판단
- 네트워크 관점에서 절차에 따라 설명하면 되나 프론트, 백 관점에서 질문할 수도 있음
- 사용자가 입력한 URL이 어떻게 IP로 변환되고 
요청 메시지가 전달되는 절차와 
HTTP 프로토콜, TCP 프로토콜을 거쳐 패킷이 되는 과정, 
응답 메시지를 받은 서버에서 HTTP 응답 메시지를 구성하여 클라이언트로 전송하는 것을 
절차에 맞게 순서대로 설명

## network 관점에서 웹 동작 방식 설명

| 동작                    | 출발                           | 도착                           |
|-----------------------|------------------------------|------------------------------|
| User input            | User                         | Browser                      |
| URL                   | Browser                      | Application layer - HTTP     |
| domain name           | Application layer - HTTP     | DNS server                   |
| IP Address            | DNS Server                   | Application layer - HTTP     |
| HTTP request message  | Application layer - HTTP     | Transport layer - TCP        |
| TCP/IP packet         | Client Transport layer - TCP | Server Transport layer - TCP |
| HTTP request message  | Transport layer - TCP        | Application layer - HTTP     |
| URL                   | Application layer - HTTP     | Server                       |
| response data         | Server                       | Application layer - HTTP     |
| HTTP response message | Application layer - HTTP     | Transport layer - TCP        |
| TCP/IP packet         | Server Transport layer - TCP | Client Transport layer - TCP |
| HTTP response message | Transport layer - TCP        | Application layer - HTTP     |
| response data         | Application layer - HTTP     | Browser                      |
| HTML rendering        | Browser                      | User                         |

1. 사용자가 브라우저에 www.google.com(URL)을 입력, HTTP request message 생성
2. DNS lookup으로 해당 domain의 서버 IP 주소를 알아냄
3. 반환된 IP 주소로 HTTP request message를 TCP/IP 패킷으로 변환하여 서버로 전송
    - 생성된 HTTP 요청 메시지를 TCP/IP 층에 전달
    - 요청 메시지에 헤더를 추가하여 TCP/IP 패킷 생성
4. 패킷은 전기 신호로 랜선을 통해 네트워크로 전송, 목적지 IP에 도착
5. 구글 서버에 도착한 패킷은 unpacking을 통해 메시지로 복원되고 서버의 프로세스로 보내짐
6. 서버의 프로세스는 HTTP 요청 메시지에 대한 response data를 담아 HTTP response message를 생성
7. HTTP response message를 TCP/IP 패킷으로 변환하여 클라이언트 IP로 전송
8. 클라이언트는 패킷을 복원하여 응답 메시지에 담긴 데이터를 얻고 이를 바탕으로 웹 브라이저에서 HTML 렌더링을 하여 모니터에 사이트가 표시

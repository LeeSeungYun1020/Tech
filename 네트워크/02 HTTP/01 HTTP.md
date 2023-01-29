# HTTP

## 개요
- HyperText Transfer Protocol
- 서버-클라이언트 모델을 따르면서 request-response 구조로 웹 상에서 정보를 주고받을 수 있는 프로토콜
- TCP/IP 기반으로 작동하며, connectionless와 stateless 특성을 지님

## TIP
- 매우 광범위한 질문
- HTTP가 어떤 용어의 약자인지, 구성 요소나 특징을 묻기도 함
- 기본적인 구조와 특징은 꼭 숙지

## HTTP
- HyperText Transfer Protocol의 약자
- 웹 상에서 정보를 전송하기 위한 통신 프로토콜로 HTML 같은 문서 전송에 사용

## 구조
- 클라이언트가 HTTP Request를 서버에 보내면 서버는 HTTP response를 클라이언트에 전송
- request message는 start line(method, path, http version), header, body로 구성
- response message는 status line(status code, status message, http version), header, body로 구성

## 특성
- connectionless
  - 서버에 연결 후 요청에 응답을 받으면 연결을 끊음
  - 많은 사람이 이용하더라도 동시 접속을 최소화하여 더 많은 유저의 요청 처리 가능
- stateless
  - connectionless 특성 때문에 클라이언트의 이전 상태를 알 수 없음
- 정보를 유지할 수 없는 특성을 가진 HTTP의 단점 해결을 위해 쿠키, 세션, jwt 등이 도입
- 정보를 텍스트 형식으로 주고받으므로 중간에 인터셉트하여 데이터 유출이 방생 가능 -> 암호화를 추가한 프로토콜 HTTPS 등장

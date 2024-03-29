# 쿠키와 세션
## TIP
- 쿠키와 세션 각각의 특징을 제대로 이해하여 차이점 설명
- 저장 위치의 차이와 이에 따른 보안성, 부하에 대해 설명하면 좋음

## 쿠기와 세션 사용 배경
- HTTP의 connectionless(비연결성), stateless(비상태성)한 특징 때문
- 클라이언트가 요청했을 때, 요청에 맞는 응답을 보낸 후 연결을 끊고 클라이언트에 대한 상태 정보를 유지하지 않음
- 대표적으로 로그인, 장바구니 기능을 예시로 들 수 있음
  - 페이지를 이동하여도 로그인 상태가 유지되게 구현 가능
  - 페이지 재방문시 자동 로그인 기능 구현 가능
  - 쇼핑몰 장바구니 목록을 유지할 수 있음
  - 더이상 보지 않기 등 팝업 관련 기능을 제어할 수 있음

## 쿠키
- 클라이언트(브라우저)에 key-value 쌍으로 저장되는 데이터 파일
- 유효기간 내에는 브라우저가 종료되어도 계속 유지
- 서버에서 response header에 set-cookie 속성을 사용하여 클라이언트에 쿠키 생성
- 브라우저는 매요청시 쿠키를 request header에 담아 서버에 전송
- 쿠키의 생성과 저장은 구현에 따라 다를 수 있으나 원리는 동일
  - 서버가 클라이언트로부터 요청을 받으면 클라이언트에 관한 정보를 토대로 쿠키 구성
  - 서버는 클라이언트에게 보내는 응답의 헤더에 쿠키를 담아 보냄
  - 클라이언트는 응답을 받으면 브라우저가 쿠키를 쿠키 디렉토리에 저장

| Client         |                                          | Server |
|----------------|:----------------------------------------:|--------|
|                |            -- request page ->            |        |
|                |       <- response - set-cookie --        |        |
|                |  -- request - header include cookie ->   |        |
|                | <- response - with ref to cookie info -- |        |
| cookie storage |                                          |        |

## 세션
- 쿠키를 사용하여 사용자 정보를 서버에 저장하여 관리하는 방법
- 클라이언트 구분을 위해 각 클라이언트마다 세션 ID를 부여하고 클라이언트는 쿠키에 세션 ID를 저장
- 유효기간이 있어 일정 시간 응답이 없으면 세션을 종료(서버에서 해당 세션 삭제 가능)할 수 있고 브라우저가 종료될 때까지 인증 상태 유지 가능
- 사용자 정보는 서버에 있기 때문에 쿠키보다 보안성이 좋고 서버 용량 내에서 제한 없이 데이터 저장 가능
- 단 서버 자원을 차지하므로 서버 과부하, 성능 저하의 요인이 될 수 있음

| Client                           |                                                   | Server                                |
|----------------------------------|:-------------------------------------------------:|---------------------------------------|
|                                  |                -- request page ->                 |                                       |
|                                  |      <- response - set-cookie(session ID) --      |                                       |
|                                  | -- request - header include cookie(session ID) -> |                                       |
|                                  |     <- response - with ref to session info --     |                                       |
| cookie storage<br/>(session ID)  |                                                   | DB or Memory<br/>(session ID + info)  |

## 세션이 보안이 좋은데 쿠키를 사용할 이유는 없겠네요?
- 세션은 서버 자원을 사용하기 때문에 서버가 느려질 수 있고 서버 자원이 부족할 수 있음
- 쿠키를 사용하면 서버 자원의 낭비를 방지하여 웹사이트 속도를 높일 수 있음
- 보안성이 중요하지 않은 정보는 쿠키를 사용하는 편이 나을 수 있음

## 쿠키를 사용하는 예시
- 로그인 - 자동 로그인, 페이지 이동시에도 유지, 아이디 저장
- 팝업 - *일 간 다시 보지 않기
- 쇼핑몰 장바구니
# 쿠키와 세션을 이용한 로그인
## TIP
- HTTP는 비연결성, 비상태성 특성 때문에 서버는 클라이언트가 로그인 하더라도 이후 요청에서 로그인 했는지 알 수 없음
- 쿠키와 세션을 활용하면 로그인 상태를 유지 가능
- 어떤 절차로 로그인이 되고 상태가 저장되는지 이해하여 설명할 수 있어야 함
  - 화이트보드에 그려보라고 요청하는 경우 있음

## 인증과 인가
- 인증(authentication): 사용자가 누구인지 확인하는 과정, 회원가입/로그인
- 인가(authorization): 사용자가 요청하는 것에 대해 권한이 있는지 확인하는 절차

## 쿠키와 세션을 통한 인증과 인가
1. 클라이언트가 로그인하면 서버는 회원 정보를 대조하여 **인증**
2. 서버는 회원 정보를 세션 저장소에 생성하고 session ID를 발급
3. 서버는 http response header 쿠키에 발급한 session ID를 담아 전송
4. 클라이언트(브라우저)는 쿠키 저장소에 session ID를 저장, 이후에 http request 전송 시 쿠키에 session ID를 담아 전송
5. 서버는 쿠키에 담긴 session ID를 세션 저장소에서 찾아 회원 정보를 확인(**인가**)
6. 서버는 response message에 회원 정보를 바탕으로 처리된 데이터를 담아 클라이언트에 전송

- 사용자가 로그인하면 서버는 session ID를 발급하여 쿠키로 클라이언트에게 전송
- 클라이언트는 session ID를 쿠키 저장소에 저장하고 요청 시마다 헤더에 담아서 보냄
- 서버는 session ID에 해당하는 클라이언트 정보를 세션 저장소에서 가져옴
- 클라이언트 정보에 맞는 맞춤 응답 가능

## 장단점
- session ID만 쿠키에 담아 요청하므로 요청마다 사용자 정보를 쿠키에 담아 전송하는 것보다는 안전
- Session hijacking: session ID가 노출되므로 노출된 session ID로 다른 사용자가 서버에 요청하면 서버는 구별해낼 수 있는 방법이 없음
  - https를 사용하거나 session에 짧은 주기의 만료 시간을 설정
- 로드 밸런싱 및 서버 효율성 관리 및 확장이 어려워질 수 있음
  - 여러 대의 서버를 사용하는 시스템의 경우, 세션 저장소가 분리되어 있으므로 로그인한 유저는 처음 로그인했던 서버를 통해서만 서비스 가능

| Client |                                                 | Server |                        | Database<br/>(or memory) |
|--------|:-----------------------------------------------:|--------|:----------------------:|--------------------------|
|        |                   -- Login ->                   |        |                        |                          |
|        |                                                 |        |   <- check member ->   | User database            |
|        |                                                 |        |  -- create session ->  | Session storage          |
|        |                                                 |        |    <- session ID --    |                          |
|        | <- response --<br/>(cookie include session ID)  |        |                        |                          |
|        |  -- request -><br/>(cookie include session ID)  |        |                        |                          |
|        |                                                 |        | -- check session ID -> | Session storage          |
|        |                                                 |        |    <- user info --     |                          |
|        | <- response --<br/>(include user specific data) |        |                        |                          |

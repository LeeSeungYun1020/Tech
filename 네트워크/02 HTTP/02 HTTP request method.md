# HTTP request method
## 개요
- GET, POST, PUT, DELETE, PATCH 등이 있음
- GET: 리소스 요청
- POST: 리소스 생성, 기타 데이터 처리 요청
- PUT: 리소스 전체 교체(여러 번 요청해도 같은 효과)
- PATCH: 리소스의 일부 필드 교체
- DELETE: 리소스 삭제

## TIP
- 매우 자주 나옴
- GET, POST 비교가 가장 자주 등장 -> 차이점(데이터를 어디에 포함하는지, 캐시 가능 여부, 보안, 용도)
- PATCH, PUT의 차이 -> PUT은 전체 리소스, PATCH는 일부 리소스 변경한다는 점 기억!

## GET
- 클라이언트가 서버에 리소스를 요청할 때 사용
- URL 주소 뒤에 쿼리 스트링을 key-value 쌍으로 parameter 포함하여 전송
- 캐시 가능, 한 번 서버에 GET 요청한 적이 있다면 브라우저가 결과를 저장해두었다가 동일한 요청시 저장된 값을 가져올 수 있음

## POST
- 클라이언트가 바디를 통해 전달한 데이터를 서버에게 데이터 처리를 요청할 때 사용
- 서버는 리소스에 따라 다양한 처리 - 주로 데이터 생성이며 그 외 변경, 특정 프로세스도 처리

## PUT
- 리소스 전체 교체
- 해당 리소스 없으면 생성
- 여러 번 요청해도 같은 효과

## PATCH
- 리소스의 일부 필드 교체

## GET과 POST를 비교하여 설명
- GET은 클라이언트가 서버에게 리소스를 요청할 때 사용
- POST는 클라이언트가 서버에게 데이터 처리를 요청할 때 사용

- GET은 필요한 정보 특정을 위해 URL 뒤에 쿼리 스트링을 붙여 전달
- POST는 전달할 데이터를 바디에 포함하여 전달

- GET은 URL의 쿼리 스트링까지 포함하여 브라우저 히스토리에 남으며 캐시 가능(같은 요청시 빠르게 접근 가능)
- POST는 브라우저 히스토리에 남지 않고 캐시도 불가능

## PUT과 PATCH를 비교하여 설명
- 서버의 리소스를 업데이트한다는 공통점이 있음
- PUT은 리소스 전체를 교체
- PATCH는 리소스의 일부 필드를 교체
# Index 설정할 column 선택
## 개요
- index는 where 절에서 자주 조회되고, 수정 빈도가 낮으며, 카디널리티는 높고, 선택도가 낮은 column을 선택해서 설정하는 것이 가장 좋음
- 조회 활용도: 높을수록 적합(where 절에서 자주 사용)
- 수정 빈도: 낮을수록 적합
- 카디널리티: 높을수록 적합(데이터 중복이 적음)
- 선택도: 낮을수록 적합

## 카디널리티와 선택도
- 카디널리티: 데이터가 중복되지 않는 정도
  - Ex: 주민등록번호, 사번, 학번은 중복되는 값이 없으므로 카디널리티가 높음
- 선택도: 데이터에서 특정 값을 잘 골라낼 수 있는 정도
  - Ex: 모든 데이터가 unique할 경우 선택도는 1

## TIP
- index를 어떤 column에 대해 생성해야 좋은지 판단 근거를 묻는 것
- index를 사용하면 검색 속도가 빨라지지만 추가 저장 공간이 필요하고 데이터 변경 시 속도가 느려짐
- 몇 가지 예시를 가져와서 이러한 경우에 index를 적용하는게 좋을지 안좋을지 질문
  - 조회 활용도와 수정 빈도, 데이터 중복 정도를 고려해서 답변

## 효과적인 index 사용 방법
- select where 절에 자주 사용되는 column에 대해 index를 생성
- 데이터 수정 빈도가 낮을수록 적합, 데이터 변경 시 index 재구성 필요하기 때문
- 데이터 중복이 높은 column은 효과 별로 없음(성별은 종류가 2가지 뿐이므로 생성하지 않는 것이 좋음, 선택도가 낮을 때 유리)
- 데이터 양이 많을수록 index로 인한 성능 향상이 큼(데이터가 적은 경우 index의 혜택보다 손해가 클 수 있음)
- join 조건으로 자주 사용되는 column
- 한 테이블에 index가 너무 많으면 데이터 수정시 소요되는 시간이 많이 길어질 수 있음(테이블당 4-5개 권장)


## 예상 질문
### index 사용하면 성능 향상되니까 모든 칼럼에 사용하면 되겠네요?
- 아님
- select where 절에서 성능 향상
- 데이터 수정 시에는 성능 저하 가능 -> 모든 index를 업데이트 해야하기 때문
- 또한 index마다 별도의 저장 공간도 차지
- 따라서 무분별하게 index를 생성해서는 안됨

### 고객 DB에서 성별 column에 index를 생성하면 좋을까요?
- 아님
- 성별은 남, 여 2가지 뿐이므로 카디널리티가 매우 낮고 선택도는 매우 높음
- 탐색 범위 축소에 큰 도움이 되지 않음
- index의 이점은 매우 적고 오히려 저장 공간 차지와 데이터 수정 시 성능 저하를 고려할 때, 생성하지 않는 것이 좋음

### 그렇다면 boolean 값에서 true가 1%, false가 99%라면 index를 생성하는 것이 좋을까요?
- 아님
- 비율에 차이가 있더라도 두 종류이므로 카디널리티는 매우 낮고 선택도는 매우 높음
- index가 주는 이점은 매우 작고 저장 공간 차지와 성능 저하를 고려할 떄, 생성하지 않는 것이 좋음
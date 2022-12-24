# Primary key
## 개요
- candidate key 중 선택한 main key
- 각 row(행)를 구분하는 유일한 column(열)
- 중복 및 널 값 불가
- 테이블당 하나만 지정해야

## TIP
- 키와 관련된 기본적인 용어 숙지
- 후보키, 대체키, 복합키 같이 키 관련 용어 묶어서 정리 필요

## Relation
- 데이터베이스에서 사용되기 위한 조건을 갖춘 테이블
- 제약 조건
  - 테이블의 셀은 단일 값
  - 동일하지 않은 row

## Super key, 슈퍼 키
- 각 row를 유일하게 식별할 수 있는 하나 이상의 속성들의 집합
- 유일성: 하나의 키 값으로 특정 row만을 유일하게 찾아낼 수 있는 속성

## Candidate key, 후보 키
- Super key 중 더이상 쪼개질 수 없는 Super key
- 각 row를 유일하게 식별하는데 필요한 최소한의 column들의 집합
- 최소성: 모든 row를 유일하게 식별하는데 꼭 필요한 속성만으로 구성

## Primary key, 기본 키
- candidate key 중 선택한 main key -> 유일성과 최소성을 모두 만족
- 각 row(행)를 구분하는 유일한 column(열)
- 중복 및 널 값 불가
- 테이블당 하나만 지정

## Alternative key, 대체 키
- 후보 키가 여러 개일 경우, 기본 키(primary key)로 지정되지 않은 후보 키(candidate key)

## Foreign key, 외래 키
- 다른 테이블의 primary key와 연결(참조)되는 테이블의 column

## Composite key, 복합 키
- 테이블에서 각 row를 식별할 수 있는 두 개 이상의 column으로 구성된 후보 키(candidate key)

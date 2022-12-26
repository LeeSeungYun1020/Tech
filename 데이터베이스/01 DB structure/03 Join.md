# Join
## 개요
- 여러 개의 테이블을 서로 연결하여 하나의 결과로 만드는 것
- inner join은 두 테이블에 모두 있는 내용만 join
- left outer join은 왼쪽 테이블의 모든 row(행)에 대해 join 진행

## TIP
- inner join과 left outer join의 차이를 이해

## SQL
- select * from A inner join B on A.b_id = B.a_id;
- select * from A left join B on A.b_id = B.a_id;
- left join에서 오른쪽 테이블에 없는 항목은 null로 채워짐
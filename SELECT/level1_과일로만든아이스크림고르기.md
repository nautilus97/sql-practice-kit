# 과일로 만든 아이스크림 고르기

### 문제 설명
다음은 아이스크림 가게의 상반기 주문 정보를 담은 `FIRST_HALF` 테이블과 아이스크림 성분에 대한 정보를 담은 `ICECREAM_INFO` 테이블입니다. `FIRST_HALF` 테이블 구조는 다음과 같으며, `SHIPMENT_ID`, `FLAVOR`, `TOTAL_ORDER`는 각각 아이스크림 공장에서 아이스크림 가게까지의 출하 번호, 아이스크림 맛, 상반기 아이스크림 총주문량을 나타냅니다. `FIRST_HALF` 테이블의 기본 키는 `FLAVOR`입니다.

| NAME         | TYPE       | NULLABLE |
| ------------ | ---------- | -------- |
| SHIPMENT_ID  | INT(N)     | FALSE    |
| FLAVOR       | VARCHAR(N) | FALSE    |
| TOTAL_ORDER  | INT(N)     | FALSE    |

`ICECREAM_INFO` 테이블 구조는 다음과 같으며, `FLAVOR`, `INGREDIENT_TYPE`은 각각 아이스크림 맛, 아이스크림의 성분 타입을 나타냅니다. `INGREDIENT_TYPE`에는 아이스크림의 주 성분이 설탕이면 `sugar_based`라고 입력되고, 아이스크림의 주 성분이 과일이면 `fruit_based`라고 입력됩니다. `ICECREAM_INFO`의 기본 키는 `FLAVOR`입니다. `ICECREAM_INFO` 테이블의 `FLAVOR`는 `FIRST_HALF` 테이블의 `FLAVOR`의 외래 키입니다.

| NAME            | TYPE       | NULLABLE |
| --------------- | ---------- | -------- |
| FLAVOR          | VARCHAR(N) | FALSE    |
| INGREDIENT_TYPE | VARCHAR(N) | FALSE    |

---

### 문제
상반기 아이스크림 총주문량이 3,000보다 높으면서 아이스크림의 주 성분이 과일인 아이스크림의 맛을 총 주문량이 큰 순서대로 조회하는 SQL 문을 작성해주세요.

---

### ICECREAM_INFO 테이블이 다음과 같다면

| FLAVOR           | INGREDIENT_TYPE |
| ---------------- | --------------- |
| chocolate        | sugar_based     |
| vanilla          | sugar_based     |
| mint_chocolate   | sugar_based     |
| caramel          | sugar_based     |
| white_chocolate  | sugar_based     |
| peach            | fruit_based     |
| watermelon       | fruit_based     |
| mango            | fruit_based     |
| strawberry       | fruit_based     |
| melon            | fruit_based     |
| orange           | fruit_based     |
| pineapple        | fruit_based     |

---

상반기 아이스크림 총주문량이 3,000보다 높은 아이스크림 맛은 `chocolate`, `strawberry`, `melon`, `white_chocolate`입니다. 이 중에 아이스크림의 주 성분이 과일인 아이스크림 맛은 `strawberry`와 `melon`이고, 총주문량이 큰 순서대로 아이스크림 맛을 조회하면 `melon`, `strawberry` 순으로 조회되어야 합니다. 따라서 SQL 문을 실행하면 다음과 같이 나와야 합니다.

| FLAVOR    |
| --------- |
| melon     |
| strawberry|



---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT a.FLAVOR
from FIRST_HALF 
LEFT JOIN ICECREAM_INFO b
ON a.FLAVOR = b.FLAVOR
where a.TOTAL_ORDER > 3000 and b.INGREDIENT_TYPE = 'fruit_based'
```

``` sql
--- 재용 코드2
SELECT FLAVOR
from FIRST_HALF
where TOTAL_ORDER > 3000 and FLAVOR in (
    select FLAVOR
    from ICECREAM_INFO
    where INGREDIENT_TYPE = 'fruit_based'
)
```
### 소감
```plaintext
코드1 (JOIN 사용)
JOIN을 이용해 'FIRST_HALF 테이블의 모든 컬럼'과 'ICECREAM_INFO 테이블의 INGREDIENT_TYPE 컬럼'을 합친 하나의 테이블 생성'
이 테이블에서 조건 2개를 and로 분기해 처리해줌

코드2 (서브쿼리 사용, 서브쿼리 사용해본 경험이 거의 없어서 일부러 해봄)
4번 라인부터 있는 select로 인해 두번째 조건에 맞는 FLAVOR 컬럼의 값들이 리스트로 추출됨
이 리스트를 where col in (리스트) 형태로 넣어 조건에 사용
```

<br/>


## RED Part

### 코드
```sql
-- 이열 코드
SELECT ...;
```
### 소감
```plaintext
짧은 소감
또는 배우게 된 개념 간단하게
```
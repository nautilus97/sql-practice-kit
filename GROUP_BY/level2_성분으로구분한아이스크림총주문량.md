# 성분으로 구분한 아이스크림 총 주문량

## 문제 설명

다음은 아이스크림 가게의 상반기 주문 정보를 담은 `FIRST_HALF` 테이블과 아이스크림 성분에 대한 정보를 담은 `ICECREAM_INFO` 테이블입니다. `FIRST_HALF` 테이블 구조는 다음과 같으며, `SHIPMENT_ID`, `FLAVOR`, `TOTAL_ORDER`는 각각 아이스크림 공장에서 아이스크림 가게까지의 출하 번호, 아이스크림 맛, 상반기 아이스크림 총주문량을 나타냅니다. `FIRST_HALF` 테이블의 기본 키는 `FLAVOR` 입니다.

| NAME         | TYPE        | NULLABLE |
|--------------|-------------|----------|
| SHIPMENT_ID  | INT(N)      | FALSE    |
| FLAVOR       | VARCHAR(N)  | FALSE    |
| TOTAL_ORDER  | INT(N)      | FALSE    |

`ICECREAM_INFO` 테이블 구조는 다음과 같으며, `FLAVOR`, `INGREDIENT_TYPE`은 각각 아이스크림 맛, 아이스크림의 성분 타입을 나타냅니다. `INGREDIENT_TYPE`에는 아이스크림의 주 성분이 설탕인 경우 `sugar_based`라고 입력되고, 아이스크림의 주 성분이 과일이면 `fruit_based`라고 입력됩니다. `ICECREAM_INFO` 테이블의 기본 키는 `FLAVOR` 입니다.

| NAME            | TYPE        | NULLABLE |
|-----------------|-------------|----------|
| FLAVOR          | VARCHAR(N)  | FALSE    |
| INGREDIENT_TYPE | VARCHAR(N)  | FALSE    |

`ICECREAM_INFO` 테이블의 `FLAVOR`는 `FIRST_HALF` 테이블의 `FLAVOR` 외래 키입니다.

## 문제

상반기 동안 각 아이스크림 성분 타입과 성분 타입에 대한 아이스크림의 총주문량을 총주문량이 작은 순서대로 조회하는 SQL 문을 작성해 주세요. 이때 총주문량을 나타내는 컬럼명은 `TOTAL_ORDER`로 지정해주세요.

### 예시

예를 들어 `FIRST_HALF` 테이블이 다음과 같고

| SHIPMENT_ID | FLAVOR           | TOTAL_ORDER |
|-------------|------------------|-------------|
| 101         | chocolate        | 3200        |
| 102         | vanilla          | 2800        |
| 103         | mint_chocolate   | 1700        |
| 104         | caramel          | 2600        |
| 105         | white_chocolate  | 3100        |
| 106         | peach            | 2450        |
| 107         | watermelon       | 2150        |
| 108         | mango            | 2900        |
| 109         | strawberry       | 3100        |
| 110         | melon            | 3150        |
| 111         | orange           | 2900        |
| 112         | pineapple        | 2900        |

`ICECREAM_INFO` 테이블이 다음과 같다면

| FLAVOR           | INGREDIENT_TYPE |
|------------------|-----------------|
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

상반기에 아이스크림의 주 성분이 설탕인 아이스크림들에 대한 총주문량을 구하면 3,200 + 2,800 + 1,700 + 2,600 + 3,100 = 13,400입니다. 아이스크림의 주 성분이 과일인 아이스크림들에 대한 총주문량을 구하면 3,100 + 2,450 + 2,150 + 2,900 + 3,150 + 2,900 + 2,900 = 19,550입니다. 따라서 총주문량이 작은 순서대로 조회하면 다음과 같이 나와야 합니다.

| INGREDIENT_TYPE | TOTAL_ORDER |
|-----------------|-------------|
| sugar_based     | 13400       |
| fruit_based     | 19550       |


---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT INGREDIENT_TYPE, SUM(TOTAL_ORDER) as TOTAL_ORDER
from FIRST_HALF A JOIN ICECREAM_INFO B on A.FLAVOR = B.FLAVOR
group by INGREDIENT_TYPE
order by TOTAL_ORDER
```
### 소감
```plaintext
SELECT에서 JOIN과 ORDER BY를 사용했었어서 쉽게 풀수 있었음
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

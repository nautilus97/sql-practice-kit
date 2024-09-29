# 인기있는 아이스크림

## 문제 설명

`FIRST_HALF` 테이블은 아이스크림 가게의 상반기 주문 정보를 담은 테이블입니다. `FIRST_HALF` 테이블 구조는 다음과 같으며, `SHIPMENT_ID`, `FLAVOR`, `TOTAL_ORDER` 는 각각 아이스크림 공장에서 아이스크림 가게까지의 출하 번호, 아이스크림 맛, 상반기 아이스크림 총주문량을 나타냅니다.

| NAME         | TYPE      | NULLABLE |
|--------------|-----------|----------|
| SHIPMENT_ID  | INT(N)    | FALSE    |
| FLAVOR       | VARCHAR(N)| FALSE    |
| TOTAL_ORDER  | INT(N)    | FALSE    |

## 문제

상반기에 판매된 아이스크림의 맛을 총주문량을 기준으로 내림차순 정렬하고 총주문량이 같다면 출하 번호를 기준으로 오름차순 정렬하여 조회하는 SQL문을 작성해주세요.

### 예시

예를 들어 `FIRST_HALF` 테이블이 다음과 같을 때

| SHIPMENT_ID | FLAVOR          | TOTAL_ORDER |
|-------------|-----------------|-------------|
| 101         | chocolate       | 3200        |
| 102         | vanilla         | 2800        |
| 103         | mint_chocolate  | 1700        |
| 104         | caramel         | 1600        |
| 105         | white_chocolate | 2900        |
| 106         | peach           | 2450        |
| 107         | watermelon      | 2600        |
| 108         | mango           | 2900        |
| 109         | strawberry      | 3150        |
| 110         | melon           | 3150        |
| 111         | orange          | 2950        |
| 112         | pineapple       | 2900        |

상반기 아이스크림 맛을 총주문량을 기준으로 내림차순 정렬하고 총주문량이 같은 경우 출하 번호를 기준으로 오름차순 정렬하면 `chocolate`, `melon`, `strawberry` 순으로 조회됩니다.




---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT FLAVOR
from FIRST_HALF
order by TOTAL_ORDER desc, SHIPMENT_ID
```
### 소감
```plaintext
ordey by를 두 컬럼에 대해 실행해보는 예제
같은 level 1인데 '흉부외과또는일반외과의사목록출력하기' 문제에서 미리 해봐서 쉽게 함
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
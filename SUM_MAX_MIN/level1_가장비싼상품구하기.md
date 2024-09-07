# 가장 비싼 상품 구하기

## 문제 설명

다음은 어느 의류 쇼핑몰에서 판매 중인 상품들의 정보를 담은 `PRODUCT` 테이블입니다.  
`PRODUCT` 테이블은 아래와 같은 구조로 되어있으며, `PRODUCT_ID`, `PRODUCT_CODE`, `PRICE` 는 각각 상품 ID, 상품코드, 판매가를 나타냅니다.

| Column name   | Type        | Nullable |
|---------------|-------------|----------|
| PRODUCT_ID    | INTEGER     | FALSE    |
| PRODUCT_CODE  | VARCHAR(8)  | FALSE    |
| PRICE         | INTEGER     | FALSE    |

상품 별로 중복되지 않는 8자리 상품코드 값을 가지며, 앞 2자리는 카테고리 코드를 의미합니다.

---

## 문제

`PRODUCT` 테이블에서 판매 중인 상품 중 가장 높은 판매가를 출력하는 SQL문을 작성해주세요.  
이때 컬럼명은 `MAX_PRICE`로 지정해주세요.

---

## 예시

다음은 `PRODUCT` 테이블의 예시입니다.

| PRODUCT_ID | PRODUCT_CODE | PRICE  |
|------------|--------------|--------|
| 1          | A1000001     | 10000  |
| 2          | A2000005     | 9000   |
| 3          | C1000006     | 22000  |

가장 높은 판매가는 22,000 원이므로, 다음과 같은 결과가 나와야 합니다.

| MAX_PRICE  |
|------------|
| 22000      |

---
## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT ...;
```
### 소감
```plaintext
짧은 소감
또는 배우게 된 개념 간단하게
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

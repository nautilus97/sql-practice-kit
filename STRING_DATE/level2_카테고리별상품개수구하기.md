# 카테고리 별 상품 개수 구하기

## 문제 설명
다음은 어느 의류 쇼핑몰에서 판매중인 상품들의 정보를 담은 `PRODUCT` 테이블입니다.  
`PRODUCT` 테이블은 아래와 같은 구조로 되어있으며, `PRODUCT_ID`, `PRODUCT_CODE`, `PRICE`는 각각 상품 ID, 상품코드, 판매가를 나타냅니다.

| Column name   | Type        | Nullable |
|---------------|-------------|----------|
| PRODUCT_ID    | INTEGER     | FALSE    |
| PRODUCT_CODE  | VARCHAR(8)  | FALSE    |
| PRICE         | INTEGER     | FALSE    |

상품 별로 중복되지 않는 8자리 상품코드 값을 가지며, 앞 2자리는 카테고리 코드를 의미합니다.

## 문제
`PRODUCT` 테이블에서 상품 카테고리 코드(`PRODUCT_CODE` 앞 2자리) 별 상품 개수를 출력하는 SQL문을 작성해주세요.  
결과는 상품 카테고리 코드를 기준으로 오름차순 정렬해주세요.

## 예시
예를 들어 `PRODUCT` 테이블이 다음과 같다면

| PRODUCT_ID | PRODUCT_CODE | PRICE |
|------------|--------------|-------|
| 1          | A1000011     | 10000 |
| 2          | A1000045     | 9000  |
| 3          | C3000002     | 22000 |
| 4          | C3000006     | 15000 |
| 5          | C3000010     | 30000 |
| 6          | K1000023     | 17000 |

상품 카테고리 코드 별 상품은 아래와 같으므로,
- `A1`: `PRODUCT_ID`가 1, 2인 상품
- `C3`: `PRODUCT_ID`가 3, 4, 5인 상품
- `K1`: `PRODUCT_ID`가 6인 상품

다음과 같은 결과가 나와야 합니다.

| CATEGORY | PRODUCTS |
|----------|----------|
| A1       | 2        |
| C3       | 3        |
| K1       | 1        |


---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT substring(PRODUCT_CODE, 1,2) as CATEGORY, COUNT(*)
from PRODUCT
group by CATEGORY
order by PRODUCT_CODE
```
### 소감
```plaintext
substring(컬럼, s, n) : 문자열을 s번쨰 문자부터 n개 잘라냄
left(PRODUCT_CODE, 2)를 사용해도 된다(왼쪽부터 2개 잘라냄)
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

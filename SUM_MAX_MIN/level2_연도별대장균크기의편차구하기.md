# 연도별 대장균 크기의 편차 구하기

## 문제 설명

대장균들은 일정 주기로 분화하며, 분화를 시작한 개체를 부모 개체, 분화가 되어 나온 개체를 자식 개체라고 합니다.  
다음은 실험실에서 배양한 대장균들의 정보를 담은 `ECOLI_DATA` 테이블입니다. `ECOLI_DATA` 테이블의 구조는 다음과 같으며,  
`ID`, `PARENT_ID`, `SIZE_OF_COLONY`, `DIFFERENTIATION_DATE`, `GENOTYPE`는 각각 대장균 개체의 ID, 부모 개체의 ID, 개체의 크기,  
분화되어 나온 날짜, 개체의 형질을 나타냅니다.

| Column name          | Type    | Nullable | 
|----------------------|---------|----------|
| ID                   | INTEGER | FALSE    |
| PARENT_ID            | INTEGER | TRUE     |
| SIZE_OF_COLONY       | INTEGER | FALSE    |
| DIFFERENTIATION_DATE | DATE    | FALSE    |
| GENOTYPE             | INTEGER | FALSE    |

최초의 대장균 개체의 `PARENT_ID`는 `NULL` 값입니다.

## 문제

분화된 연도(`YEAR`), 분화된 연도별 대장균 크기의 편차(`YEAR_DEV`), 대장균 개체의 ID(`ID`)를 출력하는 SQL 문을 작성해주세요.  
분화된 연도별 대장균 크기의 편차는 분화된 연도별 가장 큰 대장균의 크기 - 각 대장균의 크기로 구하며 결과는 연도에 대해 오름차순으로 정렬하고  
같은 연도에 대해서는 대장균 크기의 편차에 대해 오름차순으로 정렬해주세요.

### 예시

예를 들어 `ECOLI_DATA` 테이블이 다음과 같다면

| ID  | PARENT_ID | SIZE_OF_COLONY | DIFFERENTIATION_DATE | GENOTYPE |
|-----|-----------|----------------|----------------------|----------|
| 1   | NULL      | 10             | 2019/01/01           | 5        |
| 2   | NULL      | 2              | 2019/01/01           | 3        |
| 3   | 1         | 100            | 2020/01/01           | 4        |
| 4   | 2         | 100            | 2020/01/01           | 4        |
| 5   | 2         | 17             | 2020/01/01           | 6        |
| 6   | 4         | 101            | 2021/01/01           | 22       |

분화된 연도별 가장 큰 대장균의 크기는 다음과 같습니다.

- 2019: 10
- 2020: 101
- 2021: 101

따라서 각 대장균의 분화된 연도별 대장균 크기의 편차는 다음과 같습니다.

- ID 1: 10 - 10 = 0
- ID 2: 10 - 2 = 8
- ID 3: 100 - 100 = 0
- ID 4: 100 - 100 = 0
- ID 5: 100 - 17 = 83
- ID 6: 101 - 101 = 0

이를 분화된 연도에 대해 오름차순으로 정렬하고 같은 연도에 대해서는 대장균 크기의 편차에 대해 오름차순으로 정렬하면 결과는 다음과 같아야 합니다.

| YEAR | YEAR_DEV | ID |
|------|----------|----|
| 2019 | 0        | 1  |
| 2019 | 8        | 2  |
| 2020 | 0        | 3  |
| 2020 | 0        | 4  |
| 2020 | 83       | 5  |
| 2021 | 0        | 6  |



---
## BLACK Part

### 코드
```sql
-- 재용 코드1
SELECT YEAR, B.max_size_of_colony - A.SIZE_OF_COLONY as YEAR_DEV, ID
from ECOLI_DATA A
JOIN (
    SELECT year(DIFFERENTIATION_DATE) as YEAR,
        MAX(SIZE_OF_COLONY) as max_size_of_colony
    from ECOLI_DATA
    GROUP BY YEAR
) B
on year(A.DIFFERENTIATION_DATE) = B.YEAR
order by YEAR, YEAR_DEV

-- 재용 코드2
WITH MAX_EACH_YEAR AS (
    SELECT year(DIFFERENTIATION_DATE) as YEAR,
        MAX(SIZE_OF_COLONY) as max_size_of_colony
    from ECOLI_DATA
    GROUP BY YEAR
)

select YEAR, B.max_size_of_colony - A.SIZE_OF_COLONY as YEAR_DEV, ID
from ECOLI_DATA A
JOIN MAX_EACH_YEAR B
on year(A.DIFFERENTIATION_DATE) = B.YEAR
order by YEAR, YEAR_DEV

```
### 소감
```plaintext
첫번째 코드는 JOIN 안에 서브쿼리를 넣음
두번째 코드는 WITH 구문을 사용해 서브쿼리를 분리함. 기능적 차이는 없고 가독성 차이임

YEAR를 만들때 date_format()을 사용하면 문자열 타입이라 에러남. year()를 사용해 정수타입으로 출력해야함
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

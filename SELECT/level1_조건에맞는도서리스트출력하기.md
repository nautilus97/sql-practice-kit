# 조건에 맞는 도서 리스트 출력하기

## 문제 설명

다음은 어느 한 서점에서 판매중인 도서들의 도서 정보(`BOOK`) 테이블입니다.

`BOOK` 테이블은 각 도서의 정보를 담은 테이블로 아래와 같은 구조로 되어있습니다.

| Column name       | Type        | Nullable | Description                 |
|-------------------|-------------|----------|-----------------------------|
| BOOK_ID           | INTEGER     | FALSE    | 도서 ID                     |
| CATEGORY          | VARCHAR(N)  | FALSE    | 카테고리 (경제, 인문, 소설, 생활, 기술) |
| AUTHOR_ID         | INTEGER     | FALSE    | 저자 ID                     |
| PRICE             | INTEGER     | FALSE    | 판매가 (원)                 |
| PUBLISHED_DATE    | DATE        | FALSE    | 출판일                      |

## 문제

`BOOK` 테이블에서 `2021년`에 출판된 `인문` 카테고리에 속하는 도서 리스트를 찾아서 도서 ID(`BOOK_ID`), 출판일(`PUBLISHED_DATE`)을 출력하는 SQL문을 작성해주세요.

결과는 출판일을 기준으로 오름차순 정렬해주세요.

### 예시

예를 들어 `BOOK` 테이블이 다음과 같다면

| BOOK_ID | CATEGORY | AUTHOR_ID | PRICE  | PUBLISHED_DATE |
|---------|----------|-----------|--------|----------------|
| 1       | 인문     | 1         | 10000  | 2020-01-01     |
| 2       | 경제     | 2         | 9000   | 2021-02-05     |
| 3       | 인문     | 2         | 11000  | 2021-04-11     |
| 4       | 인문     | 3         | 10000  | 2021-03-15     |
| 5       | 생활     | 1         | 12000  | 2021-01-10     |

조건에 속하는 도서는 도서 ID가 3, 4인 도서이므로 다음과 같습니다.

| BOOK_ID | PUBLISHED_DATE |
|---------|----------------|
| 3       | 2021-04-11     |
| 4       | 2021-03-15     |

그리고 출판일 오름차순으로 정렬하여야 하므로 다음과 같은 결과가 나와야 합니다.

| BOOK_ID | PUBLISHED_DATE |
|---------|----------------|
| 4       | 2021-03-15     |
| 3       | 2021-04-11     |

### 주의사항

`PUBLISHED_DATE`의 데이터 포맷에 예시와 동일해야 정답처리 됩니다.




---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT BOOK_ID, date_format(PUBLISHED_DATE, '%Y-%m-%d') as PUBLISHED_DATE
from BOOK
where CATEGORY = '인문' and date_format(PUBLISHED_DATE, '%Y') = 2021
order by PUBLISHED_DATE
```
### 소감
```plaintext
앞에서 날짜 비교함수를 위한 함수를 미리 알아둬서 쉬웠음
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
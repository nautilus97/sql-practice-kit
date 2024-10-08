# 자동차 대여 기록에서 장기/단기 대여 구분하기

## 문제 설명

다음은 어느 자동차 대여 회사의 자동차 대여 기록 정보를 담은 `CAR_RENTAL_COMPANY_RENTAL_HISTORY` 테이블입니다. `CAR_RENTAL_COMPANY_RENTAL_HISTORY` 테이블은 아래와 같은 구조로 되어있으며, `HISTORY_ID`, `CAR_ID`, `START_DATE`, `END_DATE` 는 각각 자동차 대여 기록 ID, 자동차 ID, 대여 시작일, 대여 종료일을 나타냅니다.

| Column name | Type    | Nullable |
|-------------|---------|----------|
| HISTORY_ID  | INTEGER | FALSE    |
| CAR_ID      | INTEGER | FALSE    |
| START_DATE  | DATE    | FALSE    |
| END_DATE    | DATE    | FALSE    |


## 문제

`CAR_RENTAL_COMPANY_RENTAL_HISTORY` 테이블에서 대여 시작일이 2022년 9월에 속하는 대여 기록에 대해서 대여 기간이 30일 이상이면 '장기 대여' 그렇지 않으면 '단기 대여'로 표시하는 컬럼(컬럼명: `RENT_TYPE`)을 추가하여 대여기록을 출력하는 SQL문을 작성해주세요. 결과는 대여 기록 ID를 기준으로 내림차순 정렬해주세요.

## 예시

예를 들어 `CAR_RENTAL_COMPANY_RENTAL_HISTORY` 테이블이 다음과 같다면

| HISTORY_ID | CAR_ID | START_DATE | END_DATE   |
|------------|--------|------------|------------|
| 1          | 4      | 2022-09-27 | 2022-11-27 |
| 2          | 3      | 2022-10-03 | 2022-11-04 |
| 3          | 2      | 2022-09-05 | 2022-09-05 |
| 4          | 1      | 2022-09-01 | 2022-09-30 |
| 5          | 3      | 2022-09-16 | 2022-10-15 |

2022년 9월의 대여 기록 중 '장기 대여'에 해당하는 기록은 대여 기록 ID가 1, 4인 기록이고, '단기 대여'에 해당하는 기록은 대여 기록 ID가 3, 5인 기록이므로 대여 기록 ID를 기준으로 내림차순 정렬하면 다음과 같이 나와야 합니다.

| HISTORY_ID | CAR_ID | START_DATE | END_DATE   | RENT_TYPE |
|------------|--------|------------|------------|-----------|
| 5          | 3      | 2022-09-16 | 2022-10-13 | 단기 대여  |
| 4          | 1      | 2022-09-01 | 2022-09-30 | 장기 대여  |
| 3          | 2      | 2022-09-05 | 2022-09-05 | 단기 대여  |
| 1          | 4      | 2022-09-27 | 2022-10-26 | 장기 대여  |

---
## 주의사항

`START_DATE`와 `END_DATE`의 경우 예시의 데이트 포맷과 동일하게 정렬처리 됩니다.

---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT HISTORY_ID, CAR_ID,
    date_format(START_DATE, '%Y-%m-%d') START_DATE, date_format(END_DATE, '%Y-%m-%d') END_DATE,
    if(DATEDIFF(END_DATE,START_DATE)+1 >= 30, '장기 대여', '단기 대여') as RENT_TYPE
from CAR_RENTAL_COMPANY_RENTAL_HISTORY
where date_format(START_DATE, '%Y-%m') = '2022-09'
order by HISTORY_ID DESC
```
### 소감
```plaintext
DATEDIFF(A,B)는 A에서 B와의 일수 차이를 반환해줌
SQL의 if문은 삼항연산자처럼 쓰임 -> if(조건, 참인경우 값, 거짓인경우 값)

대여한 첫날부터 1일차라 두 날짜의 차이는 1일차가 빠진 일수임
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

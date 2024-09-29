# 서울에 위치한 식당 목록 출력하기

## 문제 설명

다음은 식당의 정보를 담은 `REST_INFO` 테이블과 식당의 리뷰 정보를 담은 `REST_REVIEW` 테이블입니다. `REST_INFO` 테이블은 다음과 같으며 `REST_ID`, `REST_NAME`, `FOOD_TYPE`, `VIEWS`, `FAVORITES`, `PARKING_LOT`, `ADDRESS`, `TEL` 은 식당 ID, 식당 이름, 음식 종류, 조회수, 즐겨찾기수, 주차장 유무, 주소, 전화번호를 의미합니다.

| Column name  | Type        | Nullable | 
|--------------|-------------|----------|
| REST_ID      | VARCHAR(5)  | FALSE    |
| REST_NAME    | VARCHAR(50) | FALSE    |
| FOOD_TYPE    | VARCHAR(30) | TRUE     |
| VIEWS        | NUMBER      | TRUE     |
| FAVORITES    | NUMBER      | TRUE     |
| PARKING_LOT  | VARCHAR(1)  | TRUE     |
| ADDRESS      | VARCHAR(100)| TRUE     |
| TEL          | VARCHAR(100)| TRUE     |

`REST_REVIEW` 테이블은 다음과 같으며 `REVIEW_ID`, `REST_ID`, `MEMBER_ID`, `REVIEW_SCORE`, `REVIEW_TEXT`, `REVIEW_DATE` 는 각각 리뷰 ID, 식당 ID, 회원 ID, 점수, 리뷰 텍스트, 리뷰 작성일을 의미합니다.

| Column name  | Type        | Nullable | 
|--------------|-------------|----------|
| REVIEW_ID    | VARCHAR(10) | FALSE    |
| REST_ID      | VARCHAR(10) | TRUE     |
| MEMBER_ID    | VARCHAR(100)| TRUE     |
| REVIEW_SCORE | NUMBER      | TRUE     |
| REVIEW_TEXT  | VARCHAR(1000) | TRUE    |
| REVIEW_DATE  | DATE        | TRUE     |

## 문제

`REST_INFO`와 `REST_REVIEW` 테이블에서 서울에 위치한 식당들의 식당 ID, 식당 이름, 음식 종류, 즐겨찾기수, 주소, 리뷰 평균 점수를 조회하는 SQL문을 작성해주세요. 이때 리뷰 평균점수는 소수점 셋째 자리에서 반올림 해주시고 결과는 평균점수를 기준으로 내림차순 정렬해주세요. 평균점수가 같다면 즐겨찾기수를 기준으로 내림차순 정렬해주세요.

### 예시

`REST_INFO` 테이블이 다음과 같고

| REST_ID | REST_NAME    | FOOD_TYPE | VIEWS  | FAVORITES | PARKING_LOT | ADDRESS                            | TEL          |
|---------|--------------|-----------|--------|-----------|-------------|------------------------------------|--------------|
| 00028   | 대우부대찌개 | 한식      | 52310  | 10        | N           | 경기도 용인시 처인구 남사읍 처인성로 309         | 031-235-1235 |
| 00039   | 광주식당     | 한식      | 23001  | 20        | N           | 경기도 부천시 산업로88번길 60                 | 031-235-6423 |
| 00035   | 삼호식당     | 일식      | 532123 | 80        | N           | 서울특별시 강서구 가로공원로76가길              | 02-135-1266  |

`REST_REVIEW` 테이블이 다음과 같을 때

| REVIEW_ID   | REST_ID | MEMBER_ID            | REVIEW_SCORE | REVIEW_TEXT             | REVIEW_DATE |
|-------------|---------|----------------------|--------------|-------------------------|-------------|
| R000000062  | 00028   | soobin97@naver.com    | 5            | 부찌 국물에서 사브사브 맛이나요 깔끔 | 2022-04-12  |
| R000000066  | 00028   | yealim1130@gmail.com  | 5            | 김치찌개 최고입니다.                   | 2022-02-02  |
| R000000067  | 00028   | yelin1130@gmail.com   | 5            | 햄이 많아서 좋아요                     | 2022-02-22  |
| R000000068  | 00035   | ksy01136@gmail.com    | 5            | 속상한데 깔끔좋아요                     | 2022-02-15  |
| R000000069  | 00035   | yoonys95@naver.com    | 4            | 비린내가 전혀없었어요                  | 2022-04-16  |

SQL을 실행하면 다음과 같이 출력되어야 합니다.

| REST_ID | REST_NAME | FOOD_TYPE | FAVORITES | ADDRESS                        | SCORE |
|---------|-----------|-----------|-----------|--------------------------------|-------|
| 00035   | 삼호식당  | 일식      | 80        | 서울특별시 강서구 가로공원로76가길 | 4.50  |




---

## BLACK Part

### 코드
```sql
-- 재용 코드
select REST_ID, REST_NAME, FOOD_TYPE, FAVORITES, ADDRESS, ROUND(AVG(REVIEW_SCORE), 2) as SCORE
from (
    SELECT a.REST_ID, REST_NAME, FOOD_TYPE, FAVORITES, ADDRESS, REVIEW_SCORE
    from REST_INFO a
    INNER JOIN REST_REVIEW b
    on a.REST_ID = b.REST_ID
    where ADDRESS like '서울%'
    ) b
GROUP BY REST_ID
order by SCORE DESC, FAVORITES DESC
```
### 소감
```plaintext
sub query가 익숙해져서 할만했음
코드 제출후에 안건데, 서브쿼리 내부에서 REST_REVIEW를 b로 선언했고 서브쿼리 결과도 b로 선언함
확인해보니 REST_INFO a와 REST_REVIEW b는 서브쿼리 내부에서만 유효함

GROUP BY는 pandas DataFrame에서 자주 써서 익숙해짐

주소중에 '경상북도 서울구' 이런 주소가 있는듯
like 뒤에 %서울%로 쓰면 제출 오답처리됨
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
# 평균 일일 대여 요금 구하기

## 문제 설명

다음은 어느 자동차 대여 회사에서 대여 중인 자동차들의 정보를 담은 `CAR_RENTAL_COMPANY_CAR` 테이블입니다.  
`CAR_RENTAL_COMPANY_CAR` 테이블은 아래와 같은 구조로 되어있으며,  
`CAR_ID`, `CAR_TYPE`, `DAILY_FEE`, `OPTIONS` 는 각각 자동차 ID, 자동차 종류, 일일 대여 요금(원), 자동차 옵션 리스트를 나타냅니다.

| Column name | Type          | Nullable |
|-------------|---------------|----------|
| CAR_ID      | INTEGER       | FALSE    |
| CAR_TYPE    | VARCHAR(255)  | FALSE    |
| DAILY_FEE   | INTEGER       | FALSE    |
| OPTIONS     | VARCHAR(255)  | FALSE    |

자동차 종류는 `세단`, `SUV`, `승합차`, `트럭`, `리무진` 이 있습니다.  
자동차 옵션 리스트는 콤마(`;`)로 구분된 키워드 리스트(예: `열선시트`, `스마트키`, `주차감지센서`)로 되어있으며,  
키워드 종류는 `주차감지센서`, `스마트키`, `네비게이션`, `통풍시트`, `열선시트`, `후방카메라`, `가죽시트` 가 있습니다.


## 문제

`CAR_RENTAL_COMPANY_CAR` 테이블에서 자동차 종류가 `SUV`인 자동차들의 평균 일일 대여 요금을 출력하는 SQL문을 작성하세요.  
이때, 평균 일일 대여 요금은 소수 첫 번째 자리에서 반올림하고, 컬럼명은 `AVERAGE_FEE` 로 지정해주세요.


## 예시

다음은 `CAR_RENTAL_COMPANY_CAR` 테이블의 예시입니다.

| CAR_ID | CAR_TYPE | DAILY_FEE | OPTIONS                     |
|--------|----------|-----------|-----------------------------|
| 1      | 세단     | 16000     | 가죽시트, 열선시트, 후방카메라 |
| 2      | SUV      | 14000     | 스마트키, 네비게이션, 열선시트 |
| 3      | SUV      | 22000     | 주차감지센서, 후방카메라, 가죽시트 |

`SUV`에 해당하는 자동차들의 평균 일일 대여 요금은 **18,000원**으로, 다음과 같은 결과가 나와야 합니다.

| AVERAGE_FEE |
|-------------|
| 18000       |



---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT ROUND(AVG(DAILY_FEE), 0) as AVERAGE_FEE
from CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = 'SUV'
```
### 소감
```plaintext
AVG(컬럼명) : 컬럼들의 평균을 구함(컬럼 타입에 관계없이 DOUBLE 타입 리턴해주는듯)

ROUNT(n, d) : 숫자 n을 소수점 d번쨰 자리에서 반올림

ORIGIN as TARGET : ORIGIN 컬럼을 TARGET이런 이름으로 출력한다. as를 생략해도 된다
```

<br/>


## RED Part

### 코드
```sql
-- 이열 코드

SELECT ROUND(AVG(DAILY_FEE), 0)
AS AVERAGE_FEE 
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = 'SUV';
```
### 소감
```plaintext
SELECT, AS, FROM, WHERE, ROUND 배우게 됨
익숙해지면 level_1 문제는 금방 풀듯
```




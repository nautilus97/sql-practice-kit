# 문제별 내용 정리

## level1_평균 일일 대여 요금 구하기 문제 풀이

이 문제는 SQL의 **집계 함수**와 **조건문**을 요구하는 문제야. 특히 평균을 구하는 집계 함수 `AVG()`와, 특정 조건에 맞는 데이터를 필터링하는 `WHERE` 절을 사용하는 방법을 알아야 해.

먼저 이 문제를 풀기 위해 필요한 SQL 문법과 개념을 몇 가지 설명할게:

1. **`SELECT`문**: SQL에서 데이터를 조회하는 기본적인 구문이야. 이 문제에서는 특정 자동차 종류의 평균 요금을 조회해야 하니까 `SELECT`문을 사용할 거야.
    
2. **`AVG()` 함수**: `AVG()`는 평균을 계산해주는 집계 함수야. 이 함수는 숫자 데이터를 받아 그 값들의 평균을 반환해.
    
    예시: `SELECT AVG(Daily_Fee) FROM CAR_RENTAL_COMPANY_CAR;`
    
3. **`WHERE` 절**: 특정 조건을 만족하는 데이터만 조회할 때 쓰는 절이야. 이 문제에서는 `CAR_TYPE`이 'SUV'인 데이터만 조회해야 하니까, `WHERE CAR_TYPE = 'SUV'`를 사용하면 돼.
    
    예시: `SELECT * FROM CAR_RENTAL_COMPANY_CAR WHERE CAR_TYPE = 'SUV';`
    
4. **별칭 (Alias)**: 조회한 값에 별칭을 줄 수 있어. 이 문제에서는 평균 값을 조회할 때 그 결과를 `AVERAGE_FEE`라는 이름으로 반환하라고 했으니까, `AS` 키워드를 이용해서 별칭을 줄 수 있어.
    
    예시: `SELECT AVG(Daily_Fee) AS AVERAGE_FEE FROM CAR_RENTAL_COMPANY_CAR;`

이 문제를 풀 때는 아래 과정을 따르면 돼:

1. `CAR_TYPE`이 'SUV'인 데이터만 필터링하기 위해 `WHERE` 절을 사용해.
2. 그 후에, `SUV` 차량의 `DAILY_FEE` 값들의 평균을 구하기 위해 `AVG()` 함수를 사용해.
3. 결과에 별칭을 `AVERAGE_FEE`로 줘.
# 경기도에 위치한 식품창고 목록 출력하기

## 문제 설명

다음은 식품창고의 정보를 담은 `FOOD_WAREHOUSE` 테이블입니다.  
`FOOD_WAREHOUSE` 테이블은 다음과 같으며 `WAREHOUSE_ID`, `WAREHOUSE_NAME`, `ADDRESS`, `TLNO`, `FREEZER_YN`는 창고 ID, 창고 이름, 창고 주소, 전화번호, 냉동시설 여부를 의미합니다.

| Column name      | Type        | Nullable | Description        |
|------------------|-------------|----------|--------------------|
| WAREHOUSE_ID     | VARCHAR(10) | FALSE    | 창고 ID            |
| WAREHOUSE_NAME   | VARCHAR(20) | FALSE    | 창고 이름          |
| ADDRESS          | VARCHAR(100)| TRUE     | 창고 주소          |
| TLNO             | VARCHAR(20) | TRUE     | 전화번호           |
| FREEZER_YN       | VARCHAR(1)  | TRUE     | 냉동시설 여부      |

## 문제

`FOOD_WAREHOUSE` 테이블에서 경기도에 위치한 창고의 ID, 이름, 주소, 냉동시설 여부를 조회하는 SQL문을 작성해주세요.  
이때 냉동시설 여부가 `NULL`인 경우, `N`으로 출력시켜 주시고 결과는 창고 ID를 기준으로 오름차순 정렬해주세요.


## 예시

다음은 `FOOD_WAREHOUSE` 테이블의 예시입니다.

| WAREHOUSE_ID | WAREHOUSE_NAME | ADDRESS                            | TLNO         | FREEZER_YN |
|--------------|----------------|------------------------------------|--------------|------------|
| WH0001       | 창고_경기1      | 경기도 안산시 상록구 용담로 141      | 031-152-1332 | Y          |
| WH0002       | 창고_충북1      | 충청북도 진천군 진천읍 씨제이로 110  | 043-623-9900 | Y          |
| WH0003       | 창고_경기2      | 경기도 이천시 마장면 덕평로 811     | 031-221-7241 | NULL       |
| WH0004       | 창고_경기3      | 경기도 김포시 대곶면 율생중앙로205번길 | 031-671-1900 | N          |
| WH0005       | 창고_충남1      | 충청남도 천안시 동남구 광덕면 신덕리길 9 | 041-876-5421 | Y          |

SQL을 실행하면 다음과 같이 출력되어야 합니다.

| WAREHOUSE_ID | WAREHOUSE_NAME | ADDRESS                            | FREEZER_YN |
|--------------|----------------|------------------------------------|------------|
| WH0001       | 창고_경기1      | 경기도 안산시 상록구 용담로 141      | Y          |
| WH0003       | 창고_경기2      | 경기도 이천시 마장면 덕평로 811     | N          |
| WH0004       | 창고_경기3      | 경기도 김포시 대곶면 율생중앙로205번길 | N          |

---


## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT WAREHOUSE_ID, WAREHOUSE_NAME, ADDRESS, ifnull(FREEZER_YN, 'N') as FREEZER_YN
from FOOD_WAREHOUSE
where ADDRESS like '경기%'
order by WAREHOUSE_ID
```
### 소감
```plaintext
짧은 소감
ifnull 함수를 이용하면 null값을 특정 값으로 대체할수 있다
COALESCE 사용하려했는데 스펠링이 자꾸 기억 안남
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


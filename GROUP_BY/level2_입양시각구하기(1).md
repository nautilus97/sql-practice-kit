# 입양 시각 구하기(1)

## 문제 설명

`ANIMAL_OUTS` 테이블은 동물 보호소에서 입양 보낸 동물의 정보를 담은 테이블입니다.  
`ANIMAL_OUTS` 테이블의 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `NAME`, `SEX_UPON_OUTCOME` 는 각각 동물의 아이디, 생물 종, 입양일, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME              | TYPE        | NULLABLE |
|-------------------|-------------|----------|
| ANIMAL_ID         | VARCHAR(N)  | FALSE    |
| ANIMAL_TYPE       | VARCHAR(N)  | FALSE    |
| DATETIME          | DATETIME    | FALSE    |
| NAME              | VARCHAR(N)  | TRUE     |
| SEX_UPON_OUTCOME  | VARCHAR(N)  | FALSE    |

## 문제

보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다.  
09:00부터 19:59까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요.  
이때 결과는 시간대 순으로 정렬해야 합니다.

### 예시

SQL문을 실행하면 다음과 같이 나와야 합니다.

| HOUR | COUNT |
|------|-------|
| 9    | 1     |
| 10   | 2     |
| 11   | 2     |
| 12   | 3     |
| 13   | 4     |
| 14   | 1     |
| 15   | 1     |
| 16   | 3     |
| 17   | 2     |
| 18   | 1     |
| 19   | 2     |


---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT HOUR(DATETIME) as HOUR, count(*) as COUNT
from ANIMAL_OUTS
# where HOUR(DATETIME) >= 9 and HOUR(DATETIME) < 20
group by HOUR(DATETIME)
HAVING HOUR >= 9 and HOUR < 20
order by HOUR
```
### 소감
```plaintext
시각 조건이 row마다도 있다. 또한 그루핑 기준도 시각이다.
따라서 where로 필터링해도 되고 HAVING으로 필터링해도 된다
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

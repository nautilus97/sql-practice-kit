# 모든 레코드 조회하기

## 문제 설명

`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE` 는 각각 동물의 아이디, 생물 종, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME             | TYPE        | NULLABLE |
|------------------|-------------|----------|
| ANIMAL_ID        | VARCHAR(N)   | FALSE    |
| ANIMAL_TYPE      | VARCHAR(N)   | FALSE    |
| DATETIME         | DATETIME     | FALSE    |
| INTAKE_CONDITION | VARCHAR(N)   | FALSE    |
| NAME             | VARCHAR(N)   | TRUE     |
| SEX_UPON_INTAKE  | VARCHAR(N)   | FALSE    |

동물 보호소에 들어온 모든 동물의 정보를 `ANIMAL_ID`순으로 조회하는 SQL문을 작성해주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.

| ANIMAL_ID     | ANIMAL_TYPE   | DATETIME              | INTAKE_CONDITION  | NAME  | SEX_UPON_INTAKE   |
|---------------|---------------|-----------------------|-------------------|-------|-------------------|
| A349996   	| Cat	        | 2018-01-22 14:32:00	| Normal	        | Sugar | Neutered Male     |
| A350276	    | Cat	        | 2017-08-13 13:50:00   | Normal	        | Jewel | Spayed Female     |
| A350375	    | Cat	        | 2017-03-06 15:01:00   | Normal	        | Meo   | Neutered Male     |
| A352555	    | Dog	        | 2014-08-08 04:20:00   | Normal            | Harley| Spayed Female     |

---

본 문제는 Kaggle의 "Austin Animal Center Shelter Intakes and Outcomes"에서 제공하는 데이터를 사용하였으며 ODbL의 적용을 받습니다.




---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT *
from ANIMAL_INS 
order by ANIMAL_ID
```
### 소감
```plaintext
간단한 문제
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
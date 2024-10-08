# 루시와 엘라 찾기

## ### 문제 설명
`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는 각각 동물의 아이디, 생물 종, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| Column name        | Type        | Nullable |
|--------------------|-------------|----------|
| ANIMAL_ID          | VARCHAR(N)  | FALSE    |
| ANIMAL_TYPE        | VARCHAR(N)  | FALSE    |
| DATETIME           | DATETIME    | FALSE    |
| INTAKE_CONDITION   | VARCHAR(N)  | FALSE    |
| NAME               | VARCHAR(N)  | TRUE     |
| SEX_UPON_INTAKE    | VARCHAR(N)  | FALSE    |

동물 보호소에 들어온 동물 중 이름이 Lucy, Ella, Pickle, Rogan, Sabrina, Mitty인 동물의 아이디와 이름, 성별 및 중성화 여부를 조회하는 SQL 문을 작성해주세요.

이때 결과는 아이디 순으로 조회해주세요. 예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME           | INTAKE_CONDITION | NAME  | SEX_UPON_INTAKE |
|-----------|-------------|--------------------|------------------|-------|-----------------|
| A373219   | Cat         | 2014-07-29 11:43:00| Normal           | Ella  | Spayed Female   |
| A377750   | Dog         | 2017-10-25 17:17:00| Normal           | Lucy  | Spayed Female   |
| A353259   | Dog         | 2016-05-08 12:57:00| Injured          | Bj    | Neutered Male   |
| A354540   | Cat         | 2014-12-11 11:48:00| Normal           | Tux   | Neutered Male   |
| A354597   | Cat         | 2014-05-02 12:16:00| Normal           | Ariel | Spayed Female   |

SQL 문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME  | SEX_UPON_INTAKE |
|-----------|-------|-----------------|
| A373219   | Ella  | Spayed Female   |
| A377750   | Lucy  | Spayed Female   |

본 문제는 Kaggle의 "Austin Animal Center Shelter Intakes and Outcomes"에서 제공하는 데이터를 사용하였으며 ODbL의 적용을 받습니다.


---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE
from ANIMAL_INS
where NAME in ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
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

# 중성화 여부 파악하기

## 문제 설명
`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는 각각 동물의 아이디, 생물 종, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| Column name        | Type        | Nullable |
|--------------------|-------------|----------|
| ANIMAL_ID          | VARCHAR(N)  | FALSE    |
| ANIMAL_TYPE        | VARCHAR(N)  | FALSE    |
| DATETIME           | DATETIME    | FALSE    |
| INTAKE_CONDITION   | VARCHAR(N)  | FALSE    |
| NAME               | VARCHAR(N)  | TRUE     |
| SEX_UPON_INTAKE    | VARCHAR(N)  | FALSE    |

보호소의 동물이 중성화되었는지 아닌지 파악하려 합니다. 중성화된 동물은 `SEX_UPON_INTAKE` 컬럼에 'Neutered' 또는 'Spayed'라는 단어가 들어있습니다. 동물의 아이디와 이름, 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 중성화가 되었다면 'O', 아니라면 'X'라고 표시해주세요.

## 예시
예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME           | INTAKE_CONDITION | NAME       | SEX_UPON_INTAKE |
|-----------|-------------|--------------------|------------------|------------|-----------------|
| A355753   | Dog         | 2015-09-10 13:14:00| Normal           | Elijah     | Neutered Male   |
| A373219   | Cat         | 2014-07-29 11:43:00| Normal           | Ella       | Spayed Female   |
| A382192   | Dog         | 2015-03-13 13:14:00| Normal           | Maxwell 2  | Intact Male     |

- 중성화된 동물: Elijah, Ella
- 중성화하지 않은 동물: Maxwell 2

따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME      | 중성화 |
|-----------|-----------|--------|
| A355753   | Elijah    | O      |
| A373219   | Ella      | O      |
| A382192   | Maxwell 2 | X      |

\* 컬럼 이름은 일치하지 않아도 됩니다.

본 문제는 Kaggle의 "Austin Animal Center Shelter Intakes and Outcomes"에서 제공하는 데이터를 사용하였으며 ODbL의 적용을 받습니다.


---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT ANIMAL_ID, NAME,
    CASE
        WHEN SEX_UPON_INTAKE like '%Neutered%' THEN 'O'
        WHEN SEX_UPON_INTAKE like '%Spayed%' THEN 'O'
        WHEN SEX_UPON_INTAKE like '%Intact%' THEN 'X'
    END as '중성화'
from ANIMAL_INS
order by ANIMAL_ID
```
### 소감
```plaintext
CASE - WHEN - THEN 구문에서 like를 사용하려면, CASE뒤가 아닌 WHEN 뒤에 컬럼명을 붙여야함
값이 일치하는지 검사할땐 CASE 뒤에 컬럼명을 붙임
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

# 이름이 있는 동물의 아이디

## 문제 설명

`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는 각각 동물의 아이디, 생물 종, 보호 시작 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME             | TYPE        | NULLABLE | 
|------------------|-------------|----------|
| ANIMAL_ID        | VARCHAR(N)  | FALSE    |
| ANIMAL_TYPE      | VARCHAR(N)  | FALSE    |
| DATETIME         | DATETIME    | FALSE    |
| INTAKE_CONDITION | VARCHAR(N)  | FALSE    |
| NAME             | VARCHAR(N)  | TRUE     |
| SEX_UPON_INTAKE  | VARCHAR(N)  | FALSE    |

## 문제

동물 보호소에 들어온 동물 중, 이름이 있는 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.

### 예시

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME           | INTAKE_CONDITION | NAME        | SEX_UPON_INTAKE |
|-----------|-------------|--------------------|------------------|-------------|-----------------|
| A434523   | Cat         | 2015-11-20 14:18:00| Normal           | NULL        | Spayed Female   |
| A562649   | Dog         | 2014-03-20 18:06:00| Sick             | NULL        | Spayed Female   |
| A524634   | Dog         | 2015-01-02 18:54:00| Normal           | *Belle      | Intact Female   |
| A465637   | Dog         | 2017-06-04 08:17:00| Injured          | *Commander | Neutered Male   |

이름이 있는 동물의 ID는 `A524634`와 `A465637`입니다. 따라서 SQL을 실행하면 다음과 같이 출력되어야 합니다.

| ANIMAL_ID |
|-----------|
| A465637   |
| A524634   |



---


## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT ANIMAL_ID
from ANIMAL_INS
# where not isnull(NAME)
where NAME is not null
```
### 소감
```plaintext
null값이 아닌 값을 체크하기 위해 isnull() 함수에 not을 붙이거나 컬럼 is not null로 체크 가능
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


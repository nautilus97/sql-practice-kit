# 고양이와 개는 몇 마리 있을까

## 문제 설명

`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다.  
`ANIMAL_INS` 테이블 구조는 다음과 같으며,  
`ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE` 는 각각 동물의 아이디, 생물 종류, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME              | TYPE        | NULLABLE |
|-------------------|-------------|----------|
| ANIMAL_ID         | VARCHAR(N)  | FALSE    |
| ANIMAL_TYPE       | VARCHAR(N)  | FALSE    |
| DATETIME          | DATETIME    | FALSE    |
| INTAKE_CONDITION  | VARCHAR(N)  | FALSE    |
| NAME              | VARCHAR(N)  | TRUE     |
| SEX_UPON_INTAKE   | VARCHAR(N)  | FALSE    |


## 문제

동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요.  
이때 고양이를 개보다 먼저 조회해주세요.


## 예시

다음은 `ANIMAL_INS` 테이블의 예시입니다.

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME  | SEX_UPON_INTAKE |
|-----------|-------------|---------------------|------------------|-------|-----------------|
| A373219   | Cat         | 2014-07-29 11:43:00 | Normal           | Ella  | Spayed Female   |
| A377750   | Dog         | 2017-10-25 17:17:00 | Normal           | Lucy  | Spayed Female   |
| A354540   | Cat         | 2014-12-11 11:48:00 | Normal           | Tux   | Neutered Male   |

고양이는 2마리, 개는 1마리 들어왔습니다.   
따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_TYPE | count |
|-------------|-------|
| Cat         | 2     |
| Dog         | 1     |

---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT ANIMAL_TYPE, count(ANIMAL_TYPE) as count
from ANIMAL_INS
GROUP BY ANIMAL_TYPE
order by ANIMAL_TYPE 
```
### 소감
```plaintext
Cat이 먼저 Dog가 나중이므로 오름차순 order by
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

# 진료과별 총 예약 횟수 출력하기


## 문제 설명

---

## BLACK Part

### 코드
```sql
-- 재용 코드
SELECT MCDP_CD as '진료과 코드', COUNT(*) as '5월예약건수'
from APPOINTMENT 
# where date_format(APNT_YMD, '%Y-%m') = '2022-05'
where YEAR(APNT_YMD) = 2022 and MONTH(APNT_YMD) = 5
GROUP by MCDP_CD
order by COUNT(*), MCDP_CD
```
### 소감
```plaintext
날짜 조건은 date_format을 사용해도 되고, AND로 연도와 월을 체크해도 됨
as로 한글 별칭을 정한 경우, order by에서 이 한글 별칭을 사용하면 에러남
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

# 프로그래머스 SQL 문제 풀이

https://school.programmers.co.kr/learn/challenges?tab=sql_practice_kit
<br/>
두 명의 팀원이 프로그래머스 SQL 문제를 풀고 풀이 과정을 기록한 Repo
<br/>

## Repo 구성

- 문제 유형별로 폴더를 구분<br/>
- 문제 당 하나의 md 파일로 관리<br/>

```plaintext
sql-practice-kit/
├── SELECT/
│   ├── 문제1
│   ├── 문제2
├── JOIN/
│   ├── 문제1
└── README.md
```
<br/>


## md 파일 규칙
### 1. 제목 작성
- {레벨}_{문제이름}.md<br/>
- 문제이름 쓸 때 띄어쓰기 X
```plaintext
level1_평균일일대여요금구하기.md
```
<br/>


### 2. 내용 구성

- 문제 설명
```plaintext
문제 설명 및 문제, 예시
```
<br/>

- 재용 풀이 및 소감
```MySQL
# 재용 코드
SELECT
```
```plaintext
# 소감
```
```plaintext
# 코드 리뷰(Optional)
# Code Review by 이열
# ~~
```


<br/>

- 이열 풀이 및 소감
```MySQL
# 이열 코드
SELECT
```
```plaintext
# 소감
```
```plaintext
# 코드 리뷰(Optional)
# Code Review by 재용
# ~~
```



<br/>

### 3. 커밋 규칙

#### Commit Message 형식
```plaintext
[타입] : [타입]별 설명

문서 작성 : 어디 폴더 어느 문서인지 *필요에 따라 상세 작성
문제 풀이 : 카테고리 / 레벨 / 문제 이름
풀이 수정 : 카테고리 / 레벨 / 문제 이름
코드 리뷰 : 카테고리 / 레벨 / 문제 이름 / by {리뷰어_이름}
```

  
#### Commit Message 예시
```plaintext
문서 작성 : SELECT 폴더에 doc.md 작성
select 관련 개념과 문법들을 정리한 문서입니다
```
```plaintext
풀이 수정 : SELECT / Level 2 / 과일로 만든 아이스크림 고르기
// Commit Message에서는 문제이름 그대로 사용
```
```plaintext
코드 리뷰 : SELECT / Level 1 / 평균 일일 대여 요금 구하기 / by 재용
이열의 코드에 리뷰 작성하였습니다. 확인해주세요
```

#### 개별 Branch 및 Pull Request 사용

- 각 팀원은 자신만의 코드명을 사용하여 브랜치를 생성
- 브랜치 이름 형식: `{코드명}`
  - 예시: `BLACK`, `RED`
  
- 작업이 완료되면 Pull Request를 생성해 팀원의 리뷰를 받은 후 main 브랜치에 Merge
- PR 과정에서 피드백을 주고받고, 필요한 경우 수정 후 Merge

### ⭐️ **PULL_REQUEST_GUIDE.md를 참고하세요** ⭐️







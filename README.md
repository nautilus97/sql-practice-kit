# 프로그래머스 SQL 문제 풀이

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


## md 파일 규칙
### 1. 제목 작성
- {레벨}_{문제이름}.md<br/>
- 문제이름 쓸 때 띄어쓰기 X
```plaintext
level1_평균일일대여요금구하기.md
```
### 2. 내용 구성

- 문제 설명
```plaintext
문제 설명 및 문제, 예시
```
- 재용 풀이 및 소감
```MySQL
SELECT
# 재용 코드
```
```plaintext
소감(Optional)
```


- 이열 풀이 및 소감
```MySQL
SELECT
# 이열 코드
```
```plaintext
소감(Optional)
```

### 3. 커밋 규칙

#### Commit Message 형식
```plaintext
{문제종류} - {문제이름} ({레벨}) : [타입]
```
[타입]은 작업의 성격을 표시
- 풀이 : 문제 풀이 작성
- 수정 : 코드 수정 또는 문제 해결
- 문서 : 문서 작성 또는 수정
  
##### _예시_
```plaintext
SELECT - 평균 일일 대여 요금 구하기 (level 1) : 풀이

// Commit Message에서는 문제이름에 띄어쓰기 사용
```
```plaintext
JOIN - 과일로 만든 아이스크림 고르기 (level 2) : 수정
```

#### 개별 Branch 및 Pull Request 사용

- 각 팀원은 자신만의 코드명을 사용하여 브랜치를 생성
- 브랜치 이름 형식: `{코드명}/{문제종류}`
  - 예시: `BLACK/join`, `RED/select`
  
- 작업이 완료되면 Pull Request를 생성해 팀원의 리뷰를 받은 후 main 브랜치에 Merge
- PR 과정에서 코드 리뷰를 통해 피드백을 주고받고, 필요한 경우 수정 후 Merge










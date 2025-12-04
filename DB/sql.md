# SQL이 뭘까

SQL(Structured Query Language)은 관계형 데이터베이스 관리 시스템(RDBMS)에서 데이터를 다루기 위해 사용하는 언어다.
데이터를 조회하고, 삽입하고, 수정하고, 삭제하는 모든 과정이 SQL을 통해 이루어진다.

즉, SQL은 *데이터베이스와 대화하기 위한 표준 언어*라고 볼 수 있다.

## SQL에서 많이 쓰는 명령어

SQL은 목적에 따라 여러 가지 명령어로 나뉜다. 대표적으로 다음과 같다.

DDL (Data Definition Language)

데이터베이스와 테이블 구조를 정의하는 명령어

CREATE : 데이터베이스, 테이블 생성

ALTER : 테이블 구조 변경

DROP : 테이블, 데이터베이스 삭제

```sql
-- 테이블 생성 예시
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## DML (Data Manipulation Language)

데이터를 조작(삽입, 수정, 삭제)하는 명령어

INSERT : 데이터 삽입

UPDATE : 데이터 수정

DELETE : 데이터 삭제

```sql
-- 데이터 삽입
INSERT INTO users (name, email) VALUES ('홍길동', 'hong@example.com');

-- 데이터 수정
UPDATE users SET name = '김철수' WHERE id = 1;

-- 데이터 삭제
DELETE FROM users WHERE id = 1;

```

## DQL (Data Query Language)

데이터를 조회하는 명령어

SELECT : 데이터 조회

```sql
-- 모든 데이터 조회
SELECT * FROM users;

-- 조건을 걸어서 조회
SELECT name, email FROM users WHERE name = '홍길동';

```

## DCL (Data Control Language)

사용자의 권한과 보안을 제어하는 명령어

GRANT : 권한 부여

REVOKE : 권한 회수

자주 사용하는 SQL 구문

WHERE 절

조건을 걸어 특정 데이터만 조회할 수 있다.

```sql
SELECT * FROM users WHERE email LIKE '%@example.com';

```

ORDER BY 절

데이터를 정렬한다

```sql
SELECT * FROM users ORDER BY created_at DESC;

```

GROUP BY 절

데이터를 그룹화하고 집계함수를 함께 사용한다.

```sql
SELECT COUNT(*) AS user_count, email
FROM users
GROUP BY email;

```

JOIN

두 개 이상의 테이블을 연결해 원하는 데이터를 조회할 수 있다.

```sql

SELECT u.name, o.order_date
FROM users u
JOIN orders o ON u.id = o.user_id;

```

- COALESCE(col1, col2, co3,…)
    - 가장 왼쪽에서 null이 아닌 값을 반환하는 sql 함수
    - ex) COALESCE(col1, ‘~~’) - col1이 null이면 ~~ 반환 아니면 그대로
    - 여러개도 가능
        COALESCE(null, null, ‘a’, ‘b’) - a (이미 a에서 값을 반환해서 b는 반환 x)

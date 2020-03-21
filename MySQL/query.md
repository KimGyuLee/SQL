인프런 SQL/DB(MySQL)  
-------------------------------------------------------------------
*Tool : WorkBench

### 데이터베이스 만들기
~~~sql
SHOW DATABASES;  # 현재 데이터베이스 보기

CREATE DATABASE dbname;  # 데이터베이스 만들기

DROP DATABASE IF EXISTS dbname;  # 데이터베이스 삭제하기 (IF EXISTS 생략 가능)

USE dbname;  # 테이블을 만들기 전에, 테이블을 만들 어떤 데이터베이스를 사용하겠다는 명령을 해야한다
~~~

### 테이블 만들기
~~~sql
# 사용할 데이터베이스를 선택했다면, 테이블을 만들어야 한다
# 테이블에서는 필드(컬럼)와 필드의 데이터형(숫자, 문자 등)을 정의해야 한다
# 테이블에서 Primary key가 될 필드를 지정해줘야 한다

CREATE TABLE tablename (
 ID INT,
 TITLE TEXT,
 ORI_PRICE INT,
 DISCOUNT_PRICE INT,
 PRIMARY KEY (ID)
 );

# 데이터형으로 FLOAT, DOUBLE, INT, TEXT를 많이 쓴다

SHOW TABLES;  # 테이블 확인하기

DROP TABLE myproduct;  # 테이블 삭제하기
~~~





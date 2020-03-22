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
 ID INT UNSIGNED NOT NULL AUTO_INCREMENT,
 TITLE TEXT,
 ORI_PRICE INT,
 DISCOUNT_PRICE INT,
 PRIMARY KEY (ID)
 );

# 데이터형으로 FLOAT, DOUBLE, INT, TEXT를 많이 쓴다
# UNSIGNED : 음수 값을 넣지 못하는 대신, 양수 값을 더 많이 넣을 수 있다. PRIMARY KEY 값의 경우 많이 한다.
# NOT NULL : NULL값이 되면 안된다는 것, 반드시 어떤 값이 들어가야한다는 것이다. PRIMARY KEY는 자동으로 NOT NULL이 된다.
# AUTO_INCREMENT : 최근 값(가장 큰 값)에 1을 자동으로 더해서 값을 지정해준다. (1, 2, 3 --> 4)

SHOW TABLES;  # 테이블 확인하기

DROP TABLE myproduct;  # 테이블 삭제하기

DESC myproduct;  # 테이블 구조 확인하기C
~~~

![캡처](https://user-images.githubusercontent.com/58073455/77239926-83da5300-6c23-11ea-996d-103a53f577bd.PNG)

### 테이블 변경하기
~~~sql


~~~



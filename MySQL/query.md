인프런 SQL/DB(MySQL)  
-------------------------------------------------------------------
*Tool : WorkBench

## 섹션 2. SQL 기초 문법의 이해 (데이터베이스 만들기)  

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
ALTER TABLE tablename ADD COLUMN columnname VARCHAR(10) NOT NULL;  # 컬럼 추가하기

ALTER TABLE tablename MODIFY COLUMN columnname VARCHAR(20) NOT NULL;  # 컬럼의 데이터 타입 변경하기

ALTER TABLE tablename CHANGE COLUMN columnname(원래이름) newname(새로운이름) VARCHAR(10);  # 컬럼명, 컬럼의 데이터 타입 변경하기

ALTER TABLE tablename DROP COLUMN columnname;  # 컬럼 삭제하기
~~~


## 섹션 3. SQL 기초 문법의 이해 (데이터 다루기)
- CRUD : CREATE(생성), READ(읽기), UPDATE(수정), DELETE(삭제)

### 데이터 입력하기
~~~sql
INSERT INTO tablename VALUES (1, 'i7', '7700', 'Kaby Lake');  # 컬럼 순서대로 값 입력하기 (모든 컬럼에 값 지정)

INSERT INTO mytable (name, model_num, model_type) VALUES('i7', '7700k', 'Kaby Lake');  
# 원하는 컬럼에만 값 입력하기 (id 값은 자동으로 입력되므로 입력하지 않음)
~~~

### 데이터 검색하기(읽기)
~~~sql
SELECT * FROM tablename;  # 테이블 내 모든 값 읽기 (SELECT : 읽기 / * : 모든 컬럼)

SELECT columnname FROM tablename;  # 해당 컬럼만 읽기

SELECT columnname1, columnname2 FROM tablename;  # 컬럼 여러개 선택해서 읽기

SELECT columnname AS 표시이름 FROM tablename;  # 해당 컬럼을 내가 원하는 이름으로 표시해서 읽기

SELECT columnname1 AS 표시이름1, columnname2 AS 표시이름2 FROM tablename;  # 컬럼 여러개를 내가 원하는 이름으로 표시해서 읽기
~~~

~~~sql
SELECT columnname FROM tablename ORDER BY id ASC;  # 지정 컬럼 기준 오름차순 정렬 (문자열로 된 컬럼을 기준으로 하는 것도 가능)

SELECT columnname FROM tablename ORDER BY id DESC;  # 지정 컬럼 기준 내림차순 정렬
~~~

~~~sql
SELECT * FROM mytable WHERE columnname = 'i5' OR columnname2 = 'i7';  # 조건에 맞는 데이터 가져오기

SELECT * FROM tablename WHERE columnname LIKE '%7%';  # 부분적으로 일치하는 데이터 가져오기 (7을 포함한 경우)

SELECT * FROM tablename WHERE columnname LIKE '7__';  # 부분적으로 일치하는 데이터 가져오기 (7로 시작하고 뒤에 두글자가 붙는 경우)

SELECT * FROM tablename WHERE columnname LIKE '7__' AND columnname2 Like '%6%';  # 부분적으로 일치하는 데이터 가져오기
~~~

~~~sql
SELECT * FROM tablename LIMIT 5;  # 위에서부터 5개만 보여주기

SELECT * FROM tablename LIMIT 2, 2;  # 3번째부터 2개 보여주기
~~~

#### 조건 조합 시 순서
SELECT FROM WHERE ORDER BY LIMIT
~~~sql
SELECT id, name FROM mytable WHERE id < 4 AND name LIKE '%i%' ORDER BY name DESC LIMIT 2;
~~~

### 데이터 수정하기
~~~sql
UPDATE mytable SET columnname = 'i3', columnname = '5500k' WHERE columnname = 3;  # 조건에 맞는 데이터의 값 수정하기
~~~

### 데이터 삭제하기
~~~sql
DELETE FROM mytable WHERE columnname = 1;  # 조건에 맞는 데이터 삭제하기
~~~

## 섹션 4. 파이썬으로 다루는 MySQL
- library : PyMySQL 

### PyMySQL 시작
~~~python
import pymysql

db = pymysql.connect(host='localhost', port=3306, 
user='root', passwd='abcde', db='ecommerce', charset='utf8')

# host : 접속할 mysql server 주소
# port : 접속할 mysql server 의 포트 번호
# user : mysql ID
# passwd : mysql ID의 암호
# db : 접속할 데이터베이스
# charset='utf8' : 한글이 깨질 수 있으므로 연결 설정에 넣어줌
~~~






















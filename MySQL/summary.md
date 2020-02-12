1.RDBMS (Relational Database Management System) - 데이터베이스와 RDBMS 이해
----------------------------
- DBMS : 데이터베이스를 관리하는 시스템/프로그램
- 데이터가 커지면서 많은 데이터를 효율적으로 관리해야하는 문제를 해결하고, 수많은 데이터에서 필요한 데이터만 빠르게 검색할 수 있는 기능을 제공해주는 프로그램
- 데이터베이스 프로그램 종류 중 가장 많이 쓰이는 것은 RDBMS이다. (RDBMS에는 대표적으로 Oracle, MySQL, Microsoft SQL Server가 있다.)
- 최근에는 빅데이터를 다루는 영역에서 MongoDB, Redis, Hive, HBase와 같은 DBMS가 사용되기도 한다.  
- 데이터베이스 대신 Elasticsearch, Solr와 같은 검색 엔진을 사용하는 경우도 있다.  
(source: https://db-engines.com/en/ranking)  
- SQL 언어를 익히면 RDBMS에 속하는 모든 데이터베이스를 사용할 수 있다.

* **RDBMS 구조의 이해**
  - RDBMS = Relational Database Management System = 관계형 데이터베이스 관리 시스템
  - 관계형 데이터베이스 = 테이블
  - 테이블을 만들어서 그 안에 여러 항목들을 정의한 후, 테이블간의 관계를 설정해서 데이터를 관리하는 방식이 RDBMS이다. (엑셀을 예로 들면 테이블은 각각의 Sheet이고, 그 테이블 안의 항목들은 column이 될 수 있다.)  

* **테이블**
  - 현업에서는 '필드', '레코드'를 많이 쓴다.
![테이블](https://user-images.githubusercontent.com/58073455/73455942-548e2f00-43b4-11ea-95d3-03583e5ee3ab.png)
  - Primary Key : 특정 레코드를 지칭할 때 사용할 수 있도록, 각 레코드에만 있는 unique한 속성이 되는 컬럼이 primary key이다.
  

2.Create-Databases  - SQL 기초 문법의 이해 (데이터베이스 만들기)
----------------------------
* **데이터베이스 스키마 (Schema)**
  - 테이블, 각 테이블에 들어가야하는 필드, 테이블간의 관계를 정의한 것이다. 즉, 데이터베이스 설계도이다.  
![RDBMS구조](https://user-images.githubusercontent.com/58073455/73455432-6ae7bb00-43b3-11ea-95e6-0a5a70be0550.png)  

* **SQL**
  - 모든 관계형 데이터베이스에서 사용가능한 언어이다. 관계형 데이터베이스의 스키마를 정의하거나, 데이터를 추가, 수정, 삭제하는 등의 명령을 수행할 수 있다.
  - SQL은 크게 세 가지 종류로 나뉜다.
    - 데이터 정의 언어 : 데이터 구조 정의 (스키마를 정의하는 기능)
    - 데이터 조작 언어 : 데이터 CRUD (생성, 읽기, 갱신, 삭제)
    - 데이터 제어 언어 : 데이터 핸들링 권한 설정, 데이터 무결성 처리 등

* **데이터베이스 만들기**
  - 데이터베이스 안에는 여러 개의 데이터베이스 이름이 존재한다.
  - 각 데이터베이스 이름 안에는 여러 개의 테이블이 존재한다.  
  
~~~sql
CREATE DATABASE dbname;  # 생성  (= CREATE SCHEMA dbname;)  
~~~~  

~~~sql
SHOW DATABASES;  # 데이터베이스 목록 보기  
~~~~  

~~~sql
DROP DATABASE (IF EXISTS) dbname;   # 데이터베이스 삭제 (if exists는 생략 가능)   
~~~~  

~~~sql
USE dbname;  # 데이터베이스 사용  
~~~~  

  ![WORKBENCH화면](https://user-images.githubusercontent.com/58073455/73460812-712e6500-43bc-11ea-8208-7a8facfa6eb6.PNG)  
  
* **테이블 만들기**
  - USE dbname; 명령 후 테이블을 만들어야 한다.

~~~sql
CREATE TABLE table_name (
    field_name data_type, 
    primary_key KEY
    );
~~~    
 
 EX.
~~~sql
CREATE TABLE myproduct (
    MYKEY INT (UNSIGNED) (NOT NULL) (AUTO_INCREMENT),
    # UNSIGNED는 음수를 저장할 수 없는 대신 양수를 더 높은 수까지 저장할 수 있다. 보통 PRIMARY KEY가 되는 필드는 UNSIGNED인 경우가 많다.
    # NOT NULL는 해당 필드에 값이 할당되지 않는 경우를 허락하지 않겠다는 의미이다.
    # AUTO_INCREMENT는 현재까지 저장되어있는 레코드 중 PRIMARY KEY 값이 가장 큰 것에 1을 더하는 것을 의미한다. (새로운 레코드가 들어왔을 때, 자동으로 PRIMARY KEY 값을 지정해주기 위함이다.)
    ID TEXT,
    TITLE TEXT,
    ORI_PRICE INT,
    DISCOUNT_PRICE INT,
    DELEVERY TEXT,
    PRIMARY KEY (MYKEY)  # 괄호안에 PRIMARY KEY가 될 필드명을 넣는다. PRIMARY KEY는 NULL값이 들어가면 안된다.
    );
~~~~  

* **데이터 타입**  
  
  ![숫자형데이터타입](https://user-images.githubusercontent.com/58073455/73470547-67602e00-43cb-11ea-8405-02c55d568d69.png)  
  ![문자형데이터타입](https://user-images.githubusercontent.com/58073455/73470586-73e48680-43cb-11ea-86c3-1ba10625668d.png)  
  ![시간형데이터타입](https://user-images.githubusercontent.com/58073455/73470613-7c3cc180-43cb-11ea-9b9c-4cff254b9b2e.png)  
  

* **테이블 보기/삭제**

~~~sql
SHOW TABLES;  # 테이블 보기
~~~  

~~~sql
DROP TABLE table_name;  # 테이블 삭제
~~~  

~~~sql
DESC table_name;  # 테이블의 구조 보기
~~~~  

![워크벤치2](https://user-images.githubusercontent.com/58073455/73472780-ef940280-43ce-11ea-9275-1d1fd8688b63.PNG)


* **테이블 구조 수정**

~~~sql
# 테이블에 새로운 컬럼(필드) 추가
ALTER TABLE table_name ADD COLUMN column_name # [추가할 컬럼명][추가할 컬럼 데이터형]
~~~

~~~sql
# 테이블 컬럼(필드) 타입 변경
ALTER TABLE table_name MODIFY COLUMN column_name # [변경할 컬럼명][변경할 컬럼 데이터형]
~~~

~~~sql
# 테이블 컬럼(필드) 이름 변경
ALTER TABLE table_name CHANGE COLUMN [변경할 컬럼명][변경할 컬럼명][변경할 컬럼 데이터형]
# 컬럼명과 데이터형을 한번에 바꿀 수 있다.
~~~

~~~sql
# 테이블 컬럼(필드) 삭제
ALTER TABLE table_name DROP column_name
~~~

![워크벤치3](https://user-images.githubusercontent.com/58073455/73475114-13594780-43d3-11ea-89aa-d5f13bcb92b1.PNG)


3.Handling-Databases  - SQL 기초 문법의 이해 (데이터 다루기)
----------------------------
## 데이터 생성
~~~sql
SHOW DATABASES; # 데이터베이스 보기

USE dbname;  # 데이터베이스 중 하나 선택하기

SHOW TABLES;  # 데이터베이스 내 테이블 보기

DESC table_name;  # 테이블 구조 보기 

INSERT INTO table_name VALUES(1, 'i7', '7700', 'Kaby Lake'); # 각 컬럼에 들어갈 value 입력

INSERT INTO mytable (name, model_num, model_type) VALUES('i7', '7700K', 'Kaby Lake');
# id를 auto_increment로 지정해놓았을 경우, id를 제외하고 입력하면 id는 저절로 생성됨
~~~


4.MySQL-in-Python -   
----------------------------



5.Crawling-and-MySQL  
----------------------------



6.SQL-for-Data-Analysis  
----------------------------


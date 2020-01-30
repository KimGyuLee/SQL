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
SHOW DATABASES;  # 데이터베이스 목록 보기  
DROP DATABASE (IF EXISTS) dbname;   # 데이터베이스 삭제 (if exists는 생략 가능)   
USE dbname;  # 데이터베이스 사용  
~~~~

  ![WORKBENCH화면](https://user-images.githubusercontent.com/58073455/73460812-712e6500-43bc-11ea-8208-7a8facfa6eb6.PNG)  
  
* **테이블 만들기**
  - USE dbname; 명령 후 테이블을 만들어야 한다.

~~~sql
CREATE TABLE table_name(field_name data_type primary_key);
~~~




  


3.Handling-Databases  - SQL 기초 문법의 이해 (데이터 다루기)
----------------------------



4.MySQL-in-Python -   
----------------------------



5.Crawling-and-MySQL  
----------------------------



6.SQL-for-Data-Analysis  
----------------------------


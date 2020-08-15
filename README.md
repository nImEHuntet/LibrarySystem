# Library Management System

### Overview
The library management system based on Spring + Spring MVC + MyBatis uses Maven for package management. The main functions include: book query, book management, book editing, reader management, book borrowing and returning, and borrowing and returning log records.

### Environment configuration
#### Development Environment：Windows 10，IntelliJ IDEA 2018.3
#### Run configuration
1. First install Mysql5.7, set the user name as root, and the password as 123456, and ensure that it is running, and execute the library.sql file to import data.
2. Then configure Maven to the environment variable and run it in the source code directory
```sh
# mvn jetty:run
```
3. Use a browser to visit http://localhost:8080 to enter the system.

### Concept Design
Users are divided into two categories: readers and librarians. Librarians can modify reader information, modify bibliographic information, view all loan and return logs, etc.; readers can only modify personal information, borrow or return books, and view their own loan and return logs.
<img src="./preview/1.png" style="width: 50%"><img src="./preview/2.png" style="width: 50%;float: right">

#### Database E-R Diagram
<img src="./preview/3.png">

### Logic Design
There are 6 tables:

#### 1. Book list book_info
| name         |Input    |length|Decimal | NULL | USE     | Pkey  |
| :----------- | :------ | ---- | ------ | ---- | --------| ----  |
| book_id      | bigint  | 20   | 0      | no   | 图书号   | ✔    |
| name         | varchar | 20   | 0      | no   | 书名     |      |
| author       | varchar | 15   | 0      | no   | 作者     |      |
| publish      | varchar | 20   | 0      | no   | 出版社   |      |
| ISBN         | varchar | 15   | 0      | no   | 标准书号 |      |
| introduction | text    | 0    | 0      | ys   | 简介     |      |
| language     | varchar | 4    | 0      | no   | 语言     |      |
| price        | decimal | 10   | 2      | no   | 价格     |      |
| pub_date     | date    | 0    | 0      | no   | 出版时间 |      |
| class_id     | int     | 11   | 0      | ys   | 分类号   |      |
| number       | int     | 11   | 0      | ys   | 剩余数量 |      |

#### 2. Database administrator table admin
| name     |Input    |length|Decimal | NULL | USE    | Pkey  |
| :------- | :------ | ---- | ------ | ---- | ------ | ---- |
| admin_id | bigint  | 20   | 0      | no   | 账号   | ✔    |
| password | varchar | 15   | 0      | no   | 密码   |      |
| username | varchar | 15   | 0      | ys   | 用户名 |      |

#### 3. Book classification table class_info
| name       |Input    |length|Decimal | NULL | USE   | Pkey  |
| :--------- | :------ | ---- | ------ | ---- | ------ | ---- |
| class_id   | int     | 11   | 0      | no   | 类别号 | ✔    |
| class_name | varchar | 15   | 0      | no   | 类别名 |      |

#### 4. Lending information table lend_list
| name      |Input   |length|Decimal | NULL | USE     | Pkey  |
| :-------- | :----- | ---- | ------ | ---- | -------- | ---- |
| ser_num   | bigint | 20   | 0      | no   | 流水号   | ✔    |
| book_id   | bigint | 20   | 0      | no   | 图书号   |      |
| reader_id | bigint | 20   | 0      | no   | 读者证号 |      |
| lend_date | date   | 0    | 0      | ys   | 借出日期 |      |
| back_date | date   | 0    | 0      | ys   | 归还日期 |      |

#### 5. Debit Card Information Form reader_card
| name      |Input    |length|Decimal | NULL | USE     | Pkey  |
| :-------- | :------ | ---- | ------ | ---- | -------- | ---- |
| reader_id | bigint  | 20   | 0      | no   | 读者证号 | ✔    |
| password  | varchar | 15   | 0      | no   | 密码     |      |
| username  | varchar | 15   | 0      | ys   | 用户名   |      |

#### 6. Reader Information Form reader_info
| name      |Input    |length|Decimal | NULL | USE     | Pkey  |
| :-------- | :------ | ---- | ------ | ---- | -------- | ---- |
| reader_id | bigint  | 20   | 0      | no   | 读者证号 | ✔    |
| name      | varchar | 10   | 0      | no   | 姓名     |      |
| sex       | varchar | 2    | 0      | no   | 性别     |      |
| birth     | date    | 0    | 0      | no   | 生日     |      |
| address   | varchar | 50   | 0      | no   | 地址     |      |
| phone     | varchar | 15   | 0      | no   | 电话     |      |

### function display (will soon add  localization images)
#### 1. Home page login
Admin account: 123456/123456
Reader account: 10000/123456
<img src="./preview/5.png">

#### 2. Administrator system
Login with
##### 2.1 Book Management
<img src="./preview/6.png">

##### 2.2 Book details
<img src="./preview/7.png">

##### 2.3 Reader Management
<img src="./preview/8.png">

##### 2.4 Borrowing and returning management
<img src="./preview/9.png">

#### 3. Reader System
##### 3.1 View all books
<img src="./preview/10.png">

##### 3.2 Viewing personal information, you can modify personal information
<img src="./preview/11.png">

##### 3.3 Viewing personal borrowing status
<img src="./preview/12.png">



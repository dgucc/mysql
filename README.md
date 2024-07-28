#MySQL - Linux Mint 20

Check linux version  

`$ lsb_release -a`  


Install mysql

`$ sudo apt-get update`  
`$ sudo apt-get install mysql-server`

Check status
`$ sudo systemctl status mysql`

Assign root user password

```bash
$ sudo mysql -u root
mysql> SELECT user,host,authentication_string,plugin FROM mysql.user WHERE user='root';
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'admin';
mysql> FLUSH PRIVILEGES;
mysql> quit
```  



Login to mysql 
`$ mysql -u root -p`  

```bash
mysql> show databases;
mysql> create database sample;

```


---
[Download sample database](https://github.com/datacharmer/test_db/tree/master)  

```
$ git clone https://github.com/datacharmer/test_db.git
$ cd test_db
$ mysql -u root -p < employees.sql`  
$ mysql -u root -p
mysql> show databases;
mysql> use employees;;
mysql> describe employees;
mysql> show tables;
+----------------------+
| Tables_in_employees  |
+----------------------+
| current_dept_emp     |
| departments          |
| dept_emp             |
| dept_emp_latest_date |
| dept_manager         |
| employees            |
| salaries             |
| titles               |
+----------------------+
8 rows in set (0,01 sec)
mysql> describe employees;
+------------+---------------+------+-----+---------+-------+
| Field      | Type          | Null | Key | Default | Extra |
+------------+---------------+------+-----+---------+-------+
| emp_no     | int           | NO   | PRI | NULL    |       |
| birth_date | date          | NO   |     | NULL    |       |
| first_name | varchar(14)   | NO   |     | NULL    |       |
| last_name  | varchar(16)   | NO   |     | NULL    |       |
| gender     | enum('M','F') | NO   |     | NULL    |       |
| hire_date  | date          | NO   |     | NULL    |       |
+------------+---------------+------+-----+---------+-------+


```

---

Remove the existing files.  

```bash
$ sudo apt-get remove --purge mysql*  
$ sudo apt-get purge mysql*  
$ sudo apt-get autoremove  
$ sudo apt-get autoclean  
$ sudo apt-get remove dbconfig-mysql
```

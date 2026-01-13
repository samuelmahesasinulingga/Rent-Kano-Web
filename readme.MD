# SQL Injection Demo Application

## Description
This is a simple PHP web application that intentionally contains a SQL Injection
vulnerability for educational and demonstration purposes. The application is
designed to show how SQL Injection works and how it can be mitigated using
secure coding practices.

---

## Prerequisites
- XAMPP (Apache, PHP, MySQL)
- Web browser

---

## Deployment Steps
1. Clone this repository:
   ```bash
   git clone https://github.com/samuelmahesasinulingga/SQLInjection-Lab.git

2. Move the project folder into the XAMPP htdocs directory:
   ```
   C:\xampp\htdocs\SQLInjection
   ```
3. Start Apache and MySQL from XAMPP Control Panel.

4. Create a database named `sqli_demo`.
   ```sql
   CREATE DATABASE sqli_demo;
   ```

5. Create table users. Below the source code:
   ```
   CREATE TABLE `users` (
     `id` int(11) NOT NULL,
     `username` varchar(50) DEFAULT NULL,
     `password` varchar(50) DEFAULT NULL
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
   ```   

6. Insert username and password to table
   ```
   INSERT INTO `users` (`id`, `username`, `password`) VALUES (1, 'admin', 'admin123');
   ```

## How to Run
1. Open the following URL in your browser:
   http://localhost/SQLInjection/login.html

2. Test login with username and password authentic 
   ```
   username : admin
   password : admin123
   ```
   If login is successful, you will be redirected to the dashboard page.

## How to exploit SQL Injection
You can bypass the login authentication by entering the following payload: 
```
Username: ' OR 1=1 #
Password: anything
```
This payload manipulates the SQL query so that the condition always evaluates to true, allowing authentication without valid credentials.


## Fix
The SQL Injection vulnerability is fixed in the `fix/sql-injection` branch using prepared statements.
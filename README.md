# 🎥 Cinema-app
## Project description
Cinema-app is A REST web-application for tickets reservation.
It implements the main functionality such as:
- displaying movies that
  are currently in the box office
- shopping cart with the ability to
  add tickets to it and create an order based on the added tickets
- searching for available movie session by date
-------
Features
---
|Operation|Endpoint `http://localhost:8080`...|Role|
|---------|--------|----|
|Register new user|POST: `/register`|Any                 |
|Get list of movies, cinema halls <p>Get movie session by movie</p>|GET:`/cinema-halls`, `/movies` <p>GET:`/movie-sessions/available`</p>|`USER`, `ADMIN`|
|Get user|GET: `/users/by-email`|`ADMIN`|
|Add new cinema hall, movies,<p>movie-session</p>|POST: `/cinema-halls`, `/movies`,<p>POST: `/movie-sessions`</p>|`ADMIN`|
|Update movie session|PUT: `/movie-sessions/{id}`|`ADMIN`|
|Delete movie session|DELETE: `/movie-sessions/{id}`|`ADMIN`|
|Get list of orders, shopping-carts|GET: `/orders`, `/shopping-carts/by-user`|`USER`|
|Add order|POST: `/orders/complete`|`USER`|
|Update shopping-cart|PUT: `/shopping-carts/movie-sessions`|`USER`|
-----------------
Structure
-----------------
Project was built according to n-tier architecture:
- Controllers (Presentation tier) - take main part in request/response cycle, receive data from users and invoke business logic of services to procces it and store in database. Send back data to users, when they request it.
- Services (Application tier) - this layer coordinates work of all application, procces commands and performs calculations.
- DAO (Data tier) - here information is stored and retrieved.
------------------
Relations in DB
------------------
![alt text](img/Hibernate_Cinema_Uml.png)
-----------------
Technologies
-----------------
- JDK 11
- Maven 4.0
- Hibernate 5.6.14.Final
- Spring (Core, Web) 5.3.20
- Spring Security 5.6.10
- MySQL 8.0.22
- TomCat 9.0.68
------------------
Installation
-----------------
- Clone this project from GitHub
```bash
git clone github.com/AndriiMatveev/cinema-app
```
- Install [MySQL](https://dev.mysql.com/doc/mysql-installation-excerpt/5.7/en/)
- Create a schema in your MySQL DB.
  You can run the following query:<br>
```
CREATE SCHEMA IF NOT EXISTS `cinema-app` DEFAULT CHARACTER SET utf8;
```
- Install [Apache Tomcat v.9.x.x](https://tomcat.apache.org/download-90.cgi)
- Change URL, username, password and JDBC driver in [db.properties](src/main/resources/db.properties)
- Configure Tomcat server
- Download [Postman](https://www.postman.com) desktop version and write your data in query
- A default user with ADMIN role is created in [DataInitializer](src/main/java/cinema/DataInitializer.java) when the project starts



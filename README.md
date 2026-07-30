# 🚆 Train Ticket Reservation System

> A web-based application for searching trains, booking tickets, managing users, and viewing reservation history.

![Java](https://img.shields.io/badge/Java-8%2B-orange)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)
![Maven](https://img.shields.io/badge/Maven-Build%20Tool-red)
![Tomcat](https://img.shields.io/badge/Apache%20Tomcat-9-yellow)
![Status](https://img.shields.io/badge/Status-Active-success)

---

## 📖 About the Project

The **Train Ticket Reservation System** is a Java web application developed using:

- Java
- JSP and Servlets
- JDBC
- MySQL
- Maven
- Apache Tomcat

The application allows users to register, log in, search available trains, book tickets, and view their booking history.

Administrators can manage trains and view registered users.

---

## ✨ Features

### 👤 User Features

- 📝 New user registration
- 🔐 User login and logout
- 🚆 View available trains
- 🔎 Search trains by source and destination
- 🎫 Book train tickets
- 📜 View booking history
- 👤 Update user profile

### 🛠️ Admin Features

- 🔐 Admin login
- ➕ Add new trains
- 📋 View all trains
- ✏️ Update train details
- 🗑️ Delete trains
- 👥 View registered users

---

## 🧰 Technology Stack

| Technology | Usage |
|---|---|
| ☕ Java | Backend development |
| 🌐 JSP | Dynamic web pages |
| ⚙️ Servlets | Request and response handling |
| 🔌 JDBC | Database connectivity |
| 🐬 MySQL | Database management |
| 📦 Maven | Build and dependency management |
| 🐱 Apache Tomcat | Web application server |
| 🎨 HTML, CSS, JavaScript | Frontend development |
| 🌿 Git | Version control |
| 🐙 GitHub | Source code hosting |

---

## 📂 Project Structure

```text
train-ticket-reservation/
│
├── 📁 src/
│   ├── application.properties
│   └── com/shashi/
│       ├── beans/
│       ├── constant/
│       ├── service/
│       │   └── impl/
│       ├── utility/
│       └── servlet/
│
├── 📁 WebContent/
│   ├── CSS/
│   ├── JS/
│   ├── images/
│   └── JSP files
│
├── 📁 Screenshots/
├── 📄 pom.xml
├── 📄 settings.xml
├── 📄 Dummy-Database.md
└── 📄 README.md
⚙️ Installation and Setup
1️⃣ Prerequisites

**Install the following software**:

☕ Java JDK 8 or later
📦 Apache Maven
🐬 MySQL Server 8.0 or later
🐱 Apache Tomcat 9
🌿 Git
💻 VS Code or Eclipse

Check the installed versions:

java -version
mvn --version
mysql --version
git --version
2️⃣ **Clone the Repository**
git clone https://github.com/RamMohanKavuri/train-ticket-reservation.git

Move into the project folder:

cd train-ticket-reservation
3️⃣** Create the MySQL Database**

Login to MySQL:

mysql -u root -p

Create and select the database:

CREATE DATABASE train_reservation;

USE train_reservation;
4️⃣** Create Database Tables**
CUSTOMER Table
CREATE TABLE CUSTOMER (
    MAILID VARCHAR(40) PRIMARY KEY,
    PWORD VARCHAR(20) NOT NULL,
    FNAME VARCHAR(20) NOT NULL,
    LNAME VARCHAR(20),
    ADDR VARCHAR(100),
    PHNO BIGINT NOT NULL
);
ADMIN Table
CREATE TABLE ADMIN (
    MAILID VARCHAR(40) PRIMARY KEY,
    PWORD VARCHAR(20) NOT NULL,
    FNAME VARCHAR(20) NOT NULL,
    LNAME VARCHAR(20),
    ADDR VARCHAR(100),
    PHNO BIGINT NOT NULL
);
TRAIN Table
CREATE TABLE TRAIN (
    TR_NO INT PRIMARY KEY,
    TR_NAME VARCHAR(70) NOT NULL,
    FROM_STN VARCHAR(20) NOT NULL,
    TO_STN VARCHAR(20) NOT NULL,
    SEATS INT NOT NULL,
    FARE DECIMAL(10,2) NOT NULL
);
HISTORY Table
CREATE TABLE HISTORY (
    TRANSID VARCHAR(36) PRIMARY KEY,
    MAILID VARCHAR(40),
    TR_NO INT,
    DATE DATE,
    FROM_STN VARCHAR(20) NOT NULL,
    TO_STN VARCHAR(20) NOT NULL,
    SEATS INT NOT NULL,
    AMOUNT DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (MAILID) REFERENCES CUSTOMER(MAILID)
);
5️⃣ **Add Demo Login Data**
INSERT INTO ADMIN
VALUES (
    'admin@demo.com',
    'admin',
    'System',
    'Admin',
    'Demo Address',
    9874561230
);

INSERT INTO CUSTOMER
VALUES (
    'shashi@demo.com',
    'shashi',
    'Shashi',
    'Raj',
    'Kolkata, West Bengal',
    954745222
);
🔐 Demo Login Credentials
User Type	Email	Password
👤 User	shashi@demo.com	shashi
🛠️ Admin	admin@demo.com	admin
🔧 Database Configuration

Open:

src/application.properties

Update the MySQL configuration:

driverName=com.mysql.cj.jdbc.Driver

connectionString=jdbc:mysql://localhost:3306/train_reservation?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC

username=root

password=YOUR_MYSQL_PASSWORD

Replace:

YOUR_MYSQL_PASSWORD

with your MySQL password.

**⚠️ Never upload your real database password to a public GitHub repository.

📦 Build the Project**

Open Git Bash inside the project folder:

cd ~/OneDrive/Desktop/train-ticket-reservation

Build the application:

mvn clean package

After a successful build, you should see:

BUILD SUCCESS

The generated WAR file will be available at:

target/TrainBook-1.0.0-SNAPSHOT.war
🚀 Deploy on Apache Tomcat

Copy the WAR file to Tomcat's webapps folder:

cp target/TrainBook-1.0.0-SNAPSHOT.war \
"/c/Users/RAM/Downloads/apache-tomcat-9.0.120-windows-x64/apache-tomcat-9.0.120/webapps/"

Go to the Tomcat bin folder:

cd "/c/Users/RAM/Downloads/apache-tomcat-9.0.120-windows-x64/apache-tomcat-9.0.120/bin"

Start Tomcat:

./startup.sh

Open the application in your browser:

http://localhost:8080/TrainBook-1.0.0-SNAPSHOT
📝 New User Registration

Users can create a new account using:

New User Register

The registration details are stored in the MySQL CUSTOMER table.

The application uses:

ps.executeUpdate();

This is used because an INSERT query changes data and does not return a result set.

🧪 Verify Database Data

Login to MySQL:

mysql -u root -p

Run:

USE train_reservation;

SHOW TABLES;

SELECT * FROM CUSTOMER;

SELECT * FROM ADMIN;

SELECT * FROM TRAIN;

SELECT * FROM HISTORY;
**🛑 Stop Apache Tomcat**

Go to the Tomcat bin folder:

cd "/c/Users/RAM/Downloads/apache-tomcat-9.0.120-windows-x64/apache-tomcat-9.0.120/bin"

Stop Tomcat:

./shutdown.sh
📸 Screenshots

Add your project screenshots inside the Screenshots folder.

Example:

**## 🏠 Home Page**

![Home Page](Screenshots/home-page.png)

**## 🔐 User Login**

![User Login](Screenshots/user-login.png)

**## 🚆 Train Search**

![Train Search](Screenshots/train-search.png)
🔄 Application Flow
User
  ↓
Register / Login
  ↓
Search Available Trains
  ↓
Select Train
  ↓
Book Ticket
  ↓
Booking Saved in MySQL
  ↓
View Booking History
👨‍💻 Author

Ram Mohan Kavuri

🐙 GitHub: @RamMohanKavuri

📄 License
**
This project is developed for learning and educational purposes.**

⭐ If you find this project useful, consider giving the repository a star!


After saving the README, push it using:

```bash
cd ~/OneDrive/Desktop/train-ticket-reservation

git add README.md

git commit -m "Add creative project README"

git push origin master

If your branch is main, use:

git push origin main

Also, before pushing, check:

cat src/application.properties

If your real MySQL password is present, replace it with:

password=YOUR_MYSQL_PASSWORD

Then push the project.

**
👨‍💻 Author

Ram Mohan Kavuri

GitHub: https://github.com/RamMohanKavuri**


⭐ If you find this project useful, consider giving the repository a star!

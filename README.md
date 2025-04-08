<h1 align="center">🔥 DSA Tracker - Backend API 🔥</h1>

<p align="center">
  Track your daily DSA progress, maintain solving streaks, and get automatic email reminders with this Spring Boot-powered backend system.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/SpringBoot-2.7-green?style=for-the-badge&logo=springboot" />
  <img src="https://img.shields.io/badge/Java-17-blue?style=for-the-badge&logo=java" />
  <img src="https://img.shields.io/badge/MySQL-Database-orange?style=for-the-badge&logo=mysql" />
  <img src="https://img.shields.io/badge/Security-SpringSecurity-red?style=for-the-badge&logo=springsecurity" />
</p>

---

## 📌 Overview

The **DSA Tracker Backend** is a RESTful backend application that enables users to:

- ⏱️ Track their daily DSA solving streaks.
- 📧 Receive automated email reminders if they miss a day.
- 🔐 Authenticate securely using Spring Security.
- 📊 Get streak history and performance tracking.

Built using **Spring Boot**, **Spring Scheduler**, **JavaMail**, **JPA/Hibernate**, and a **relational database (MySQL/PostgreSQL)**.

---

## 🚀 Features

- ✅ **Daily Streak Tracking**
- 📆 **Midnight CRON Jobs** for checking user activity
- 📧 **Email Reminders** for inactive users
- 🔐 **User Authentication** using Spring Security
- 📊 **Streak History** for each user
- 📦 Modular and clean service/repository architecture

---

## 🏗️ Project Structure


---

## 🧠 Key Components

### 🧍 `UserDetailsServiceImpl.java`
- Authenticates users via Spring Security.
- Retrieves users from the DB and builds `UserDetails`.

### 📈 `StreakService.java`
- Updates user streaks daily.
- Maintains `lastActiveDate` and `streakCount`.
- Prevents streak increment if already updated today.

### ⏰ `StreakScheduler.java`
- Cron-based scheduler that runs **every midnight**.
- Checks if users solved any problems today/yesterday and updates their streak accordingly.

### 📬 `ReminderScheduler.java`
- Sends an email reminder to users who didn’t solve any DSA problems **yesterday**.
- Configured with **Spring Mail** + CRON.

---

## 🛠️ Technologies Used

| Technology        | Description                            |
|------------------|----------------------------------------|
| Java 17           | Programming Language                   |
| Spring Boot       | Backend Framework                      |
| Spring Security   | Authentication and Authorization       |
| Spring Data JPA   | ORM with Hibernate                     |
| Spring Scheduler  | Task Scheduling                        |
| JavaMailSender    | Email Notification System              |
| MySQL/PostgreSQL  | Relational Database                    |

---

## ⚙️ Configuration

Update your `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/dsa_db
spring.datasource.username=root
spring.datasource.password=yourpassword

spring.jpa.hibernate.ddl-auto=update

spring.mail.username=youremail@gmail.com
spring.mail.password=your-app-password
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true


# Clone the repo
git clone https://github.com/your-username/dsa-tracker-backend.git
cd dsa-tracker-backend

# Run the project
./mvnw spring-boot:run

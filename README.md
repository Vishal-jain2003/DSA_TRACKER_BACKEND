# 🔥 DSA Tracker - Backend API

Track your daily DSA progress, maintain solving streaks, and get automatic email reminders — powered by **Spring Boot**.

---

## 📌 Overview

This backend system allows users to:
- ✅ Track daily DSA streaks
- 📬 Receive email reminders for inactivity
- 🔐 Secure login with Spring Security
- 📊 View their complete streak history

---

## 🚀 Tech Stack

- **Java 17**
- **Spring Boot**
- **Spring Security**
- **Spring Data JPA**
- **Spring Scheduler**
- **MySQL / PostgreSQL**
- **Java Mail Sender**

---

## 🗂 Project Structure

dsa_tracker_adv/ ├── entity/ # User and Streak entity classes ├── repository/ # Spring Data JPA interfaces ├── scheduler/ # Cron jobs for updating streaks and sending reminders ├── service/ # Core business logic ├── controller/ # (Expected in full app) └── application.properties # DB and mail configuration

yaml
Copy
Edit

---

## 🔑 Key Features

### ✅ `StreakService.java`
- Tracks daily solving streaks
- Saves streak only once per day
- Updates user's `lastActiveDate` and `streakCount`

### ⏰ `StreakScheduler.java`
- Runs **every midnight**
- Checks user activity and updates streak

### 📧 `ReminderScheduler.java`
- Runs **every morning**
- Sends email to users inactive yesterday

### 🔐 `UserDetailsServiceImpl.java`
- Loads user by username
- Supports Spring Security authentication

---

## ⚙️ Configuration

Update your `application.properties`:

```properties
# Database
spring.datasource.url=jdbc:mysql://localhost:3306/dsa_db
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=update

# Email Configuration
spring.mail.username=youremail@gmail.com
spring.mail.password=your-app-password
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
⏰ CRON Jobs
Task	CRON Expression	Purpose
Update Streak	0 0 0 * * ?	Every midnight
Send Reminders	0 30 9 * * ?	Every day at 9:30 AM
Test CRON (dev)	0 * * * * ?	Every minute for testing
▶️ How to Run
bash
Copy
Edit
# Clone the repo
git clone https://github.com/your-username/dsa-tracker-backend.git
cd dsa-tracker-backend

# Run the Spring Boot app
./mvnw spring-boot:run
📬 Test Email Reminders
Add a test user who didn’t solve yesterday

Temporarily set CRON to every minute:

java
Copy
Edit
@Scheduled(cron = "0 * * * * ?")
Check email inbox/logs for result

👤 Author
Vishal Jain
🎓 MCA | 💻 Java Full Stack Developer | 🧠 DSA & Backend Enthusiast
🌐 Portfolio
🔗 LinkedIn

⭐ Support
If this project helped you, star the repository — it means a lot and encourages future improvements 🙌

📈 Future Roadmap
 Add JWT-based login system

 Build leaderboard by user streak

 Add frontend (React/Next.js)

 Track questions attempted & time spent


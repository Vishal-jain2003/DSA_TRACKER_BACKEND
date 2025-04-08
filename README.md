# 💻 DSA Tracker Backend (Advanced)

Track your daily DSA progress, maintain solving streaks, and get automatic reminders — powered by **Spring Boot**.  
This backend serves as the core of your DSA Tracker app — handling users, streaks, scheduling, and more.

---

## 🚀 Features

- 🔐 User authentication with Spring Security
- 📈 Daily streak tracking per user
- ⏰ Scheduled updates at midnight
- 📬 Reminder emails for inactive users
- 🗂️ Well-structured service and scheduler layers

---

## 🛠 Tech Stack

- Java 21
- Spring Boot
- Spring Security
- Spring Data JPA
- Spring Scheduler
- Java Mail Sender
- MySQL / PostgreSQL

---


---

## ⚙️ Configuration (application.properties)

```properties
# Database Config
spring.datasource.url=jdbc:mysql://localhost:3306/dsa_db
spring.datasource.username=your_db_username
spring.datasource.password=your_db_password
spring.jpa.hibernate.ddl-auto=update

# Email Config
spring.mail.username=youremail@gmail.com
spring.mail.password=your_app_password
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true


🧠 Key Classes Overview
✅ StreakService.java
Checks if the user solved any problem today

Continues streak if solved yesterday, resets otherwise

Updates last active date and current streak count

⏰ StreakScheduler.java
Runs daily at midnight (00:00) via @Scheduled(cron = "0 0 0 * * ?")

Iterates all users and updates streaks via streakService.updateStreak(userId)

📬 ReminderScheduler.java
Runs daily at 9:30 AM

Sends email to users who were inactive yesterday

🔐 UserDetailsServiceImpl.java
Supports Spring Security

Loads user from DB by username during login

⏰ Scheduler Timing Summary
Job Name	Purpose	Cron Expression
Update Streak	Update user streak at midnight	0 0 0 * * ?
Send Reminders	Email users inactive yesterday	0 30 9 * * ?
▶️ Run Locally
bash
Copy
Edit
# Clone the repository
git clone https://github.com/your-username/dsa-tracker-backend.git
cd dsa-tracker-backend

# Run with Maven
./mvnw spring-boot:run
🔒 Security
Passwords stored securely using Spring Security

Supports login via UserDetailsServiceImpl

📬 Sample Email Reminder
Subject: Don’t lose your streak!
Body: You didn’t solve any DSA problems yesterday. Solve today to keep the streak alive! 💪

🧩 Future Enhancements
 Add leaderboard by longest streak

 Add REST APIs for frontend

 Implement JWT authentication

 Add solved problem tracking

🙋‍♂️ Author
Vishal Jain
🚀 MCA | Java Backend Developer | DSA Enthusiast
🌐 Portfolio
🔗 LinkedIn

🌟 Star the Repo
If this helped you or inspired your own project, feel free to ⭐ star this repository. It helps others discover it and supports continued development!

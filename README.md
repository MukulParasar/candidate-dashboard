# 🚀 Backend Engineering Assignment: Core API & Guardrails

## 📌 Overview
This project is a Spring Boot microservice that simulates a social media backend with:
- Post & Comment APIs
- Redis-based virality scoring
- Concurrency-safe guardrails (atomic locks)
- Notification batching system

---

## 🛠 Tech Stack
- Java 17
- Spring Boot 3.x
- PostgreSQL
- Redis

---

## ⚙️ Setup Instructions

### 1. Clone Repository
```bash
git clone <your-repo-url>
cd <project-folder>
```

---

### 2. Configure PostgreSQL

Create a database named:

```sql
social_db
```

Update `application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/social_db
spring.datasource.username=postgres
spring.datasource.password=password
```

---

### 3. Run Redis

```bash
redis-server
```

Verify:

```bash
redis-cli ping
# Expected output: PONG
```

---

### 4. Run Application

```bash
./mvnw spring-boot:run
```

---

## 📂 Project Structure

```
src/main/java/com/example/project
│
├── controller
├── service
├── repository
├── entity
└── scheduler
```

---

## 🧱 Database Schema

### User
- id
- username
- isPremium

### Post
- id
- authorId
- content
- createdAt

### Comment
- id
- postId
- authorId
- content
- depthLevel
- createdAt

---

## 🌐 API Endpoints

### Create Post
```
POST /api/posts
```

### Add Comment
```
POST /api/posts/{postId}/comments
```

### Like Post
```
POST /api/posts/{postId}/like
```

---

## 🔥 Redis Virality Engine

| Action         | Score |
|---------------|------|
| Bot Reply     | +1   |
| Human Like    | +20  |
| Human Comment | +50  |

Redis Key:

```
post:{id}:virality_score
```

---

## 🔒 Atomic Locks

### Horizontal Cap (Max 100 Bot Replies)
- Redis Key: `post:{id}:bot_count`
- Uses atomic `INCR`
- Reject if count > 100

### Vertical Cap (Max Depth 20)
- Reject if `depthLevel > 20`

### Cooldown Cap (10 minutes)
- Key: `cooldown:bot_{id}:human_{id}`
- Uses TTL
- Prevents repeated interaction

---

## 🧠 Thread Safety

Redis operations like `INCR` are atomic, ensuring:
- No race conditions
- Horizontal cap never exceeds 100 under concurrency

---

## 🔔 Notification Engine

### Throttling Logic
- If user received notification in last 15 mins → Store in Redis List
- Else → Send immediately

Keys:

```
user:{id}:pending_notifs
cooldown:notif:{id}
```

---

## ⏰ Scheduler (CRON)

Runs every 5 minutes:
- Fetch pending notifications
- Count interactions
- Log summary:
  ```
  Summarized Notification: X interactions
  ```
- Clear Redis list

---

## 🧪 Edge Cases

### Concurrency Test
- 200 simultaneous requests
- Only 100 allowed

### Statelessness
- No in-memory storage
- Everything handled via Redis

### Data Integrity
- DB writes only after Redis validation

---

## 📬 Postman

Import Postman collection JSON to test APIs.

---

## 🏁 Conclusion

- Redis → Gatekeeper  
- PostgreSQL → Source of truth  
- System → Stateless & scalable

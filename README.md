# 🗳️ Voting App - Kubernetes Architecture

This project demonstrates a **containerized voting application** orchestrated with **Kubernetes**, composed of multiple Pods and Services.

## 🧩 Architecture

The application is made up of the following components:

### 🎯 Frontend
- **voting-app (Python)**
  - Provides the voting interface for users.  
  - Sends votes to Redis.

### 🧠 Backend
- **worker (Python)**
  - Listens to events from Redis.  
  - Processes votes and stores results in PostgreSQL.

### 💾 Database
- **db (PostgreSQL)**
  - Stores voting results.

### ⚙️ State Storage
- **redis**
  - Temporarily stores votes in memory.

### 📊 Results
- **result-app (Node.js)**
  - Displays the current voting results.

---

## 🚀 Pod Communication

Each component runs in its own **Pod** and is exposed through a **Service**, enabling internal communication within the cluster:


```plaintext
[voting-app] --> [redis] --> [worker] --> [db]
                          ↓
                    [result-app]

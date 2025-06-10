# Online-Judge

# 🧠 Online Judge System

An end-to-end Online Judge platform built with the MERN stack, integrated with AWS for scalable code execution, and featuring secure authentication and sandboxed judging of user-submitted code.

## 🚀 Features

- 👤 JWT-based user authentication and role-based access (user/admin)
- 📋 Problem listing with descriptions, constraints, and test cases
- 💻 Code editor with language selection and submission
- 🔄 Asynchronous judging using Docker and AWS SQS
- 📈 Admin panel to upload problems and test cases
- 📦 Scalable and secure Docker-based code execution engine

---

## 🛠️ Tech Stack

### 🖥️ Frontend
- React.js (with Axios + React Router)
- Monaco Code Editor
- Tailwind CSS

### 🌐 Backend
- Node.js + Express
- JWT Auth + Bcrypt
- MongoDB (Atlas)

### ☁️ Cloud Infrastructure (AWS)
- S3 — Test case & code storage
- SQS — Code submission queue
- EC2 (or Lambda) — Judging service with Docker
- IAM — Secure access control
- CloudWatch — Execution logs
- Route 53 + ACM — Domain and HTTPS

---

## ⚙️ System Architecture

Client (React) → API (Express) → MongoDB
↓
AWS SQS (Queue)
↓
Judging Microservice (EC2/Lambda + Docker)
↓
Results stored back in MongoDB


---

## 📂 Project Structure

/client ← React frontend
/server ← Express backend
/judger ← Docker-based code executor
/infrastructure ← AWS scripts 

---

## 🧪 Judging Logic

- User submits code → stored in DB → pushed to SQS
- Judger fetches submission:
  - Loads problem + test cases
  - Executes in Docker container with time/memory limits
  - Compares output with expected
  - Updates MongoDB with result
- Result is polled/shown on frontend

---

## 🔐 Authentication

- Passwords hashed with Bcrypt
- JWT tokens used for stateless auth
- Role-based access (`user`, `admin`) middleware 

---

## 🧰 Setup Instructions

### 1. Clone the repository



- "git clone https://github.com/your-username/online-judge.git'
- "cd online-judge"

---

### 2. Setup Environment Variables

Create .env files in /server and /judger:


PORT=5000
MONGO_URI=your_mongo_uri
JWT_SECRET=your_jwt_secret
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
AWS_REGION=...
SQS_QUEUE_URL=...

### 3. Start Backend + Frontend

cd server
npm install
npm run dev

cd ../client
npm install
npm start


### 4. Judger Setup

Build Docker images for each language

Run judger as a service that polls SQS

cd judger
npm install
node judger.js

### Sample API Routes

Auth
POST /api/auth/register

POST /api/auth/login

Problems
GET /api/problems

GET /api/problems/:id

POST /api/admin/problem (Admin only)

Submissions
POST /api/submit

GET /api/submissions/:id


## ✨ Future Enhancements
WebSocket or polling for real-time submission status

Leaderboards and contests

IDE-style error highlighting

Rate limiting & abuse detection

Redis caching for problem lists



## 📸 Screenshots
Coming soon...

## 🧑‍💻 Author
Anany Singh
Backend Developer | System Designer | MERN Enthusiast

## 📄 License
This project is licensed under the MIT License.

---

# 📱 Saathi Mandram – Job Onboarding Platform

**Saathi Mandram** is a lightweight full-stack job onboarding platform for blue-collar workers and recruiters. It allows **job seekers** to register with basic details and apply for jobs, while **recruiters** can post job listings, manage applications, and view applicants — all on a responsive web app with OTP-based authentication.
[PRESENTATION OF OUR IDEA](https://www.transfernow.net/dl/20250729G765JbK9)
---

## 🧭 Why Saathi Mandram Matters
In many parts of India, migrant workers from rural villages fall prey to exploitative middlemen, known as dalals. These agents often promise lucrative jobs in distant cities like Mumbai or Delhi, but what awaits is a cycle of wage theft, abuse, and forced labor, with no one to turn to for help.

A hostel floor attendant from Assam once shared his experience — he was sent to Bombay for work, only to realize it was a scam. He was one of the lucky few who escaped, but many others never return, falling into a system that dehumanizes and exploits them. Their voices are silenced before they’re ever heard.

Saathi Mandram is built for them — the invisible workforce, the overlooked backbone of our economy. Those who aren't looked at twice.
We aim to restore dignity, safety, and opportunity through a verified, transparent job onboarding platform that protects against fraud and connects workers directly with employers — no middlemen, no traps.

Everyone deserves a chance to work with security and respect.
Saathi Mandram ensures that those who build our cities aren’t left behind in the process.



## 🔧 Tech Stack

### ⚙️ Backend

* **Next.js API Routes** – Built-in serverless functions for handling RESTful APIs.
* **SQLite (via better-sqlite3)** – Lightweight, file-based database used for storing users, jobs, and applications.
* **Firebase Authentication** – OTP-based login system using Firebase's secure phone authentication.

### 🖥 Frontend

* **Next.js with App Router (`/app`)**
* **React Hooks & Server Components**
* **Tailwind CSS** – Utility-first CSS framework for styling.

---

## 📦 API Endpoints

### 📍 Users

#### `GET /api/users?phone=PHONE_NUMBER`

* Fetches a user by phone number.
* **Query Param**: `phone` (required)

#### `POST /api/users`

* Adds or updates a user (job seeker or recruiter).
* **Body**:

  ```json
  {
    "phone": "string",
    "name": "string",
    "age": number,
    "place": "string",
    "field_of_work": "string",
    "remarks": "string",
    "picture_link": "string",
    "years_of_experience": number,
    "is_recruiter": 0 or 1,
    "position": "string",
    "company_name": "string"
  }
  ```

---

### 📍 Jobs

#### `GET /api/jobs?phone=RECRUITER_PHONE`

* Fetches all jobs posted by a specific recruiter.
* Returns applicant count and user details for each job.

#### `POST /api/jobs`

* Creates a new job post.
* **Body**:

  ```json
  {
    "recruiter_phone": "string",
    "area_of_work": "string",
    "pay": "string",
    "job_description": "string",
    "job_type": "string",
    "benefits": "string",
    "location": "string"
  }
  ```
* Only users with `is_recruiter: 1` can post jobs.

---

### 📍 Applications

#### `POST /api/apply`

* Records a job application.
* **Body**:

  ```json
  {
    "user_phone": "string",
    "job_id": number
  }
  ```

---

## 🧑‍💼 Features

* ✅ **Job Seeker Registration**: Capture name, age, place, field, remarks, and experience.
* ✅ **Recruiter Portal**: Add company name, position, and post jobs.
* ✅ **Job Posting & Management**: Recruiters can view and manage their listings and see applicant details.
* ✅ **Firebase OTP Login**: Secure, phone number–based login system.
* ✅ **Fallback UI**: Graceful fallback to dummy data if the server is unreachable.
* ✅ **Applicant Count**: Shown live per job post.

---

## 📁 Directory Highlights

* `/app/api/users/route.js` – User management API.
* `/app/api/jobs/route.js` – Job posting and retrieval API (with applicants).
* `/app/api/apply/route.js` – Endpoint for job applications.
* `/app/recruiter/jobs/page.jsx` – Full recruiter dashboard with job list, applicant info, and job creation form.

---

## 📸 Sample UI Screens

* Recruiter dashboard with job management
* Job listing cards with applicant count
* OTP-based login screen (powered by Firebase)

---

## 💡 Future Ideas

* 🔐 JWT-based session authentication
* ☁️ Firebase Storage or S3 for image uploads
* 📱 PWA support for mobile users
* 🔎 Search and filter for job listings
* 🎤 TTS based user onboarding for the illiterate
---

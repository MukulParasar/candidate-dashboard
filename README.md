# 👨‍💼 Candidate Dashboard App

A modern Candidate Management Dashboard built with React that enables recruiters or admins to efficiently manage candidate data with authentication and full CRUD capabilities.

---

## 📌 Overview
This application simulates a lightweight Applicant Tracking System (ATS) where users can securely log in and manage candidate profiles. It focuses on usability, clean UI, and scalable frontend architecture.

---

## 🚀 Key Features

- 🔐 **Google Authentication**
  - Secure login using Google OAuth
- 📋 **Candidate Listing**
  - View all candidates in a structured format
- 🔍 **Candidate Details View**
  - Click on a candidate to see complete details
- ➕ **Add Candidate**
  - Create new candidate profiles via form
- ✏️ **Edit Candidate**
  - Update existing candidate information
- 🗑️ **Delete Candidate**
  - Remove candidates with confirmation handling
- 🔄 **Dynamic Routing**
  - Smooth navigation using React Router

---

## 🛠 Tech Stack

| Technology        | Purpose                          |
|------------------|----------------------------------|
| React            | Frontend Framework               |
| React Router     | Navigation & Routing             |
| Bootstrap 5.2    | UI Styling                       |
| CSS Variables    | Theming & Custom Styling         |
| Flexbox          | Layout Management                |

---

## ⚙️ Getting Started

### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd <project-folder>
```

---

### 2. Install Dependencies
```bash
npm install
```

---

### 3. Start Development Server
```bash
npm start
```

📍 Open your browser and navigate to:
```
http://localhost:3000
```

---

## 📂 Project Structure

```
src/
│
├── components/       # Reusable UI components
├── pages/            # Application pages (Home, Details, Form)
├── routes/           # Route configurations
├── services/         # API / data handling logic
├── assets/           # Images, styles, static files
└── App.js            # Root component
```

---

## 🧠 Design & Development Approach

- Component-based architecture for reusability
- Separation of concerns (UI, logic, routing)
- Clean and responsive UI using Bootstrap + Flexbox
- Scalable folder structure for future backend/API integration
- Emphasis on user experience and smooth navigation

---

## ⚠️ Assumptions

- Candidate data may be stored locally or via mock APIs
- Google Authentication requires proper API key setup (if implemented)
- No backend persistence unless integrated separately

---

## 🚧 Future Improvements

- 🔗 Backend integration (Node.js / Spring Boot)
- 🗄️ Database connectivity (MongoDB / PostgreSQL)
- 🔍 Search & filtering functionality
- 📊 Pagination for large datasets
- 🔐 Role-based access control (Admin/User)
- ☁️ Deployment (Vercel / Netlify)

---

## ✍️ Author

**Mukul**

---

## 🏁 Conclusion

This project demonstrates:
- Strong React fundamentals
- Clean UI/UX design
- Scalable frontend architecture
- Real-world CRUD application structure

It can be extended into a full-fledged recruitment management system with backend integration.

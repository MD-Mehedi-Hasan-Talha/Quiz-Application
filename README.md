# 🧠 Quiz Application (React + Vite)

A full-featured **Quiz Platform** where users can participate in quizzes and admins can create, manage, and publish quiz sets.
This project includes authentication, role-based access control, result analysis, and a dynamic leaderboard system.

---

## 🚀 Tech Stack

* **Frontend:** React
* **Build Tool:** Vite
* **Routing:** React Router
* **Authentication:** JWT (Access Token & Refresh Token)
* **State Management:** React State / Context API
* **UI Utilities:** NPM Libraries (Circular Progress Bar, Icons, etc.)
* **API Integration:** REST APIs (Provided)

---

## 📦 Installation & Setup

```bash
# Clone the repository
git clone https://github.com/MD-Mehedi-Hasan-Talha/Quiz-Application

# Navigate to the project directory
cd Quiz-Application

# Install dependencies
npm install

# Run the development server
npm run dev
```

👉 The application will run at:
`http://localhost:5173`

---

## 🔐 Authentication & Authorization

* Manual **Login & Registration** forms
* JWT-based authentication
* Access Token & Refresh Token handling
* Default avatar for users
* Role-based access:

  * `admin`
  * `user`

---

## 🧭 Routing Strategy

### Public Routes

* Login
* Registration
* Home (partial access)

### Private Routes

* Quiz Page
* Result Page
* Leaderboard Page
* Dashboard
* Admin Pages

> ⚠️ Private routes are determined logically and protected accordingly.

---

## 🏠 Home Page Features

* Displays quiz cards using the **Quiz List API**
* If the user is logged in:

  * A Welcome Section is visible
* If the user is not logged in:

  * Welcome Section is hidden
* Clicking a quiz card:

  * Logged-in user → Quiz Page
  * Not logged-in user → Login Page

---

## 🧩 Quiz Participation Rules

* A user can attempt a quiz **only once**
* Admins cannot participate in their own quizzes
* Users cannot move to the next question without selecting an answer
* A quiz cannot be submitted without at least one question

---

## 📝 Quiz Page (`quiz_page.html`)

* Questions are shown **one at a time**
* All questions are fetched at once using the **Get Quiz API**
* Navigation is handled sequentially using a **Next** button
* Answer options are **randomly shuffled** for each user
* Sidebar displays:

  * Total number of questions
  * Number of answered questions
  * Number of remaining questions

---

## 📤 Quiz Submission

* After answering all questions:

  * **Submit Quiz Attempt API** is called
* API response provides:

  * Submitted Answers array
  * Correct Answers array
* Score calculation is handled **on the client side**
* User is redirected to the **Result Page** after submission

---

## 📊 Result Page (`result.html`)

### Result Summary

* Total score
* Number of correct answers
* Number of wrong answers

### Circular Progress Bar

* Built using an NPM library
* Displays the percentage of correct answers

### Answer Breakdown

* User-selected answers
* Correct answers
* Wrong answers
* Visual indicators (colors/icons) for clarity

📌 Data source:

* **Get Quiz Attempts API**

---

## 🏆 Leaderboard (`leaderboard_page.html`)

* Quiz set–specific leaderboard
* Displays:

  * Participant ranking
  * Correct answer count
  * Wrong answer count
* Top 5 participants shown in a separate list
* User’s name is highlighted if present in the Top 5

### Leaderboard Logic

* API returns unsorted quiz attempt data
* Client-side logic:

  * Evaluate correct vs wrong answers
  * Calculate scores
  * Sort and rank participants

---

## 🛠 Admin Panel (Admin Only)

### Dashboard (`dashboard.html`)

* Displays quizzes created by the admin
* Uses **Quiz Set List API**
* Includes a **Create a New Quiz** card

---

## 🧪 Quiz Creation Workflow

### Step 1: Create Quiz Set

**Page:** `quiz_set_page.html`

* Set quiz title
* Set quiz description
* Initial state: `draft`
* API used:

  * **Create Quiz Set**

---

### Step 2: Add Quiz Questions

**Page:** `quiz_set_entry_page.html`

* Add question title
* Add multiple options
* Only **one correct answer** is allowed
* API used:

  * **Add Question**

---

## ✏️ Question Management

* Update a question:

  * **Update Question API**
* Delete a question:

  * **Delete Question API**

---

## 📢 Publish / Unpublish Quiz

* Quiz sets are created in `draft` state by default
* Admin can publish or unpublish a quiz set
* API used:

  * **Update Quiz API**

---

## 🔒 Admin Access Control

* Pages inside the `/dist/admin` directory:

  * Accessible only by admins
* User role is determined from the API response (`role` property)

---

## ✅ Additional Business Rules

* Admin cannot attempt their own quiz
* User must select an answer before proceeding
* Quiz cannot be submitted or published without questions
* Each quiz attempt is allowed only once per user

---

## 📌 Notes

* Result calculation and leaderboard generation are typically handled server-side
* For this assignment, all calculations are implemented **on the client side**

---

## 📄 License

This project is developed for educational and assignment purposes.

# ReactJS Client-Side Form Validation System

> **Assignment 6:** Design, develop and deploy a web application to demonstrate client-side validation using **ReactJS**.

---

## 🚀 Quick Start: How to Run

You have two convenient ways to run this application:

### Method 1: Run with Vite Dev Server (Recommended)

1. Open your terminal in this directory (`c:\Users\vedku\assignment_6`).
2. Run the development server:
   ```bash
   npm run dev
   ```
3. Open your browser and navigate to:
   ```text
   http://localhost:3000
   ```
   *(or the local port displayed in your terminal)*

---

### Method 2: Instant No-Install Browser Demo (Zero Setup)

If you need to quickly preview the project without running commands:
1. Simply double-click the file [standalone-demo.html](file:///c:/Users/vedku/assignment_6/standalone-demo.html) in Windows File Explorer.
2. It will open directly in Google Chrome, Microsoft Edge, or any modern web browser with the full interactive React application loaded via CDN.

---

## 🛠️ Build & Deployment Commands

- **Build for Production:**
  ```bash
  npm run build
  ```
  *(Generates the optimized production bundle inside the `dist/` directory)*

- **Preview the Production Build Locally:**
  ```bash
  npm run preview
  ```

---

## 🌟 Key Features & Validation Rules Demonstrated

| Field | Validation Type | Rule & Behavior |
| :--- | :--- | :--- |
| **Full Name** | Regex & Length | Required, minimum 3 chars, letters and spaces only (`^[a-zA-Z\s]+$`). |
| **Email Address** | Standard RFC Regex | RFC compliant format (`student@domain.com`). Prevents malformed addresses. |
| **Mobile Number** | Numeric & Pattern | 10 numeric digits, must begin with digits 6–9. |
| **Date of Birth** | Dynamic Age Calculation | Client-side age calculation (`calculateAge()`). Requires age &ge; 18 years. |
| **Gender** | Group Selection | Interactive radio button validation. |
| **Department / Course** | Dropdown Selector | Required dropdown selection. |
| **Password** | Strength & Criteria | Min 8 chars, 1 uppercase, 1 lowercase, 1 digit, 1 special character. Real-time visual progress bar & criteria checklist. |
| **Confirm Password** | Cross-field Matching | Dynamically verifies that password and confirmation match in real time. |
| **Avatar Upload** | File Validation | Validates MIME type (JPG, PNG, WEBP) and byte size (&le; 2MB) with live image thumbnail preview. |
| **Bio / SOP** | Live Counter | Live character countdown with a 200-character ceiling. |
| **Terms & Conditions** | Boolean Checkbox | Required checkbox declaration before submission. |
| **Interactive Feedback & Captcha** | Tab 2 | 5-star interactive rating, character limit counter, and dynamic random math security challenge. |
| **Dark / Light Mode** | UI Persistence | Toggle switch with full theme customization. |
| **One-Click Sample Data** | Demo Convenience | "Auto-fill Sample Data" button to instantly test a valid submission during evaluation. |

---

## 📁 Project Structure

```text
assignment_6/
├── index.html                   # HTML entry point
├── package.json                 # Project dependencies & scripts
├── vite.config.js               # Vite build configuration
├── standalone-demo.html         # Standalone zero-install runnable demo
├── README.md                    # Project documentation & run guide
└── src/
    ├── main.jsx                 # React root renderer
    ├── App.jsx                  # Main application & tab navigator
    ├── index.css                # CSS styling, glassmorphism, responsive grid & themes
    ├── components/
    │   ├── Navbar.jsx           # Top navigation bar with theme toggle
    │   ├── FormField.jsx        # Reusable controlled input with validation status
    │   ├── RegistrationForm.jsx # Core registration form with 10 validation rules
    │   ├── PasswordStrengthMeter.jsx # Visual password strength scoring bar
    │   ├── FeedbackForm.jsx     # Interactive rating & math captcha
    │   ├── ValidationGuide.jsx  # Academic viva reference & documentation
    │   └── SuccessModal.jsx     # Submission summary popup & JSON export
    └── utils/
        └── validationRules.js   # Centralized regex patterns & validation logic
```

---

## 🌐 Free 1-Click Deployment (Vercel / Netlify / GitHub Pages)

### Deploying to Vercel:
1. Push this folder to a GitHub repository.
2. Visit [vercel.com](https://vercel.com) and click **"Add New Project"**.
3. Import your repository; Vercel automatically detects Vite and deploys in seconds.

### Deploying to Netlify:
1. Run `npm run build` to generate the `dist` folder.
2. Drag and drop the `dist` folder onto [app.netlify.com/drop](https://app.netlify.com/drop).

# Academic Assignment Report

**Course / Subject:** Full Stack Web Development / Front-End Web Engineering  
**Assignment Title:** Design, Develop, and Deploy a Web Application to Demonstrate Client-Side Validation using REACTJS  
**Assignment Number:** Assignment 6  
**Technology Stack:** React 18, JavaScript (ES6+), HTML5, CSS3, Vite  

---

## 1. Problem Statement & Objective

### 1.1 Problem Statement
> *"Design, develop and deploy a web application to demonstrate the client-side validation using REACTJS. Students have to do Client-side validation / Interactive type applications."*

### 1.2 Objectives
1. **Design a user-centric, responsive UI** that captures diverse user inputs (Text, Email, Phone, Dates, Radio buttons, Dropdowns, Passwords, File uploads, Checkboxes).
2. **Implement robust client-side validation rules** using React's *Controlled Components* architecture and state hooks (`useState`, `useEffect`).
3. **Provide immediate interactive feedback** through real-time regex pattern testing, password strength scoring, dynamic age evaluation, and visual indicators (error alerts, checkmarks, dynamic colors).
4. **Deploy the web application** to a live public hosting platform (GitHub Pages / Vercel / Netlify).

---

## 2. Architecture & Design

### 2.1 Component Hierarchy Diagram

```
App.jsx (Root State, Theme Management, Tab Navigation)
│
├── Navbar.jsx (Branding, Academic Metadata, Light/Dark Theme Switcher)
│
├── Tabs Navigation (Switch between Forms & Guide)
│   ├── Tab 1: RegistrationForm.jsx (10 Input Constraints & Image Upload)
│   │   ├── FormField.jsx (Reusable Controlled Input + Visual Indicators)
│   │   └── PasswordStrengthMeter.jsx (Real-time scoring & checklist)
│   │
│   ├── Tab 2: FeedbackForm.jsx (Interactive 5-star rating + Dynamic Math Captcha)
│   │   └── FormField.jsx
│   │
│   └── Tab 3: ValidationGuide.jsx (Technical Reference & Viva Notes)
│
├── SuccessModal.jsx (Summary Table of Validated Fields & JSON Export)
└── Footer.jsx
```

### 2.2 Controlled Component Workflow

In this application, all input elements are **Controlled Components**. The form state is maintained inside the component's state using `useState`.

```
User Types/Interacts 
       │
       ▼
`onChange` / `onBlur` Event Fired
       │
       ▼
`validationRules.js` processes input against Regex & Business Rules
       │
       ▼
React State updated: `formData`, `errors`, `touched`
       │
       ▼
Component Re-renders with dynamic CSS classes:
  - `.is-valid` (Green border + Checkmark)
  - `.is-invalid` (Red border + Error Message)
```

---

## 3. Comprehensive Validation Rules & Specifications

| Field | Input Type | Validation Rules & Constraints | Regex / Logic |
| :--- | :--- | :--- | :--- |
| **Full Name** | `text` | Required; min 3 chars, max 50 chars; letters and spaces only. | `/^[a-zA-Z\s]{3,50}$/` |
| **Email Address** | `email` | Required; RFC 5322 compliant format. | `/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/` |
| **Mobile Number** | `tel` | Required; exactly 10 digits; must start with 6, 7, 8, or 9. | `/^[6-9]\d{9}$/` |
| **Date of Birth** | `date` | Required; past date only; computed age must be &ge; 18 years. | `calculateAge(dob) >= 18` |
| **Gender** | `radio` | Required; must choose Male, Female, or Other. | Non-empty selection |
| **Department** | `select` | Required; must select valid academic program. | Non-empty string |
| **Password** | `password`| Min 8 chars; &ge;1 Uppercase, &ge;1 Lowercase, &ge;1 Number, &ge;1 Special Symbol. | Evaluated via 5 criteria + Strength score (0–4) |
| **Confirm Password** | `password`| Required; must strictly match the password field in real-time. | `value === allValues.password` |
| **Avatar Upload** | `file` | Optional; must be PNG, JPG, or WEBP; file size &le; 2MB. | `file.size <= 2 * 1024 * 1024` + MIME check |
| **Bio / SOP** | `textarea`| Max 200 characters with live character counter. | `value.length <= 200` |
| **Terms Checkbox** | `checkbox`| Required boolean flag; must be checked. | `value === true` |
| **Math Captcha** | `number` | Required; dynamic challenge `num1 + num2 = ?` generated on mount. | `parseInt(input) === expectedAnswer` |

---

## 4. Test Cases & Verification Table

| Test Case ID | Field Tested | Input Given | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-01** | Full Name | `"A123"` | Error: *"Alphabets and spaces only."* | Error displayed | **PASS** |
| **TC-02** | Full Name | `"Al"` | Error: *"Full name must be at least 3 characters."* | Error displayed | **PASS** |
| **TC-03** | Full Name | `"Aarav Sharma"` | Marked valid (green border + checkmark) | Marked valid | **PASS** |
| **TC-04** | Email | `"invalid-email@"` | Error: *"Please enter a valid email address."* | Error displayed | **PASS** |
| **TC-05** | Email | `"test@college.edu"` | Marked valid | Marked valid | **PASS** |
| **TC-06** | Mobile | `"1234567890"` | Error: *"Please enter a valid 10-digit number starting with 6-9."* | Error displayed | **PASS** |
| **TC-07** | Mobile | `"9876543210"` | Marked valid | Marked valid | **PASS** |
| **TC-08** | Date of Birth | Date giving age = 15 | Error: *"You must be at least 18 years old."* | Error displayed | **PASS** |
| **TC-09** | Date of Birth | Date giving age = 22 | Displays `"Age: 22 yrs (Eligible)"` | Valid & Eligible | **PASS** |
| **TC-10** | Password | `"pass"` | Strength: *"Very Weak"*; criteria checklist highlights unfulfilled items | Meter updates | **PASS** |
| **TC-11** | Password | `"StrongPass123!"` | Strength: *"Strong"* (100% green bar); all 5 checkmarks satisfied | Meter 100% | **PASS** |
| **TC-12** | Confirm Pass | `"DifferentPass!"` | Error: *"Passwords do not match."* | Error displayed | **PASS** |
| **TC-13** | File Upload | 5MB PDF file | Error: *"Invalid file format. Please upload JPG, PNG, or WEBP."* | Error displayed | **PASS** |
| **TC-14** | Submit Button | Form with missing fields | Auto-scrolls to first invalid field and highlights all missing inputs | Form highlighted | **PASS** |
| **TC-15** | Submit Button | Completely valid form | Opens Success Modal with summary table & Export JSON button | Modal displayed | **PASS** |

---

## 5. Deployment Guide

### Option A: Free Deployment via GitHub Pages
1. Push this project folder to a GitHub repository:
   ```bash
   git init
   git add .
   git commit -m "Assignment 6: React Client-Side Validation"
   git remote add origin https://github.com/<your-username>/assignment_6.git
   git push -u origin main
   ```
2. The included GitHub Actions workflow (`.github/workflows/deploy.yml`) will automatically build and publish the site to:
   ```
   https://<your-username>.github.io/assignment_6/
   ```

### Option B: Free Deployment via Vercel / Netlify
- **Vercel:** Run `npx vercel` in this folder or link your GitHub repo.
- **Netlify:** Drag and drop the `dist/` directory onto [app.netlify.com/drop](https://app.netlify.com/drop).

---

## 6. Viva Voce Questions & Answers

**Q1: What is the primary difference between Client-Side and Server-Side Validation?**  
*Answer:* Client-side validation occurs inside the user's browser before data is submitted over the network. It provides instant user feedback, improves responsiveness, and reduces load on the server. Server-side validation occurs on the backend server and is mandatory for security, as client-side checks can be bypassed using developer tools or direct HTTP requests (e.g., Postman/cURL).

**Q2: What are Controlled Components in React?**  
*Answer:* Controlled components are React form elements whose state is controlled directly by React rather than the DOM. The input value is bound to a state variable (`value={formData.field}`), and changes are handled by event callbacks (`onChange={handleChange}`).

**Q3: Why validate on both `onBlur` and `onChange`?**  
*Answer:* Validating immediately on the first keystroke (`onChange`) creates a poor user experience by showing errors before the user has finished typing. By combining `onBlur` (which flags a field as "touched" when the user clicks away) with `onChange` (which provides live re-validation only after a field has been touched), users get non-intrusive, helpful feedback.

**Q4: How does the Password Strength Meter compute score?**  
*Answer:* It tests the input string against 5 independent regular expression criteria: minimum 8 characters, presence of uppercase letters, lowercase letters, numbers, and special symbols. The score (0 to 4) determines the progress bar width and color (Red &rarr; Orange &rarr; Yellow &rarr; Blue &rarr; Green).

---

## 7. Conclusion

The developed ReactJS web application successfully satisfies all requirements of Assignment 6 by demonstrating diverse, robust, and interactive client-side validations. The application includes controlled components, real-time regex matching, password strength indicators, age verification, file upload constraints, dark/light themes, and automated deployment pipelines.

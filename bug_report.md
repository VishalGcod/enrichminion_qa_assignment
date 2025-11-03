# 🐞 Bug Report – EnrichMinion QA Assignment

This document contains key bugs found during manual testing.  
All bugs are validated through UI behavior and Network tab logs.

---

## 📋 Summary

| Category | Count |
|---|---|
Total Bugs Found | 18
Included Major Bugs | 7
UI Bugs | 14
API/Backend Bugs | 3
Auth/Session Bugs | 1

---

## 🧠 Legend

- **Severity:** Critical / High / Medium / Low  
- **Priority:** P1 / P2 / P3  
- **RCA:** Frontend / Backend / Both  

---

## ✅ Bugs

### **BUG-001 – Duplicate Email Allows Registration**
**Severity:** High  
**Priority:** P1  
**Steps to Reproduce:**
1. Register with a valid email
2. Verify email and login
3. Try registering again with same email  

**Expected Result:**  
System should show error: *"Email already registered"* and block registration.

**Actual Result:**  
Registration accepted / no proper error displayed.

**RCA:** Backend should block duplicate user creation + Frontend must validate
**Evidence:** (https://drive.google.com/file/d/1hCVzzX-CZ5lnPaXWFU7r5nRut7OH_BeS/view?usp=sharing)

---

### **BUG-002 – Logout Not Clearing Session Completely**
**Severity:** High  
**Priority:** P1  
**Steps:** login in two tabs → Sign out → open other loggedin URL → still logged in  
**Expected:** User signed out must sign out everywhere 
**Actual:** One tab still authenticated / session persists  
**RCA:** Backend token/session not invalidated 
**Evidence:** (https://drive.google.com/file/d/1OqlSaJ8bmTse0lDJV1rhBX15_Djk_I1B/view?usp=sharing)

---

### **BUG-003 – Password Reset Link Redirects to Login Page**
**Severity:** High  
**Priority:** P1  
**Steps:** Login page → Request reset password → click email link  
**Expected:** Navigate to reset password page  
**Actual:** Redirects to login screen
**RCA:** Frontend routing issue
**Evidence:** (https://drive.google.com/file/d/1cy97txeAr8oFcX9T2weVqRoF65BeLxZZ/view?usp=sharing)

---

### **BUG-004 – Wrong Email Error Retained On Navigation**
**Severity:** Medium  
**Priority:** P2  
**Steps:** Reset password → Enter wrong/invalid email → navigate back to login/signup  
**Expected:** Error message should reset  
**Actual:** Error message persists  
**RCA:** State not cleared on navigation  
**Evidence:**  (https://drive.google.com/file/d/1zkSY8QZmWJ9aEUR19l6WbfFJTcRwsEiI/view?usp=sharing)
---

### **BUG-005 – Multiple Error Messages on Invalid Signup Data**
**Severity:** Medium  
**Priority:** P2  
**Steps:** Enter valid data → Click confirmation link → enter invalid info → Click confirmation link
**Expected:** Show single clear error  
**Actual:** Shows **two** error messages  
**RCA:** Validation triggered multiple times no state cleared 
**Evidence:** (https://drive.google.com/file/d/1VmqrqpTiX8TNAptT3BcQxwqXkZ4qlnqc/view?usp=sharing)

---

### **BUG-006 – Wrong Color for Error Messages**
**Severity:** Low  
**Priority:** P3  
**Expected:** Standard red error color for consistency  
**Actual:** Incorrect color used  
**RCA:** UI theme inconsistency  
**Evidence:** (https://drive.google.com/file/d/1ykaDVS7vhM8olJlOW15X80ItwFnYywlv/view?usp=sharing)

---

### **BUG-007 – Google Login Doesn’t Trigger OAuth Flow**
**Severity:** Critical  
**Priority:** P1  
**Steps:** login/registration page → Click "Login with Google"  
**Expected:** Google account chooser & login  
**Actual:** No auth popup / no flow  
**RCA:** OAuth config missing or frontend error
**Evidence:** (https://drive.google.com/file/d/1Bn2OhxtZFyFJKf4rX-8IiJQcrMAe_lY0/view?usp=sharing)

---

### **BUG-008 – Invalid Email Accepted in Reset Password**
**Severity:** Medium  
**Priority:** P2  
**Steps:** login page → Click Forgot Password → Enter `123@co` → submit  
**Expected:** Email validation error  
**Actual:** System accepts it  
**RCA:** UI Input validation failure  
**Evidence:** (https://drive.google.com/file/d/1fvwd4P4iuuSHhTFZZ5PT8f4zywZBX_0s/view?usp=sharing)

---

### **BUG-009 – Flicker Incorrect Name After Login**
**Severity:** Low  
**Priority:** P3  
**Steps:** Login → click logo  
**Expected:** Stable correct name  
**Actual:** Shows invalid name for a moment  
**RCA:** UI state issue
**Evidence:** (https://drive.google.com/file/d/1z-1ZbMG4-pamKag-QpSavLCX0r-ospGp/view?usp=sharing)

---

### **BUG-010 – Enrichment Pull Data Hover Action Does Nothing**
**Severity:** Medium  
**Priority:** P2  
**Steps:** Hover "Pull Data" → select HubSpot  
**Expected:** API call or tooltip or menu  
**Actual:** No action, no API call  
**RCA:** UI Menu not implemented or broken
**Evidence:** (https://drive.google.com/file/d/1PL20dS9mIwyF1px5fINvFdC0wyych_5r/view?usp=sharing)

---

### **BUG-011 – CSV Delete + Reupload Fails**
**Severity:** High  
**Priority:** P1  
**Steps:** Upload file → delete → re-upload  
**Expected:** Should allow re-upload  
**Actual:** File does not upload again  
**RCA:** UI File state not reset  
**Evidence:** (https://drive.google.com/file/d/1kXxRWCGvFQUHDfZjI5qFa50DQEr7AKY_/view?usp=sharing)

---

### **BUG-012 – CSV Upload Message Shows “undefined”**
**Severity:** Medium  
**Priority:** P2  
**Steps:** Upload CSV  
**Expected:** Show upload time  
**Actual:** Shows “undefined”  
**RCA:** API response not parsed / undefined variable  
**Evidence:** (https://drive.google.com/file/d/1Oz2haOQtRWLVp7sAiMmXFQ5DptF6yHrz/view?usp=sharing)

---

### **BUG-013 – Points Not Deducted correctly Enrichment**
**Severity:** Critical  
**Priority:** P1  
**Steps:** Upload CSV  
**Expected:** Credits must decrease  
**Actual:** No deduction  
**RCA:** Backend logic failure  
**Evidence:** (https://drive.google.com/file/d/1PL20dS9mIwyF1px5fINvFdC0wyych_5r/view?usp=sharing)


### BUG-014 – Clay Webhook URL Validation Missing
**Severity:** Medium
**Priority:** P2
**Steps:** Check upload history → Click Clay Webhook → add url → Submit
**Expected:** Proper url validation
**Actual:** Accepts anything
**RCA:** UI Issue
**Evidence:** (https://drive.google.com/file/d/1WWYRcSVXkGZ7gn3peYeM9IClu73Wnujn/view?usp=sharing)

---

### BUG-015 – Catch-All Email Verify Fails with 400
**Severity:** High
**Priority:** P1
**Steps:** Check upload history → Click and verify using Catchall Verification or enrichment → add data → Next → Upload
**Expected:** verification must be successfull
**Actual:** API returns error(400)
**RCA:** UI not handling properly
**Evidence:** (https://drive.google.com/file/d/1P3UPO_xMJkWP_o33KcYtHfby0Q1q4npr/view?usp=sharing)

---

### BUG-016 – Logo Redirects to Wrong Page
**Severity:** Medium
**Priority:** P2
**Steps:** land on default page after login → Click on logo
**Expected:** Redirects to email finder
**Actual:** Redirects to phone finder
**RCA:** UI routing was not handled properly
**Evidence:** (https://drive.google.com/file/d/1-4Y3FuLnWnWOOZi-x-Sz9X9FHrOtaLzc/view?usp=sharing)

---

### BUG-017 – Salesforce Option in Upload History Non-Functional
**Severity:** Medium
**Priority:** P2
**Steps:** Check upload history → In actions click salesforce
**Expected:** Redirects to salesforce or related tab
**Actual:** Button exists but no action triggered 
**RCA:** UI Menu not implemented or broken
**Evidence:** (https://drive.google.com/file/d/1ghbj-nJlFBhpSwbAv23sb4BlTdwezmyj/view?usp=sharing)

---

### BUG-018 – Table Sorting Shows Random “Unsort”
**Severity:** Low
**Priority:** P3
**Steps:** Check upload history → Search valid data
**Expected:** Proper results to be displayed in table
**Actual:** Sorting state behavior inconsistent 
**RCA:** UI sorting/Search is not consistent
**Evidence:** (https://drive.google.com/file/d/12mWXRngeRBgNEQp2Ytp_YwWZOoqKbCTa/view?usp=sharing)
---

## ✅ Conclusion
Total defects show issues across:

- Authentication/session handling  
- Input validation  
- Billing/credit logic  
- UI consistency  
- File handling  

Further testing recommended for:
- API validation and permissions  
- Billing logic  
- OAuth configuration


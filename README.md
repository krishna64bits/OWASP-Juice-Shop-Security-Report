# Web Application Security Testing Report
## OWASP Juice Shop

### 📌 Project Overview

This document outlines the findings from a hands-on security assessment conducted on the OWASP Juice Shop web application. The primary goal was to identify real-world vulnerabilities, understand exploitation techniques, and learn effective mitigation strategies commonly used in secure system engineering.

---

### 🧪 Security Weaknesses Evaluated

| **Attack Type** | **What Was Demonstrated** |
|----------------|---------------------------|
| **Session Hijacking** | Reusing stolen browser tokens to impersonate an authenticated user |
| **IDOR** | Accessing unauthorized data by manipulating numeric object references in API calls |
| **Access Control Testing** | Attempting to visit admin pages without login – access was correctly denied |
| **2FA Bypass Attempt** | Trying random OTP codes – server rejected them all, showing strong validation |
| **CSRF** | Submitting a forged form – failed because JWT tokens are not auto-sent |
| **XSS** | Injecting JavaScript via search bar – popup confirmed successful execution |
| **SQL Injection** | Bypassing login page using specially crafted email input |
| **JWT Manipulation** | Decoding and analyzing the JSON web token for privilege escalation attempts |
| **Password Reset Weakness** | Exploiting simple security questions and lack of email confirmation |

---

### 🛠️ Environment & Tools Used

| **Component** | **Details** |
|---------------|-------------|
| Target App | OWASP Juice Shop (running via Docker) |
| OS | Kali Linux |
| Browser | Firefox with Developer Tools |
| Token Decoder | jwt.io |

---

### 🔐 Recommended Security Controls

Based on the test results, the following practices should be adopted:

- **Enforce password complexity** – Minimum 12 characters with mixed character types
- **Use adaptive hashing** – Algorithms like bcrypt for password storage
- **Deploy multi-factor authentication** – Adds an extra verification layer
- **Apply rate limiting** – Prevents automated brute force attacks
- **Eliminate plaintext secrets** – Never store or transmit credentials unencrypted

---

### 📊 Final Takeaways

This security assessment revealed both strengths and weaknesses in the Juice Shop application:

✅ **What Worked Well:**
- Admin panel access was properly restricted
- OTP validation effectively blocked 2FA bypass attempts
- JWT signature verification prevented token tampering

⚠️ **What Was Exploitable:**
- Session tokens could be reused (session hijacking)
- API endpoints leaked other users' data (IDOR)
- Search functionality allowed script injection (XSS)
- Login page was vulnerable to SQL injection
- Password reset relied on guessable security questions

---

### 📝 Closing Statement

Testing the OWASP Juice Shop provided valuable hands-on experience with common web application flaws. The lab clearly shows that while some security mechanisms work as intended, others leave the application exposed to serious risks. Adopting secure coding practices, validating all inputs, and implementing proper authentication flows are essential steps toward building resilient web applications.

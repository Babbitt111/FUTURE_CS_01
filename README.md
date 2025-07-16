# FUTURE_CS_01 – Task 1: Web Application Security Testing

This repository documents my work on Task 1 of my cybersecurity internship, where I performed vulnerability testing on DVWA (Damn Vulnerable Web App). I used manual techniques and scanning tools to identify and exploit common web application vulnerabilities, mapped them to the OWASP Top 10, and compiled a full security assessment report.

---

## Objective

To explore and exploit common web application vulnerabilities in a controlled environment using industry-standard tools, and to document findings with screenshots, impact analysis, and remediation strategies.

---

## Tools Used

- DVWA – Damn Vulnerable Web Application
- OWASP ZAP – Vulnerability scanner and request editor
- Firefox Developer Tools – Manual inspection and request capture
- Python HTTP Server – Used to host CSRF attack page
- Kali Linux – Security testing operating system
- Google Docs / Word – Report compilation

---

## Vulnerabilities Tested

### 1. SQL Injection
- **Payload**: `' OR '1'='1 --`
- **Impact**: Authentication bypass
- **OWASP Mapping**: A1 – Injection
- **Remediation**: Use parameterized queries and validate input
- **Screenshot**:  
  ![SQL Injection Exploit](screenshots/sql_injection.png)

### 2. Reflected XSS
- **Payload**: `<script>alert('XSS')</script>`
- **Impact**: JavaScript execution via URL
- **OWASP Mapping**: A3 – Cross-Site Scripting
- **Remediation**: Encode output and apply CSP
- **Screenshot**:  
  ![Reflected XSS](screenshots/reflected_xss.png)

### 3. Stored XSS
- **Payload**: `<img src=x onerror=alert('XSS')>`
- **Impact**: Persistent script execution
- **OWASP Mapping**: A3 – Cross-Site Scripting
- **Remediation**: Sanitize input and encode output
- **Screenshot**:  
  ![Stored XSS](screenshots/stored_xss.png)

### 4. CSRF (Successful Exploit)
- **Method**: Request replay using captured token
- **Payload**:
    password_current=password password_new=Test1234 password_conf=Test1234 Change=Change user_token=1c25f1684d9f5e0c3e6b0a5b0e3d0c8b

- **Impact**: Admin password changed silently
- **OWASP Mapping**: A5 – Broken Access Control
- **Remediation**: Use unpredictable CSRF tokens, validate origin headers, and apply SameSite cookies
- **Screenshot**:  
![CSRF Exploit](screenshots/csrf_attack.png)

---

## OWASP Top 10 Coverage

- A1 – Injection: Confirmed via SQLi
- A2 – Broken Authentication: Confirmed through login bypass
- A3 – Cross-Site Scripting: Confirmed via reflected and stored XSS
- A5 – Broken Access Control: Confirmed via CSRF exploit
- A6 – Security Misconfiguration: Observed default DVWA settings

---

## Risk Ratings

- SQL Injection: Critical
- Stored XSS: High
- Reflected XSS: Medium
- CSRF Replay: High

---

## Deliverables

- Security Assessment Report (PDF)
- Screenshots of each exploit
- Source code of CSRF attack page
- OWASP Top 10 checklist
- GitHub documentation

---

## Skills Gained

- Web application vulnerability scanning
- Security documentation and reporting
- Ethical hacking and penetration testing
- Threat modeling and risk analysis

---

## Author

Ridwan Seun Ahmed  
Cybersecurity Intern  
Location: Remote
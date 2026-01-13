# Web Application Firewall (WAF) Implementation using ModSecurity on Apache

## Overview

This repository documents a **hands-on laboratory practice** focused on implementing a **Web Application Firewall (WAF)** using **ModSecurity** on an **Apache Web Server**.

The lab demonstrates how security controls can be enforced at the web server layer to **detect and block malicious requests**, such as SQL Injection attempts and unauthorized access based on IP address.

All configurations and tests were performed in a controlled environment and validated through direct request testing and server responses.

---

## Environment

- Operating System: Ubuntu (Virtual Machine)
- Web Server: Apache 2
- WAF Module: ModSecurity (Apache module)


---

## Practiced Scenarios

### 1. Apache Status Verification

Before deploying security controls, the Apache service status was verified to ensure the web server was running correctly.

**Purpose:**
- Confirm service readiness
- Avoid misconfiguration during WAF deployment

---

### 2. ModSecurity Installation and Activation

ModSecurity was installed and enabled as an Apache module to act as a Web Application Firewall.

**Outcome:**
- ModSecurity successfully loaded
- Apache restarted without errors

---

### 3. SQL Injection Protection Rule

A custom rule was configured to **detect SQL Injection attempts** on the `id` parameter.

When a user attempted to manipulate the parameter using suspicious characters, the WAF responded with:

- HTTP Status Code: **403 Forbidden**
- Custom message: **"Terdeteksi Serangan SQL Injection"**

**Security Impact:**
- Prevents unauthorized database manipulation
- Demonstrates input validation at the WAF layer

**Evidence:**

![SQL Injection Blocked](Screenshots/sql-injection-blocked.png)

---

### 4. IP-Based Access Restriction

Another rule was implemented to **restrict access based on client IP address**.

When a request originated from a blocked IP, the server returned:

- HTTP Status Code: **403 Forbidden**
- Custom message: **"Akses Ditolak"**

**Security Impact:**
- Enforces network-level access control
- Useful for blocking malicious or untrusted sources

**Evidence:**

![IP Restriction](Screenshots/ip-restriction.png)

---

## Key Learnings

- Web Application Firewalls operate before application logic is executed
- ModSecurity rules can be customized to match specific attack patterns
- Proper WAF configuration significantly reduces attack surface
- Security testing should always be validated with real request attempts

---

## Conclusion

This lab demonstrates practical experience in:

- Deploying a Web Application Firewall
- Writing and applying ModSecurity rules
- Blocking SQL Injection attempts
- Restricting access based on IP address

The implementation reflects real-world defensive techniques commonly used in **Blue Team and SOC environments**.



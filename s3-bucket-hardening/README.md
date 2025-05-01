# 🛡️ Secure S3 Bucket Hardening Project

## 📌 Project Overview
This project demonstrates how to properly configure and secure an AWS S3 bucket.  
It highlights common **misconfigurations** (like public access) that can lead to data breaches, and provides step-by-step **remediation actions** following AWS security best practices.

**Key Skills Demonstrated:**  
- S3 bucket creation and configuration  
- Public vs private access control  
- Misconfiguration detection using AWS Trusted Advisor  
- Policy updates for secure bucket settings  
- Enabling server-side encryption (SSE-S3)

---

## ⚙️ Environment Setup
- AWS Free Tier account
- AWS Console access
- AWS CLI (optional for additional verification)

## 🧪 Steps and Documentation

### 🔹 1. S3 Bucket Creation
- Created a bucket named `jiaming-sec-demo-bucket`.
- Intentionally **unchecked** "Block all public access" to simulate a real-world misconfiguration.
- Uploaded a test file (`hello.txt`) to the bucket.

**Screenshot:**  
![bucket-created](./screenshots/bucket-created.png)

---

### 🔹 2. Misconfiguration Verification
- Made the uploaded file **public**.
- - Accessed the file publicly via direct URL:
  ```plaintext
  http://[bucket-name].s3.amazonaws.com/hello.txt
  ```
- Confirmed that the object was accessible **without authentication** (security risk).

**Screenshot:**  
![public-access-warning](./screenshots/public-access-warning.png)

---

### 🔹 3. Misconfiguration Detection
- Used **AWS Trusted Advisor** to scan the environment.
- Trusted Advisor flagged the public S3 bucket as a **security risk**.
  
**Screenshot:**  

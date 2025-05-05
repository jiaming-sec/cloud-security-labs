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
![trusted-advisor-warning](./screenshots/trusted-advisor-warning.png)

- **Alternative:**  
  Verified the bucket ACL using AWS CLI:
  ```bash
  aws s3api get-bucket-acl --bucket jiaming-sec-demo-bucket
  ```

### 🔹 4. Remediation: Restrict Public Access
- Enabled **Block all public access** settings on the S3 bucket.
- Updated bucket policies to remove any public permissions.

**Actions Taken:**
- Enabled all four options under "Block Public Access":
  - Block Public ACLs
  - Block Public Bucket Policies
  - Ignore Public ACLs
  - Restrict Public Bucket Policies

**Screenshot:**  
![block-public-access-settings](./screenshots/block-public-access-settings.png)

---

### 🔹 5. Remediation: Enable Server-Side Encryption (SSE-S3)
- Enabled **default encryption** for all new objects uploaded to the bucket.
- Chose **SSE-S3** (AWS-managed keys) for simplicity and compliance.

**Screenshot:**  
![encryption-settings](./screenshots/encryption-settings.png)

---

## 🧐 Lessons Learned
- **Public access control** must be explicitly managed — by default or through automated monitoring tools (Trusted Advisor, AWS Config).
- **Server-side encryption** should be enabled to protect data at rest.
- **IAM policies and bucket policies** should follow the **principle of least privilege**.
- **Regular audits** of S3 permissions can catch misconfigurations early.

---

## 🛡️ Best Practices Highlighted
- Always **block public access** unless absolutely required.
- Use **AWS Trusted Advisor** and **AWS Config** to continuously monitor S3 bucket permissions.
- Apply **server-side encryption** to protect sensitive data at rest.
- Follow **IAM least privilege** principle for user and service access to buckets.

---

## 📚 References
- [AWS S3 Security Best Practices](https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html)
- [AWS Trusted Advisor Documentation](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html)
- [AWS Server-Side Encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/serv-side-encryption.html)

---

# ✨ Project Status
✅ Completed S3 misconfiguration simulation  
✅ Detected with Trusted Advisor  

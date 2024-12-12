# 🌐 How I Tackled a Secure Network Design Assessment at WGU

In this post, I’ll share how I completed a **Secure Network Design performance assessment** for my WGU class. This project focused on merging two companies’ networks securely while meeting compliance requirements and staying within a tight budget. It was a fantastic challenge that required applying technical knowledge, strategic thinking, and compliance expertise.

---

## 🏢 The Scenario

For this assessment, I acted as the cybersecurity professional for **Company A**, a financial institution. The goal? Integrate its network with **Company B**, a smaller medical software provider. Here’s what I had to address:

- **Key Challenges**:
  - Fixing **network vulnerabilities** and outdated infrastructure.
  - Designing a **secure hybrid network** (on-premises + cloud).
  - Ensuring compliance with **PCI DSS** and **HIPAA**.
  - Staying within a **$50,000 budget**.

The final deliverable was a **network merger and implementation plan** with justifications and a network diagram.

---

## 🛠️ The Process

Here’s how I approached the project, step by step:

### 1️⃣ **Assessing Network Problems**
I started by analyzing the provided **network diagrams** and **vulnerability reports** to identify critical issues:

#### 🔍 **Company A’s Issues**:
- Open ports on critical systems, exposing them to exploitation.
- Weak password policies (e.g., 8-character passwords with no complexity).
- Limited remote access infrastructure and outdated software (Windows Server 2012).

#### 🔍 **Company B’s Issues**:
- Outdated operating systems (e.g., Windows XP) and poor patching practices.
- Lack of network segmentation, increasing the risk of lateral movement.
- Insecure Java RMI server configuration, vulnerable to remote code execution.

---

### 2️⃣ **Designing a Secure Network**
The next step was creating a **secure network topology diagram**. My design included:

- **Firewalls**:
  - Repurposed Company A’s Fortinet firewall and Company B’s Sophos XG firewalls for segmentation.
- **Routers**:
  - Upgraded to Cisco Catalyst 8200 routers for modern security and scalability.
- **Cloud-Based SIEM**:
  - Integrated Microsoft Sentinel for real-time threat detection and monitoring.
- **Wireless Access Points**:
  - Added Cisco Catalyst 9105AXI access points for secure, high-speed connectivity.
- **Infrastructure Upgrades**:
  - Installed Cat6a cables for higher bandwidth and replaced outdated systems.

---

### 3️⃣ **Applying Security Principles**
The design focused on two key principles:

#### 🔒 **Zero Trust Architecture (ZTA)**:
- Enforced strict **Multi-Factor Authentication (MFA)**.
- Implemented **network segmentation** to isolate critical systems and reduce lateral movement.

#### 🛡️ **Defense in Depth**:
- Layered multiple security controls, including firewalls, endpoint protection, and cloud-based SIEM.

---

### 4️⃣ **Ensuring Compliance**
To meet **PCI DSS** and **HIPAA** requirements, I incorporated:

- **PCI DSS**:
  - Segmented the Cardholder Data Environment (CDE).
  - Used encryption and MFA to secure access.

- **HIPAA**:
  - Applied encryption to protect medical data during storage and transmission.
  - Restricted access to medical systems using MFA and segmentation.

---

### 5️⃣ **Budget Management**
Balancing security needs with the $50,000 budget was critical. Here’s how I allocated resources:

- **$15,000** for VPN concentrators and MFA deployment.
- **$10,000** for cloud-based SIEM and backup services.
- **$15,000** for hardware upgrades (e.g., firewalls, routers).
- **$10,000** for employee training and incident response planning.

---

## 🎯 Final Thoughts

This project was an excellent exercise in **real-world cybersecurity problem-solving**. It emphasized the importance of balancing **security, compliance, and budget constraints** while designing a secure network architecture.

### 💡 **Key Takeaways**:
- **Break it down**: Tackling the assessment section by section made it more manageable.
- **Focus on compliance**: Aligning solutions with PCI DSS and HIPAA requirements is crucial in regulated industries.
- **Stay within budget**: Thoughtfully repurpose existing hardware to make the most of limited resources.

If you’re a WGU student working on this assessment, I hope this post helps you approach the project with confidence. Good luck!

---

💬 **Have thoughts or questions?** Drop a comment below, or reach out if you’d like to discuss cybersecurity design!

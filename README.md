# ☁️ CloudSystem – AWS-Based Personal Cloud Lab

CloudSystem is a real-world AWS infrastructure project designed to simulate a secure, modular cloud environment. It serves as my hands-on personal cloud lab and blueprint for production-level infrastructure — built manually from scratch without GUIs or CloudFormation.

> 🔧 Every subnet, route, rule, and policy is manually configured — no shortcuts, no templates. This is DevSecOps from the ground up.

---

## 🧠 Skills Demonstrated

- **AWS Networking:** VPC, Subnets, Route Tables, NAT, IGW
- **Security Engineering:** Bastion hosts, SSH jumpbox, SG chaining
- **DevSecOps Practices:** Flow logs, IAM hardening, CI/CD validation
- **Documentation Discipline:** GitHub-validated markdown notes
- **Modular Design:** Each cloud service is built as an isolated component (portfolio, AI, storage)

---

## ✅ Phase 1: Core Infrastructure (Complete)

| Component            | Description                                      |
|----------------------|--------------------------------------------------|
| `VPC`                | 10.0.0.0/16 custom network                       |
| Public & Private Subnets | Multi-AZ setup with separation of concerns   |
| Internet Gateway / NAT | Secure internet flow separation               |
| Bastion EC2 (Public) | SSH jump point — IP-restricted                  |
| Kali EC2 (Private)   | No public IP — SSH via Bastion only             |
| Security Groups      | Layered access control between zones            |
| Flow Logs            | VPC-level logging into CloudWatch               |
| CI/CD                | Markdown lint via GitHub Actions                |

📄 Full breakdown in [`notes/vpc-subnetting.md`](notes/vpc-subnetting.md)

---

## 🧩 Phase 2: Modular Services (In Progress)

| Module                | Description                                       |
|------------------------|---------------------------------------------------|
| 🔜 Portfolio Site       | S3-hosted static site with HTTPS via CloudFront   |
| 🔜 Private Storage      | IAM-controlled S3 bucket with file manager        |
| 🔜 Domain Email Hub     | SES setup with custom domain                      |
| 🔜 AI Dashboard         | EC2-hosted panel for internal tools (e.g., CloudNova) |
| 🔜 Internal VM Manager  | Web interface for managing private EC2 instances |

---

## 🛡️ Security Model

- 🔒 No public IPs on private instances  
- 🔐 Bastion SG locked to my IP only  
- 🪪 IAM roles scoped to least privilege  
- 📈 Flow Logs routed to CloudWatch  
- ⚔️ Zero Trust prep (SSM & GuardDuty in Phase 3)

---

## 📁 Repository Structure

```bash
/cloudsystem
├── notes/
│   └── vpc-subnetting.md
├── screenshots/
│   └── vpc-creation.png
├── .github/
│   └── workflows/
│       └── markdown-check.yml
└── README.md

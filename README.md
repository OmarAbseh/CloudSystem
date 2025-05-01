# CloudSystem ☁️ – Personal Cloud Infrastructure Lab

CloudSystem is a full AWS-based infrastructure project designed to simulate
and deploy a real-world, secure cloud environment. It serves as my personal
cloud lab and modular digital workspace, with components like private VMs,
storage, AI assistants, and email all isolated within a custom-built VPC.

> 🔐 Everything is built manually — no GUI templates, no CloudFormation.
> Every subnet, route, and permission is configured by hand for mastery.

---

## 🧠 Skills Demonstrated

- 🔹 AWS Networking: VPC, Subnets, IGW, NAT, Route Tables
- 🔹 Security Engineering: Bastion host, SSH jump, SG chaining
- 🔹 DevSecOps Practices: CI/CD (GitHub Actions), Flow Logs, isolation
- 🔹 Infrastructure Documentation: Clean, CI-validated markdown logs
- 🔹 Modular Design: Each service is containerized in purpose

---

## ✅ Phase 1: Infrastructure (Completed)

| Component               | Description                                  |
|-------------------------|----------------------------------------------|
| **VPC**                 | `10.0.0.0/16` with public/private subnets    |
| **Internet Gateway**    | Public subnet access                         |
| **NAT Gateway**         | Private subnet outbound access               |
| **Route Tables**        | Split traffic per subnet type                |
| **Bastion EC2**         | SSH from my IP only                          |
| **Kali EC2 (Private)**  | SSH-only via bastion                         |
| **Security Groups**     | Segmented and stateful                       |
| **Flow Logs**           | CloudWatch traffic monitoring                |
| **CI/CD**               | Markdown linting via GitHub Actions         |

Detailed logs: `notes/vpc-subnetting.md`

---

## 🧩 Phase 2: Modular Services (In Progress)

| Module               | Description                                    |
|----------------------|------------------------------------------------|
| 🔜 Portfolio Site     | Static site on S3 + HTTPS + Route53           |
| 🔜 Personal Storage   | IAM-scoped buckets with CLI access            |
| 🔜 Email Hub          | Domain-based email via SES                    |
| 🔜 AI Panel           | Local/private LLM bots with GUI frontend      |
| 🔜 VM Manager         | Web-based access to private Kali/Windows VMs  |

---

## 🛡️ Security Model

- No public IPs except bastion
- SSH restricted by source IP and SG chaining
- NAT gateway prevents inbound traffic to private VMs
- IAM least privilege enforced
- Flow logs and CloudWatch insights enabled

---

## 📁 Repo Structure

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

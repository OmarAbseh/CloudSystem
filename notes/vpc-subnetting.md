## Step 1 - VPC Creation
 - VPC Name: CloudSystem-VPC
 - CIDR Block: 10.0.0.0/16
 - DNS Resolution: Enabled
 - DNS Hostnames: Disabled (to be enabled later)
 - Created via AWS console manually
## STEP 2 — Subnet Creation
 - Created 2 Public Subnets:
        - `10.0.1.0/24` in AZ `us-east-1a`
        - `10.0.2.0/24` in AZ `us-east-1b`
 - Created 2 Private Subnets:
        - `10.0.3.0/24` in AZ `us-east-1a`
        - `10.0.4.0/24` in AZ `us-east-1b`
 - Public subnets will later attach to Internet Gateway.
 - Private subnets will later route internet traffic via NAT Gateway.
 - They will be used for:
        - Public EC2 (bastion, web)
        - Private EC2 (Kali, Windows)

## STEP 3 — Internet Gateway
 - Created IGW named `CloudSystem-IGW`
 - Attached to CloudSystem-VPC
 - Will update the public route table next to forward 0.0.0.0/0 traffic to IGW


## STEP 4 — Route Tables
 - Created 2 route tables:
 ### Public-RT
        - Routes 0.0.0.0/0 → CloudSystem-IGW
        - Associated with:
            - PublicSubnet-1a
            - PublicSubnet-1b
 ### Private-RT
        - No internet route yet (will add NAT next)
        - Associated with:
            - PrivateSubnet-1a
            - PrivateSubnet-1b

## STEP 5 — NAT Gateway
 - Allocated Elastic IP: CloudSystem-NAT-EIP
 - Created NAT Gateway: CloudSystem-NATGW in PublicSubnet-1a
 - Updated Private-RT:
        - 0.0.0.0/0 → CloudSystem-NATGW
 Private subnets can now reach internet securely.


## STEP 6 — Security Group + Bastion EC2
 - Created SG: Bastion-SG
    - Inbound: SSH (port 22) from my IP only
    - Outbound: Allow all
 - Launched EC2: Cloud-Bastion
    - PublicSubnet-1a
    - Auto-assign public IP
    - Connected via SSH

## STEP 7 — Private EC2 + SSH Jump
 - Created SG: Private-VMs-SG
    - SSH allowed from Bastion-SG only
 - Launched EC2: Kali-VM (Ubuntu base)
    - PrivateSubnet-1a
    - No public IP
    - Accessed via SSH jump through bastion
 - SSH Jump Pattern:
    - Local → Bastion → Kali
## STEP 8 — VPC Flow Logs
 - Created Flow Log for CloudSystem-VPC
 - Captures: All traffic (accepted + rejected)
 - Destination: CloudWatch Log Group (`CloudSystem-FlowLogs`)
 - IAM Role: Auto-created for publishing permissions(CloudSystemFlowRole)
 - Used for monitoring, audits, and security alerts

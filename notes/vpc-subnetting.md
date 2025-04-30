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

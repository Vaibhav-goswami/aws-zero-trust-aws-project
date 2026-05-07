# VPC Configuration

## VPC Details
- Name: zt-vpc-prod
- CIDR: 10.0.0.0/16
- Region: us-east-1 (N. Virginia)
- Internet Gateway: NOT ATTACHED
- DNS Resolution: Enabled
- DNS Hostnames: Enabled

## Subnets
| Name | CIDR | AZ | Purpose |
|------|------|----|---------|
| zt-subnet-app-1a | 10.0.1.0/24 | us-east-1a | App Servers |
| zt-subnet-app-1b | 10.0.2.0/24 | us-east-1b | App Servers |
| zt-subnet-ep-1a | 10.0.3.0/24 | us-east-1a | VPC Endpoints |
| zt-subnet-ep-1b | 10.0.4.0/24 | us-east-1b | VPC Endpoints |

## Route Table
- Name: zt-rt-private
- Routes: 10.0.0.0/16 → local ONLY
- No 0.0.0.0/0 route (fully private)

## Security Groups
| Name | Purpose |
|------|---------|
| zt-sg-nlb | NLB traffic control |
| zt-sg-app | EC2 app server protection |
| zt-sg-endpoints | VPC Endpoint access control |
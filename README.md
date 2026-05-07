# Zero-Trust Network with Private Endpoints

## Project Overview
A production-grade Zero-Trust security architecture on AWS where no resource has a public IP address. All communication occurs within a private VPC using AWS PrivateLink, VPC Interface Endpoints, and WAF protection.

## Cloud Provider
Amazon Web Services (AWS) — Region: ap-south-1 (Mumbai)

## Architecture
- Private VPC (10.0.0.0/16) with no Internet Gateway
- 4 Private Subnets across 2 Availability Zones
- VPC Endpoints for S3, DynamoDB, and SSM
- Internal Network Load Balancer
- CloudFront + AWS WAF (OWASP Top 10)
- EC2 with no public IP, no SSH
- Access via AWS Session Manager only

## Services Used
| Service | Resource Name | Purpose |
|---------|---------------|---------|
| VPC     | zt-vpc-prod   | Private Network |
| EC2     | zt-app-server-1 | App Server |
| NLB     | zt-nlb-internal | Internal Load Balancer |
| WAF     | zt-waf-acl-prod | OWASP Protection |
| CloudFront | zt-cloudfront-prod | Public Edge |
| IAM Role | zt-role-ec2-app | SSM Access |

## Security Features
- No public IP on any resource
- No SSH keys — Session Manager only
- WAF with OWASP Top 10 rules
- VPC Flow Logs for traffic monitoring
- Least-privilege Security Groups

## Project Proof
Screenshots available in `/screenshots` folder

## Synopsis
Refer to ZeroTrust_Synopsis.docx
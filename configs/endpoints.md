# VPC Endpoints Configuration

## Gateway Endpoints (Free)

### S3 Endpoint
- Name: zt-ep-s3
- Service: com.amazonaws.us-east-1.s3
- Type: Gateway
- Route Table: zt-rt-private
- Policy: Full Access

### DynamoDB Endpoint
- Name: zt-ep-dynamodb
- Service: com.amazonaws.us-east-1.dynamodb
- Type: Gateway
- Route Table: zt-rt-private
- Policy: Full Access

---

## Interface Endpoints (SSM — 3 Required)

### SSM Endpoint
- Name: zt-ep-ssm
- Service: com.amazonaws.us-east-1.ssm
- Type: Interface
- Subnets: zt-subnet-ep-1a, zt-subnet-ep-1b
- Security Group: zt-sg-endpoints
- Private DNS: Enabled

### SSM Messages Endpoint
- Name: zt-ep-ssmmessages
- Service: com.amazonaws.us-east-1.ssmmessages
- Type: Interface
- Subnets: zt-subnet-ep-1a, zt-subnet-ep-1b
- Security Group: zt-sg-endpoints
- Private DNS: Enabled

### EC2 Messages Endpoint
- Name: zt-ep-ec2messages
- Service: com.amazonaws.us-east-1.ec2messages
- Type: Interface
- Subnets: zt-subnet-ep-1a, zt-subnet-ep-1b
- Security Group: zt-sg-endpoints
- Private DNS: Enabled

---

## Why Private Endpoints?
- AWS service traffic stays within AWS network
- No internet traversal for S3, DynamoDB, SSM
- Eliminates need for NAT Gateway
- Core Zero-Trust requirement
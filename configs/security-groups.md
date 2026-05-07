# Security Groups Configuration

## zt-sg-nlb (NLB Security Group)
### Inbound Rules
| Type | Protocol | Port | Source |
|------|----------|------|--------|
| HTTPS | TCP | 443 | 0.0.0.0/0 |

### Outbound Rules
| Type | Protocol | Port | Destination |
|------|----------|------|-------------|
| Custom TCP | TCP | 8080 | zt-sg-app |

---

## zt-sg-app (Application Security Group)
### Inbound Rules
| Type | Protocol | Port | Source |
|------|----------|------|--------|
| Custom TCP | TCP | 8080 | zt-sg-nlb |

### Outbound Rules
| Type | Protocol | Port | Destination |
|------|----------|------|-------------|
| HTTPS | TCP | 443 | zt-sg-endpoints |

---

## zt-sg-endpoints (VPC Endpoints Security Group)
### Inbound Rules
| Type | Protocol | Port | Source |
|------|----------|------|--------|
| HTTPS | TCP | 443 | 10.0.0.0/16 |

### Outbound Rules
| Type | Protocol | Port | Destination |
|------|----------|------|-------------|
| All Traffic | All | All | 0.0.0.0/0 |

---

## Zero Trust Principle
- No resource directly accessible from internet
- All rules are least-privilege
- SG-to-SG rules used instead of IP ranges
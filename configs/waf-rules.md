# AWS WAF Configuration

## Web ACL Details
- Name: zt-waf-acl-prod
- Scope: CloudFront (Global)
- Region: us-east-1 (N. Virginia)
- Default Action: Allow
- Associated Resource: zt-cloudfront-prod

---

## Managed Rule Groups (OWASP Top 10)

| Rule Group | Priority | Purpose |
|------------|----------|---------|
| AWSManagedRulesCommonRuleSet | 1 | Core OWASP Top 10 Protection |
| AWSManagedRulesSQLiRuleSet | 2 | SQL Injection Prevention |
| AWSManagedRulesKnownBadInputsRuleSet | 3 | Malicious Input Blocking |
| AWSManagedRulesLinuxRuleSet | 4 | Linux Exploit Prevention |
| AWSManagedRulesAmazonIpReputationList | 5 | Known Bad Actor IPs |

---

## Custom Rules

### Rate Limiting Rule
- Name: RateLimitPerIP
- Type: Rate-based
- Limit: 2000 requests per 5 minutes
- Aggregation: Per IP Address
- Action: Block

---

## CloudFront Integration
- CloudFront acts as single public entry point
- WAF inspects all incoming requests
- NLB remains private (no public access)
- All blocked requests logged to CloudWatch

---

## Zero Trust Benefits
- No direct access to application servers
- All traffic filtered through WAF
- OWASP Top 10 vulnerabilities blocked
- Rate limiting prevents DDoS attacks
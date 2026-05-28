# AWS Scalable WordPress Cloud Architecture

A production-grade, high-availability WordPress infrastructure 
designed on AWS Europe (Ireland) region.

## Architecture Overview

- **Region:** eu-west-1 (Ireland)
- **Availability Zones:** eu-west-1a, eu-west-1b
- **Monthly Cost Estimate:** ~$3,733 (AWS Pricing Calculator)

## Services Used

| Service | Purpose |

| EC2 (m6g.xlarge) | WordPress instances with Auto Scaling |
| Application Load Balancer | HTTP/HTTPS traffic distribution |
| RDS for MariaDB (Multi-AZ) | Relational database with high availability |
| ElastiCache (Memcached + Redis) | In-memory caching layer |
| CloudFront | CDN for global content delivery |
| S3 | Static file storage |
| EFS | Shared file system across EC2 instances |
| WAF | DDoS protection and traffic filtering |
| Route 53 | DNS management |
| CloudWatch | Monitoring, metrics and alarms |
| VPC | Multi-tier network (public/app/data subnets) |
| NAT Gateway | Secure outbound internet for private subnets |

## Network Design

- Public Subnet: Internet Gateway, NAT Gateway, VPN Server
- App Subnet: WordPress EC2 instances
- Data Subnet: RDS, ElastiCache, EFS Mount Targets

## Security

- WAF filters malicious traffic and prevents DDoS attacks
- NACL and Security Groups provide layered network security
- NAT Gateway blocks direct inbound access to private resources
- AWS Private Certificate Authority for communication security

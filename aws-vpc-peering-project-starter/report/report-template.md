# AWS VPC Peering Project Report

**Student:** [Name]  
**Batch:** [Batch]  
**Region:** [AWS Region]  
**Completion date:** [Date]

## 1. Objective
[Explain the goal of connecting two non-overlapping VPCs privately.]

## 2. Architecture
[Insert `diagrams/architecture.svg` or a rendered image and explain each component.]

## 3. Resource inventory
| Resource | Actual AWS ID | CIDR/private IP | Notes |
|---|---|---|---|
| VPC A | [ID] | `10.10.0.0/16` | |
| VPC B | [ID] | `10.20.0.0/16` | |
| Bastion | [Instance ID] | `10.10.1.10` | Public IP: [record] |
| App-A | [Instance ID] | `10.10.2.10` | No public IP |
| App-B | [Instance ID] | `10.20.1.10` | No public IP |
| Peering | [pcx ID] | [actual status] | |

## 4. Routes and security
[Summarize all route tables, subnet associations and inbound rules. Explain forward and return routes.]

## 5. Actual validation results
| Test | Actual result | Evidence file |
|---|---|---|
| Baseline ping before peering/routes | [Result] | [File] |
| App-A to App-B ping | [Result] | [File] |
| App-B to App-A ping | [Result] | [File] |
| SSH to App-B through bastion | [Result] | [File] |
| Controlled ICMP failure | [Result] | [File] |
| Rule restored and recovery | [Result] | [File] |
| App-A/App-B have no public IP | [Result] | [File] |

## 6. Troubleshooting
[Describe issues you actually encountered and how you resolved them.]

## 7. What I learned
[Explain VPC CIDRs, peering, routes, security groups, bastion access and private connectivity in your own words.]

## 8. Cleanup
[Record what was deleted and include evidence. Check Billing for remaining chargeable resources.]

Replace all placeholders with actual details. Do not report expected results as completed tests.

# AWS VPC Peering Project

**Student:** [Add name]  
**Batch:** [Add batch]  
**AWS Region:** [Add region]  
**Status:** Starter documentation prepared. Complete the AWS lab and attach genuine evidence before submission.

## Objective
Connect two non-overlapping VPCs using VPC peering and private IPv4 addresses. Use one public bastion in VPC A for administration; both application instances must remain without public IPv4 addresses.

## Address plan
| Resource | CIDR / private IP |
|---|---|
| VPC A (`ewb-vpc-a`) | `10.10.0.0/16` |
| Public subnet A | `10.10.1.0/24` |
| Private subnet A | `10.10.2.0/24` |
| Bastion | `10.10.1.10` + public IPv4 |
| App-A | `10.10.2.10`, no public IPv4 |
| VPC B (`ewb-vpc-b`) | `10.20.0.0/16` |
| Private subnet B | `10.20.1.0/24` |
| App-B | `10.20.1.10`, no public IPv4 |

## Contents
- `diagrams/architecture.svg` — conceptual architecture.
- `docs/network-plan.md` — route tables and security-group rules.
- `docs/build-and-test-checklist.md` — build and validation checklist.
- `docs/troubleshooting-and-viva.md` — troubleshooting and viva preparation.
- `evidence/README.md` — screenshots and terminal output to capture.
- `report/report-template.md` — final report outline.

## Build sequence
1. Create both VPCs, subnets, route tables, and the Internet Gateway for VPC A.
2. Configure security groups and launch three EC2 instances.
3. Capture the failed baseline ping before peering/routes.
4. Create and accept the peering connection.
5. Add routes on both VPCs and the bastion public subnet.
6. Capture two-way ping, SSH-through-bastion, controlled failure, and recovery.
7. Complete the PDF report and clean up resources.

## Safety and costs
EC2, EBS and public IPv4 usage may incur charges. Check pricing/credits before launching. Never commit private keys, passwords, tokens or credentials. Do not open SSH or ICMP to `0.0.0.0/0`. Expected results are not proof of execution; use your own genuine evidence.

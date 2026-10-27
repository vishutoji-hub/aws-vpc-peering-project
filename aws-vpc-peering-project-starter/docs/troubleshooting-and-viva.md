# Troubleshooting and Viva

## Troubleshooting
- **Bastion SSH timeout:** check current public IP, your current IPv4 `/32` in the inbound rule, public subnet association and Internet Gateway default route.
- **App-A SSH fails:** check `10.10.1.10/32` SSH rule, private IP, key pair, `ec2-user`, and instance state.
- **App-B SSH fails:** check public subnet route to VPC B through peering, VPC B return route, and App-B SSH source `10.10.1.10`.
- **Ping fails:** check Active peering, both private route tables, correct `pcx-...` target, destination Echo Request rule and actual IPs.
- **Peering cannot be created:** check for overlapping VPC CIDRs, including secondary CIDRs.
- **`Permission denied (publickey)`:** check local key path, selected key pair, username `ec2-user` and file permissions.
- **Private host cannot download packages:** no NAT gateway or Internet route is part of this lab; package downloads are not required.

## Viva questions
1. **Why must VPC CIDRs not overlap?** So routes can distinguish destinations and the peering connection can be established.
2. **Why is a return route needed?** The destination must know how to send replies back to the source VPC.
3. **Why is App-B SSH source the bastion private IP?** The bastion initiates a separate SSH connection to App-B.
4. **Why doesn't Active peering guarantee ping success?** Route tables and security groups must also allow the traffic.
5. **Can VPC B use VPC A's Internet Gateway through peering?** No; peering is not a transit connection.
6. **What does a bastion host do?** Provides a controlled administration entry point to private instances.
7. **What does the controlled failure prove?** That the destination's ICMP inbound rule affects ping, and restoring it restores connectivity if other settings are correct.
8. **Why use `/32` rules?** `/32` limits the source to one IPv4 address.

# Build and Test Checklist

Only tick a task after doing it in AWS and saving evidence.

## Network
- [ ] Check AWS Region, account credits and displayed costs.
- [ ] Create VPC A `10.10.0.0/16`; subnets `10.10.1.0/24` and `10.10.2.0/24`.
- [ ] Attach `ewb-igw-a` to VPC A.
- [ ] Associate the public route table with public subnet; add `0.0.0.0/0` → Internet Gateway.
- [ ] Associate VPC A private route table with its private subnet; no Internet default route.
- [ ] Create VPC B `10.20.0.0/16` and private subnet `10.20.1.0/24`.
- [ ] Create/associate VPC B private route table. VPC B has no Internet Gateway.
- [ ] Disable automatic public IPv4 assignment for private subnets.

## Security and EC2
- [ ] Create security groups per `network-plan.md`.
- [ ] Create key pair `ewb-lab`; store `.pem` securely on your own computer.
- [ ] Launch bastion `10.10.1.10` with public IPv4.
- [ ] Launch App-A `10.10.2.10` and App-B `10.20.1.10`, both without public IPv4.
- [ ] Record instance IDs, private IPs and bastion public IP.
- [ ] Connect to bastion and App-A using SSH.

## Peering and validation
- [ ] Before peering/routes, run from App-A: `ping -c 4 10.20.1.10`; save baseline failure.
- [ ] Create peering connection, accept it, and wait for Active.
- [ ] Add `10.20.0.0/16` → `pcx-...` to both VPC A route tables.
- [ ] Add `10.10.0.0/16` → `pcx-...` to VPC B private route table.
- [ ] From App-A, run `ping -c 4 10.20.1.10`.
- [ ] From App-B, run `ping -c 4 10.10.2.10`.
- [ ] From laptop, test SSH to App-B through the bastion.
- [ ] Temporarily remove only App-B's inbound ICMP rule sourced from `10.10.2.10/32`; repeat App-A ping and capture failure.
- [ ] Restore the rule and capture successful ping recovery.
- [ ] Capture routes, associations, security groups, Active peering, private IP-only app hosts, and cleanup.

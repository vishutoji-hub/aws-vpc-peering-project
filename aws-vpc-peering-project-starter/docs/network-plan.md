# Network Plan

## Subnets and instances
| Name | CIDR / private IP | Notes |
|---|---|---|
| `ewb-vpc-a` | `10.10.0.0/16` | VPC A |
| `ewb-a-public` | `10.10.1.0/24` | Bastion subnet |
| `ewb-a-private` | `10.10.2.0/24` | App-A subnet |
| `ewb-vpc-b` | `10.20.0.0/16` | No Internet Gateway |
| `ewb-b-private` | `10.20.1.0/24` | App-B subnet |
| `ewb-bastion` | `10.10.1.10` | Public IPv4 enabled |
| `ewb-app-a` | `10.10.2.10` | No public IPv4 |
| `ewb-app-b` | `10.20.1.10` | No public IPv4 |

## Route tables
Keep each existing local route. Replace `pcx-...` with the actual active peering ID.

### `ewb-rt-a-public` (associated with `ewb-a-public`)
- `10.10.0.0/16` → `local`
- `0.0.0.0/0` → `ewb-igw-a`
- `10.20.0.0/16` → `pcx-...`

### `ewb-rt-a-private` (associated with `ewb-a-private`)
- `10.10.0.0/16` → `local`
- `10.20.0.0/16` → `pcx-...`

### `ewb-rt-b-private` (associated with `ewb-b-private`)
- `10.20.0.0/16` → `local`
- `10.10.0.0/16` → `pcx-...`

## Inbound security groups
| Security group | Protocol/port | Source |
|---|---|---|
| `ewb-sg-bastion` | SSH TCP 22 | Your current public IPv4 `/32` |
| `ewb-sg-app-a` | SSH TCP 22 | `10.10.1.10/32` |
| `ewb-sg-app-a` | ICMPv4 Echo Request (type 8, code 0) | `10.20.1.10/32` |
| `ewb-sg-app-b` | SSH TCP 22 | `10.10.1.10/32` |
| `ewb-sg-app-b` | ICMPv4 Echo Request (type 8, code 0) | `10.10.2.10/32` |

Keep the default outbound rules and default network ACLs for this beginner lab. Never expose SSH/ICMP to `0.0.0.0/0`. If IPs change, update the `/32` rules and commands too.

## Tags and inventory
Suggested tags: `Project = EWB-VPC-Peering`; `Student = [student name]`. Record actual resource IDs in the final report.

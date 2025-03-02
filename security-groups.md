# Security Groups

## Facts

- They live outside of instances
- They are stateful - If x is allowed in the inbound group, it will get a response
regardless of outbound rules

- Can be viewed as attachable firewalls
- Can be attached to resouces such as EC2, databases, S3, and more

- Only has **one** rule, **allow**
- Can control inbound and outbound

## Protocols

- TCP
- UDP

## Ports

- Single port or range
Standard Ports

| Name | Port |
| ---- | -----|
| FTP | 21 |
| SSH/SFTP | 22 |
| HTTP | 80 |
| HTTPs | 443 |
| RDP Win | 3389 |
| MySQL | 3306 |
| PostgreSQL | 5432 |
| Redis | 6379 |

## Sources

Blocks of IP addresses (CIDR):

- 10.0.0.0/16 - 64k IPs
- 0.0.0.0/0 - All IPs
- 172.24.145.123/32 - Single IP

Prefix list:

- Set of blocks of IPs

Other security groups:

- Allow access from one resource to another

- Can allow source to be the group it self


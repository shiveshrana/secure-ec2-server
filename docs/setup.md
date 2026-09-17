# EC2 Setup

## Instance Configuration

| Setting | Value |
|---|---|
| Instance Name | `secure-ec2-server` |
| AMI | Amazon Linux 2023 |
| Instance Type | `t3.micro` |
| Architecture | x86_64 |
| Root Storage | EBS gp3 |
| Public IPv4 | Enabled |
| SSH Key | `secure-ec2-key` |
| Security Group | `secure-ec2-sg` |

## Network Configuration

The instance was deployed into the default VPC and a public subnet with a public IPv4 address.

The public address allows:

- SSH administration
- Public HTTP access to the Nginx server

## Security Group

Inbound traffic:

| Protocol | Port | Source |
|---|---:|---|
| SSH | 22 | Administrator public IP `/32` |
| HTTP | 80 | `0.0.0.0/0` |

## SSH Connection

The EC2 instance was accessed using SSH from a Windows PowerShell terminal.

### Connection

```bash
ssh -i "<PATH_TO_KEY>" ec2-user@<EC2_PUBLIC_IP>

## Nginx Installation

Nginx was installed on the Amazon Linux EC2 instance.

### Installation

```bash
sudo dnf update -y
sudo dnf install nginx -y
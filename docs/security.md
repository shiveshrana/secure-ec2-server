# Security Configuration

## SSH

Port `22` is restricted to the administrator's public IP using `/32`.

This reduces unnecessary exposure of the SSH service to the public internet.

## HTTP

Port `80` is open to `0.0.0.0/0` because the Nginx website is intended to be publicly accessible.

## Public IPv4

The EC2 instance has a public IPv4 address so that it can be reached from the internet.

## Key-Based Authentication

SSH access uses the EC2 key pair instead of password authentication.
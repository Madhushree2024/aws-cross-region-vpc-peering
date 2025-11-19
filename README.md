# aws-cross-region-vpc-peering
This small project shows how two EC2 instances, running in two different AWS regions, can talk to each other privately using VPC Peering.
The idea is to prove that even when instances are in separate regions, they can still communicate through their private IPs without using the internet.

What the Setup Looks Like
Region A – ap-south-1 (Mumbai)

VPC-A

CIDR: 10.0.0.0/16

Subnet-A

10.0.1.0/24

EC2-A

Private IP: 10.0.1.10

This is the instance we use to ping the other region.

Region B – us-east-1 (N. Virginia)

VPC-B

CIDR: 172.16.0.0/16

Subnet-B

172.16.1.0/24

EC2-B

Private IP: 172.16.1.20

Connection Between Regions

A VPC Peering Connection is created between VPC-A and VPC-B.

Route tables are updated on both sides so the private networks can reach each other.

What This Demo Shows

Once the peering is active and routing is correct:

EC2 in Region A can ping EC2 in Region B using private IP

EC2 in Region B can ping EC2 in Region A using private IP

No internet gateway, no NAT, no VPN — just private network connectivity.

This confirms the peering is successfully established.

Why This Is Useful

This setup is helpful for:

Multi-region architectures

Database replication across regions

Private communication without exposing anything to the internet

Testing connectivity between different CIDR blocks

Files Included

architecture-diagram.png
A simple diagram showing both regions, VPCs, subnets, and EC2 instances.

steps.md
The step-by-step guide on how to create the entire setup.

ping-test-results.png
Screenshot showing EC2-A pinging EC2-B and vice versa.

How to Use This Repository

Open the steps.md file and follow each step in order.

Deploy both VPCs, subnets, and EC2s.

Create the peering connection.

Update the route tables.

Use SSH to connect to both EC2s and run ping tests.

That's all — once both instances respond over private IPs, the configuration is working.

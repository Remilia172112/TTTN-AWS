---
title: "Week 2 Worklog"
date: 2026-03-16
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Master foundational knowledge of AWS networking and security (VPC, VPN, Security Group, NACL).
* Successfully deploy and configure a complete Custom VPC network (including Public/Private Subnets, Route Tables, IGW, and NAT Gateway).
* Set up and establish an SSH connection to a Linux EC2 instance via the Visual Studio Code environment.
* Discuss and finalize the practical project topic with team members.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Read and study available materials on basic AWS networking services <br> - Learn the theory of Virtual Private Cloud (VPC), Subnets (Public & Private), and Route Tables | 03/16/2026 | 03/16/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Research deeper into network connectivity and security <br> - Read documentation on Internet Gateway (IGW), NAT Gateway, and VPN <br> - Learn about network security layers: Security Groups (SG) and Network Access Control Lists (NACL) | 03/17/2026 | 03/17/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Network Design Practice:** <br>&emsp; + Create a Custom VPC <br>&emsp; + Initialize Public and Private Subnets <br>&emsp; + Set up Internet Gateway and NAT Gateway <br>&emsp; + Configure Route Tables to route network traffic | 03/18/2026 | 03/18/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Security & EC2 Practice:** <br>&emsp; + Create and configure SGs and NACLs for Inbound/Outbound traffic <br>&emsp; + Launch EC2 instances (Linux) and place them in the corresponding Subnets <br> - Set up the VS Code environment locally to prepare for SSH | 03/19/2026 | 03/19/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Connection Practice:** Configure the SSH config file and remote SSH into the Linux EC2 directly on VS Code <br> - Team meeting: Discuss, evaluate feasibility, and finalize the final Project topic | 03/20/2026 | 03/20/2026 | |

### Week 2 Achievements:

* Understood AWS network architecture and distinguished between core components:
  * VPC (Virtual Private Cloud)
  * Public Subnet (Internet-facing) & Private Subnet (Isolated, high security)
  * Security Group (Instance-level security) & NACL (Subnet-level security)
  * NAT Gateway & Internet Gateway
* Successfully designed and configured a complete network system, ensuring that virtual machines in the Private Subnet can access the internet to download packages (via NAT Gateway) but cannot be accessed from the outside.
* Successfully launched Linux EC2 virtual machines within the correctly designated network partitions.
* Successfully configured a remote SSH connection using Visual Studio Code, making programming and server administration more visual and convenient compared to using a pure terminal.
* The team had an active discussion and agreed on the specific direction and topic for the practical project.
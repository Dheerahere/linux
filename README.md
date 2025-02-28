# Account Setup
- In  the first step, I'd create a Microsoft Azure account using email address that university provoded me.

- Then I got  to know about the cloud and its' importance. 

- Additionally, I explored student benefits  and open an student account and Azure give me $100 worth of credits that I can use to purchase any package within the environment.


# Create Virtual Machine
- I created virtual machine where I have to work later on this course.

- Then I select Marketplace from Ubuntu Server 24.04 LTS gen 2 Server published by Canonical. 

- I named my machine "dheera-robotics".

- I choose B series version 2 which is Standard_B2ls_v2.

- Later, I create a new resource group for the machine and subnet to place the machine in.

# Link my HAMK email to my GitHub account

- I create a new repository named "linux" for the assignment.

- Then I add my HAMK email as a secondary mail for version control.
![Capture](https://github.com/user-attachments/assets/3a84a112-ad6f-434f-9572-9fc9a2ffde70)


This document details the process of creating users and managing permissions in a Linux environment. The tasks include creating different types of users, managing sudo privileges, and setting up a shared directory with specific permissions.

Task 1: Creating User Tupu
The adduser script was used to create the Tupu user. This script provides an interactive way to create a new user with all necessary directories and settings.

sudo adduser tupu
Creating User Tupu

The adduser script automatically:

Creates the home directory
Sets up default shell
Prompts for password
Creates user-specific group
Sets up basic profile
Task 2: Creating User Lupu
Initially, I tried using the following given command:

sudo useradd -m -d /home/lupu -s /bin/bash -G lupu lupu
However, this resulted in an error:

Command error

The issue was that we tried to add the user to a group that didn't exist yet. To fix this, we modified the command to include the -U flag, which automatically creates a user group with the same name as the user:

sudo useradd -m -d /home/lupu -s /bin/bash -U lupu
Creating User Lupu

After creation, Set the password:

sudo passwd lupu
Creating User Lupu

Task 3: Creating System User Hupu
Created a system user Hupu with restricted login capabilities:

sudo useradd --system --shell /bin/false hupu
Creating System User Hupu

This creates a system account that:

Has no login shell (/bin/false)
Is typically used for running services
Has no home directory by default
Task 4: Adding Sudo Privileges
Added sudo privileges for both Tupu and Lupu users using the usermod command:

sudo visodu
Then adding:

tupu ALL=(ALL:ALL) ALL
lupu ALL=(ALL:ALL) ALL
Adding Sudo Privileges

Alternative method using:

sudo usermod -aG sudo tupu
sudo usermod -aG sudo lupu
Adding Sudo Privileges

Task 5: Setting Up Shared Directory
This task required creating a shared directory with specific permissions for Tupu and Lupu. Here's the detailed solution:

First, created a new group for the shared directory:
sudo groupadd projekti
Created the directory:
sudo mkdir /opt/projekti
Added Tupu and Lupu to the projekti group:
sudo usermod -aG projekti tupu
sudo usermod -aG projekti lupu
Set group ownership and permissions:
sudo chown :projekti /opt/projekti
sudo chmod 2770 /opt/projekti
Setting Up Shared Directory

The permission setup (2770) breaks down as:

2: SetGID bit (ensures new files inherit group ownership)
7: Owner has full permissions (read/write/execute)
7: Group has full permissions (read/write/execute)
0: Others have no permissions
This configuration ensures:

Only Tupu and Lupu can access the directory
New files automatically inherit the projekti group
Other users cannot access the directory
Both users have full control over the directory and its contents
To verify the setup:

sudo ls -la /opt/projekti
Setting Up Shared Directory


# Markdown and Linux Exercise

## Author - Fatiha Mahmud Dheera - BEIRP24A6

---

## Part 1: Markdown exercise

### Content

- Introduction to Markdown
- Markdown syntax basics
- Introduction to Linux
- Basic commands

#### Markdown examples

- **This is a Bold text**
- _This is a italic text_
- [Assignment 4 - Link
- `This can be a code block `

| No  | Description |
| --- | ----------- |
| 1   | Title       |
| 2   | Text        |
| 3   | Text        |
| 4   | Text        |

This is a Sample Image

![Boy Using Linux](./Images/image1.jpg)

---

## Part 2: Linux Exercise

1. Open a Linux command prompt (terminal).

![](./Images/2.png)

2. Create a new directory named markdown_linux_assignment with the command:

- mkdir markdown_linux_harjoitus
- Go to the created directory with the command: cd markdown_linux_harjoitus

The name **markdown_linux_harjoitus** used as the directory name

![](./Images/3.png)

3. Create a new empty file named README.md with the command:

- touch README.md

![](./Images/4.png)

4. Check that the file was created successfully with the command:

- ll

![](./Images/5.png)

5. Open README.md file in a text editor, for example, using a nano editor:

- nano README.md

![](./Images/6.png)
![](./Images/7.png)

6. Add the existing Markdown content to the file and save the changes.

![](./Images/8.png)

---

## Part 3: Git version control

1. Initialize a new Git repository in the directory with markdown_linux_assingment command:

- git init

![](./Images/9.png)

2. Add README.md file to the Git repository with the command:

- git add README.md

![](./Images/10.png)

3. Make your first commit with the command:

- git commit -m "Initial commit: Added README.md with Markdown and Linux instructions"

![](./Images/11.png)

---

Assingment 6 - APT
Objective:
By completing this assignment, you will:

✅ Learn how to install, update, remove, and search for software using APT (Advanced Package Tool).
✅ Understand how to manage repositories and resolve package dependencies.
✅ Gain hands-on experience in troubleshooting package installation issues.
Instructions
Perform the following tasks step by step, documenting your commands and outputs. If you encounter any errors, note them and describe how you resolved them.

Part 1: Understanding APT & System Updates (15 min)
Check your system’s APT version:
Run the following command to display the installed APT version: apt --version

Record the output.



Update the package list:
Run the command: sudo apt update


Explain why this step is important.
This will check with the current installed versions and the latest stable versions that you can download

- Get the latest package information
- Check whats need to be updated
- Get the security and bug fixes paches
- Update packages without dependancy issues
Upgrade installed packages:
Run: sudo apt upgrade -y


What is the difference between update and upgrade?

upgrade: This will update the packages in the linux system.

update: This will list down the updatable packages in the system without updating them.

View pending updates (if any):
Run: apt list --upgradable
Take note of any pending updates.


Part 2: Installing & Managing Packages (20 min)
Search for a package using APT:
Find an image editor using: apt search image editor


Pick one package from the list and write down its name.
xpaint/noble 2.9.1.4-4.1build2 amd64 simple paint program for X

View package details:
Get detailed information about the selected package: apt show
What dependencies does it require?
Install the package:
Run: sudo apt install -y
Confirm that the package is successfully installed.
Check installed package version:
Run: apt list --installed | grep
What version was installed?
Part 3: Removing & Cleaning Packages (10 min)
Uninstall the package:
Run: sudo apt remove -y
Is the package fully removed?
Remove configuration files as well:
Run: sudo apt purge -y
What is the difference between remove and purge?
Clear unnecessary package dependencies:
Run: sudo apt autoremove -y
Why is this step important?
Clean up downloaded package files:
Run: sudo apt clean
What does this command do?
Part 4: Managing Repositories & Troubleshooting (15 min)
List all APT repositories:
Run: cat /etc/apt/sources.list
What do you notice in this file?
Add a new repository (example: universe repository):
Run: sudo add-apt-repository universe sudo apt update
What types of packages are found in the universe repository?
Simulate an installation failure and troubleshoot:
Try installing a non-existent package: sudo apt install fakepackage
What error message do you get?
How would you troubleshoot this issue?
Submission Requirements
A markdown document containing:
The commands you used.
Screenshots (if possible) of important outputs.
Answers to the questions provided in each step.
Submit your work via GitHub repository URL.
Bonus Challenge (Optional):
Use apt-mark to hold and unhold a package so it doesn't get updated. sudo apt-mark hold sudo apt-mark unhold
Why would you want to hold a package?





* Linux Virtualization Exercise 7
Part 1: Virtualization Concepts
Key Concepts Overview
Virtualization

Virtualization is a technology that allows the creation of virtual versions of computing resources, including hardware platforms, storage devices, and network resources. It enables multiple virtual systems to run on a single physical machine.

Hypervisor

A hypervisor (or Virtual Machine Monitor) is software that creates and manages virtual machines. There are two types:

Type 1 (Bare Metal): Runs directly on hardware (e.g., VMware ESXi, Xen) Type 2 (Hosted): Runs on top of an operating system (e.g., VirtualBox, VMware Workstation)

Virtual Machines (VMs)

VMs are complete virtualized computing environments that include their own:

Operating system
Virtual hardware (CPU, RAM, storage, network interfaces)
Isolated system resources
Containers

Containers are lightweight, portable environments that package application code and dependencies. They:

Share the host OS kernel
Are more resource-efficient than VMs
Start up faster and are more portable
VMs vs. Containers Comparison
Architecture

VMs: Complete isolation with dedicated kernel and resources
Containers: Shared kernel with isolated user space
Resource Utilization

VMs: Higher overhead due to running complete OS
Containers: Lower overhead, shares host OS resources
Isolation Level

VMs: Complete hardware-level isolation
Containers: Process-level isolation
Part 2: Multipass Implementation
Installation
# Install Multipass
sudo snap install multipass
Basic Commands Implementation
# Launch default Ubuntu instance
multipass launch --name primary-vm
Command output

# List running instances
multipass list
Command output

# View instance details
multipass info primary-vm
Command output

# Access instance shell
multipass shell primary-vm
Command output

# Execute command on instance
multipass exec primary-vm -- ls -la
Command output

# Stop instance
multipass stop primary-vm

# Delete instance
multipass delete primary-vm
Command output

Cloud-init Configuration
Start a New Instance with Multipass

Command output

To start a new instance using this cloud-init configuration, you can use the following multipass command:

multipass launch --name my-instance --cloud-init cloud-init
Command output

File sharing
# Create shared directory
mkdir ~/shared-folder

# Mount to instance
multipass mount ~/shared-folder my-instance:/shared
Command output

Part 3: LXD Implementation
# Create container
lxc launch ubuntu:20.04 test-container

# List containers
lxc list

# Execute commands
lxc exec test-container -- apt update

# Stop container
lxc stop test-container

# Delete container
lxc delete test-container
Command output

Part 4: Docker Implementation
Installation
# Install Docker Engine
sudo apt update
sudo apt install docker.io

# Start and enable Docker
sudo systemctl start docker
sudo systemctl enable docker
Basic Docker Commands

# Pull image
docker pull ubuntu:latest

# Run container
docker run -it ubuntu:latest

# List containers
docker ps

# Build from Dockerfile
docker build -t myapp .

# Stop container
docker stop container_id
Command output

Part 5: Snap Implementation
Install snapcraft
First, install Snapcraft if you haven't already:

sudo apt update
sudo apt install snapcraft -y
If you're on a non-Ubuntu system, you may need to install Snapcraft via Snap:

sudo snap install snapcraft --classic
Create a project directory
Create a directory for your Snap project:

mkdir my-snapcraft
cd my-snapcraft
Create the Application Script
We’ll make a simple Bash script that prints "Hello, Snap!".

mkdir bin
nano bin/hello-snap
Paste the following content into the file:

#!/bin/bash
echo "Hello, Snap!"
Save and exit (in nano, press CTRL+X, then Y, then Enter).

Make the script executable:

chmod +x bin/hello-snap
Create the snapcraft YAML file
Snapcraft requires a snapcraft.yaml file to define how the Snap should be built. Create the file:

nano snapcraft.yaml
Add the following content:

name: my-snapcraft
base: core22
version: "1.0"
summary: "A simple Snapcraft app"
description: "This is a simple Snap application that prints Hello, Snap!"

grade: stable
confinement: strict

apps:
  hello:
    command: bin/hello-snap

parts:
  hello:
    plugin: dump
    source: .
Command output

This configuration:

Names the Snap my-snapcraft
Uses the core22 base (Ubuntu 22.04)
Defines a simple app that runs bin/hello-snap
Uses the dump plugin to include our script in the package
Build the snap package
Run the following command to build your Snap:

snapcraft
If it's the first time running Snapcraft, it may prompt you to install additional dependencies.

Install and run your snap
Once the build is complete, install the generated .snap file (e.g., my-snapcraft_1.0_amd64.snap):

sudo snap install my-snapcraft_1.0_amd64.snap --dangerous
The --dangerous flag is needed because it’s not from the official Snap store.

Now, run your Snap:

my-snapcraft.hello
You should see:

Hello, Snap!
Command output



## Assingment 8

### Linux Server Firewall Configuration

### Introduction

This document outlines the configuration of a Linux firewall (using ufw - Uncomplicated Firewall) to protect server services and prevent common network attacks.

### Base configuration

#### 1. Enable UFW on system start

```bash
sudo systemctl enable ufw
sudo ufw enable
```

#### 2. Default Policies

```bash
# Set default policies to deny incoming and allow outgoing
sudo ufw default deny incoming
sudo ufw default allow outgoing
```
![Command output](./images/w8-fw-default-policies.jpg)

### Service Rules

#### SSH Server

```bash
# Allow incoming SSH connections on standard port 22
# This enables secure remote administration of the server
sudo ufw allow 22/tcp

# Implement rate limiting for SSH to prevent brute force attacks
# Limits connection attempts from the same IP address
sudo ufw limit ssh comment 'Rate limit SSH connections'
```
![Command output](./images/w8-fw-ssh-rules.jpg)

#### Web Server (HTTP/HTTPS) rules

```bash
# Allow incoming HTTP traffic on port 80
# Required for standard web server operation
sudo ufw allow 80/tcp

# Allow incoming HTTPS traffic on port 443
# Required for secure web server operation using SSL/TLS
sudo ufw allow 443/tcp
```
![Command output](./images/w8-fw-web-rules.jpg)

### Logging Configuration

```bash
# Enable logging for all blocked connections
sudo ufw logging on

# Enable high-level logging to track all connections
sudo ufw logging high

# Log location: /var/log/ufw.log
# Logs both allowed and denied connections for monitoring
```
![Command output](./images/w8-fw-enable-logging.jpg)

### Protection Against Common Attacks

#### 1. SYN Flood Protection

```bash
# Add to /etc/sysctl.conf
# Enable SYN cookies to prevent SYN flood attacks
net.ipv4.tcp_syncookies = 1

# Increase backlog queue to handle more concurrent SYN packets
net.ipv4.tcp_max_syn_backlog = 2048

# Reduce number of SYN-ACK retries to limit resource consumption
net.ipv4.tcp_synack_retries = 2

# Also add these parameters for additional SYN flood protection
net.ipv4.tcp_syn_retries = 5
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_ecn = 0
net.ipv4.tcp_wmem = 4096 87380 8388608
net.ipv4.tcp_rmem = 4096 87380 8388608

# Apply settings
sudo sysctl -p
```
![Command output](./images/w8-fw-syn-flood.jpg)

#### 2. Additional Protection Measures

#### Block invalid packets

**What are invalid packets?**

Invalid packets include any incoming connections that don’t start with the SYN flag alone.

In a standard TCP Three-Way Handshake, every new connection begins with a SYN packet.

If a TCP connection starts with a different flag or an unusual combination of flags – like those generated by port-scanning tools such as Nmap – these packets should be blocked.

**How UFW blocks invalid packets**

Default rules added by UFW on /etc/ufw/before.rules file:

```bash
# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP
```

Add these two rules below the ones added by default by UFW:

```bash
-A ufw-before-input -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -j ufw-logging-deny
-A ufw-before-input -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -j DROP
```
![Command output](./images/w8-fw-invalid-packets-rule.jpg)

Don't forget to add them to the before6.rules file as well:

```bash
-A ufw6-before-input -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -j ufw6-logging-deny
-A ufw6-before-input -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -j DROP
```

Reference: [ivansalloum.com](https://ivansalloum.com/how-to-block-invalid-packets-with-ufw/)

#### Block ping (ICMP) requests

**What is ICMP flood attack?**

An ICMP flood attack, also known as a ping flood, is a type of Denial of Service (DoS) attack. It overwhelms a system by sending a huge number of ICMP packets, specifically echo requests (pings).

**How to prevent ICMP requests**

By commenting the lines below to block ping requests (icmp protocol) by ufw on file /etc/ufw/before.rules:

```bash
# ok icmp codes for INPUT
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# ok icmp code for FORWARD
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT
```
![Command output](./images/w8-fw-icmp-block.jpg)

Reference: [indusface.com](https://www.indusface.com/learning/icmp-flood-attacks/)

Reference: [andreyka26.com](https://andreyka26.com/how-to-block-ping-icmp-requests-using-ufw#edit-etcufwbeforerules)

Now, reload UFW:

```bash
sudo ufw reload
```

### Verification and Monitoring

```bash
# Display current rule status
sudo ufw status verbose

# Verify logging is working
sudo tail -f /var/log/ufw.log

# Test service accessibility
nc -zv [server-ip] 22
nc -zv [server-ip] 80
nc -zv [server-ip] 443
```
![Command output](./images/w8-fw-verification.jpg)

### Implementation Notes

#### Rule Order

- Rules are processed in order from top to bottom
- More specific rules are placed before general rules
- Default policies act as a catch-all for undefined traffic

#### Security Considerations

- All unnecessary ports remain closed by default
- Rate limiting on SSH prevents automated attacks
- SYN flood protection helps maintain service availability
- Logging enables security monitoring and incident response

#### Maintenance Requirements

- Regular log review required
- Update rules as service requirements change
- Monitor for unusual patterns in blocked traffic

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
- [Assignment 4 - Link](https://github.com/Rashmika-Dineth/Linux/tree/main/Assignment%204)
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

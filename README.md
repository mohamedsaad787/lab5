# lab5

## Task 1 – Group and User Creation

### 1. Create Group

Command:
groupadd -g 35000 sysadmins


### 2. Create Users

Command:
useradd -g sysadmins sysadmin1
useradd -g sysadmins sysadmin2


### 3. Set Initial Password

Command:
echo "sysadmin1:redhat" | chpasswd
echo "sysadmin2:redhat" | chpasswd


## Task 2 – Password Aging and Account Expiry

### 1. Set Maximum Password Age

Command:
chage -M 30 sysadmin1
chage -M 30 sysadmin2
### 2. Set Account Expiration Date

Command:
date -d "+90 days" +%Y-%m-%d
Command:
chage -E "$(date -d '+90 days' +%Y-%m-%d)" sysadmin1
chage -E "$(date -d '+90 days' +%Y-%m-%d)" sysadmin2
### 3. Force Immediate Password Change

Command:
chage -d 0 sysadmin1
chage -d 0 sysadmin2


### 1. Create Directory

Command:
mkdir -p /opt/sysadmin_tools

### 2. Change Group Ownership

Command:
chgrp sysadmins /opt/sysadmin_tools

### 3. Grant Group Write Access Using Symbolic Method

Command:
chmod g+w /opt/sysadmin_tools

### 4. Set Required Permissions Using Octal Method

Command:
chmod 770 /opt/sysadmin_tools


## Task 4 – Verification

### 1. Verify Directory Metadata

Command:
ls -ld /opt/sysadmin_tools


### 2. Switch to sysadmin1

Command:
su - sysadmin1
### 3. Navigate to Shared Directory
Command:
cd /opt/sysadmin_tools
### 4. Create audit.txt

Command:
touch audit.txt
### 5. Switch to sysadmin2

Command:
su - sysadmin2
### 6. Access Shared Directory

Command:
cd /opt/sysadmin_tools
Command:
ls -l /opt/sysadmin_tools/audit.txt

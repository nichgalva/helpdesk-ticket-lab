# Help Desk Ticket Lab (Active Directory)

## 📌 Overview
> Hands-on help desk ticket simulation demonstrating real-world troubleshooting using Active Directory and Windows environments.

Each scenario is structured as a help desk ticket with:
- Issue
- Cause
- Investigation steps
- Resolution
- Verification

---

## 🧱 Lab Environment

- Hypervisor: VirtualBox  
- Windows Server 2019 (Domain Controller)  
- Windows 10 (Client Machine)  
- Domain: homelab.local  
- Internal lab network  

---

## 🎯 Objective

To simulate Tier 1 / Tier 2 help desk responsibilities including:
- Diagnosing user issues
- Troubleshooting Active Directory problems
- Resolving authentication and access control issues
- Validating fixes through testing

---

# 🎫 Ticket Scenarios

---

## 🎫 Ticket #1 — User Cannot Log Into Domain

### 🧾 Issue
User `testuser` is unable to log into the domain.

### 🔍 Cause
Incorrect DNS configuration on client machine preventing domain resolution.

### 🛠️ Investigation
- Verified IP configuration using `ipconfig /all`
- Tested domain resolution using `nslookup homelab.local`
- Confirmed DNS pointing to incorrect DNS (8.8.8.8) instead of domain controller

📸 **DNS misconfiguration on client**

![DNS Broken](screenshots/02-dns-broken.png)

📸 **nslookup failing to resolve domain**

![NSLookup Fail](screenshots/05-nslookup-fail.png)

### ✅ Resolution
Updated DNS settings on CLIENT01 to point to Domain Controller:
- 192.168.10.10


📸 **DNS configuration corrected**

![DNS Fixed](screenshots/06-dns-fixed.png)

### ✔️ Verification
User successfully logged into domain after DNS correction.

📸 **Successful domain login**

![Login Success](screenshots/07-login-success.png)

---

## 🎫 Ticket #2 — Access Denied to Shared Folder

### 🧾 Issue
User `jsmith` unable to access HR shared folder.

### 🔍 Cause
Missing security group permissions due to removed HR-Users group.

### 🛠️ Investigation
- Checked NTFS permissions on `C:\Departments\HR`
- Confirmed HR-Users group missing
- Verified access denied from client machine

📸 **Access denied when opening HR folder**

![Access Denied](screenshots/09-access-denied.png)

📸 **Security tab showing missing HR-Users group**

![Permission Check](screenshots/10-permission-check.png)

### ✅ Resolution
Re-added HR-Users group and assigned appropriate permissions.

📸 **HR-Users group re-added to folder permissions**

![Permission Fixed](screenshots/11-permission-fixed.png)

### ✔️ Verification
User regained access to HR folder from client machine.

📸 **Access to HR folder restored**

![Access Restored](screenshots/12-access-restored.png)

---

## 🎫 Ticket #3 — Account Lockout

### 🧾 Issue
User `mlopez` account locked after failed login attempts.

### 🔍 Cause
Multiple incorrect password attempts triggered lockout policy.

### 🛠️ Investigation
- Checked Active Directory Users and Computers
- Verified account lock status under user properties

📸 **Account locked error on login**

![Account Locked](screenshots/13-account-locked.png)

📸 **Account lockout confirmed in Active Directory**

![Lockout Confirmed](screenshots/14-lockout-confirm.png)

### ✅ Resolution
Unlocked user account in Active Directory.

📸 **Account unlocked in AD**

![Account Unlocked](screenshots/15-account-unlocked.png)

### ✔️ Verification
User successfully logged in after unlock.

📸 **Login restored successfully**

![Login Restored](screenshots/16-login-restored.png)
---

## 🎫 Ticket #4 — Client Not Joined to Domain

### 🧾 Issue
CLIENT01 unable to authenticate domain users.

### 🔍 Cause
Machine removed from domain and placed in WORKGROUP.

### 🛠️ Investigation
- Verified system membership settings
- Confirmed client machine was not joined to the domain

📸 **Client machine showing WORKGROUP instead of domain**

![Workgroup](screenshots/17-workgroup.png)

📸 **Domain login failure**

![Domain Login Fail](screenshots/18-domain-login-fail.png)

### ✅ Resolution
Rejoined CLIENT01 to `homelab.local` domain using domain admin credentials.

📸 **Domain join successful**

![Domain Join Success](screenshots/20-domain-join-success.png)

### ✔️ Verification
Domain login restored successfully.

📸 **Successful domain login**

![Domain Login Success](screenshots/21-domain-login-success.png)

---

## 🎫 Ticket #5 — Network Connectivity Failure

### 🧾 Issue
Client unable to reach domain resources or services.

### 🔍 Cause
Incorrect IP configuration causing network isolation.

### 🛠️ Investigation
- Checked IP configuration via `ipconfig`
- Verified incorrect subnet assignment (192.168.50.x)

📸 **Incorrect IP configuration**

![Wrong IP](screenshots/22-wrong-ip.png)

📸 **Ping failure to domain controller**

![Ping Fail](screenshots/23-ping-fail.png)

📸 **ipconfig showing incorrect network**

![IP Config Wrong](screenshots/24-ipconfig-wrong.png)

### ✅ Resolution
Restored correct network settings:
- IP: 192.168.10.20
- DNS: 192.168.10.10

📸 **Correct IP configuration restored**

![IP Fixed](screenshots/25-ip-fixed.png)

### ✔️ Verification
Network connectivity and domain access restored.

📸 **Successful ping to domain controller**

![Ping Success](screenshots/26-ping-success.png)

---

## 🧠 Key Takeaways

- Practiced real-world IT help desk troubleshooting workflows  
- Strengthened Active Directory and DNS troubleshooting skills  
- Learned how misconfigurations impact authentication and access  
- Applied structured problem-solving (Issue → Cause → Fix → Verify)
- Simulated common help desk tickets and applied structured troubleshooting methodology in a controlled lab environment

---

## 🔧 Skills Demonstrated

- Active Directory User Management  
- DNS Troubleshooting  
- Windows Networking  
- NTFS Permissions & Access Control  
- Account Lockout Management  
- Client/Server Domain Integration  

---

## 🚀 Future Improvements

- Implement Group Policy Objects (GPOs)  
- Automate user creation with PowerShell  
- Add ticket logging system (simulated Service Desk workflow)  
- Expand lab with multiple clients and departments

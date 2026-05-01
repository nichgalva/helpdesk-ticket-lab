# Help Desk Ticket Lab (Active Directory)

## 📌 Overview
This project simulates real-world IT help desk scenarios using an Active Directory home lab environment.  
It focuses on troubleshooting common user issues including authentication failures, network problems, access control, and account lockouts.

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
- Confirmed DNS pointing to external server (8.8.8.8)

### ✅ Resolution
Updated DNS settings on CLIENT01 to point to Domain Controller:
- 192.168.10.10

### ✔️ Verification
User successfully logged into domain after DNS correction.

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

### ✅ Resolution
Re-added HR-Users group and assigned appropriate permissions.

### ✔️ Verification
User regained access to HR folder from client machine.

---

## 🎫 Ticket #3 — Account Lockout

### 🧾 Issue
User `mlopez` account locked after failed login attempts.

### 🔍 Cause
Multiple incorrect password attempts triggered lockout policy.

### 🛠️ Investigation
- Checked Active Directory Users and Computers
- Verified account lock status under user properties

### ✅ Resolution
Unlocked user account in Active Directory.

### ✔️ Verification
User successfully logged in after unlock.

---

## 🎫 Ticket #4 — Client Not Joined to Domain

### 🧾 Issue
CLIENT01 unable to authenticate domain users.

### 🔍 Cause
Machine removed from domain and placed in WORKGROUP.

### 🛠️ Investigation
- Verified system membership settings
- Confirmed domain relationship broken

### ✅ Resolution
Rejoined CLIENT01 to `homelab.local` domain using domain admin credentials.

### ✔️ Verification
Domain login restored successfully.

---

## 🎫 Ticket #5 — Network Connectivity Failure

### 🧾 Issue
Client unable to reach domain resources or services.

### 🔍 Cause
Incorrect IP configuration causing network isolation.

### 🛠️ Investigation
- Checked IP configuration via `ipconfig`
- Verified incorrect subnet assignment (192.168.50.x)

### ✅ Resolution
Restored correct network settings:
- IP: 192.168.10.20
- DNS: 192.168.10.10

### ✔️ Verification
Network connectivity and domain access restored.

---

## 🧠 Key Takeaways

- Practiced real-world IT help desk troubleshooting workflows  
- Strengthened Active Directory and DNS troubleshooting skills  
- Learned how misconfigurations impact authentication and access  
- Applied structured problem-solving (Issue → Cause → Fix → Verify)

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

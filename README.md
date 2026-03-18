# Active Directory Simulation Lab – EmiratesGas

This project demonstrates a **lab simulation of Identity and Access Management (IAM)** using **Windows Server Active Directory Domain Services (AD DS)** for a fictional Oil & Gas company called **EmiratesGas**.

The lab includes **domain setup, network configuration, Organizational Units (OUs), users, groups, and Group Policy Objects (GPOs)** to simulate a real-world enterprise environment.

---

## 🏢 Organization Overview

**EmiratesGas** operates across three locations:

* Abu Dhabi
* Dubai
* Sharjah

Each location is structured using **Active Directory Organizational Units (OUs)** with department-based grouping.

---

## 🎯 Project Objectives

* Deploy a **Domain Controller on Windows Server**
* Configure **Active Directory Domain Services (AD DS)**
* Design a **multi-location OU structure**
* Create **users and security groups**
* Implement **Group Policies (GPOs)**
* Simulate **IAM controls and access restrictions**

---

## 🌐 Network Design

```
Internet
   ↓
Router (Gateway: 10.0.5.1)
   ↓
Switch
 ┌────────────┬────────────┬────────────┐
 │            │            │            │
Server     Abu Dhabi     Dubai       Sharjah
(DC)        Clients      Clients      Clients
```

| Device      | IP Address           | Role              |
| ----------- | -------------------- | ----------------- |
| Gateway     | 10.0.5.1             | Network Router    |
| Server (DC) | 10.0.5.3             | Domain Controller |
| Clients     | 10.0.5.4 – 10.0.5.12 | Domain Users      |

---

## 🖥️ Domain Configuration

* **Domain Name:** `emiratesgas.ai`
* **Server IP:** `10.0.5.3`
* **Roles Installed:**

  * Active Directory Domain Services (AD DS)
  * DNS

---

## 🗂️ Active Directory Structure (OUs + Groups + Users)

Below is the **complete hierarchical structure combining Organizational Units (OUs), Groups, and Users**:

```text
emiratesgas.ai
│
├── AbuDhabi (OU)
│   │
│   ├── Exploration (Group)
│   │   └── Ahmed.Exp (User | 10.0.5.4)
│   │
│   ├── Drilling (Group)
│   │   └── EngOmar.Dril (User | 10.0.5.5)
│   │
│   └── Production (Group)
│       └── James.Prod (User | 10.0.5.6)
│
├── Dubai (OU)
│   │
│   ├── Logistics (Group)
│   │   └── Mohamed.Log (User | 10.0.5.7)
│   │
│   ├── SupplyChain (Group)
│   │   └── Ava.Supply (User | 10.0.5.8)
│   │
│   └── Maintenance (Group)
│       └── Noah.Maint (User | 10.0.5.9)
│
└── Sharjah (OU)
    │
    ├── IT (Group)
    │   └── Michael.IT (User | 10.0.5.10)
    │
    ├── HSE (Group)
    │   └── Sara.Safety (User | 10.0.5.11)
    │
    └── HR (Group)
        └── Fatima.HR (User | 10.0.5.12)
```

---

## 🔐 Group Policy Objects (GPOs)

Policies are configured using **Group Policy Management Console (gpmc.msc)** and linked to respective Organizational Units (OUs).


## Default Domain Policy

### Password Policy
* Enforces **password complexity requirements**
* Password history: **5 previous passwords remembered**
* Maximum password age: **90 days**
* Minimum password length: **10 characters**
> ✅ Ensures strong authentication and prevents password reuse.

### Account Lockout Policy
* Lockout threshold: **3 failed login attempts**
* Lockout duration: **15 minutes**
* Reset account lockout counter after: **15 minutes**
> 🛡️ Protects against brute-force and unauthorized login attempts.


## ABU DHABI POLICY

### Restrict Control Panel & PC Settings
* Blocks access to Control Panel and system settings
> 🔒 Prevents unauthorized system configuration changes.

### Disable PowerShell
* Disables PowerShell execution for standard users
> ⚠️ Reduces risk of script-based attacks and misuse.


## DUBAI POLICY

### Disable Command Prompt (CMD)
* Prevents access to Command Prompt
> 🚫 Stops execution of unauthorized commands and scripts.


## SHARJAH POLICY

### Disable Shutdown / Restart / Hibernate
* Removes power options from the user interface
> ⚡ Prevents accidental or unauthorized system shutdowns.


## OUT OF OFFICE/ SERVICE POLICY

### Restrict User Access During Absence
* Temporarily disables or restricts user login access
> 🧑‍💼 Ensures account security while the user is away.

### Prevent Access to Organization Server
* Blocks access to internal systems and domain resources
> 🔐 Protects sensitive data during absence periods.

---

## 🧪 IAM Concepts Demonstrated

* Organizational Unit (OU) Design
* Role-Based Access Control (RBAC)
* Group Policy Enforcement
* Multi-location AD Structure
* User Access Restrictions
* Security Hardening

---

## 📸 Screenshots

* [EmiratesGas subnet network created](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/01_EmiratesGas_Subnet_Network.png)
* Connected Windows Server and All PCs to the Network
* Ping PC to PC to ensure connectivity on the Network
* Ping server from/to each PC
* Active Directory Installed
* Promoted to Domain Services
* Logged in to Windows Server as Domain Controller
* Abu Dhabi OU, groups and users created
* Dubai OU, groups and users created
* Sharjah OU, groups and users created
* Group Policy Objects created and linked to OUs
* Dafault domain policy - Password policy
* Dafault domain policy - Account Lockout policy
* Abu Dhabi Policy - CPanel and PC Settings restricted
* Abu Dhabi Policy - Powershell restricted
* Dubai Policy - Comand prompt restricted
* Sharjah Policy - Disabled poweroff, restart and hybenate
* Out of Office - Denied user access when absence
* DNS configuration on all PCs
* All PC/Users connected the domain server
* Abu Dhabi users CPanel, PC settings and powershell restricted
* Dubai users cmd restricted
* Sharjah users before poweroff disable
* Sharjah users after poweroff disabled

---

## 📚 Key Takeaways

* Built a **realistic enterprise AD environment**
* Applied **IAM principles in a hands-on lab**
* Implemented **centralized access control using GPOs**
* Designed a **scalable multi-location directory structure**

---

## ✅ Conclusion

This lab provides a **practical simulation of Identity and Access Management** in a corporate environment, demonstrating how **Active Directory, OUs, users, and GPOs** work together to enforce **security and operational control**.

---

## Author

**Ahmed Olatunji**  
Cybersecurity Analyst

---

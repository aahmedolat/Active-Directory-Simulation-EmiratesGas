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
* [Connected Windows Server and All PCs to the Network](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/02_Sever_PCs_Network.png)
* [Ping PC to PC to ensure connectivity on the Network](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/03_Ping_All_PC_to_PC.png)
* [Ping server from/to each PC](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/04_Ping_All_PCs_to_WinServer.png)
* [Active Directory Installed](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/05_AD_Installation.png)
* [Promoted to Domain Services](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/06_DS_Promoted.png)
* [Logged in to Windows Server as Domain Controller](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/07_LoggedIn_Domain_Controller_Server.png)
* [Abu Dhabi OU, groups and users created](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/08_AbuDhabi_OU_Groups_Users.png)
* [Dubai OU, groups and users created](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/09_Dubai_OU_Groups_Users.png)
* [Sharjah OU, groups and users created](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/10_Sharjah_OU_Groups_Users.png)
* [Group Policy Objects created and linked to OUs](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/11_GPOs_Created_Linked_OUs.png)
* [Dafault domain policy - Password policy](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/12_Password_Policy.png)
* [Dafault domain policy - Account Lockout policy](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/13_AccLoockout_Policy.png)
* [Abu Dhabi Policy - CPanel and PC Settings restricted](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/14_CP_PC_Settings_Policy_Enabled.png)
* [Abu Dhabi Policy - Powershell restricted](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/15_Powershell_Restricted.png)
* [Dubai Policy - Comand prompt restricted](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/16_Command_Prompt_Restricted.png)
* [Sharjah Policy - Disabled poweroff, restart and hybenate](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/17_Shutdown_Restart_Disabled.png)
* [Out of Office - Denied user access when absence](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/18_Outof_Office_Access_Denied.png)
* [DNS configuration on all PCs](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/19_DNS_Configured_All_PC.png)
* [All PC/Users connected the domain server](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/20_Linked_All_PCs_to_Domain.png)
* [Abu Dhabi users CPanel, PC settings and powershell restricted](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/21_AbuDhabi_PCs_CPanel_PCsettings_PowerShell_Restricted.png)
* [Dubai users cmd restricted](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/22_Dubai_PCs_CMD_Restricted.png)
* [Sharjah users before poweroff disable](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/23_Sharjah_Users_Before_Power_Disable.png)
* [Sharjah users after poweroff disabled](https://github.com/aahmedolat/Active-Directory-Simulation-EmiratesGas/blob/main/Screenshots/24_Sharjah_Users_After_Power_Disabled.png)

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

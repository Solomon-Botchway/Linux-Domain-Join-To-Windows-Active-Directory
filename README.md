# Linux-Domain-Join-To-Windows-Active-Directory
   ## Overview

To extend the enterprise environment beyond Windows systems, a Linux workstation (PC02) was integrated into the Active Directory domain.

This project demonstrates centralized identity management across multiple operating systems using Active Directory as the single authentication source.

---                
# Enterprise Architecture

```text
                            INTERNET
                                │
                        Home Router
                                │
                   Hyper-V External Switch
                                │
        ┌───────────────────────┼───────────────────────┐
        │                       │                       │

      DC01                    PC01                    PC02
Windows Server           Windows 11            Linux Workstation
    2022                  Enterprise

 Active Directory
 DNS
 Group Policy
 File Services
 Print Services
 Software Repository
 Event Collector

        │                       │                       │
        └────────────── solotech.local ────────────────┘

                Centralized Authentication

                         IT-Team
                           │
             ┌─────────────┴─────────────┐
             │                           │

          PC01                        PC02

             Users, Policies, Drives,
             Printers and Security
         controlled through Active Directory
```

## Environment

| Device | Operating System | Role |
|----------|----------|----------|
| DC01 | Windows Server 2022 | Domain Controller |
| PC01 | Windows 11 Enterprise | Domain Workstation |
| PC02 | Linux Desktop | Linux Domain Workstation |

Domain:

```text
solotech.local
```

---

## Project Objectives

- Join Linux to Active Directory
- Centralize authentication through AD
- Restrict workstation access using AD security groups
- Eliminate local account dependency
- Implement role-based access control

---

## Linux Domain Join Process

### 1. Configure DNS

Linux was configured to use the domain controller as its primary DNS server.

```text
DNS Server:
192.168.10.10
```

This enabled Linux to locate:

- Active Directory
- Kerberos Services
- LDAP Services

---

### 2. Install Required Components

Installed:

```text
realmd
sssd
adcli
krb5
samba-common
oddjob
```

These components provide:

- Kerberos authentication
- Active Directory integration
- User account resolution
- Domain enrollment

---

### 3. Discover Domain

Verified Linux could locate:

```text
solotech.local
```

and communicate with the domain controller.

---

### 4. Join Active Directory

Joined Linux workstation to:

```text
solotech.local
```

using domain administrator credentials.

Result:

```text
PC02
```

was automatically created within:

```text
Active Directory Users and Computers
→ Computers
```

---

### 5. Configure Centralized Authentication

Enabled:

- Active Directory login
- Domain user authentication
- User directory creation
- Identity resolution

Users can now authenticate using:

```text
SOLTECH\username
```

equivalent Linux login formats.

---

### 6. Restrict Access Using Security Groups

Login restrictions were configured so that only:

```text
IT-Team
```

members can access the Linux workstation.

Denied Groups:

```text
HR-Team

Finance-Team

Sales-Team

CustomerService-Team
```

---

## Access Control Model

```text
IT-Team
    ↓
Access Granted

All Other Department Groups
    ↓
Access Denied
```

This provides:

- Least Privilege
- RBAC
- Centralized Identity Governance

---

## Enhanced Session Investigation

A parallel investigation was conducted into improving Linux and Hyper-V integration.

### Objective

Enable:

- Clipboard Redirection
- Host to Guest Copy & Paste
- Improved GUI Experience

### Technologies Evaluated

- xRDP
- Xorg
- Xvnc

### Outcome

Successfully established enhanced functionality through:

```text
xRDP
+
Xvnc
```

before simplifying the final deployment configuration.

This provided valuable experience in:

- Linux Remote Desktop Services
- Virtualization Integration
- Linux Desktop Administration

---

## Validation

Successfully verified:

| Test | Result |
|---------|---------|
| Domain Discovery | ✅ |
| Domain Join | ✅ |
| AD Computer Object Created | ✅ |
| Domain Authentication | ✅ |
| IT-Team Login | ✅ |
| Non-IT Login Blocked | ✅ |

---

## Skills Demonstrated

### Active Directory

- Computer Object Management
- Domain Join Procedures
- Security Group Administration
- Identity Management

### Linux Administration

- Linux Domain Integration
- Kerberos Authentication
- SSSD Configuration
- Realmd Administration
- Linux Access Control

### Security

- RBAC
- Least Privilege
- Directory-Based Authentication
- Cross-Platform Identity Management

### Infrastructure

- Hyper-V
- Linux Virtualization
- DNS Integration
- Enterprise Authentication Services

---

## Business Outcome

The SoloTech lab evolved from a Windows-only Active Directory environment into a hybrid Windows/Linux infrastructure with centralized authentication, access control, and identity management.

This implementation reflects the type of environment commonly found in enterprise organizations where Linux and Windows systems coexist and rely on a shared identity platform.

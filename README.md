🏢 Active Directory Lab Setup (TechCorp)

📌 Overview

This project demonstrates a complete Active Directory (AD) environment setup including:

- Domain creation
- Organizational Units (OU)
- Users & Groups
- File Server with permissions
- Access-Based Enumeration (ABE)
- Group Policy Objects (GPO)

---

🌳 Active Directory Structure

techcorp.local
│
├── HR
│   ├── Users
│   │   ├── arjun.varma
│   │   ├── riya.sharma
│   ├── Groups
│   │   ├── HR_Group
│
├── IT
│   ├── Users
│   │   ├── aditya.rao
│   │   ├── vikram.singh
│   ├── Groups
│   │   ├── IT1_Group
│
├── Common
│   ├── Groups
│   │   ├── All_Employees
│   ├── Computers
│       ├── VM1

---

⚙️ Setup Steps

1️⃣ Domain Setup

- Installed Windows Server
- Configured Static IP
- Installed Active Directory Domain Services (AD DS)
- Promoted to Domain Controller

Domain: techcorp.local

---

2️⃣ Users & Groups

Users

- HR: arjun.varma, riya.sharma
- IT: aditya.rao, vikram.singh

Groups

- HR_Group
- IT1_Group
- All_Employees

Group Membership

HR_Group → HR users
IT1_Group → IT users
All_Employees → All users

---

3️⃣ Client Machine (VM1)

- Created VM using ISO
- Configured DNS → Domain Controller IP
- Joined domain:

techcorp.local

- Moved VM1 to:

OU=Common → Computers

---

📁 File Server Setup

Folder Structure

C:\Shares
│
├── HR
├── IT
├── Public

---

🔐 Permissions Configuration

🚫 Root Folder (C:\Shares)

Removed:

- Users
- Authenticated Users
- HR_Group
- IT_Group

Kept only:

SYSTEM
Administrators

---

📁 HR Folder

HR_Group → Modify

---

📁 IT Folder

IT1_Group → Full Control

---

📁 Public Folder

All_Employees → Read

---

⚠️ Important

- Disabled inheritance for all subfolders
- Applied explicit permissions

---

🔍 Access-Based Enumeration (ABE)

Enabled via:

Server Manager → File and Storage Services → Shares → Properties

✔ Ensures users only see folders they have access to

---

🧪 Access Result

User Type| Visible Folders
HR| HR only
IT| IT only
Others| Public only

---

⚙️ Group Policy Objects (GPO)

🎨 Wallpaper Policy

User Configuration → Desktop Wallpaper
Path: \\Server\Shares\Public\wallpaper.jpg

---

🔌 USB Restriction

Computer Configuration → Removable Storage Access
→ Deny All Access

---

🚫 Control Panel Restriction

User Configuration → Control Panel
→ Prohibit access

---

🔗 GPO Linking

- Linked GPOs to:

OU=HR
OU=IT

---

🔄 Apply Policies

gpupdate /force

---

🧪 Verification

gpresult /r

---

🧠 Key Concepts Learned

- Active Directory structure (OU, Users, Groups)
- Group-based access control
- NTFS vs Share permissions
- Access-Based Enumeration (ABE)
- GPO (User vs Computer policies)
- Domain join & client management
- Troubleshooting permissions & inheritance

---

🎯 Conclusion

This lab demonstrates a real-world enterprise Active Directory setup with:

✔ Secure file access
✔ Proper permission management
✔ Policy enforcement using GPO
✔ Clean OU-based structure

---

🚀 Future Improvements

- Network Drive Mapping
- Printer Deployment via GPO
- Folder Redirection
- Roaming Profiles

---

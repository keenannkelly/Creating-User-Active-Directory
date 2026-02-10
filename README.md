# Creating Users in Active Directory

A step-by-step guide demonstrating user account creation and management in Active Directory Domain Services, showcasing essential identity and access management skills for enterprise IT administration.

## 🎯 Project Overview

This project demonstrates the process of creating and configuring user accounts in Active Directory using the Active Directory Users and Computers (ADUC) console, highlighting fundamental skills required for managing enterprise user identities.

# 🎥 Watch Me Build This Lab!
**[▶️ Watch Here](https://www.loom.com/share/84d24abc8532413fb6b843388e3efbcd)**

## 🏗️ Environment

**Domain**: keenan.local  
**Tool**: Active Directory Users and Computers (ADUC)  
**Platform**: Windows Server 2025  
**Example User**: Bob Rich  
**Container**: Users OU  

## 📋 User Creation Process

### Step 1: Accessing Active Directory
- Opened Windows Server virtual machine with Active Directory configured
- Clicked **Start Menu** or pressed **Windows Key**
- Typed **"active"** in search box
- System populated available Active Directory tools
- Selected **"Active Directory Users and Computers"** from results list

**Alternative Access Methods**:
- Server Manager → Tools → Active Directory Users and Computers
- Run command: `dsa.msc`
- Administrative Tools folder

### Step 2: Navigating to the Domain
- Located domain in ADUC console tree
- Expanded **keenan.local** domain
- Viewed domain structure and organizational units
- Prepared to navigate to Users container

**Domain Structure Visible**:
```
keenan.local
├── Builtin
├── Computers
├── Domain Controllers
├── ForeignSecurityPrincipals
├── Managed Service Accounts
├── Program Data
└── Users
```

### Step 3: Adding a New User
- Clicked dropdown arrow next to **keenan.local** domain
- Selected **"Users"** container from the list
- Right-clicked on **Users** container
- Clicked **"Action"** in the menu bar
- Hovered over **"New"**
- Selected **"User"** from submenu

**What this does**: Opens the New Object - User wizard for account creation.

### Step 4: Entering User Details
- **New Object - User** dialog box appeared
- Entered user information:
  - **First name**: Bob
  - **Last name**: Rich
  - **Full name**: Bob Rich (auto-populated)
  - **User logon name**: brich
  - **User logon name (pre-Windows 2000)**: KEENAN\brich
- Verified domain suffix: **@keenan.local**
- Confirmed all details were correct
- Clicked **"Next"** to proceed

**Naming Convention Best Practices**:
- First initial + last name (e.g., brich)
- First name + last initial (e.g., bobr)
- First.Last (e.g., bob.rich)
- Employee ID numbers

### Step 5: Setting a Password
- **Password configuration screen** appeared
- Created secure password for the user
- Entered password in **"Password"** field
- Re-entered password in **"Confirm password"** field
- **Unchecked**: "User must change password at next logon"
- **Checked**: "Password never expires"
- Clicked **"Next"** to confirm password settings

**Password Options Explained**:
- ✅ **User must change password at next logon** - Forces password change on first login (unchecked for this demo)
- ✅ **User cannot change password** - Prevents user from changing their password
- ✅ **Password never expires** - Exempts account from password expiration policy (checked)
- ✅ **Account is disabled** - Creates disabled account for future use

### Step 6: Completing User Creation
- **Summary screen** displayed user details
- Reviewed all information:
  - Full name: Bob Rich
  - Logon name: brich@keenan.local
  - Password settings confirmed
- Clicked **"Finish"** to complete user creation process
- System created user account in Active Directory
- Success confirmation appeared

### Step 7: Verify User Creation
- Navigated to **Users** container under keenan.local domain
- Scrolled through user list
- Located **Bob Rich** in the user list
- Verified user account properties:
  - Display name: Bob Rich
  - User logon name: brich@keenan.local
  - Account status: Enabled

**✅ Success!** The user has been successfully created and is ready for use.

## 🔧 User Account Properties

### Basic Information
```
Name:                 Bob Rich
Username:             brich
Domain:               keenan.local
Full UPN:             brich@keenan.local
Pre-2000 Logon:       KEENAN\brich
Container:            CN=Users,DC=keenan,DC=local
```

### Account Settings
```
Password:             Set (secure)
Password Expiration:  Never expires
Account Status:       Enabled
Logon Hours:          All hours allowed
Logon Workstations:   All workstations
Account Expires:      Never
```

## 🎓 Skills Demonstrated

### Active Directory Management
- ✅ ADUC console navigation
- ✅ User account creation
- ✅ Password policy configuration
- ✅ Account property management
- ✅ Domain user administration

### Identity Management
- ✅ User provisioning
- ✅ Naming convention implementation
- ✅ Security policy application
- ✅ Account verification
- ✅ Access control basics

### Windows Server Administration
- ✅ Administrative tools usage
- ✅ Domain services management
- ✅ User lifecycle management
- ✅ Security best practices

## 🔐 Security Considerations

### Password Policy Best Practices
```
✅ Strong password complexity
✅ Minimum password length (8+ characters)
✅ Password history enforcement
✅ Account lockout policies
✅ Regular password rotation (except service accounts)
```

### Account Security
```
✅ Principle of least privilege
✅ Appropriate group membership
✅ Account expiration for temporary users
✅ Disabled accounts for terminated users
✅ Regular account audits
```

### Production Recommendations
```
⚠️  "Password never expires" should be used sparingly
⚠️  "User must change password at next logon" recommended for new users
⚠️  Implement strong password policies
⚠️  Use account expiration for contractors/temps
⚠️  Enable account lockout policies
```
## 👨‍💻 Author

**Keenan Kelly**

This project demonstrates practical Active Directory user management skills essential for enterprise IT administration and identity management roles.

## 📄 Related Projects

- [Configuring Active Directory](https://github.com/keenannkelly/Configuring-Active-Directory) - AD DS installation and setup
- [Creating a VM on AWS](https://github.com/keenannkelly/Creating-VM-on-AWS) - Windows Server deployment
- [EC2 RDP Connection](https://github.com/keenannkelly/EC2-RDP-Connection) - Remote server access

---

*Demonstrating enterprise identity and access management with Active Directory user administration*

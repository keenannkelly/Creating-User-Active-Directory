# Creating Users in Active Directory

A step-by-step guide demonstrating user account creation and management in Active Directory Domain Services, showcasing essential identity and access management skills for enterprise IT administration.

## 🎯 Project Overview

This project demonstrates the process of creating and configuring user accounts in Active Directory using the Active Directory Users and Computers (ADUC) console, highlighting fundamental skills required for managing enterprise user identities.

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

## 💻 PowerShell Alternative

### Create User with PowerShell
```powershell
# Create new AD user
New-ADUser -Name "Bob Rich" `
           -GivenName "Bob" `
           -Surname "Rich" `
           -SamAccountName "brich" `
           -UserPrincipalName "brich@keenan.local" `
           -Path "CN=Users,DC=keenan,DC=local" `
           -AccountPassword (ConvertTo-SecureString "P@ssw0rd123!" -AsPlainText -Force) `
           -Enabled $true `
           -PasswordNeverExpires $true `
           -ChangePasswordAtLogon $false

# Verify user creation
Get-ADUser -Identity brich
```

### Bulk User Creation
```powershell
# Import users from CSV
$users = Import-Csv "C:\users.csv"

foreach ($user in $users) {
    New-ADUser -Name "$($user.FirstName) $($user.LastName)" `
               -GivenName $user.FirstName `
               -Surname $user.LastName `
               -SamAccountName $user.Username `
               -UserPrincipalName "$($user.Username)@keenan.local" `
               -Path "CN=Users,DC=keenan,DC=local" `
               -AccountPassword (ConvertTo-SecureString $user.Password -AsPlainText -Force) `
               -Enabled $true
}
```

## 🛠️ Common User Management Tasks

### Modify User Properties
```powershell
# Add email address
Set-ADUser -Identity brich -EmailAddress "bob.rich@keenan.local"

# Add phone number
Set-ADUser -Identity brich -OfficePhone "555-1234"

# Add department
Set-ADUser -Identity brich -Department "IT"

# Add job title
Set-ADUser -Identity brich -Title "Systems Administrator"
```

### Reset User Password
```powershell
# Reset password
Set-ADAccountPassword -Identity brich -Reset -NewPassword (ConvertTo-SecureString "NewP@ssw0rd!" -AsPlainText -Force)

# Force password change at next logon
Set-ADUser -Identity brich -ChangePasswordAtLogon $true
```

### Disable/Enable User Account
```powershell
# Disable account
Disable-ADAccount -Identity brich

# Enable account
Enable-ADAccount -Identity brich

# Check account status
Get-ADUser -Identity brich | Select-Object Enabled
```

### Add User to Groups
```powershell
# Add user to security group
Add-ADGroupMember -Identity "IT Admins" -Members brich

# Verify group membership
Get-ADPrincipalGroupMembership -Identity brich
```

## 📊 User Account Lifecycle

### 1. Provisioning (Creation)
```
✅ Create user account
✅ Set initial password
✅ Configure account properties
✅ Assign to appropriate groups
✅ Set permissions and access
```

### 2. Modification (Updates)
```
✅ Update contact information
✅ Change department/title
✅ Modify group memberships
✅ Adjust permissions
✅ Reset passwords
```

### 3. Deprovisioning (Removal)
```
✅ Disable account immediately
✅ Remove from security groups
✅ Revoke access permissions
✅ Archive mailbox (if applicable)
✅ Delete account after retention period
```

## 🔍 Verification Commands

### Check User Exists
```powershell
# Verify user in AD
Get-ADUser -Identity brich

# Check user details
Get-ADUser -Identity brich -Properties *

# Search by name
Get-ADUser -Filter "Name -like '*Bob Rich*'"
```

### Test User Login
```powershell
# Test credentials
$cred = Get-Credential -UserName "keenan\brich"
Test-Connection -ComputerName DC01 -Credential $cred
```

## 🚨 Troubleshooting

### User Cannot Login
**Problem**: User account created but cannot authenticate

**Solutions**:
```
1. Verify account is enabled
   Get-ADUser -Identity brich | Select-Object Enabled

2. Check password is set correctly
   Set-ADAccountPassword -Identity brich -Reset

3. Verify logon hours
   Get-ADUser -Identity brich -Properties LogonHours

4. Check account expiration
   Get-ADUser -Identity brich -Properties AccountExpirationDate
```

### User Not Appearing in ADUC
**Problem**: User created but not visible

**Solutions**:
```
1. Refresh ADUC console (F5)
2. Check correct OU/container
3. Verify replication status
   repadmin /showrepl
4. Check for filter settings in ADUC
```

### Password Policy Conflicts
**Problem**: Cannot set password as configured

**Solutions**:
```
1. Check domain password policy
   Get-ADDefaultDomainPasswordPolicy

2. Verify fine-grained password policy
   Get-ADUserResultantPasswordPolicy -Identity brich

3. Ensure password meets complexity requirements
```

## 📈 Best Practices

### Naming Conventions
```
✅ Consistent username format across organization
✅ Clear, professional display names
✅ Documented naming standards
✅ Avoid special characters in usernames
✅ Consider future scalability
```

### Account Management
```
✅ Use Organizational Units (OUs) for organization
✅ Implement Group Policy for user settings
✅ Regular account audits
✅ Disable unused accounts promptly
✅ Document account creation procedures
```

### Security
```
✅ Enforce strong password policies
✅ Implement account lockout policies
✅ Use least privilege principle
✅ Regular security group reviews
✅ Enable audit logging
```

## 🎯 Real-World Applications

### Enterprise Scenarios
- **New Employee Onboarding** - Create accounts for new hires
- **Contractor Management** - Temporary accounts with expiration
- **Service Accounts** - Non-expiring passwords for applications
- **Test Accounts** - Development and testing environments
- **Administrative Accounts** - Separate admin credentials

### Integration Points
- **Email Systems** - Exchange/Office 365 mailbox creation
- **File Servers** - Home directory and shared folder access
- **Applications** - SSO and LDAP authentication
- **VPN Access** - Remote access authentication
- **Workstation Login** - Domain computer authentication

## 📚 Additional Resources

- [Active Directory Users and Computers](https://docs.microsoft.com/windows-server/identity/ad-ds/get-started/adac/introduction-to-active-directory-administrative-center-enhancements--level-100-)
- [New-ADUser PowerShell Cmdlet](https://docs.microsoft.com/powershell/module/activedirectory/new-aduser)
- [Active Directory Best Practices](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory)
- [User Account Management](https://docs.microsoft.com/windows-server/identity/ad-ds/manage/understand-default-user-accounts)

## 👨‍💻 Author

**Keenan Kelly**

This project demonstrates practical Active Directory user management skills essential for enterprise IT administration and identity management roles.

## 📄 Related Projects

- [Configuring Active Directory](https://github.com/keenannkelly/Configuring-Active-Directory) - AD DS installation and setup
- [Creating a VM on AWS](https://github.com/keenannkelly/Creating-VM-on-AWS) - Windows Server deployment
- [EC2 RDP Connection](https://github.com/keenannkelly/EC2-RDP-Connection) - Remote server access

---

*Demonstrating enterprise identity and access management with Active Directory user administration*
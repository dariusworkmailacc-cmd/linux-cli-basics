# Windows NTFS ACL & Temporary Access Lab (PowerShell)

## Goal
Practice managing local users,groups,permissions,inheritance and 
time-limited scheduled tasks

## What I learned

## 1. Users,Groups and Permissions
- Using groups to setup temporary access 
- Basics of ACL

### 2. Local User and Group Management
- Created local users
- Created local group
- Added users to the group
- verified if the steps were done and i could see the users.

Best practice is to verify if the command went through as intended.

### 3. NTFS Permissions with icacls
- Used icacls to grant and remove permissions
- Learned that icacls syntax is very strict
- Permissions were granted to the group, not users.

Permission format used:
Group: (OI)(CI)(M)

- OI = Files inherit
- CI = Folders inherit
= M = Modify

### 4. Inheritance
- Permissions set on a parent directory with inheritance go directly
to files and folders, removing the issue of permissions needing to be 
readded individually
- Explicit permissions override inherited ones.
- Removing permissions on a child does nothing if they are inherited 
from a parent

Parent permissions flow downward unless inheritance is broke

### 5. Access removal

- Used iccalcs /remove to remove a group from an ACL
- remove deletes ACEs only
- Users and groups are not deleted when permission is removed.
- ACL changes were verified after executing.

### 6. Temporary Access Concept

- NTFS permissiosn do not support expiration
- Temporary access is enforced through automation.
- TIme-limted access = grant permissions + scheduled removal

### 7. Schedules Tasks (PowerShell)

- A scheduled task consists of:
 - Action (what runs)
 - Trigger (when it runs)
 - Priveleges (who runs it)
 - Action and trigger must be defined separately.
 - Powershell scheduled tasks were created using:
  - New-ScheduleTaskAction
  - New-ScheduleTaskTrigger
  - Register-ScheduleTask

### 8. Automated ACL Removal

 - Scheduled task executed PowerShell with icacls
 - Task was manually triggered to confrim behavior
 - Verified that group permissions were removed from the folder ACL
 
### 9. Cleanup

- Scheduled task was removed
- Local users were deleted
- Local group was deleted.
- Test directory was deleted.

Order of commands matter to avoid problems with orphaned access and automation.



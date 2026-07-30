

![alt text](class2-screenshots/2a.png)


![alt text](class2-screenshots/2b.png)


![alt text](class2-screenshots/2c.png)


![alt text](class2-screenshots/2d.png)


![alt text](class2-screenshots/2e.png)




---

### Overall Security Skills Gained From Class-02

After completing this lab, I can demonstrate knowledge of:

✅ IAM user management

✅ IAM group management

✅ Least privilege implementation

✅ AWS managed policies

✅ Permission troubleshooting

✅ Role-based access control

✅ AWS CLI authentication

✅ Access key management

✅ Permission boundaries

✅ Cloud security governance



---

# Class-02

**Date:** 07/06/26

### Module 04: Identity and Access Management

* **IAM (Identity and Access Management):** Create and manage Users, Groups, Roles, and permissions.

┌───────────────┐          ┌─────────┐
                      │               │◄─────────┤ Users   │ Group
                      │               │          └─────────┘
                      │               │
  ┌──────────┐        │               │
  │ Root     ├───────►│  AWS Account  │
  └────┬─────┘        │               │
       │              │               │
       │ Users        │               │
       ▼              │               │          ┌─────────┐
  ┌──────────┐        │               │◄─────────┤ Users   │ Group
  │ Admin    ├───────►│               │          └─────────┘
  └────┬─────┘        └───────▲───────┘
       │                      │
       │                      │
       ▼                      │
 Admin create Users   ┌───────┴───────┐
                      │ User User User│

---

## 1. AWS Management Console User *(User through Browser)*

### Users Types

* AWS Management Console Access User
* CLI User

### Least Privilege Principle

*(Richard & John, newly joined the company)*

#### Assigned Permissions:

* **EC2 ReadOnly** Permission
* **S3 ReadOnly** Permission
* **CloudWatch Read** Permission


┌─────────────────────────┐
         │ Richard                 │
         │   │                     │
         │   ▼                     │
         │  User                   │
         │                         │
         │ John                    │
         │   │                     │
         │   ▼                     │
         │  User                   │
         └─────────────────────────┘
                      ▲
                      │
                      │         ┌───────────┐         ┌────────────────┐
 Root ──────► Admin ──┴────────►│   Users   │◄────────┤ IT Department  │
                                └───────────┘ Group   └───────┬────────┘
                                                              │
                                                              ├─► EC2 Full
                                                              ├─► S3 Full
                                                              ├─► RDS Full
                                                              ├─► ECS Full
                                                              ├─► EKS Full
                                                              └─► EFS Full

                                ┌───────────┐
                                │   Users   │ Group
                                └───────────┘

--------------xxxxxxxxxx------------




![alt text](class2-screenshots/2f.png)



![alt text](class2-screenshots/2g.png)




---

**(2) Programmatic Access User** (without Browsers)

* CLI, SDKs, SDKs, APIs others tools

CLI → Command Line Interface

CDKs → Cloud Development Kit

SDKs → Software Development Kit

APIs → Application Programming Interface

→ **Types of Users** 1. AWS Management Console User (Users through Browsers)

2. Programmatic Access User (Without Browsers)

* CLI, CDKs, SDKs, APIs (Through Command Line Interface CLI)

---

→ **Permission Boundary** ```
Permission Boundary
│
├─── EC2 Read-Only ──────────┐
│                            │
(for Restrict user)                   ▼
┌───────────────┐                  EC2 Full
│  User   User  │                  S3 Full
│    \     /    │                  RDS Full
│     User      ├─────────────────►ECS Full
│    /     \    │                  EKS Full
│  User   User  │                  EFS Full
└───────┬───────┘
│
└─► for particular user

```


```

Permission Boundary
│
├─── EC2 Read-Only ──────────┐
│                            │
(for Restrict user or                 ▼
entire group)               ┌───────────┐ Group              EC2 Full
│ User User │                    S3 Full
│           ├───────────────────►RDS Full
│ User User │                    ECS Full
└─────┬─────┘                    EKS Full
Group │                          EFS Full
│
└─► for entire group
│
▼
all users in this group

```

```

-------------xxxxxxxxxxxxxx----------


![alt text](class2-screenshots/2h.png)


![alt text](class2-screenshots/2i.png)



---

→ **LAB for AWS Management Console User** *(Users through Browser)* **Step 1 :-** IAM ──► (Search - IAM)

↓

IAM Users

↓

Create User

→ **User details** → User name

* ProdAdmin

☑ Provide user access to the AWS Management console

→ Console password

→ Custom password

* Admin@12345

→ **Set Permissions** → Permissions options

→ Attach policies directly

→ Permissions policies

* (search)

✓ AdministratorAccess

→ **Tags** → Key

* Project

→ Value

* Training

→ **Download .csv file** (for Username & password)


--------------xxxxxxxxxxxxx-----------

![alt text](class2-screenshots/2j.png)



![alt text](class2-screenshots/2k.png)

---

**Step 2 :- Console sign in details** → **Console sign-in-URL** * ─────────────────────

→ **Username** * ProdAdmin

→ **Console Password** * ─────────────────────

(copy user link)

│

└─────────────┐

▼

**Step 3 :- Open New tab (browser)** → **Copy and paste User link** ↓

**login through ProdAdmin** **Step 4 :-** IAM

↓

IAM Users

↓

ProdAdmin

↓

→ **Permission Policies** * AdministratorAccess

**Step 5 :- In ProdAdmin Account** → IAM

↓

IAM Users

↓

Create User

→ **User details** → **User name** * Richard

✓ Provide User access to the AWS Management console


-------------xxxxxxxxxxxxx---------



![alt text](class2-screenshots/2l.png)



![alt text](class2-screenshots/2m.png)



---

→ **Console password** → **Custom password** * Richard@123

→ **Set permissions** → **permission options** * Attach policies directly

→ **permission policies** * EC2ReadOnlyAccess ✓

* S3ReadOnlyAccess ✓

* CloudWatchReadOnlyAccess ✓

*{ This policies given to Richard user by an ProdAdmin (Administrator) }*

→ **Tags** → **Key** * Project

→ **Value** * Training

→ **Download .csv file** *(for Username & Password)* ---

**Step 6 :-** **Create User John same as it is as Richard and given to these three permissions.** → **permission policies** * EC2ReadOnlyAccess ✓

* S3ReadOnlyAccess ✓
* CloudWatchReadOnlyAccess ✓

*{ This policies given to John user by an ProdAdmin (Administrator) }*

```
                       Root User (me)
                             │
                             │ create
                             ▼
                 ProdAdmin (Administrator)
                             │
                             │ create
             ┌───────────────┴───────────────┐
             ▼                               ▼
          Richard                          John

```

-------xxxxxxxxxx------------


![alt text](class2-screenshots/2n.png)


![alt text](class2-screenshots/2o.png)


---

**Step 7 :-** In New tab (browser)

↓

→ Copy and paste User link

↓

Log in through Richard.

→ Create EC2 Instance

→ EC2

↓

Launch Instance

*{ Richard cannot create EC2 Instance, Not have a permission, No Rights ❌ }*

---

**Step 8 :- In ProdAdmin Account** → Create a EC2 Instance (Linux server)

* Webserver

→ **VPC** * Default VPC

→ **Subnet** * 1a

→ **Auto-Assign Public IP** * Enable

→ **Security Group** → WEB-SG

* Allow SSH ✓
* Allow HTTP ✓

---

**Step 9 :- In ProdAdmin Account** ↓

IAM

↓

IAM Users

↓

Richard

↓

→ **Permission Policies** * AmazonEC2ReadOnlyAccess ✓

* AmazonS3ReadOnlyAccess ✓
* CloudWatchReadOnlyAccess ✓

} Remove this policies


------------xxxxxxxxxxxxxx------------


![alt text](class2-screenshots/2p.png)



![alt text](class2-screenshots/2q.png)


---

→ **Remove** → **Add permissions** → **Attach permissions** * EC2FullAccess

* S3FullAccess

* CloudWatchFullAccess

*{ Add this policies to Richard User }*

---

**Step 10 :- In Richard Account** ↓

EC2

→ **Webserver** ──► **stop** ──► **yes ✓** *{ bcz Richard have a EC2 Full Access }*

---

**Step 11 :- In ProdAdmin Account** ↓

IAM

↓

IAM Usergroups

↓

Create group

↓

→ **User group name** * IT-Group ✓

→ **Attach permission policies** * EC2FullAccess ✓

* S3FullAccess ✓
* RDSFullAccess ✓
* EFSFullAccess ✓
* ECSFullAccess ✓
* EKSFullAccess ✓
* CloudWatchFullAccess ✓
* VPCFullAccess ✓

*{ Give a permission to IT-Group }*



------------xxxxxxxxxxx----------


![alt text](class2-screenshots/2r.png)


![alt text](class2-screenshots/2s.png)


![alt text](class2-screenshots/2t.png)




---

```
             ProdAdmin (Administrator)
                         │
                         │ create
         ┌───────────────┴───────────────┐
         ▼                               ▼
    User-IT-01                      User-IT-02

```

**Step 12 :- In ProdAdmin Account** ↓

→ **IAM** ↓

**IAM Users** ↓

→ **Create User** → **User details** → **User name** * User-IT-01

* User-IT-02

✓ Provide User access to the AWS Management console

→ **Console password** → **Custom password** * IT1@12345

* IT2@12345

→ **Set permissions** → **permissions options** * Add user to group

→ **User groups** * IT-Group ✓

```
           ProdAdmin (Administrator)
                       │
                       │ Create Group
                       ▼
                   IT-Group
                       │
                       │ User Members
       ┌───────────────┴───────────────┐
       ▼                               ▼
  User-IT-01                      User-IT-02
       ▲                               ▲
       │          Permission ✓         │
       └───────────────────────────────┘

```

---

**Step 13 :-** IAM

↓

IAM Usergroup

↓

IT-Group

↓

→ **Users** → User-IT-01

→ User-IT-02

*{ member users of ITGroup all permission }*

→ **Permissions** → **permission policies** * ─────────────────────

*{ all this permissions given to User1 & User2 individually }*

---------xxxxxxxxx----------


![alt text](class2-screenshots/2u.png)



![alt text](class2-screenshots/2v.png)



---

→ **LAB for Programmatic Access User (without Browsers)** **Through Command Line Interface CLI.** **Step 1 :- How to prepare laptop for CLI** Google ─────────────► install aws cli on windows

↓

Windows ✓

↓

① Download and run the

AWS CLI MSI installer

for Windows

↓

→ Click on link and download

**Step 2 :- Restart PC** **Step 3 :- Command Prompt** `aws --version` *(for check installation)* `aws configure` *(CMD connect to AWS)* AWS Access Key ID :- ─────────

AWS Secret Access Key :- ─────

*(Copy & paste from Root Key File or Excel File)* Default region name :- ap-south-1 *(for Mumbai Region)* Default output format :- json

```
                 Output format
                       │
       ┌───────────────┼───────────────┐
       ▼               ▼               ▼
     text            table            json

```

------------xxxxxxxxxxxx--------



![alt text](class2-screenshots/2w.png)


![alt text](class2-screenshots/2x.png)




Here is the transcribed text from your image:

---

**Step 4 :- In ProdAdmin Account** → **Create a CLI User** → **IAM** ↓

**IAM Users** ↓

→ **Create User** → **User Name** * User-CLI-01

☒ Provide User access to the AWS Management console

→ **Set permissions** → **permission options** * Attach policy directly

→ **permission policies** * Administrator Access

```
                      CLI User
                         │
                         ▼
              ✓ Admin (Administrator)

```

---

**Step 5 :- IAM** ↓

**IAM Users** ↓

→ **User-CLI-01** ↓

**Security credentials** ↓

→ **Create access key** → **Use case** * Command Line Interface (CLI) ✓

→ **Access key** * ─────────────────────

→ **Secret Access Key** * ─────────────────────

→ **Download .csv file ✓**


-----------xxxxxxxxxxxx-----------



![alt text](class2-screenshots/2y.png)



---

**Note :- ► Best Practices** **Access key and Secret Access Key of a User can be stored in AWS Secrets Manager or in Parameter Store AWS Systems Manager**

---

**Step 6 :-** `aws s3 ls`

`aws s3 mb s3://mybucket`

`aws s3 ls`

`dir *.png`

`dir *.pdf`

`dir`

`aws s3 cp newkey.pem s3://mybucket` *(Upload file in bucket)* `aws s3 ls s3://mybucket` *(for check objects in bucket)* `aws s3 rb s3://mybucket --force` *(for delete bucket)* `cls`

*{ CLI User ──► Administrator }* *{ Full access to create bucket }*

---------xxxxxxxxxxxx--------


![alt text](class2-screenshots/2z.png)


---

→ **LAB for Permission Boundary**

**Step 7 :- In ProdAdmin Account** → **IAM** ↓

**IAM Users** ↓

→ **Richard** → **Permissions** → **Add permissions** → **Attach policies directly** * RDSFullAccess ✓

* EFSFullAccess ✓

→ **Permission boundary** → **Set permissions boundary** * EC2ReadOnlyAccess ✓

---

**Step 8 :- Log in through Richard Account** → **EC2** ↓

**Webserver** ──► **(Stop)** ↓

**(Start)** ──► **(NO ❌)** *(Permission boundary Not allow ❌)* ```
Richard
│
┌──────────────┴──────────────┐
▼                             ▼
Permission                Permission Boundary
│                             │
▼                             ▼
EC2FullAccess                 EC2ReadOnly

```

```


__________XXXXXXXXXX___________



## post lab cleanup


Your Class-02 documentation is already structured well for a GitHub lab repository. For **post-lab cleanup**, you should document it because in a real AWS security role, cleanup is part of **cloud governance, cost control, and security hygiene**. Even if you did not face errors, documenting cleanup proves you understand the complete lifecycle: **create → test → validate → remove resources**.

Add this section at the end of Class-02:

---

# Post Lab Cleanup — Class-02 IAM Security Lab

## Purpose

After completing IAM experiments, remove unnecessary users, access keys, policies, and resources to maintain AWS account security and avoid unauthorized access.

---

# Cleanup Order

```text
                 AWS IAM LAB CLEANUP

                         │

                         ▼

        1. Remove Access Keys (CLI Users)

                         │

                         ▼

        2. Delete IAM Users

                         │

                         ▼

        3. Delete IAM Groups

                         │

                         ▼

        4. Remove Custom Policies / Permissions

                         │

                         ▼

        5. Terminate EC2 Resources

                         │

                         ▼

        6. Delete S3 Test Bucket

```

---

# Step 1: Remove CLI Access Keys

### Navigate:

```
IAM
 │
 └── Users
       │
       └── User-CLI-01
              │
              └── Security Credentials
                     │
                     └── Access Keys
                            │
                            └── Delete Access Key
```

### Reason:

Access keys provide programmatic access to AWS.

Removing unused keys prevents:

* Unauthorized AWS CLI access
* Credential leakage
* Accidental resource creation

---

# Step 2: Delete IAM Users

Delete temporary users created during the lab.

Users:

```
ProdAdmin

Richard

John

User-IT-01

User-IT-02

User-CLI-01
```

### Navigation:

```
IAM
 │
 └── Users
        │
        └── Select User
                │
                └── Delete User
```

### Reason:

Unused IAM accounts increase security risk and violate the principle of least privilege.

---

# Step 3: Delete IAM Groups

Delete the test group:

```
IT-Group
```

Navigation:

```
IAM

 ↓

User Groups

 ↓

IT-Group

 ↓

Delete Group
```

### Reason:

Groups should only exist when actively managing users and permissions.

---

# Step 4: Remove Permission Boundary

If a permission boundary was created:

```
IAM

 ↓

Users

 ↓

Richard

 ↓

Permissions

 ↓

Remove Permission Boundary
```

### Reason:

Temporary security restrictions created for testing should be removed after validation.

---

# Step 5: Remove Test EC2 Instance

The EC2 instance created during permission testing:

```
Webserver
```

Navigation:

```
EC2

 ↓

Instances

 ↓

Select Webserver

 ↓

Instance State

 ↓

Terminate Instance
```

### Reason:

EC2 instances continue generating costs if left running.

---

# Step 6: Delete S3 Test Bucket

Bucket created during CLI testing:

```
mybucket
```

Command:

```bash
aws s3 rb s3://mybucket --force
```

or AWS Console:

```
S3

 ↓

Select Bucket

 ↓

Empty Bucket

 ↓

Delete Bucket
```

### Reason:

Test buckets may contain uploaded files or sensitive data.

---

# Step 7: Verify Remaining IAM Resources

Final verification:

```
IAM Dashboard

Check:

✓ No unnecessary users

✓ No unused access keys

✓ No temporary groups

✓ No excessive permissions

✓ No unused policies

```

---

# Security Practice Learned

By performing cleanup after the IAM lab, I learned:

* Identity lifecycle management
* Removal of unused credentials
* Cloud account hygiene
* Least privilege maintenance
* Prevention of unauthorized AWS access
* AWS resource cost management

---


## Lab 2: Create Read-Only Users (Richard & John)
AWS Concept Learned:
Least Privilege Principle
IAM Managed Policies
Read-only access control
AWS Policies Used:
EC2ReadOnlyAccess
S3ReadOnlyAccess
CloudWatchReadOnlyAccess
Real-World Problem:

Developers or auditors need to view resources but should not modify production infrastructure.



## Lab 3: Testing User Permission Restrictions
AWS Concept Learned:
Permission validation
Access denied troubleshooting
IAM policy enforcement
Real-World Problem:

A user attempts an action that is outside their job responsibility.

Example:

Richard tries to create an EC2 instance but receives an access denied error.




## Lab 4: Modify User Permissions (Read Only → Full Access)
AWS Concept Learned:
Policy modification
Permission updates
Privilege management
Real-World Problem:

An employee receives a promotion and requires additional AWS permissions.




## Lab 5: IAM Groups (IT-Group)
AWS Concept Learned:
Role-based access control (RBAC)
Group-based permission management
Policies Applied:
EC2FullAccess
S3FullAccess
RDSFullAccess
EFSFullAccess
ECSFullAccess
EKSFullAccess
VPCFullAccess
Real-World Problem:

Managing permissions individually for hundreds of employees is difficult.

Solution:

Create groups and assign permissions once.



## Lab 6: IAM Programmatic Access User (AWS CLI)
AWS Concept Learned:
Access Keys
AWS CLI authentication
Programmatic access
Commands Practiced:
aws configure

aws s3 ls

aws s3 mb s3://mybucket

aws s3 cp file.txt s3://mybucket

aws s3 rb s3://mybucket --force
Real-World Problem:

Applications and automation tools need AWS access without logging into the AWS Console.




## Lab 7: Permission Boundary
AWS Concept Learned:
Permission boundaries
Security guardrails
Privilege escalation prevention
Real-World Problem:

An administrator gives a user powerful permissions, but security policy should limit the maximum permission level.

Example:

User Permission:

EC2FullAccess

Permission Boundary:

EC2ReadOnlyAccess

Result:

User cannot perform actions beyond the boundary.
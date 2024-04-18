
# Basic concepts

**Security**: A system is secure when it acts as expected to:
- Allows each user to perform operations to which they're authorized
- Prevents each user from performing operations that are not authorized

**Goals of security**:
- Confidentiality
- Integrity
- Availability

**Threats to confidentiality**:
- Illegal access to the system (*usurpation*), being able to obtain copies of data and stored programs accessible to the legal user
- Access to communications (*sniffing*), being able to obtain copies of messages or files exchanged between machines
- Physical access to the machine or storage device, being able to make copies or stealing the hardware
- Logical or physical access to data and program backups
- Access to data/programs through the use of social engineering
- Accessing data/programs by using malware

**Threats to integrity**:
- Improper access to the system (usurpation), being able to modify data and stored programs accessible to the legal user
- Access to communications (sniffing, man in the middle), being able to access messages or files exchanged between machines, modifying them or inventing new ones
- Physical access to the machine or storage device, being able to directly modify the stored data/programs
- Changing data/programs through the use of social engineering
- Using malware

**Threats to availability**:
- System saturation by using malware (worms, bacteria, ...)
- System saturation through DoS attacks
- Elimination or failure of system of communications hardware
- Shutting down the system
- Suppression of system power or communications devices

**Threat**: A set of circumstances whose likelihood of occurring is significant

**Vulnerability**: Weakness (technical, physical, procedural, human, ...) in the security of a system

**Exploit**: Technique that allows you to exploit a vulnerability to launch an attack

**Control or countermeasure**: Protective measure that eliminates or reduces a risk. Maybe:
- Prevention
- Hindrance
- Detour
- Detection
- Recovery
They can be provided by the Operating System or other components (technological, human, organizational)

# Security and the Operating System

The OS must provide mechanisms for:
- Avoid vulnerabilities in its operation
- Perform effective authentication of users accessing the system
- Effectively control resource usage
- Incorporate measures against harmful software (*malware*)

## Updates

Any newly installed operating system must be upgraded immediately:
- Since the date of system distribution, it is likely that vulnerabilities have been discovered in the system or in the applications installed in it
- The available security updates must therefore be downloaded and installed

All operating system currently have tools that make the task easier: Windows Update or apt-get, rpm, ... , on Linux.
After the initial update, an update schedule must be set to keep the system safe from *exploits*. Consider that you can NOT be aware of ALL vulnerabilities

![[Pasted image 20240418093336.png]]

## System configuration

In addition to updating the system, special care must be taken with the initial **configuration** of the system. 

1 $\rightarrow$ In particular, it is important to install only those services that will be used. Unused services are an additional danger:
 - They don't offer anything to users
 - Provide new fronts of attack
 - No one is usually aware of them, so any attack can spend a lot of unnoticed time

2 $\rightarrow$ In addition, you have to configure the limits (disk, memory, processes, etc.) that each user can use to avoid the hoarding of resources by some user

3 $\rightarrow$ Privileges must be assigned to users very carefully (*minimum privilege*):
- Do not allow access to *sensitive* programs (system configuration programs, user management programs, etc.)
- Don't allow normal users to install apps
- Restrict the use of resources (such as the network)

4 $\rightarrow$ Do not enable un-encrypted communications

5 $\rightarrow$ Restrict the machines from which sensitive operations can be performed (management access, backups, etc.)

6 $\rightarrow$ Take into account specific system-specific precautions

# User authentication

You must make sure:
- Unauthorized users will **NOT** be able to access the system
- Authorized users **CAN** access the system

User authentication can be based on:
- Something the user **knows**: *password, pin*, ...
- Something the user **has**: magnetic card, key, ...
- Who **is** the user: biometrics
- Several of the above

## Password authentication

Most commonly used mechanism because it does not require special hardware, the False Rejection Rate (FRR) is null and the False Acceptance Rate (FAR) is also null, but it's the most easily attackable:
- Anyone can try to find out passwords
- Passwords must be stored in the system, then someone can try to get them (To solve this problem, they're stored encrypted, preferible with a non-reversible encryption)
- Regardless of whether you get the encrypted password file or not, you can try to find out:
	- Using social engineering:
		- Obtaining them directly from the user
		- Using user-related information
	- By "brute force" attack

Some precautions that can be taken:
- Ensure that all users have strong passwords
- Do not leave any account without a password
- Do not store passwords in files accessible by normal users
- Do not store passwords that are unencrypted or with reversible encryption
- Do not leave open sessions unattended
- Block accounts with excessive unsuccessful access attempts
- Monitor log files to locate suspicious access
- Disable unused accounts
- Rename known accounts (administrator, guest, ...)

Some issues depends on the user education and/or the administrator; others can be monitored by technical means

## Authentication using physical tokens

Users are identified by something they own like a magnetic card. It's easily usable:
- Requires special hardware, but it's not usually very expensive
- The False Rejection Rate (FRR) is null
- The False Acceptance Rate (FAR) is also null

Almost all OS provide mechanisms to incorporate them as an access control element

## Biometric authentication

Users identify themselves with some feature of their own like fingerprints, iris... . It's not used very often:
- Requires special hardware, relatively expensive
- Fase Rejection Rate (FRR) may become unacceptable
- False Acceptance Rate (FAR) can be dangerously high
- Manufacturers often adjust the acceptance threshold by preferring to reject legal users than accept unauthorized users
- Almost all OS provide mechanisms to incorporate them as an access control element

## Other mechanisms

- Using a private - public key pair or user certificates:
	- In this case it can only be accessed from machines that have installed the private part of the user's key
- Using "one time passwords"
- Using two-factor authentication

# Resource protection

## The access matrix

In general, an access matrix should be managed as the primary protection model. Rows: **Clients**; Columns: **Resources**

M\[ i , j ] - Client permissions i on resource j

There're two implementations of this matrix:
- **Access control lists (by columns)** $\rightarrow$ Each resource saves the list of clients with their permissions (vector column of the array)
- **Capabilities (per row)** $\rightarrow$ Each client saves the list of capabilities (resource+permissions) that it has available

## Access control lists

When a customer makes a request about a resource the OS (protection mechanism) checks whether the client is in the resource ACL

>[!ACL inconveniences]
>- Lack of scalability:
>		Many customers $\rightarrow$ Very large ACL
>		Many resources $\rightarrow$ Many ACL
>	
>- Solution:
>		Group of clients $\rightarrow$ Decreases the number of ACL entries
>		Group of clients $\rightarrow$ Decreases the number of ACL

## Protection domains

Each OS determines who is granted or not to execute some type of access to resources. Unix distinguishes three domains: owner, group and other users.
In Unix, with the ACL package installed, you can include n domains: independent users in any number, groups in any number and "other"
In Windows, you can include n domains: standalone users in any number and groups in any number

## Types of access

Each OS determines between which types of access it distinguishes, being able to guarantee or deny them. In Unix, there are three types: read, write and run. The combination of file permissions and the directories that contain them gives more flexibility (but little more)

### Windows

Basic operations by domain:
- Control Total
- Modify
- Reading and executing
- Show folder content
- Read
- Write

Advanced operations per domain
- Control Total
- Browse Folder/Run File
- List folder/read data
- reading attributes
- extended reading attributes
- create files/write data
- create folder/append data
- writing attributes
- extended writing attributes
- delete files/folders
- Remove
- reading permissions
- change permits
- take possession

## Capabilities

**Access control mechanism with capabilities**. When a customer makes a request about a resource:
- The client presents the capacity over the resource
- The OS (protection mechanism) checks the capacity for the requested operation. Analog to cinema entry
- No ACL or similar should be accessed

![[Pasted image 20240418133822.png]]


# Malware

There're many types of malware:
- Trojan horses
- Viruses, worms, bacteria, ...
- Rootkits
- Logic bombs, traps, back doors, ...

Against them, there are several techniques that can be used:
- Firewalls
- Antivirus
- Jailing
- IDS (Intrusion Detection Systems)
- User education:
	- Signed programs
	- Opening file attachments
	- ...

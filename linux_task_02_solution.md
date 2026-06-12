# Linux Assignment 2: Users, Groups, and Permissions (Completed by Kripa SB)

## Section A: User Identification

**Execution Commands:**
```bash
whoami
id
cat /etc/passwd
```

**Responses:**
1. **Current Username**: *(The output of the `whoami` command will show your logged-in user).*
2. **UID Explained**: The User ID (UID) is a numerical value assigned by Linux to uniquely identify a specific user account. 
3. **GID Explained**: The Group ID (GID) is the unique number for the user's primary group.
4. **Contents of `/etc/passwd`**: This configuration file acts as a database for all registered users on the system. It holds details like the username, UID, GID, home directory path, and the default shell.

*(Remember to capture a screenshot of your terminal here!)*

## Section B: Creating Groups and Users

**Group Creation:**
```bash
sudo groupadd interns
sudo groupadd cyberteam
```

**User Creation:**
```bash
sudo useradd -m student1
sudo useradd -m student2
sudo useradd -m student3
```

**Assigning Memberships:**
```bash
sudo usermod -a -G interns student1
sudo usermod -a -G cyberteam student2
sudo usermod -a -G interns,cyberteam student3
```

**Verification Step:**
```bash
groups
id student1
id student2
```
*(Screenshot required for verification)*

## Section C: File Ownership Modification

**Creating the Environment:**
```bash
mkdir CyberSecurity_Project
cd CyberSecurity_Project
touch report.txt notes.txt credentials.txt
```

**Viewing Default Ownership:**
```bash
ls -l
```

**Transferring Ownership:**
```bash
sudo chown student1 report.txt
```

**Documentation:**
- **Original Owner:** (Your default username)
- **New Owner:** student1
- **Command Used:** `sudo chown student1 report.txt`

## Section D: Modifying File Permissions

**File Setup:**
```bash
touch security_policy.txt
ls -l security_policy.txt
```

**Applying Permission Changes:**

- **Read Only** (r--r--r--):
  ```bash
  chmod 444 security_policy.txt
  ```
  *(Take screenshot)*

- **Read & Write** (rw-rw-r--):
  ```bash
  chmod 664 security_policy.txt
  ```
  *(Take screenshot)*

- **Full Access** (rwxrwxrwx):
  ```bash
  chmod 777 security_policy.txt
  ```
  *(Take screenshot)*

## Section E: Permission Analysis Breakdown

* **755**: 
  * Owner: Read/Write/Execute
  * Group: Read/Execute
  * Others: Read/Execute
  * **Use Case**: Typically used for directories or executable scripts that everyone needs to be able to access or run, but only the creator can edit.

* **644**: 
  * Owner: Read/Write
  * Group: Read Only
  * Others: Read Only
  * **Use Case**: The default for most standard files (like text documents). Anyone can read the contents, but only the owner has modification rights.

* **777**: 
  * Owner: Read/Write/Execute
  * Group: Read/Write/Execute
  * Others: Read/Write/Execute
  * **Use Case**: Used for public folders where all users need unrestricted access to create, modify, and delete files. It is rarely used for individual files due to security vulnerabilities.

* **600**: 
  * Owner: Read/Write
  * Group: No Access
  * Others: No Access
  * **Use Case**: Used for securing confidential files, such as cryptographic keys (`id_rsa`), ensuring no other user on the system can view them.

* **700**: 
  * Owner: Read/Write/Execute
  * Group: No Access
  * Others: No Access
  * **Use Case**: Used for private, restricted directories (like a user's `~/.ssh` folder) to prevent anyone else from entering or listing the contents.

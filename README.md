<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Prepare
- Step 2: Create Folders
- Step 3: Set Share Permissions
- Step 4: Test Access
- Step 5: Create a Security Group
- Step 6: Set Folder Permissions for the Security Group
- Step 7: Test Access as a Normal User
- Step 8: Add User to the Security Group
- Step 9: Test Access as the User (Again)

<h2>Actions and Observations</h2>

<p>  
file:///C:/Users/Cherylda%20Moses/Downloads/81308.jpg 
</p>
<p>

**Prepare:**
- Ensure you have access to a Windows Server (DC-1) and a Windows Client (Client-1) within the same domain.

**Create Folders**
- On DC-1, create the necessary folders on the C:\ drive, such as "read-access," "write-access," "no-access," and "accounting."

**Set Share Permissions:**
- Share each folder with specific permissions:
    
     - "read-access" for "Domain Users" with "Read" permission.
     - "write-access" for "Domain Users" with "Read/Write" permission.
     - "no-access" for "Domain Admins" with "Read/Write" permission.

- Leave "accounting" for now.

**Test Access:**
- On Client-1, try to access the shared folders:

- Determine which folders you can access.

- Find out where you can create files.

- Evaluate the permissions and access results.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

**Create a Security Group:**
- On DC-1, create a new security group in Active Directory, e.g., "ACCOUNTANTS."

**Set Folder Permissions for the Security Group:**
- Assign specific folder permissions for the "ACCOUNTANTS" group:

- Set "Read/Write" permissions for the "accounting" folder.

**Test Access as a Normal User:**
- On Client-1, log in as a normal user (e.g., <someuser>).

- Try to access the "accounting" folder; it should fail.

**Add User to the Security Group:**
- On DC-1, add the user <someuser> to the "ACCOUNTANTS" Security Group.

**Test Access as the User (Again):**
- Log in to Client-1 as <someuser> and attempt to access the "accounting" share in \\DC-1\.

- Verify if access is now granted.
</p>
<br />


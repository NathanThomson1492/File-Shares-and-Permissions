<p align="center">

</p>

<h1>File Shares and Permissions Tutorial</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />






<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Services


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Setting up Fileshares and Permissions</h2>

1. Create four sample files with various permissions
2. Log into client machine as a normal user and attempt to access sample files 
3. Create a new security group named "Accountants"
4. Add one of our sample users to the "Accountants" security group
5. Observe newly acquired access privileges

<h2>Introduction</h2>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
<br />

<p>Using your domain administrator account, which follows the format mydomain.com\jane_admin, establish a connection or log into the DC-1 server. Using a standard user account, formatted as mydomain<someuser>, establish a connection or log into the Client-1 machine.</p>

<br />

<p>On the DC-1 server, navigate to the C:\ drive and create four distinct folders named “read-access,” “write-access,” “no-access,” and “accounting.”</p>

![3 create4Folders](https://github.com/user-attachments/assets/060a75b3-a6a0-403d-8a87-0396fe43c223)

<br />
<br />

<h4> Assign the following permissions to the folders for the “Domain Users” group: </h4>
<ul>
  <li>For the folder named “read-access,” assign the “Read” permission to the “Domain Users” group. </li>
<br />
  
![5 DOMUSERS_permission_READ](https://github.com/user-attachments/assets/825125be-5f26-407d-bf7f-1de6173f8e7b)

<br />
  <li>For the folder named “write-access,” assign the “Read/Write” permissions to the “Domain Users” group.</li>
<br />
  
![6 DOMUSERS_permission_write](https://github.com/user-attachments/assets/9e9c693f-d1cf-46e1-832f-54c895a157d4)
<br />
  <li>For the folder named “no-access,” assign the “Read/Write” permissions to the “Domain Admins” group. The “accounting” folder will be configured later. </li>

<br />

![7 DOMADMINS_read-write_PERM](https://github.com/user-attachments/assets/7984b77d-cd0b-47db-8823-cb921f2e3d77)

</ul>
<br />
<br />
<p>
On the Client-1 machine, open the Run dialog (Start > Run) and enter the path \dc-1 to navigate to the shared folders. Attempt to access the folders you created on DC-1. Determine which folders you can access and identify which folders allow you to create new items. Evaluate if the access permissions align with the expected outcomes.
</p>

![10 permission_DENIED](https://github.com/user-attachments/assets/f8f2de0a-803d-419b-beb4-767d01012efd)

![10b PERMISSIONwrite](https://github.com/user-attachments/assets/c2779658-7ed7-4b76-899d-291dfd31764e)

![10c READpermission](https://github.com/user-attachments/assets/fec32282-1bfb-4e0b-bb84-4fc2c27a34c6)

<p>
  Return to the DC-1 server and open Active Directory. Create a new security group named “ACCOUNTANTS.”
</p>

![11 createACCOUNTANTSsecurgroup](https://github.com/user-attachments/assets/19ae7c6b-68a4-4892-8594-8ead4651e050)
<br />
<br />


<p>
On the “accounting” folder created earlier on the C:\ drive of DC-1, set the following permissions: Assign the “Read/Write” permissions to the “ACCOUNTANTS” security group.
</p>

![13 ACCOUNTANTS_readwrite](https://github.com/user-attachments/assets/4df84288-25d5-48f3-82a6-42131c7fde92)
<br />
<br />

<p> On the Client-1 machine, log in as the standard user account <someuser> and attempt to access the “accounting” folder. The access attempt should fail initially. </p>

![14normyUSERdeniedACCOUNTING](https://github.com/user-attachments/assets/28616e91-09f0-466e-993d-236dee5eca1b)
<br />
<br />

<p>
Log out of Client-1 and return to DC-1. Add the user <someuser> to the “ACCOUNTANTS” security group in Active Directory.
</p>

![16 ADDemmaTOaccountants](https://github.com/user-attachments/assets/887216b1-500e-426d-9aec-9ce6cddbb728)
<br />
<br />

<p>
Sign back into Client-1 using the <someuser> account and try to access the “accounting” folder in the shared path \DC-1. Verify whether the user can now access the folder with the updated group membership.
</p>

![17 EMMAaccessTOaccounting](https://github.com/user-attachments/assets/875fd060-f120-4af0-997e-0ceb1171d37c)











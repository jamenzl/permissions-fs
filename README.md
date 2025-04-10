<p align="center">
<img src="https://i.imgur.com/vFTy0Qc.png" alt="File Sharing/Permissions"/>
</p>

<h1>File Sharing and Permissions</h1>
This tutorial outlines the understanding and use of file sharing and permissions in Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create some sample file shares with various permissions
- Attempt to access file shares as a normal user
- Create an "ACCOUNTANTS" Security group, assign permissions, and test access

<h2>Deployment and Configuration Steps</h2>

Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
</p>
<br />
<p>
<img src="https://i.imgur.com/KzOyoAY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Connect/log into Client-1 as a normal user (mydomain\<someuser>)
</p>
<br />
<p>
<img src="https://i.imgur.com/wlj6rDo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On DC-1, on the C:\ drive, create four (4) folders: "read-access", "write-access", "no-access", and "accounting"
</p>
<br />
<p>
<img src="https://i.imgur.com/mGaWz1r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set the following permissions (share the folder)
  
Folder: “read-access”, Group: “Domain Users”, Permission: “Read”

Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”

Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”

(Skip accounting for now)

</p>
<br />
<p>
<img src="https://i.imgur.com/fNIsOJB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/BRTTT3h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/UjamQur.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On Client-1, navigate to the shared folder (start, run, \\dc-1)
</p>
<br />
<p>
<img src="https://i.imgur.com/9l4Wk4p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Try to access the folders you just created.  Which folders can you access? Which folders can you create stuff in? Does it make sense?
</p>
<br />
<p>

When finished, go back into DC-1, in Active Directory, create a security group called "ACCOUNTANTS"
</p>
<br />
<p>
<img src="https://i.imgur.com/RZqY0Q8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On the “accounting” folder you created earlier, set the following permissions:

Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”

</p>
<br />
<p>
<img src="https://i.imgur.com/mYbddSy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On Client-1, as <<someuser>>, try to access the accountants folder.  It should fail.
</p>
<br />
<p>
<img src="https://i.imgur.com/u1wA5Ez.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log out of Client-1 as <<someuser>>

On DC-1, make <someuser> a member of the "ACCOUNTANTS" Security Group
</p>
<br />
<p>
<img src="https://i.imgur.com/gQukRT7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Sign back into Client-1 as <someuser> and try to access the "accounting" share in \\DC-1\ - Does it work now?
</p>
<br />
<p>
<img src="https://i.imgur.com/UVr2zcf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

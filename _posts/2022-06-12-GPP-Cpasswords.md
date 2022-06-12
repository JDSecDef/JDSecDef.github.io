---
layout: post
title: "Finding and decrypting cpasswords in Group Policy Preferences"
date: 2022-06-12
author: By JD
---

## What are Group Policy Preferences
<p>Group Policy Preferences (GPP) is a collection of Group Policy client-side extensions that enable settings that were previously unavailable in Group Policy, such as mapping drives, scheduled tasks and start menu settings. GPP allows administrators.

A security risk exists because the GPP xml files are accessible and readable to all authenticated users in a domain. These files are stored in the SYSVOL share on domain controllers. 

These xml files can be easily searched using the below command in command prompt.</p>

~~~cmd
findstr /S /I cpassword \\<FQDN>\\sysvol\<FQDN>\policies\*.xml
~~~

<p>Any cpassword values found can be decrypted using the Get-Decryptedcpassword.ps1 PowerShell script to reveal the clear text password. After downloading the PowerShell script, import the function using the below command in PowerShell:</p>

~~~powershell
Import-Module .\Get-Decryptedcpassword.ps1
~~~

<p>Once the function is imported, decrypt the cpassword value using the below command:</p>

~~~powershell
Get-Decryptedcpassword <cpasswordvalue>
~~~

![useful image]({{ https://jdsecdef.github.io/ }}/assets/cpassworddecrypted.png)

[Click here to Download the PowerShell script to decrypt cpassword values](/assets/Get-Decryptedcpassword.ps1)

<!-- <p>Copy the Microsoft.ActiveDirectory.Management.dll from a computer that has RSAT installed from the following location:</P>

<ul><li>C:\Windows\Microsoft.NET\assembly\GAC_64\Microsoft.ActiveDirectory.Management</li></ul>

![useful image]({{ https://jdsecdef.github.io/ }}/assets/ADRSATdll.png)

<p>Then import the DLL as a module using the following command:</p>

<pre><code>Import-Module .\Microsoft.ActiveDirectory.Management.dll</code></pre>

[Click here to Download the RSAT dll](/assets/Microsoft.ActiveDirectory.Management.dll) -->
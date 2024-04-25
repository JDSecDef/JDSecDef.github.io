---
layout: post
title: Finding and decrypting cpasswords in Group Policy Preferences
date: 2022-06-12 13:32:20 +0300
description: Finding and decrypting cpasswords in Group Policy Preferences
img: PSDecrypt.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Productivity, Workflow] # add tag
---
## What are Group Policy Preferences
<p>Group Policy Preferences (GPP) is a collection of Group Policy client-side extensions that enable settings that were previously unavailable in Group Policy, such as mapping drives, scheduled tasks and start menu settings. GPP allows administrators.

A security risk exists because the GPP xml files are accessible and readable to all authenticated users in a domain. These files are stored in the SYSVOL share on domain controllers. 

These xml files can be easily searched using the below command in command prompt. Remember to replace the FQDN value with the actual domain value.</p>

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

![PowerShell]({{site.baseurl}}/assets/img/decryptedcpassword.png)

[Click here to Download the PowerShell script to decrypt cpassword values](/assets/files/Get-DecryptedCpassword.ps1)


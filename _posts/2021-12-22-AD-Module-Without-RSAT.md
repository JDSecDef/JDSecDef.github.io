---
layout: post
<<<<<<< HEAD
title: "Use PowerShell AD Module Without RSAT"
=======
title: PowerShell AD Module Without RSAT
>>>>>>> d26a604010ea063042947916c33a420563a0fc1b
date: 2021-12-22
author: By JD
---

<p>Copy the Microsoft.ActiveDirectory.Management.dll from a computer that has RSAT installed from the following folder:</P>

<span style="font-size: 0.9em"> *C:\Windows\Microsoft.NET\assembly\GAC_64\Microsoft.ActiveDirectory.Management* </span>

![RSATdll-Location](/assets/ADRSATdll.png)

<p>Then import the DLL as a module using the following command:</p>

~~~powershell
Import-Module .\Microsoft.ActiveDirectory.Management.dll
~~~

[Click here to Download the RSAT dll](/assets/Microsoft.ActiveDirectory.Management.dll)
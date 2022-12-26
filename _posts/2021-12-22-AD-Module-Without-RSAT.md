---
layout: post
title: "Use PowerShell AD Module Without RSAT"
date: 2021-12-22
author: By JD
---

<p>Copy the Microsoft.ActiveDirectory.Management.dll from a computer that has RSAT installed from the following folder:</P>

<span style="font-size: 0.9em"> *C:\Windows\Microsoft.NET\assembly\GAC_64\Microsoft.ActiveDirectory.Management* </span>

<p>Then import the DLL as a module using the following command:</p>

~~~powershell
Import-Module .\Microsoft.ActiveDirectory.Management.dll
~~~

[Click here to Download the required files](/assets/ADPS.zip)
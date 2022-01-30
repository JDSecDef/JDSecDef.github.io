---
layout: post
title: "PowerShell AD Module Without RSAT"
date: 2021-12-22
---

Copy the following DLL from a computer that has RSAT installed: **C:\Windows\Microsoft.NET\assembly\GAC_64\Microsoft.ActiveDirectory.Management**

![useful image]({{ https://jdsecdef.github.io/ }}/assets/RSATdll.png)

Then import the DLL as a module using the following command:

**Import-Module .\Microsoft.ActiveDirectory.Management.dll**
---
layout: post
title: "Get Windows Defender Exclusions"
date: 2022-01-13
---

<p>In Windows 10, standard users can lookup the Windows Defender exclusions using the below PS cmd. Could be useful if customers are running Defender.</p>

~~~powershell
Get-ChildItem -Path 'HKLM:\SOFTWARE\Microsoft\Windows Defender\Exclusions\'
~~~

![PowerShell-Get-ChildItem-Output](/assets/PSgetchilditem.png)
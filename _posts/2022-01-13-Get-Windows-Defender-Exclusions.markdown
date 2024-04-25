---
layout: post
title: Get Windows Defender Exclusions
date: 13 January 2022 
description: Get Windows Defender Exclusions
img: PSgetchilditem.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
---
<p>In Windows 10, standard users can lookup the Windows Defender exclusions using the below PS cmd. Could be useful if customers are running Defender.</p>

~~~powershell
Get-ChildItem -Path 'HKLM:\SOFTWARE\Microsoft\Windows Defender\Exclusions\'
~~~

![PowerShell-Get-ChildItem-Output](/assets/img/PSgetchilditem.png)


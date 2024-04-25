---
layout: post
title: Get Windows Defender Exclusions
date: 13 January 2022 
description: Get Windows Defender Exclusions
img: Defender.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Productivity, Workflow] # add tag
---
<p>In Windows 10, standard users can lookup the Windows Defender exclusions using the below PS cmd. Could be useful if customers are running Defender.</p>

~~~powershell
Get-ChildItem -Path 'HKLM:\SOFTWARE\Microsoft\Windows Defender\Exclusions\'
~~~

![PowerShell]({{site.baseurl}}/assets/img/PSgetchilditem.png)


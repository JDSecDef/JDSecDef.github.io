---
layout: post
title: "PowerShell AD Module Without RSAT"
date: 2021-12-22
---

<p>Copy the Microsoft.ActiveDirectory.Management.dll from a computer that has RSAT installed from the following location:</P>

<ul><li>C:\Windows\Microsoft.NET\assembly\GAC_64\Microsoft.ActiveDirectory.Management</li></ul>

[Click here to Download the RSAT dll](/assets/Microsoft.ActiveDirectory.Management.dll)
                                             
![useful image]({{ https://jdsecdef.github.io/ }}/assets/ADRSATdll.png)

<p>Then import the DLL as a module using the following command:</p>

<pre><code>Import-Module .\Microsoft.ActiveDirectory.Management.dll</code></pre>
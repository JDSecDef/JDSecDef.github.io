---
layout: post
title: "PowerShell AD Module Without RSAT"
date: 2021-12-22
---

<p>Copy the following DLL from a computer that has RSAT installed:</P>

<pre><code>C:\Windows\Microsoft.NET\assembly\GAC_64\Microsoft.ActiveDirectory.Management</code></pre>

[Click here to Download the RSAT dll](/assets/Microsoft.ActiveDirectory.Management.dll)
                                             
![useful image]({{ https://jdsecdef.github.io/ }}/assets/ADRSATdll.png)

Then import the DLL as a module using the following command:</P>

<pre><code>Import-Module .\Microsoft.ActiveDirectory.Management.dll</code></pre>
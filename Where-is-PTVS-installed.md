Quick answer
============

PTVS 2.0 is installed in:

```
%ProgramFiles(x86)%\Microsoft Visual Studio <VS version>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\2.0
```

A registry value `InstallDir` containing the full installation directory is stored at:

```
(64-bit Windows) HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS version>
(32-bit Windows) HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS version>
```

where `VS version` is `12.0`, `11.0` or `10.0`. See below for full installation paths.

All Users
=========

By default, PTVS is installed for all users on the computer. Full installation paths for all released versions are shown below. (For 32-bit versions of Windows, replace `%ProgramFiles(x86)%` with `%ProgramFiles%`.)

<table style="border-spacing:0; border-collapse:collapse">
<tbody>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><strong>PTVS Version</strong></td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><strong>VS Version</strong></td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><strong>Path</strong></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2.1</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2013</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\2.1</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2.1</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2012</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 11.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\2.1</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2.1</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2010</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\2.1</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2.0</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2013</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\2.0</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2.0</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2012</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 11.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\2.0</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2.0</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2010</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\2.0</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">1.5</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2012</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 11.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\1.5</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">1.5</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2010</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\1.5</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">1.1</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2010</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\1.1</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">1.0</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2010</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%ProgramFiles(x86)%\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\1.0</code></td>
</tr>
</tbody>
</table>

Just For You
============

Prior to PTVS 2.0, an option was available to install PTVS for all users or just for you. If installed for all users, the installation paths are shown above in the previous section. Full installation paths for all released versions are shown below.

<table style="border-spacing:0; border-collapse:collapse">
<tbody>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><strong>PTVS Version</strong></td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><strong>VS Version</strong></td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><strong>Path</strong></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2.1</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">All</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">Not supported.</td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2.0</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">All</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">Not supported.</td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">1.5</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2012</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%LocalAppData%\Microsoft\VisualStudio\11.0\Extensions\Microsoft\Python Tools for Visual Studio\1.5</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">1.5</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2010</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%LocalAppData%\Microsoft\VisualStudio\10.0\Extensions\Microsoft\Python Tools for Visual Studio\1.5</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">1.1</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2010</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%LocalAppData%\Microsoft\VisualStudio\10.0\Extensions\Microsoft\Python Tools for Visual Studio\1.1</code></td>
</tr>
<tr>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">1.0</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0">2010</td>
<td style="padding:0.2em 0.5em; border:1px solid #a0a0a0"><code>%LocalAppData%\Microsoft\VisualStudio\10.0\Extensions\Microsoft\Python Tools for Visual Studio\1.0</code></td>
</tr>
</tbody>
</table>
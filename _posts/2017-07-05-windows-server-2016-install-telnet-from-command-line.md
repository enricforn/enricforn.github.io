---
layout: post
title: Windows Server 2016 - install telnet from command-line
categories: [windows]
tags: [windows, commands]
image: /images/posts/install-telnet-ws2016/header.png
---

### The easiest and fastest way to install telnet to a Windows Server 2016 from command-line

When trying to solve some kind of conectivity problem, I often use telnet. By default, windows machine do not preinstall telnet:

```
C:\>telnet google.com 80
'telnet' is not recognized as an internal or external command, operable program or batch file.
C:\>
```

You can easily install telnet from command-line with this short command:


From standard command prompt command-line:

```
dism /online /Enable-Feature /FeatureName:TelnetClient
```

From powershell console:

```
Install-WindowsFeature -name Telnet-Client
```

Have fun!

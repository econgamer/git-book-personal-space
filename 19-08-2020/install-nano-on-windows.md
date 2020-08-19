---
description: 19/08/2020
---

# Install nano on Windows

1. Install Chocolatey:

```text
powershell Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

1. Run `choco install -y nano`.
2. Run nano: `nano`.

Source: [https://superuser.com/questions/1493801/how-to-install-the-nano-cli-editor-on-windows-10](https://superuser.com/questions/1493801/how-to-install-the-nano-cli-editor-on-windows-10)


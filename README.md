<div align="center">

<pre>
██╗  ██╗██╗██╗     ██╗     ██████╗  ██████╗ ██████╗ ████████╗
██║ ██╔╝██║██║     ██║     ██╔══██╗██╔═══██╗██╔══██╗╚══██╔══╝
█████╔╝ ██║██║     ██║     ██████╔╝██║   ██║██████╔╝   ██║   
██╔═██╗ ██║██║     ██║     ██╔═══╝ ██║   ██║██╔══██╗   ██║   
██║  ██╗██║███████╗███████╗██║     ╚██████╔╝██║  ██╗   ██║   
╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚═╝      ╚═════╝ ╚═╝  ╚═╝   ╚═╝   
</pre>

**Kill whatever is running on a port — macOS · Windows · Linux**

AI-powered pentesting, vulnerability scanning, and automated hardening via [Ollama](https://ollama.com) — runs entirely on your hardware

[![Version](https://img.shields.io/badge/version-1.10.3-00b4d8?style=flat-square)](#)
[![License](https://img.shields.io/badge/license-Source%20Available-00b4d8?style=flat-square)](LICENSE)
[![macOS](https://img.shields.io/badge/macOS-00b4d8?style=flat-square&logo=apple&logoColor=white)](https://github.com/skosari/killport-mac)
[![Windows](https://img.shields.io/badge/Windows-00b4d8?style=flat-square&logo=windows&logoColor=white)](https://github.com/skosari/killport-win)
[![Linux](https://img.shields.io/badge/Linux-00b4d8?style=flat-square&logo=linux&logoColor=white)](https://github.com/skosari/killport-linux)

</div>

---

## Pick your platform

| Platform | Repo |
|---|---|
| 🍎 macOS | [skosari/killport-mac](https://github.com/skosari/killport-mac) |
| 🪟 Windows | [skosari/killport-win](https://github.com/skosari/killport-win) |
| 🐧 Linux | [skosari/killport-linux](https://github.com/skosari/killport-linux) |

---

## Install

### macOS

**Homebrew** *(recommended)*

```sh
brew install skosari/killport-mac/killport
```

**curl one-liner**

```sh
curl -fsSL https://raw.githubusercontent.com/skosari/killport-mac/main/install.sh | bash
```

**Manual**

```sh
sudo mkdir -p /usr/local/bin && \
curl -fsSL https://raw.githubusercontent.com/skosari/killport-mac/main/killport \
  -o /tmp/killport && sudo mv /tmp/killport /usr/local/bin/killport && sudo chmod +x /usr/local/bin/killport
```

---

### Windows

**PowerShell** *(elevated — Run as Administrator)*

```powershell
irm https://raw.githubusercontent.com/skosari/killport-win/main/install.ps1 | iex
```

**Command Prompt (CMD)** *(elevated — Run as Administrator)*

```cmd
curl -fsSL https://raw.githubusercontent.com/skosari/killport-win/main/install.bat -o "%TEMP%\kp-install.bat" && "%TEMP%\kp-install.bat"
```

Installs `killport.bat` to `System32` (always in PATH for CMD and PowerShell) and the implementation to `C:\ProgramData\killport\`.

> Requires Windows 10 or later.

---

### Linux

**curl** *(recommended)*

```sh
curl -fsSL https://raw.githubusercontent.com/skosari/killport-linux/main/install.sh | bash
```

**wget**

```sh
wget -qO /tmp/killport https://raw.githubusercontent.com/skosari/killport-linux/main/killport \
  && sudo mv /tmp/killport /usr/local/bin/killport \
  && sudo chmod +x /usr/local/bin/killport
```

**Manual**

```sh
sudo mkdir -p /usr/local/bin && \
curl -fsSL https://raw.githubusercontent.com/skosari/killport-linux/main/killport \
  -o /tmp/killport && sudo mv /tmp/killport /usr/local/bin/killport && sudo chmod +x /usr/local/bin/killport
```

---

## What it does

```sh
killport 3000              # kill whatever is on port 3000
killport list              # list all listening ports
killport scan 192.168.1.10 # scan ports on a remote host
killport attack 192.168.1.10  # AI pentest: scan + analyze + report
killport vuln 192.168.1.10:22 # detect CVEs for a running service
killport fix 192.168.1.10:22  # auto-harden a vulnerable service
killport audit             # review firewall rules in plain English
killport open 8080         # open a port through your firewall
killport close 8080        # close a port
killport sniff 443         # capture live traffic on a port
killport watch 3000        # monitor live connections in real time
killport cert github.com   # inspect a TLS certificate
killport dns example.com   # DNS recon + zone transfer test
killport stress 192.168.1.10:80  # authorized connection flood test
```

Full command reference and examples in each platform repo.

---

## AI Penetration Testing

> **Point it at any machine on your network. Watch an AI hunt for vulnerabilities in real time.**

`killport attack` is a fully agentic AI pentest tool powered by [Ollama](https://ollama.com) — your local AI, running entirely on your hardware, no cloud, no API keys. It **thinks**, **acts**, and **investigates** — probing services, testing credentials, hunting for exposed paths — then delivers a plain-English security report with specific fix steps.

**Everything runs locally. Your scan data never leaves your machine.**

### Setup

1. [Install Ollama](https://ollama.com/download) and pull a model:
   ```sh
   ollama pull llama3.2
   # reasoning model (slower but deeper analysis):
   ollama pull deepseek-r1:8b
   ```
2. Configure killport:
   ```sh
   killport config
   ```
3. Run:
   ```sh
   killport attack 192.168.1.10
   ```

---

## Uninstall

### macOS

```sh
killport uninstall
# or via Homebrew:
brew uninstall killport && brew untap skosari/killport-mac
```

### Windows *(Run as Administrator)*

```sh
killport uninstall
# or via PowerShell:
irm https://raw.githubusercontent.com/skosari/killport-win/main/uninstall.ps1 | iex
```

### Linux

```sh
killport uninstall
# or via curl:
curl -fsSL https://raw.githubusercontent.com/skosari/killport-linux/main/uninstall.sh | bash
```

---

<div align="center">

Made by [skosari](https://github.com/skosari) · [killport-mac](https://github.com/skosari/killport-mac) · [killport-win](https://github.com/skosari/killport-win) · [killport-linux](https://github.com/skosari/killport-linux)

</div>

<div align="center">

<pre>
██╗  ██╗██╗██╗     ██╗     ██████╗  ██████╗ ██████╗ ████████╗
██║ ██╔╝██║██║     ██║     ██╔══██╗██╔═══██╗██╔══██╗╚══██╔══╝
█████╔╝ ██║██║     ██║     ██████╔╝██║   ██║██████╔╝   ██║   
██╔═██╗ ██║██║     ██║     ██╔═══╝ ██║   ██║██╔══██╗   ██║   
██║  ██╗██║███████╗███████╗██║     ╚██████╔╝██║  ██╗   ██║   
╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚═╝      ╚═════╝ ╚═╝  ╚═╝   ╚═╝   
</pre>

**Kill whatever is running on a port — macOS · Windows · Linux · Windows CMD**

AI-powered pentesting, vulnerability scanning, and automated hardening via [Ollama](https://ollama.com) — runs entirely on your hardware

[![License](https://img.shields.io/badge/license-Source%20Available-00b4d8?style=flat-square)](LICENSE)
[![macOS](https://img.shields.io/badge/macOS-00b4d8?style=flat-square&logo=apple&logoColor=white)](https://github.com/skosari/killport-mac)
[![Windows](https://img.shields.io/badge/Windows-00b4d8?style=flat-square&logo=windows&logoColor=white)](https://github.com/skosari/killport-win)
[![Linux](https://img.shields.io/badge/Linux-00b4d8?style=flat-square&logo=linux&logoColor=white)](https://github.com/skosari/killport-linux)
[![CMD](https://img.shields.io/badge/Windows%20CMD-00b4d8?style=flat-square)](https://github.com/skosari/killport-cmd)

</div>

---

## Pick your platform

| Platform | Repo | Notes |
|---|---|---|
| 🍎 macOS | [skosari/killport-mac](https://github.com/skosari/killport-mac) | Full feature set |
| 🪟 Windows | [skosari/killport-win](https://github.com/skosari/killport-win) | Full feature set — PowerShell + CMD |
| 🐧 Linux | [skosari/killport-linux](https://github.com/skosari/killport-linux) | Full feature set |
| 🪟 Windows CMD | [skosari/killport-cmd](https://github.com/skosari/killport-cmd) | No PowerShell required — limited build |

> **Windows CMD build:** If you can't use PowerShell, `killport-cmd` is a pure batch file with no dependencies — covers kill, list, open/close ports, firewall, IP, DNS, scan, and watch. Features requiring PowerShell (attack, fix, vuln, cert, ssh, wol, etc.) are in `killport-win`.

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

---

### Windows *(full — PowerShell + CMD)*

**PowerShell** *(elevated — Run as Administrator)*

```powershell
irm https://raw.githubusercontent.com/skosari/killport-win/main/install.ps1 | iex
```

**Command Prompt (CMD)** *(elevated — Run as Administrator)*

```cmd
curl -fsSL https://raw.githubusercontent.com/skosari/killport-win/main/install.bat -o "%TEMP%\kp-install.bat" && "%TEMP%\kp-install.bat"
```

### Windows CMD-only *(no PowerShell)*

```cmd
curl -fsSL https://raw.githubusercontent.com/skosari/killport-cmd/main/killport.bat -o "%SystemRoot%\System32\killport.bat"
```

> Run as Administrator. See [killport-cmd](https://github.com/skosari/killport-cmd) for the full limited-build feature list.

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

---

## What it does

```sh
killport 3000                    # kill whatever is on port 3000
killport list                    # list all listening ports
killport open 8080               # open a port through your firewall
killport close 8080              # close a port
killport ip                      # show IP addresses and network info
killport scan 192.168.1.10       # scan ports on a remote host
killport watch 3000              # monitor live connections in real time
killport dns example.com         # DNS recon + zone transfer test
killport cert github.com         # inspect a TLS certificate
killport sniff 443               # capture live traffic on a port
killport ssh                     # generate token for zero-config SSH setup
killport ssh ks:<token>          # accept token — passwordless SSH in one step
killport ssh mini                # SSH to a saved machine by name
killport wol                     # wake a machine on your LAN
killport attack 192.168.1.10     # AI pentest: scan + analyze + report
killport vuln 192.168.1.10:22    # detect CVEs for a running service
killport fix 192.168.1.10:22     # auto-harden a vulnerable service
killport audit                   # review firewall rules in plain English
killport stress 192.168.1.10:80  # authorized connection flood test
```

Full command reference and examples in each platform repo.

---

## SSH Easy Connect

No config files, no manual key copying. Exchange a single token between two machines:

```sh
# On the machine you want to connect FROM:
killport ssh
# → outputs a token

# On the machine you want to connect TO (paste the token):
killport ssh ks:<token>
# → adds key, saves the connection, outputs return token

# Connect by name from anywhere:
killport ssh mini
killport ssh list
```

Works across all platforms — Mac↔Mac, Linux↔Linux, Mac↔Linux, and Windows↔any (killport-win).

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

### Windows CMD

```cmd
killport uninstall
```

### Linux

```sh
killport uninstall
# or via curl:
curl -fsSL https://raw.githubusercontent.com/skosari/killport-linux/main/uninstall.sh | bash
```

---

<div align="center">

Made by [skosari](https://github.com/skosari) · [killport-mac](https://github.com/skosari/killport-mac) · [killport-win](https://github.com/skosari/killport-win) · [killport-linux](https://github.com/skosari/killport-linux) · [killport-cmd](https://github.com/skosari/killport-cmd)

</div>

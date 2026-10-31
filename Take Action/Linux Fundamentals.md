# Linux CLI Basics

## What is a Terminal?

A terminal is a **text-based interface** that allows you to control your operating system by typing commands instead of clicking buttons in a Graphical User Interface (GUI).

### Why Use the Terminal in Cybersecurity?
- **Speed & Efficiency**: Typing commands and running scripts is significantly faster than navigating GUI menus.
- **Granular Control**: Provides deep access to system configurations, hidden settings, and file permissions.
- **Tool Compatibility**: Most cybersecurity, penetration testing, and forensic tools are strictly built for Command Line Interfaces (CLI).

---

## Essential Linux Navigation & File Inspection Commands

| Command | Purpose / Function | Description |
| --- | --- | --- |
| `pwd` | Print Working Directory | Displays the absolute path of the directory you are currently in. |
| `ls` | List Directory Contents | Lists all visible files and folders in your current directory. |
| `ls -l` | Detailed Directory List | Displays files with extra details, including permissions, owner, file size, and creation date. |
| `ls -al` | List All Files (Including Hidden) | Shows all files including hidden files (files starting with a dot, e.g., `.bashrc`). |
| `cd <directory>` | Change Directory | Navigates into a specific folder (e.g., `cd /etc`). |
| `cd ..` | Move Up One Directory | Moves back one level up in the directory tree. |
| `find . -name "filename"` | Find Files | Searches the system for a specific file name (e.g., `find . -name fs.txt`). |
| `cat <file>` | Concatenate & Read File | Outputs the complete text content of a file directly to the terminal (e.g., `cat fs.txt`). |

---

## System Information & Diagnostic Commands

| Command | Purpose / Function | Description |
| --- | --- | --- |
| `whoami` | Identify Current User | Prints the username of the currently logged-in account. |
| `uname -a` | System & Kernel Information | Displays detailed information about the system, including computer hostname, kernel version, OS type, and architecture. |
| `df -h` | Disk Usage | Shows available and used storage space across all mounted drives in human-readable format (MB/GB). |

# The Linux Philosophy

The Linux philosophy centers on simplicity, modularity, and openness. It advocates for building small, single-purpose programs that perform one task exceptionally well. These tools can then be combined and chained together to accomplish complex operations, promoting high efficiency, flexibility, and automation.

---

## The 5 Core Principles of Linux

| Principle | Description | Real-World Example |
| --- | --- | --- |
| **Everything is a file** | All system resources—including physical hardware devices, running processes, storage drives, and network connections—are represented as files in the file system. | Hardware devices like hard drives are accessed as files under `/dev/` (e.g., `/dev/sda`), and network sockets can be read/written like plain text files. |
| **Small, single-purpose programs** | Linux consists of modular, specialized utilities designed to perform one specific function cleanly without unnecessary features or bloat. | The `grep` utility only searches text, `wc` only counts lines/words, and `cat` only reads files. |
| **Ability to chain programs together** | Unix pipes (`\|`) allow the output of one command to serve directly as the input to another, building powerful workflows from simple tools. | Running `cat /etc/passwd \| grep "bash"` reads user accounts and instantly filters for users with bash shell access. |
| **Avoid captive user interfaces** | Linux is built natively for command-line interfaces (CLI) and shell automation, giving administrators direct control without forcing interactive GUI prompts. | Automating system updates, backups, and user provisioning through head-less shell scripts without manual UI clicks. |
| **Configuration data stored in text files** | System settings, user credentials, and application configurations are stored as human-readable plain text files rather than binary formats. | System user accounts are saved in plain text within `/etc/passwd`, and network configs reside in plain text files under `/etc/`. |

# Linux Operating System Architecture Components

The Linux operating system is built from several modular layers working together, from initial boot to the user interface.

---

## Core Linux Architecture Components

| Component | Description & Function | Key Terminology | Real-World Analogy |
| --- | --- | --- | --- |
| **1. Bootloader** | The initial software executed upon pressing the power button. Its sole task is to locate the OS Kernel on storage and load it into RAM. | • **BIOS/UEFI**: Motherboard firmware that initializes hardware and invokes the Bootloader.<br>• **GRUB**: Grand Unified Bootloader; standard bootloader in distributions like Kali Linux and Parrot OS. | Like a car's ignition switch; it doesn't drive the car itself, but provides the initial spark to start the engine. |
| **2. OS Kernel** | The core layer of the operating system acting as an abstraction layer between hardware and software. Controls CPU, RAM, and storage access via System Calls. | • **Hardware Management**: Controlling physical components.<br>• **System Calls (Syscalls)**: Requests sent by applications to access hardware.<br>• **Resource Allocation**: Distributing system capacity among running processes. | Like an orchestra conductor directing each musician (application) on when and how to play their instrument (hardware) without conflicts. |
| **3. Daemons** | Background services that run silently without a user interface. They initialize at boot and wait for specific events (e.g., handling SSH connections, printing, networking). | • **Background Processes**: Non-interactive system tasks.<br>• **Systemd**: The standard init system and service manager in modern Linux.<br>• **Network Daemons**: Services listening for network calls (e.g., `sshd`). | Like building maintenance staff working behind the scenes to keep lighting, security, and climate control running smoothly. |
| **4. OS Shell** | The command-line interpreter environment used to communicate with the OS. It interprets typed terminal commands into instructions executed by the Kernel. | • **CLI**: Command Line Interface.<br>• **Interpreter**: Translates human text into executable kernel operations.<br>• **Bash / Zsh**: Popular interactive shells used in Linux, administration, and penetration testing. | Like a real-time interpreter translating conversations between two individuals who speak completely different languages. |
| **5. Graphics Server** | The backend service managing display rendering and graphical hardware calls. Converts mouse movements and input into pixels and screen coordinates. | • **Display Server**: Service interfacing directly with the GPU.<br>• **X11 / X-Server**: Traditional standard windowing system.<br>• **Wayland**: Modern, faster replacement protocol for display servers. | Like a painter's canvas and paintbrush providing the foundation and tools to project a picture. |
| **6. Desktop Environment (DE)** | The complete Graphical User Interface (GUI) visible to the user, including windows, buttons, taskbars, wallpapers, and menus. | • **GUI**: Graphical User Interface.<br>• **Desktop Environment**: Complete suite containing window managers, icons, and themes (e.g., GNOME, KDE Plasma, XFCE, MATE). | Like interior design and room decoration making a space functional, organized, and pleasant to inhabit. |
| **7. Utilities** | Specialized single-purpose command-line or GUI programs pre-installed to perform dedicated operational tasks. | • **Coreutils**: Fundamental GNU tools included in Linux.<br>• **CLI Utilities**: Dedicated CLI commands like `ls` (list files), `cat` (read content), and `grep` (filter text). | Like a home toolkit containing a screwdriver, hammer, and tape measure—each tool designed for one specific function. |
# Linux Architecture Layers & Practical Execution Flow

Linux operates on a layered architecture where each layer serves as an abstraction interface between the physical hardware and the upper user environment. This design enforces system stability, security boundaries, and modularity.

---

## The 4 Core Layers of Linux Architecture

| Layer | Component | Functional Description & Responsibilities | Cybersecurity Relevance |
| --- | --- | --- | --- |
| **1. Hardware** | Physical Devices | Physical components that process electrical signals and execute binary instructions (`0`s and `1`s). Includes CPU, RAM, persistent storage (SSD/HDD), and network interface cards (NICs). | Understanding hardware layouts helps analyze low-level memory corruption vulnerabilities (e.g., Buffer Overflows) and physical/hardware attacks. |
| **2. Kernel** | OS Core & Hardware Abstraction | The central controller managing hardware resources, process scheduling, and memory allocation. It presents a Hardware Abstraction Layer (HAL), isolating processes into virtual memory spaces and handling requests via **System Calls (Syscalls)**. | Exploiting a vulnerability inside the Kernel (**Kernel Exploit**) allows an attacker to achieve full system control (**Root Access / Privilege Escalation**). |
| **3. Shell** | Command Interpreter (CLI) | An interactive Command Line Interface acting as a bridge between the user and the Kernel. Translates human-readable text commands into machine instructions understood by the Kernel. Examples include `Bash` and `Zsh`. | Gaining remote control over a compromised host typically involves spawning an interactive shell connection (**Reverse Shell** or **Bind Shell**). |
| **4. System Utilities** | Application & Utility Layer | Built-in single-purpose programs (GNU Coreutils) that perform specific operating system functions (e.g., file management, permission settings, text processing). | Attackers leverage built-in utilities for **Living off the Land (LotL)** techniques—using legitimate tools to perform reconnaissance and escalation without triggering antivirus alerts. |

---

## Practical Execution Flow Scenario

When you enter the command `cat /etc/passwd` into your terminal to view system user accounts, data traverses all four architecture layers sequentially:

# Linux Filesystem Hierarchy Standard (FHS) & Cybersecurity Analysis

The **Filesystem Hierarchy Standard (FHS)** defines the structure and directory layout in Linux operating systems. The filesystem is structured as an inverted tree starting from the **Root Directory (`/`)**, branching into all subdirectories.

---

## Linux Filesystem Directory Breakdown & Security Relevance

| Directory | Full Name / Description | Contents & Purpose | Cybersecurity & CTF Relevance |
| --- | --- | --- | --- |
| `/` | **Root Directory** | The absolute top-level directory of the entire filesystem. Every file and directory stems from here. | Represents the base of the entire system hierarchy. No directories exist above it. |
| `/bin` | **Essential Command Binaries** | Contains fundamental system commands and executable binaries required for basic operations (e.g., `ls`, `ping`, `cat`, `cp`, `bash`). | Accessible to all users; used extensively during initial reconnaissance and navigation. |
| `/boot` | **Boot Files** | Contains static files required to boot the operating system, including the Linux Kernel (`vmlinuz`), GRUB bootloader files, and `initramfs`. | Critical for system boot integrity; target for low-level bootkit analysis and kernel tampering. |
| `/dev` | **Device Files** | Embodies the "Everything is a file" principle. Contains special device files representing hardware components (e.g., `/dev/sda` for primary disk, `/dev/null` as data black hole, `/dev/tty` for terminals). | Useful for hardware interactions, raw disk reads, or discarding unwanted tool output to `/dev/null`. |
| `/etc` | **System Configuration Files** | Stores system-wide configuration files and application settings. | High-value target during enumeration. Key security files include:<br>• `/etc/passwd`: Lists user accounts.<br>• `/etc/shadow`: Contains password hashes (root-readable only).<br>• `/etc/sudoers`: Defines Sudo privilege escalation rules. |
| `/home` | **User Home Directories** | Personal storage space for regular system users (e.g., `/home/username/`). | Often searched for SSH private keys (`.ssh/id_rsa`), user flags (`user.txt`), and sensitive personal configurations. |
| `/lib` | **Shared Libraries** | Essential shared library files required by binaries in `/bin` and `/sbin` during system startup (equivalent to `.dll` files in Windows). | Target for shared library hijacking and privilege escalation vectors (`LD_PRELOAD`). |
| `/media` | **Removable Media** | Automatic mount point for removable media devices like USB drives and CD-ROMs. | Investigated in digital forensics for external device activity and data exfiltration artifacts. |
| `/mnt` | **Temporary Mount Point** | Directory reserved for system administrators to manually mount temporary filesystems or network shares. | Inspected during post-exploitation for mounted network drives or secondary backup disks. |
| `/opt` | **Optional Software** | Used for installing third-party applications and optional software packages that do not ship natively with the OS. | Common location for manual tool installations (e.g., tools cloned from GitHub or custom utilities like Burp Suite). |
| `/root` | **Root Home Directory** | The private home directory of the system administrator (`root` user). Distinct from the root directory `/`. | Restricted to administrative access only. On platforms like Hack The Box (HTB), it contains the final flag (`root.txt`). |
| `/sbin` | **System Administration Binaries** | Executable binaries reserved for system maintenance and administrative functions (e.g., `fdisk`, `iptables`, `ifconfig`, `reboot`). | Restricted or monitored binaries used by admins for networking, firewalling, and partition management. |
| `/tmp` | **Temporary Files** | World-writable directory used by applications to store temporary operational files. Automatically cleared upon reboot. | World-writable (`777`); acts as a primary **Staging Area** for attackers to upload payloads, scripts, and exploit binaries. |
| `/usr` | **User Binaries & Resources** | Contains user utilities, secondary non-boot binaries, documentation, and shared data. | Subdirectories include:<br>• `/usr/bin`: Non-essential executable tools.<br>• `/usr/share/wordlists`: Wordlists used for brute-forcing (e.g., `rockyou.txt`). |
| `/var` | **Variable Data** | Stores dynamic files whose contents grow and change continuously during system operation. | Key subdirectories include:<br>• `/var/log`: Stores system and application log files essential for Digital Forensics.<br>• `/var/www/html`: Default web root directory targeted during Web Hacking (LFI, File Uploads). |

# Linux Distributions & Debian Deep Dive

Linux operating systems are built as modular assemblies layered around the Linux Kernel. Understanding how distributions are packaged, deployed, and configured is crucial for system administration, enterprise deployment, and penetration testing (e.g., Hack The Box).

---

## 1. Linux Distributions (Distros)

The **Linux Kernel** itself is merely the core component that manages hardware resources; it cannot function independently as an interactive operating system. A **Linux Distribution (Distro)** is created by packaging the Kernel with a complete software ecosystem:

$$\text{Linux Distribution} = \text{Kernel} + \text{Core Utilities (GNU)} + \text{Package Manager} + \text{Desktop Environment / CLI} + \text{Software Packages}$$

### Why Cybersecurity Professionals Prefer Linux

1. **Open Source & Transparency**: Source code is fully accessible for audit, scrutiny, and modification, ensuring no hidden telemetry, backdoors, or malicious logic.
2. **Customization & Attack Surface Reduction**: Systems can be stripped down to contain only essential services, significantly reducing the overall **Attack Surface**.
3. **Granular Privilege Control & Stability**: Enforces strict permission boundaries (Root vs Unprivileged users) and offers rock-solid operational stability under heavy workloads.

---

## Linux Distributions Categorized by Domain & Use Cases

| Domain / Target Environment | Notable Distributions | Key Features & Purpose |
| --- | --- | --- |
| **Cybersecurity & Penetration Testing** | **Kali Linux**, **ParrotOS**, BackBox, BlackArch, Pentoo | Pre-loaded with hundreds of security assessment tools for penetration testing, digital forensics, and reverse engineering. |
| **Desktop & Beginner Friendly** | **Ubuntu**, **Fedora**, Linux Mint | Feature-rich Graphical User Interfaces (GUIs), widespread driver support, and large community troubleshooting bases. |
| **Enterprise & Servers** | **Debian**, **Red Hat Enterprise Linux (RHEL)**, CentOS Stream, Rocky Linux | Engineered for high reliability, long-term stability, commercial enterprise support, and continuous server availability. |
| **Specialized & Embedded** | Raspberry Pi OS, OpenWrt, Alpine Linux | Minimalist, lightweight distributions optimized for low-resource single-board computers, IoT devices, and containerized runtimes. |

---

## 2. Debian Overview & Core Security Features

**Debian** is one of the oldest, most stable foundational Linux distributions. It serves as the upstream parent distribution for popular downstream distros like Ubuntu and Kali Linux.

### 5 Pillars of Debian

1. **Rock-Solid Stability & Reliability**: Follows strict package testing phases (Unstable $\rightarrow$ Testing $\rightarrow$ Stable) to ensure zero system crashes, making it ideal for 24/7 mission-critical servers.
2. **Advanced Package Tool (APT)**: Powerful package management utility handling dependency resolution, automated software updates, and security patch deployment.
3. **Long-Term Support (LTS)**: Provides up to 5 years of official security updates and patches for stable releases, minimizing operational maintenance overhead.
4. **Deep Control vs Learning Curve**: Features a steeper initial learning curve compared to user-focused GUIs, rewarding administrators with granular command-line control over every subsystem.
5. **Security & Patch Track Record**: Managed by a dedicated security team and global open-source community that rapidly patches vulnerabilities upon public disclosure.

---

## Real-World Application

Understanding Debian architecture is directly applicable to penetration testing and cybersecurity labs:

- **Target Machine Identification**: The vast majority of Linux target instances on HTB and real-world infrastructure run Debian or Debian-derived systems (Ubuntu).
- **Privilege Escalation Vectors**: Familiarity with Debian package management enables discovering privilege escalation exploits related to elevated binaries or misconfigured Sudo permissions (e.g., `apt`, `apt-get`, or `dpkg` abuse via GTFOBins).
- **System Enumeration**: Recognizing standard Debian file layouts allows rapid discovery of service configurations, log files (`/var/log`), and sensitive credentials.
# Shells, Terminals, and Terminal Multiplexers (Tmux)

Understanding the distinction between the shell, terminal emulators, and terminal multiplexers is fundamental for mastering Linux administration, task automation, and cybersecurity operations.

---

## 1. Terminology Distinction: Shell vs Terminal vs Console

| Term | Definition & Role | Real-World Analogy |
| --- | --- | --- |
| **Shell** | The command interpreter that reads user commands, parses them, and sends instructions to the OS Kernel for execution. | The central server room processing all data and requests behind the scenes. |
| **Terminal / Terminal Emulator** | The graphical GUI window application used to display text input and output (e.g., Parrot Terminal, GNOME Terminal, Alacritty). | The receptionist desk where you hand over written requests to be forwarded to the server room. |
| **Console** | A physical or low-level, direct text-mode display connected directly to the computer hardware without a GUI. | Sitting directly inside the physical room with a direct cable hooked into the system. |

---

## 2. Terminal Multiplexers (Tmux)

A **Terminal Multiplexer** like `tmux` allows users to create, access, and control multiple terminal sessions from a single screen. It enables splitting a single terminal window into multiple panes and independent windows.

### Practical Pentesting Setup in Tmux

In penetration testing and CTF environments (such as Hack The Box), `tmux` allows concurrent execution of multiple security workflows within a single session:

- **Pane 1**: Running background enumeration tools (e.g., `nmap` or `gobuster`).
- **Pane 2**: Active exploitation and listening for incoming connections (e.g., `netcat` reverse shell listener).
- **Pane 3**: Navigating wordlist paths (`/usr/share/seclists`), executing scripts (`Impacket`), or managing active Active Directory data (`BloodHound`).
- **Session Persistence**: If an SSH or VPN connection drops, a `tmux` session continues running on the target or local host, allowing seamless reconnection without losing running jobs.

---

## 3. Types of Linux Shells

| Shell Name | Description | Key Features |
| --- | --- | --- |
| **BASH** *(Bourne-Again Shell)* | The default GNU command interpreter for most Linux distributions. | High compatibility, robust scripting capabilities, widely used for task automation. |
| **ZSH** *(Z Shell)* | Advanced interactive shell used as the default shell in Kali Linux and macOS. | Modern autocompletion, theme support (Oh My Zsh), inline syntax highlighting. |
| **FISH** *(Friendly Interactive Shell)* | A user-friendly shell focused on out-of-the-box interactive features. | Auto-suggestions based on history, web-based configuration interface. |
| **TCSH / CSH / KSH** | Older legacy shells modeled after C syntax or specific Unix variants. | Found primarily in specialized legacy enterprise systems. |

---
# Bash Prompt Structure & PS1 Customization

The **Bash Prompt** is the text-based interface string and cursor displayed in the terminal indicating that the shell is ready to receive user commands. Configuring and customizing the prompt using the `PS1` environment variable enhances operational efficiency, mistake prevention, and activity documentation during penetration testing and administration.

---

## 1. Default Prompt Anatomy & Privilege Indicators

In most Linux distributions, the default Bash prompt follows a standard template:

$$\text{Format: } \texttt{<username>@<hostname>:<current\_directory><privilege\_symbol>}$$

### Component Breakdown
- **`<username>`**: The currently logged-in account identity.
- **`<hostname>`**: The network host name of the local computer or remote server.
- **`<current_directory>`**: The current working directory path (`~` denotes the user's home directory).
- **`Privilege Symbol`**:
  - **`$`** *(Unprivileged User Shell)*: Indicates a standard user account with limited system access (e.g., `user@htb[~]$`).
  - **`#`** *(Privileged / Root Shell)*: Indicates full administrative access with complete system privileges (e.g., `root@htb[/htb]#`).

> **HTB / CTF Tip**: When spawning a reverse shell or non-interactive shell on a target host, you may only see a raw `$` or `#` prompt without formatting because the `PS1` variable has not been initialized in the non-interactive session environment.

---

## 2. The PS1 Environment Variable & Escape Sequences

The `PS1` (Prompt String 1) environment variable defines the dynamic layout, text components, and formatting of the primary shell prompt. It is persistently configured within shell resource files like `~/.bashrc` or `/etc/bash.bashrc`.

### Common PS1 Special Characters

| Special Character | Description / Output Format | Example Value |
| --- | --- | --- |
| `\u` | Current username | `kali` |
| `\h` | Short hostname (up to first `.`) | `htb` |
| `\H` | Full domain hostname | `htb.local` |
| `\w` | Full current working directory absolute path | `/var/www/html` |
| `\W` | Basename of the current directory only | `html` |
| `\d` | Current date format (`Weekday Month Day`) | `Fri Oct 30` |
| `\D{%Y-%m-%d}` | Custom formatted date | `2026-10-30` |
| `\t` | Current time in 24-hour format (`HH:MM:SS`) | `14:30:05` |
| `\T` | Current time in 12-hour format (`HH:MM:SS`) | `02:30:05` |
| `\@` | Current time in 12-hour format with AM/PM | `02:30 PM` |
| `\s` | Name of the active shell binary | `bash` |
| `\j` | Number of active background jobs managed by the shell | `2` |
| `\n` | Inserts a line break (newline) | N/A |
| `\$` | Displays `#` if UID is 0 (root), otherwise `$` | `$` or `#` |

---

## 3. Cybersecurity & Penetration Testing Applications

1. **Accurate Documentation & Reporting**:
   Including timestamps (`\t` / `\D`), target IP addresses, and absolute working paths (`\w`) in the prompt ensures that every terminal screenshot, `script` session log, or `.bash_history` entry contains unambiguous temporal and contextual data required for pentest reports.
2. **Operational Error Prevention**:
   Applying ANSI color codes to `PS1` (e.g., setting a bright red prompt for `root` sessions and green for standard users) provides an immediate visual indicator of elevated privileges, preventing destructive accidental commands on production servers.

---

## 4. Prompt Customization Tools

- **Bash Prompt Generators**: Web-based interfaces used to visually compose customized `PS1` strings with color codes and elements, generating ready-to-paste snippets for `~/.bashrc`.
- **Powerline / Starship / Oh My Posh**: Advanced prompt engines offering status segments (e.g., Git branch status, system load, network interfaces, exit codes) rendered with custom powerline glyphs and color themes.

```markdown
# 
##  Overview

In cybersecurity and penetration testing, it is impossible to memorize every command, option, and flag. Developing **self-help skills** in the command line interface (CLI) is essential for daily efficiency, troubleshooting, and solving hands-on challenges.

This guide covers built-in Linux tools and resources to help you discover options, understand command syntax, and navigate terminal documentation without relying on external search engines.

---

##  Fundamental Command: `ls`

The `ls` (List) command is one of the most basic and frequently used Linux utilities.

* **Function:** Lists files and directories within the current working path or a specified path.
* **Basic Syntax:**
  ```bash
  ls

```

---

##  Built-in Terminal Help Methods

Linux provides three main internal methods to inspect tools and learn their usage flags.

### 1. Manual Pages (`man`)

The `man` command opens a full, interactive manual page for a tool, providing a complete overview, syntax rules, available flags, and descriptions.

* **Syntax:**
```bash
man <tool>

```


* **Example:**
```bash
man ls

```



#### Navigation Controls in `man` Pages

| Key | Action |
| --- | --- |
| `h` | Display the help screen for manual navigation |
| `Up` / `Down` Arrows | Scroll through the manual line-by-line |
| `q` | Quit the manual page and return to the terminal |

---

### 2. Quick Help Flags (`--help` / `-h`)

If you need a quick reference without opening a full pager, most Linux utilities support inline help flags that print options directly into the terminal window.

* **Syntax:**
```bash
<tool> --help
<tool> -h

```


* **Examples:**
```bash
ls --help
curl -h

```



---

### 3. Keyword Search (`apropos`)

When you know what action you want to perform but cannot remember the exact command name, `apropos` searches short descriptions across all manual pages on the system.

* **Syntax:**
```bash
apropos <keyword>

```


* **Example:**
```bash
apropos sudo

```


* **Output:** Displays a list of related tools and manual entries (such as `sudo`, `sudoers`, and `visudo`) along with brief explanations.

---

##  External Tool: ExplainShell

For complex commands with multiple stacked flags, [Explainshell.com](https://explainshell.com) is an external web resource that breaks down long command strings flag-by-flag.

* **Example Complex Command:**
```bash
ssh -i id_rsa -L 8080:127.0.0.1:80 user@target

```


* **Usage:** Paste the full string into Explainshell to see an itemized breakdown explaining each flag (`-i`, `-L`, target format) individually.

---

##  Cybersecurity & Hack The Box (HTB) Context

> [!IMPORTANT]
> **Why Terminal Self-Help Matters in Security Operations:**

1. **Offline & Restricted Environments:**
During Hack The Box (HTB) challenges, red teaming operations, or practical certification exams (such as OSCP), target environments or testing networks may restrict internet access. In these scenarios, built-in commands like `man` and `--help` are your primary resources for discovering functionality.
2. **Hands-On Learning & Tinkering:**
Systematic experimentation with different command flags builds deep familiarity with Linux subsystems and essential security utilities.

---

##  Summary Checklist

* Use `ls` to list directory contents.
* Run `man <tool>` for exhaustive documentation.
* Use `<tool> --help` or `<tool> -h` for quick option lookups.
* Search unknown utilities using `apropos <keyword>`.
* Deconstruct multi-flag commands using `explainshell.com`.
```markdown
# 

## Overview

When gaining initial access or spawning a shell on a target system, the first critical step is establishing **Situational Awareness**. This involves gathering detailed information about the system environment, current user privileges, running processes, network configurations, and operating system details.

This guide covers essential Linux commands for system enumeration and remote connection management via SSH.

---

## Essential Information Gathering Tools

Below is a reference table of built-in Linux commands used to analyze system specifications, network states, and active processes.

| Command | Description |
| :--- | :--- |
| `whoami` | Displays the username of the current effective user |
| `id` | Displays User ID (UID), Primary Group ID (GID), and secondary groups |
| `hostname` | Displays or sets the system host name |
| `uname` | Prints system kernel and hardware architecture information |
| `pwd` | Prints the absolute path of the current working directory |
| `ifconfig` | Configures or displays network interface parameters (legacy tool) |
| `ip` | Modern utility to manage and display routing, devices, and interfaces |
| `netstat` | Displays active network connections and socket statistics |
| `ss` | Fast utility for investigating sockets and checking open ports |
| `ps` | Reports a snapshot of current running processes |
| `who` | Lists users who are currently logged into the system |
| `env` | Prints or modifies environment variables |
| `lsblk` | Lists information about block storage devices and partitions |
| `lsusb` | Lists connected USB devices |
| `lsof` | Lists open files and the processes that opened them |
| `lspci` | Lists all devices and cards connected to PCI buses (e.g., GPU, NIC) |

---

## Remote Access via SSH

### What is SSH?
**SSH (Secure Shell)** is a cryptographic network protocol used to securely operate and manage remote systems over an encrypted command-line interface (CLI).

### Why Use SSH?
* **Low Resource Usage:** Does not require a Graphical User Interface (GUI).
* **Security:** Encrypts all traffic between the client and server.
* **Speed:** Fast and efficient execution over remote networks.

### Syntax and Example

```bash
ssh htb-student@[IP_ADDRESS]

```

Replace `[IP_ADDRESS]` with the target machine's IP address and provide the password when prompted.

---

## Detailed Command Analysis & Privilege Escalation Relevance

### 1. `hostname`

Displays the network name assigned to the system.

```bash
meteor0x1@htb[/htb]$ hostname
nixfund

```

---

### 2. `whoami`

Identifies the active user account associated with the current shell session.

```bash
cry0l1t3@htb[/htb]$ whoami
cry0l1t3

```

> **Security Note:** Executing `whoami` immediately after getting a reverse shell determines whether you have low-privileged user access or administrator (`root`) privileges.

---

### 3. `id`

Provides deep visibility into the current user's identity and group memberships.

```bash
cry0l1t3@htb[/htb]$ id
uid=1000(cry0l1t3) gid=1000(cry0l1t3) groups=1000(cry0l1t3),1337(hackthebox),4(adm),24(cdrom),27(sudo)...

```

#### Privilege Escalation Vectors via Group Membership:

* **`sudo` Group:** Membership allows execution of commands with elevated or `root` privileges.
* **`adm` Group:** Grants read access to system log files in `/var/log`, which may contain hardcoded credentials, sensitive tokens, or internal errors.
* **Custom Groups (e.g., `hackthebox`):** Non-standard groups often indicate custom application permissions or binary access that require thorough inspection.

---

### 4. `uname` (Kernel Version Enumeration)

Prints detailed information about the operating system kernel and hardware platform.

#### Complete System Information (`uname -a`)

```bash
cry0l1t3@htb[/htb]$ uname -a
Linux box 4.15.0-99-generic #100-Ubuntu SMP Wed Apr 22 20:32:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

* **Kernel Name:** Linux
* **Hostname:** box
* **Kernel Release:** 4.15.0-99-generic
* **Architecture:** x86_64

#### Specific Kernel Release (`uname -r`)

```bash
cry0l1t3@htb[/htb]$ uname -r
4.15.0-99-generic

```

> **Security Note:** Outdated kernel versions (such as `4.15.0-99-generic`) should be searched using utilities like `searchsploit` or public databases for known local kernel exploits (Local Privilege Escalation / LPE) to obtain `root` access.

---

## Key Takeaways & Practical Mindset

* **Post-Exploitation Routine:** Always execute `whoami`, `id`, and `uname -a` immediately upon getting access.
* **Continuous Enumeration:** Group memberships and kernel versions often reveal direct paths for Privilege Escalation.
* **Adaptability:** Command-line fluency improves with repeated practical application during labs and Hack The Box (HTB) exercises.

---

## Summary Checklist

* Run `whoami` to verify current shell user context.
* Inspect group memberships using `id` for `sudo` or `adm` privileges.
* Check system kernel version using `uname -r` for exploit research.
* Analyze system state using `ps`, `netstat`, and `ip`.
* Connect securely to remote targets using `ssh user@IP`.

```markdown
# Linux Navigation & Directory Management

Command-line navigation and directory management in Linux provide total control and speed over the operating system, serving as the text-based equivalent of graphical file managers.

---

## 1. Checking Current Directory (`pwd`)

Before navigating the filesystem, you must know your current location in the directory tree.

- **Command**: `pwd` (Print Working Directory)
- **Function**: Outputs the absolute path of your current working directory.
- **Example**:
  ```bash
  cry0l1t3@htb[~]$ pwd
  /home/cry0l1t3

```

---

## 2. Listing Directory Contents (`ls`)

The `ls` command is used to inspect files and directories within a specified path.

### A. Basic Listing (`ls`)

Prints standard visible files and folders without extra metadata.

### B. Long Listing Format (`ls -l`)

Displays detailed file attributes, permissions, ownership, and timestamps.

```bash
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:37 Desktop

```

#### Detailed Column Breakdown

| Column | Content | Detailed Explanation |
| --- | --- | --- |
| **1** | `drwxr-xr-x` | **File Type & Permissions**: `d` indicates a directory (`-` for file). Followed by Read, Write, and Execute (`rwx`) permissions for Owner, Group, and Others. |
| **2** | `2` | **Hard Links**: The number of hard links pointing to the file or directory. |
| **3** | `cry0l1t3` | **Owner**: The username of the account that owns the file. |
| **4** | `htbacademy` | **Group Owner**: The primary group associated with the file. |
| **5** | `4096` | **Size**: File size in bytes (or directory metadata size). |
| **6** | `Nov 13 17:37` | **Modification Time**: Date and time of last content modification. |
| **7** | `Desktop` | **Name**: Name of the file or directory. |

> **Block Allocation Note**: The line `total 32` displayed at the top of long listings indicates total storage blocks allocated (e.g., $32 \times 1024\text{ bytes} = 32\text{ KB}$).

### C. Viewing Hidden Files (`ls -la`)

In Linux, files and directories starting with a dot (`.`) are hidden by default (e.g., `.bashrc`, `.bash_history`).

* **Command**: `ls -la` (combines `-l` for detailed view and `-a` for all files).

### D. Inspecting Remote Directories

You can view the contents of any directory without navigating into it by supplying the path argument:

```bash
ls -l /var/

```

---

## 3. Directory Navigation (`cd`)

The `cd` (Change Directory) command is used to traverse the Linux filesystem hierarchy.

### A. Absolute vs. Relative Navigation

* **Absolute Path**: Specifies the full path starting from root (`/`).
```bash
cd /dev/shm

```



### B. Previous Directory Trick (`cd -`)

Returns immediately to the directory you were located in prior to the last `cd` command:

```bash
cd -

```

### C. Tab Auto-Completion

* Pressing `[TAB]` once automatically completes folder or file names.
* Pressing `[TAB]` twice lists all matching options starting with the typed characters.

### D. Current (`.`) and Parent (`..`) Directories

* `.` (Single Dot): Represents the current working directory.
* `..` (Double Dots): Represents the parent directory one level above.
* **Move Back One Level**:
```bash
cd ..

```



---

## 4. Terminal Housekeeping & History

### Screen Clearing

* **Command**: `clear`
* **Chained Command**: `cd /dev/shm && clear`
* **Keyboard Shortcut**: `[Ctrl] + [L]`

### Command History Navigation

* **Arrow Keys (`↑` / `↓`)**: Cycle backward and forward through executed command history.
* **Reverse History Search (`[Ctrl] + [R]`)**: Type keywords to search and recall past commands directly from history (`.bash_history`).

---

## 5. Cybersecurity & Hack The Box (HTB) Applications

1. **Shared Memory (`/dev/shm`)**:
`/dev/shm` is a temporary filesystem backed directly by physical RAM. It is typically configured with world-writable permissions (`777`), making it an optimal **Staging Area** for uploading exploit scripts, payloads, and tools during privilege escalation attempts.
2. **Hidden Files Enumeration (`ls -la`)**:
Critical operational artifacts, SSH private keys (`.ssh/id_rsa`), configuration files, and command logs (`.bash_history`) reside inside hidden files (`.`). Running `ls -la` is essential during target enumeration.
3. **Operational Speed**:
Mastering `[TAB]` auto-completion, `[Ctrl] + [R]` history search, and `cd -` navigation minimizes delays during time-sensitive CTF challenges and pentesting engagements.
```markdown
# Linux File & Directory Management

Managing files and directories via the Command Line Interface (CLI) provides speed, automation, and total control over system structures compared to graphical file managers.

---

## 1. Creating Files & Directories

### A. Creating Empty Files (`touch`)
The `touch` command creates a new empty file immediately, or updates the access and modification timestamps of an existing file.

- **Syntax**:
  ```bash
  touch <filename>

```

* **Example**:
```bash
touch info.txt

```



### B. Creating Directories (`mkdir`)

The `mkdir` (Make Directory) command creates a new folder.

* **Syntax**:
```bash
mkdir <directory_name>

```


* **Example**:
```bash
mkdir Storage

```



### C. Creating Nested Directories (`mkdir -p`)

Attempting to create a subdirectory inside a non-existent parent directory throws an error. The `-p` (Parents) flag automatically creates all required parent and child directories in a single command.

* **Example**:
```bash
mkdir -p Storage/local/user/documents

```



### D. Visualizing Structure (`tree`)

The `tree` command displays directories and subdirectories in a visual, organized tree layout alongside summary statistics.

* **Example**:
```bash
tree .

```


* **Sample Output**:
```text
.
├── info.txt
└── Storage
    └── local
        └── user
            └── documents
4 directories, 1 file

```



### E. Direct Creation Using Current Directory (`.`)

The single dot (`.`) represents the current working directory. Files can be created inside distant subdirectories without leaving your current location:

```bash
touch ./Storage/local/user/userinfo.txt

```

---

## 2. Moving and Renaming (`mv`)

The `mv` (Move) command performs two distinct functions based on the destination input: renaming files or moving them across directories.

* **Syntax**:
```bash
mv <source> <destination_or_new_name>

```



### A. Renaming a File

If the destination argument is a new filename in the same directory, `mv` renames the file:

```bash
mv info.txt information.txt

```

### B. Moving Multiple Files to a Directory

Multiple files can be moved simultaneously by specifying all source files followed by the target directory:

```bash
touch readme.txt
mv information.txt readme.txt Storage/

```

---

## 3. Copying Files (`cp`)

The `cp` (Copy) command duplicates a file from a source path to a target directory while leaving the original file intact.

* **Syntax**:
```bash
cp <source_file> <destination_directory>

```


* **Example**:
```bash
cp Storage/readme.txt Storage/local/

```



---


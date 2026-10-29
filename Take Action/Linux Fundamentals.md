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

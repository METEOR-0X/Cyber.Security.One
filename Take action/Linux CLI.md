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

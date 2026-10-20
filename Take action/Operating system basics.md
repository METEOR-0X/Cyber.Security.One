# Operating System Architecture & System Layers

Hardware components (CPU, RAM, Storage) require an Operating System (OS) to manage resources and execute software efficiently. Operating systems divide memory and execution environments into two distinct spaces to ensure stability and security:

---

## 1. Kernel Space

The **Kernel** is the core component of an operating system. It acts as an abstraction layer between hardware and running applications.

- **Unrestricted Access**: Executes in ring 0 (privileged mode), granting complete, direct access to physical hardware resources.
- **Resource Management**: Directly handles low-level system operations including CPU scheduling, memory allocation, hardware driver communications, and I/O management.
- **System Stability**: Misbehavior or fatal errors within kernel space cause total system failure (e.g., kernel panic or Blue Screen of Death).

---

## 2. User Space

The **User Space** is the unprivileged layer where standard applications, processes, and user interfaces execute.

- **Restricted Access**: Operates in ring 3 (unprivileged mode) with no direct permission to access underlying physical hardware.
- **Process Isolation**: Prevents user-level software (e.g., web browsers, text editors, custom applications) from crashing or modifying other running processes or system memory.
- **System Calls**: When a user-space application requires hardware resources (such as reading a file from storage or opening a network connection), it cannot perform the action directly. Instead, it must issue a **System Call (Syscall)** to request the Kernel to execute the operation on its behalf.

- # Core Responsibilities of an Operating System

An Operating System (OS) serves as the primary software layer managing computer hardware and system resources. Below are its primary core responsibilities:

---

## OS Management Functions

| Responsibility | What the OS Does | Real-World Example |
| --- | --- | --- |
| **Process Management** | Creates, schedules, prioritizes, and terminates running programs. The OS allocates CPU time to each process, enabling seamless multitasking. | Running a web browser, music player, and code editor simultaneously without system freezing. |
| **Memory Management** | Allocates RAM to active processes, isolates memory spaces to prevent interference, and reclaims memory upon application closure. Uses virtual memory (swap/page file) when physical RAM is low. | Opening multiple heavy applications at once while the OS prevents them from overwriting each other's memory space. |
| **File System Management** | Organizes data into structured directories, handles file paths, manages access permissions, and maintains file metadata (e.g., name, size, type, timestamps). | Creating folders, saving documents, or setting a file to "read-only" status. |
| **User Management** | Controls multi-user environments, handles authentication (passwords, biometrics), and enforces permission boundaries to restrict access to sensitive resources. | Logging into a personal user account while keeping personal files inaccessible to other account profiles. |
| **Device Management** | Loads hardware drivers and provides a Universal Hardware Abstraction Layer (HAL), allowing applications to communicate with peripheral hardware via standardized commands. | Plugging in a new USB mouse, printer, or external drive and having the OS instantly recognize and interact with it. |

# Operating System Security Core Pillars

Operating System (OS) security consists of several layers of defense designed to protect hardware, system configurations, and user data from unauthorized access, accidental damage, or malicious software.

---

## Key Security Mechanisms

- **Authentication**: Verifies user identity before granting access to system resources. Common mechanisms include traditional user/password credentials, multi-factor authentication (MFA), and biometric systems (e.g., fingerprint scanners, facial recognition).
- **Permissions & Access Control**: Controls granular read, write, and execution privileges (`rwx`) for files, directories, and applications based on defined access control lists (ACLs) and user roles.
- **Process Isolation**: Ensures each process operates within its own isolated memory boundary (separating kernel space from user space). This sandboxing model prevents a compromised or faulty process from reading or modifying the memory of other processes.
- **System Protection**: Safeguards critical core files, kernel memory space, and registry/system configurations from unauthorized tampering using features like File Integrity Monitoring (FIM), Integrity Measurement, and User Account Control (UAC).

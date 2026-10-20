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

# Before learning about security, we need to understand the computer we use and how it works

## 1- Inside a computer

Inside a computer, all the elements are like our body: the motherboard is the skeleton and nerves, RAM is short-term memory, the PSU is the heart and lungs, the HDD or SSD is long-term memory, the GPU is the visual cortex, and the CPU is the brain.

| Component | Analogy / Function |
| --- | --- |
| **Motherboard** | Skeleton and nerves |
| **RAM** | Short-term memory |
| **PSU** | Heart and lungs |
| **HDD / SSD** | Long-term memory |
| **GPU** | Visual cortex |
| **CPU** | Brain |

---

## 2- When you click in start button

1. **Power Signal**: When you press the power button, a signal is sent to the PSU to allow power to flow.
2. **UEFI / BIOS Initialization**: When the components start running, they lack the awareness to know what to do. That is made possible by a program already stored on the motherboard, which is UEFI, or what we can also call BIOS.
3. **Hardware Self-Test**: Now, all components need to be fully functional and present. This is also something UEFI or BIOS can do for us; it tests all the components to make sure they are working properly and that everything the system needs is available.
4. **Select Boot Device**: In the 'Select Boot Device' step, UEFI is involved again. Now it starts prioritizing and specifying which storage devices to check first in order to boot up our operating system.
5. **Bootloader & OS Load**: Once the system identifies the boot device, the bootloader is initiated to copy the Operating System from storage into Random Access Memory (RAM). After the OS is fully loaded, UEFI relinquishes hardware control to the Operating System.

---

## 3- Type of Computers

You might think that computers are just laptops and desktops, but there are many types of computers out there. There are stationary computers that stay in one place, like desktops, and portable ones that we can take with us anywhere, like laptops. Now you should know all the main types of computers:

- **Laptop**: The first type that we all know. It comes with a screen and a keyboard, and you can take it anywhere with you to perform various tasks.
- **Desktop**: The second type, which stays fixed in one place. It is larger in size, which allows for better cooling, but it also requires more power.
- **Workstation**: The third type. It is also fixed in one place, but it delivers high performance for heavy, demanding software and complex workloads.
- **Server**: The fourth type. It provides multiple services over a network, which makes it large in size, equipped with a huge amount of RAM, and in need of high-performance cooling.

---

## 4- Hidden computers

After looking at the common computer types, let's discuss other types that many people might not recognize as computers:

- **Smartphone**: A compact computer optimized for long battery life, high mobility, and cellular connectivity (e.g., iPhones and Android devices).
- **Tablet**: A touch-first computer with a larger screen that operates primarily through touch input rather than a physical keyboard or mouse (e.g., iPads or digital drawing tablets).
- **IoT Device**: A specialized device connected to a network that performs a single specific function, such as a smart doorbell or a fitness tracker.
- **Embedded Computer**: A single-purpose computer integrated directly into another machine to execute pre-programmed tasks without requiring an internet connection (e.g., coffee maker controllers or automatic door sensors).

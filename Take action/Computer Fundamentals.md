# Before learning about security, we need to understand the computer we use and how it works

## - Inside a computer

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

## - When you click in start button

1. **Power Signal**: When you press the power button, a signal is sent to the PSU to allow power to flow.
2. **UEFI / BIOS Initialization**: When the components start running, they lack the awareness to know what to do. That is made possible by a program already stored on the motherboard, which is UEFI, or what we can also call BIOS.
3. **Hardware Self-Test**: Now, all components need to be fully functional and present. This is also something UEFI or BIOS can do for us; it tests all the components to make sure they are working properly and that everything the system needs is available.
4. **Select Boot Device**: In the 'Select Boot Device' step, UEFI is involved again. Now it starts prioritizing and specifying which storage devices to check first in order to boot up our operating system.
5. **Bootloader & OS Load**: Once the system identifies the boot device, the bootloader is initiated to copy the Operating System from storage into Random Access Memory (RAM). After the OS is fully loaded, UEFI relinquishes hardware control to the Operating System.

---

## - Type of Computers

You might think that computers are just laptops and desktops, but there are many types of computers out there. There are stationary computers that stay in one place, like desktops, and portable ones that we can take with us anywhere, like laptops. Now you should know all the main types of computers:

- **Laptop**: The first type that we all know. It comes with a screen and a keyboard, and you can take it anywhere with you to perform various tasks.
- **Desktop**: The second type, which stays fixed in one place. It is larger in size, which allows for better cooling, but it also requires more power.
- **Workstation**: The third type. It is also fixed in one place, but it delivers high performance for heavy, demanding software and complex workloads.
- **Server**: The fourth type. It provides multiple services over a network, which makes it large in size, equipped with a huge amount of RAM, and in need of high-performance cooling.

---

## - Hidden computers

After looking at the common computer types, let's discuss other types that many people might not recognize as computers:

- **Smartphone**: A compact computer optimized for long battery life, high mobility, and cellular connectivity (e.g., iPhones and Android devices).
- **Tablet**: A touch-first computer with a larger screen that operates primarily through touch input rather than a physical keyboard or mouse (e.g., iPads or digital drawing tablets).
- **IoT Device**: A specialized device connected to a network that performs a single specific function, such as a smart doorbell or a fitness tracker.
- **Embedded Computer**: A single-purpose computer integrated directly into another machine to execute pre-programmed tasks without requiring an internet connection (e.g., coffee maker controllers or automatic door sensors).
# Web Communication

## HTTP Protocol Overview

HTTP (Hypertext Transfer Protocol) is the fundamental protocol used for communication on the web. It acts as a bridge between a client (such as your web browser) and a web server.

- **Request & Response Process**: When you want to visit a website, your client sends an HTTP request to the server. The server processes this request and sends back an HTTP response containing the requested resources (for example, an HTML file to display the webpage).

---

## The Stateless Problem

HTTP is a **stateless protocol**. This means that the server treats every request as completely independent.

- **No Memory**: The server does not remember previous requests or users.
- **Example**: If you send a request to a server and then send another request just 1 second later, the server will not recognize that both requests came from the same user.

---

## The Solution: Sessions & Cookies

To overcome the stateless limitation and allow servers to remember users across multiple requests, session management using **Cookies** was introduced:

1. **ID Creation**: When you make a request (such as logging into a website), the server generates a unique **ID** for your session and stores it in a database.
2. **Sending Cookies**: Along with the requested page, the server sends this unique ID back to your browser.
3. **Browser Storage**: Your browser automatically saves this ID locally as a **Cookie**.
4. **Automatic Identification**: On subsequent requests, your browser automatically sends this Cookie back to the server. The server verifies the ID against its database.

### Practical Benefit
Because of Cookies, you do not need to re-login every time you navigate to a new page. As long as your browser presents a valid session ID, the server recognizes you as an authenticated user.
# Technical Analysis: HTTP Methods & Practical Application of GET Request

According to the official specification, the protocol defines **9 basic methods** for interaction. Among them, the **GET** method is the most widely used.

---

## The 9 Basic HTTP Methods

| Method | Description / Purpose |
| --- | --- |
| **GET** | Requests and retrieves data from the server without modifying it. |
| **POST** | Sends new data to the server (e.g., submitting a registration form). |
| **PUT** | Updates or replaces an entire file/resource on the server. |
| **DELETE** | Removes a specific resource from the server. |
| **PATCH** | Performs partial modifications to existing data on the server. |
| **HEAD** | Requests only the response headers (to check existence or metadata) without downloading the content body. |
| **OPTIONS** | Queries the server to find out which HTTP methods are supported/allowed. |
| **CONNECT** | Establishes a network tunnel to the server (commonly used with Proxies). |
| **TRACE** | Performs a loop-back test along the path to the target resource (used for diagnostic and debugging purposes). |

# HTTP Response Structure

When you request any website through a browser, your request is sent to the server, and the server responds back. An HTTP response strictly consists of two main parts:

---

## 1. Response Headers

The response header contains metadata and parameters regarding the response and the requested resources. It includes key information such as:

- **Content-Type**: Specifies the type of file returned (e.g., HTML, CSS, JavaScript, or plain text).
- **Content-Length**: Defines the size of the returned file/data.
- **Set-Cookie**: Transmits cookie parameters and session data to be stored in the browser.

---

## 2. Response Body

The response body contains the actual payload or content requested by the client. This typically includes:

- HTML source code for structural rendering.
- CSS and JavaScript files.
- Media assets such as images, videos, and documents.

- # Virtualization Basics

## The Traditional Model (Bare Metal)

In the past, running a web application required dedicated hardware—a complete physical server deployed specifically for that single application.

- **Low Resource Utilization**: A single web application typically consumed only **20% to 30%** of the server's total processing power and performance capacity.
- **High Costs & Inefficiency**: Physical servers are expensive to purchase, maintain, and require significant deployment time, leading to wasted hardware resources.

---

## The Solution: Virtualization

Virtualization solves resource underutilization by allowing multiple applications and operating systems to run concurrently on a single physical server. Each application operates within an isolated environment, behaving as if it has its own dedicated physical hardware.

---

## The Role of the Hypervisor

The key technology enabling virtualization is the **Hypervisor** (also known as a Virtual Machine Monitor):

- **Resource Allocation**: The hypervisor acts as an abstraction layer between the physical server and the virtual instances. It dynamically allocates specific amounts of **CPU, RAM, and Storage** to each virtual environment based on its needs.
- **Isolation & Optimization**: By partitioning a single hardware unit into isolated virtual environments, organizations can maximize server capacity, reduce operational costs, and streamline deployment times.

# Types of Hypervisors & Containers

As established, a **hypervisor** is the core software that creates, isolates, and manages virtual machines (VMs). There are two main types of hypervisors, along with modern containerization technologies:

---

## 1. Type 1: Native / Bare-Metal Hypervisor

A Type 1 hypervisor installs and runs directly on the physical hardware without needing a host operating system.

- **High Performance & Speed**: Direct hardware access eliminates host OS overhead, yielding maximum processing speed and minimal latency.
- **Enterprise Use Cases**: Ideal for data centers, cloud infrastructure, and production servers.
- **Examples**: VMware ESXi, Proxmox VE, Microsoft Hyper-V.

---

## 2. Type 2: Hosted Hypervisor

A Type 2 hypervisor runs as a standard software application on top of an existing host operating system (e.g., Windows, macOS, or Linux).

- **Environment Isolation**: Provides a sandboxed guest environment. Any issues, malware executions, or system crashes inside the VM remain isolated from your main host OS.
- **Resource Allocation**: The hypervisor requests virtualized CPU, RAM, and storage allocations directly from the host operating system.
- **Common Use Cases**: Personal lab environments, malware testing, software development, and running secondary OS distributions (e.g., Kali Linux).
- **Examples**: Oracle VirtualBox, VMware Workstation.

---

## 3. Containers (Lightweight Virtualization)

Containers offer a lightweight alternative to full virtual machines by running isolated applications without requiring a standalone guest operating system.

- **Kernel Sharing**: Containers leverage and share the host system's kernel rather than running a full OS stack.
- **Efficiency**: They launch in seconds and consume significantly fewer CPU and RAM resources compared to VMs.
- **Tooling**: **Docker** is the industry-standard software platform used to build, deploy, and manage containerized environments.

# Cloud Computing

## What is Cloud Computing?

Cloud computing is the delivery of computing services—including servers, storage, databases, networking, software, and CPU/RAM resources—over the internet ("the cloud").

Instead of purchasing, maintaining, and housing physical servers and data centers, you rent access to these infrastructure services from cloud providers on an as-needed basis.

---

# Problems Solved by Cloud Computing

Cloud computing resolves critical operational and infrastructural challenges faced by modern applications:

---

## 1. Global Reach & Low Latency
Deploying an application globally traditionally required physical data centers in multiple continents. With cloud computing, you can launch virtual servers in strategic geographical regions worldwide in seconds, ensuring low latency and high performance for international users.

## 2. Dynamic Scalability & Elasticity
Physical hardware cannot automatically adapt to traffic spikes. Cloud infrastructure provides automatic scaling, allowing systems to dynamically increase resources during high-traffic periods and scale down when demand drops to optimize costs.

## 3. High Availability & Disaster Recovery
Relying on a single physical server exposes applications to single points of failure. Cloud platforms offer built-in redundancy, continuous data backups, and multi-region failover configurations to maintain maximum uptime and business continuity.

## 4. Elimination of Operational Overhead
Managing physical hardware requires ongoing maintenance, cooling, security, and hardware replacement. Cloud providers handle all physical infrastructure management, allowing teams to focus entirely on software development and application security.

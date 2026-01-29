Day 2 Linux Architecture, Processes, and systemd
Linux Architecture 
```text
Applications & User
        |
    User Space
        |
   System Calls
        |
   Linux Kernel
        |
     Hardware

# 🔧 Core Components of Linux

---

## 1️⃣ Linux Kernel

### What is it?
The **Linux Kernel** is the core part of the operating system that manages hardware resources and allows software to communicate with hardware.

### What does it do?
- **CPU Management** – Decides which process uses the CPU and for how long  
- **Memory Management** – Allocates and frees RAM for running programs  
- **Device Management** – Controls hardware devices via drivers (keyboard, disk, network, etc.)  
- **Process Management** – Creates, schedules, and terminates processes  
- **System Calls** – Provides a way for applications to request services from the kernel  

### Simple Analogy
> The kernel is like a **manager** that controls and coordinates communication between hardware and software.

---

## 2️⃣ User Space

### What is it?
User space is a **restricted memory area** where all user applications and programs run.  
It is **isolated from the core operating system (Kernel)** for security and stability.

### What lives here?
- **User Applications**
  - Web browsers
  - Media players
  - Video games
- **Shells**
  - Command-line interfaces like `bash` or `zsh`
- **System Daemons**
  - Background services like `systemd` or `sshd` that manage the system behind the scenes

---

## 3️⃣ Init System / systemd

### What is it?
The **init system** is the **first process started by the kernel** during the boot sequence and the **parent of all other processes**.

### What is systemd?
- `systemd` is the modern init system used by most Linux distributions today
- It replaced the older **SysV init** system

---

## ⚙️ How Processes Work in Linux

### What is a Process?
A **process** is a running instance of a program executed by the operating system.

**Example:**
- Instagram installed → Program  
- Instagram opened and used → Process  

### How are processes created?
Linux:
- Creates processes using `fork()`
- Runs programs using `exec()`
- Manages them using the **kernel scheduler**

---

## 🔍 systemd Deep Dive

### Why systemd is important for DevOps?
- Start, stop, enable services easily using `systemctl`
- Ensures services start in the correct order
- View and manage logs

---

## 🔄 Process States

### What are process states?
Process states show what a process is doing at a given moment — running, waiting, ready, or finished.

| Process State | Code | Meaning |
|--------------|------|--------|
| New | N | Process is being created |
| Ready | R | Ready to run, waiting for CPU |
| Running | R | Currently executing on CPU |
| Sleeping (Interruptible) | S | Waiting for I/O or event |
| Sleeping (Uninterruptible) | D | Waiting for disk I/O |
| Stopped | T | Stopped by signal (Ctrl+Z) |
| Zombie | Z | Process finished but not cleaned up |
| Terminated | X | Process is fully removed |

---

## 🛠️ 5 Daily-Use Linux Commands

```bash
ls        # List files and directories
cd        # Navigate between directories
grep      # Search text/logs (very common in debugging)
ps        # Check running processes
systemctl status nginx   # Check service health

-----------------------------------------------------

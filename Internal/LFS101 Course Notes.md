---
dg-publish: true
---
# LFS101 Course Notes
___
## 1. Linux Philosophy and Concepts

**History** - Linux is a Free and Open Source Operating System (OS) Kernel initially developed for Intel x86 systems. It was created by Linus Torvalds in August 1991 along with a compilation of his thoughts to create a full-fledged Operating System. In 1992, Linux was re-licensed under GPL (General Public License) by GNU (GNU's Not Unix), an organisation under Free Software Foundation (FSF). By the late 1990s, the first general purpose GNU/Linux distributions started appearing. Today, Linux powers more than half of the servers on the internet, the majority of smartphones (via the Android system, which is built on top of Linux), more than 90 percent of the public cloud workload, and all of the world’s most powerful supercomputers.

Read more upon GNU, FSF, Richard Stallman, etc. 

**Philosophy** - Linux philosophy borrows from UNIX Operating Systems. Files are stored in a hierarchical filesystem, with the top node of the system being the **root** or simply "**/**" (FHS). Linux makes its components available via files or objects that look like files. Processes, devices, and network sockets are all represented by file-like objects and can often be worked with using the same utilities used for regular files. Linux is a fully multitasking (i.e., multiple threads of execution are performed simultaneously), multiuser operating system with built-in networking and service processes known as daemons in the UNIX world. _Linux was inspired by UNIX, but it is not UNIX._

**Why is the mascot a Penguin?**
Linux is a penguin named Tux because its creator, Linus Torvalds, was bitten by a small penguin during a zoo visit in Australia

**Why the name Linux?**
Linux is named after its creator, Linus Torvalds, as a blend of his first name and "Unix," the operating system it was inspired by, though he originally wanted to call it "Freax" (free, freak, X); the server administrator hosting the code, Ari Lemmke, created the "Linux" directory, and the name stuck. 

**Terminologies**
1. Kernel - The Linux Kernel. Acts like the intermediary between the hardware (Physical) and software (Operating System).
2. Distribution/Distro - Collection of software (including a kernel) that forms a complete Operating System (GNU/Linux). Eg. Debian, RHEL, Arch
3. Bootloader - A program that boots the Operating System. Eg. GRUB, ISOLinux
4. Service - A program that runs as a background process. Eg. httpd, named, etc.
5. Filesystem - Method of storing and organising files. Eg. ext3, ext4, fat, etc.
6. X Window System - Protocol for building Graphical Subsystems on GNU/Linux.
7. Command Line - A text based interface to command the OS.
8. Shell - Command Line Interpreter. Eg. BASH, ZSH, etc.

**Linux Distributions** - The Linux kernel is the core of the operating system. A full Linux distribution consists of the kernel plus a number of other software tools for file-related operations, user management, and software package management. Each of these tools provides a part of the complete system. Each tool is often its own separate project, with its own developers working to perfect that piece of the system. Linux distributions may be based on different kernel versions.
___
## 2. Linux Basics and System Startup

**The Boot Process** - The Linux boot process is the procedure for initializing the system. It consists of everything that happens from when the computer power is first switched on until the user interface is fully operational.

**At a Glance**
Power On -> BIOS -> Master Boot Record (MBR) or EFI Partition -> Boot Loader (Eg. GRUB) -> Kernel -> Initial RAM disk - intramfs -> sbin/init (parent process) -> Command Shell using Getty -> GUI (X Window or Wayland)

1. **BIOS (Basic Input/Output System)** - When the computer is powered on, the Basic Input/Output System (BIOS) initializes the hardware, including the screen and keyboard, and tests the main memory. This process is also called POST (Power On Self Test). The BIOS software is stored on a read-only memory (ROM) chip on the motherboard. After this, the remainder of the boot process is controlled by the operating system (OS).
2. **Master Boot Record (MBR), EFI Partition, and Boot Loader** - Once the POST is completed, system control passes from the BIOS to the boot loader. The boot loader is usually stored on one of the system’s storage devices, such as a hard disk or SSD drive, either in the boot sector (for traditional BIOS/MBR systems) or the EFI partition (for more recent (Unified) Extensible Firmware Interface or EFI/UEFI systems). Up to this stage, the machine does not access any mass storage media. Then, information on the date, time, and the most important peripherals are loaded from the CMOS values (after a technology used for the battery-powered memory store, which allows the system to keep track of the date and time even when it is powered off).
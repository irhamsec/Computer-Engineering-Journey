# FreeDOS

> FreeDOS is a free and open-source operating system that is compatible with MS-DOS. During Phase 2 of this project, FreeDOS was used to explore the boot process of a classic IBM PC-compatible computer and to better understand how operating systems interact with hardware.

---

# Introduction

After building a virtual Intel 80486 computer using 86Box, the next objective was installing an operating system.

Rather than using a modern operating system such as Windows or Linux, I chose **FreeDOS**.

The reason was simple.

Modern operating systems are extremely large and complex. Many important concepts, such as BIOS, the Master Boot Record (MBR), partitioning, formatting, and the FAT16 filesystem, are hidden from the user.

FreeDOS provides a much simpler environment where these low-level concepts are easier to observe and understand.

Instead of focusing on graphical interfaces, FreeDOS helped me understand how a computer starts from power-on and eventually reaches an operating system.

---

# What is FreeDOS?

FreeDOS is an open-source operating system designed to be compatible with **MS-DOS (Microsoft Disk Operating System).**

It provides many of the same capabilities as MS-DOS, including:

- Command-line interface (CLI)
- FAT filesystem support
- DOS utilities
- Compatibility with many DOS applications

Unlike MS-DOS, FreeDOS is actively maintained and freely available.

---

# Why Does FreeDOS Exist?

MS-DOS was originally developed by Microsoft and became one of the most widely used operating systems for IBM PC-compatible computers.

However, MS-DOS is proprietary software.

FreeDOS was created to provide a free, open-source alternative that remains compatible with DOS software while continuing to support older hardware and educational projects.

Today, FreeDOS is commonly used for:

- Learning computer architecture
- Running legacy DOS software
- BIOS updates
- Embedded systems
- Retro computing
- Computer restoration projects

---

# Why Did I Use FreeDOS?

The purpose of this project was not simply to install an operating system.

Instead, the goal was to understand the entire startup process of a personal computer.

FreeDOS was ideal because it exposes many concepts that modern operating systems hide.

Using FreeDOS allowed me to study:

- BIOS
- CMOS
- Boot process
- Master Boot Record (MBR)
- Partitioning
- Formatting
- FAT16
- Command-line operation

This made FreeDOS an excellent educational operating system for learning how classic PCs work.

---

# Installing FreeDOS During Phase 2

The installation process followed several important steps.

```
Create Virtual Hard Disk

↓

Boot from FreeDOS Installation CD

↓

Partition the Hard Disk

↓

Format the Partition

↓

Create FAT16 Filesystem

↓

Copy FreeDOS System Files

↓

Install Bootloader

↓

Restart Computer

↓

Boot from Hard Disk
```

Each of these steps introduced a new concept that became its own documentation chapter.

---

# Booting FreeDOS

One of the biggest lessons during this project was understanding what happens before the FreeDOS prompt appears.

The sequence is:

```
Power On

↓

CPU Reset

↓

BIOS

↓

POST

↓

Read CMOS

↓

Detect Hardware

↓

Select Boot Device

↓

Load MBR

↓

Execute Bootloader

↓

Read FAT16 Filesystem

↓

Load FreeDOS

↓

C:\>
```

Before this project, I thought the operating system started immediately after powering on the computer.

I now understand that many stages occur before the operating system gains control.

---

# FreeDOS Command-Line Interface

Unlike modern operating systems, FreeDOS primarily uses a **Command-Line Interface (CLI).**

Instead of interacting with windows and icons, commands are typed directly into the command prompt.

Example:

```
C:\>
```

Common commands include:

```
DIR

CD

COPY

DEL

TYPE

FORMAT

FDISK
```

Although simple, the command line provides direct control over the operating system and storage devices.

---

# System Files

FreeDOS requires several important system files during startup.

These files are loaded after the bootloader transfers control to the operating system.

Examples include:

- KERNEL.SYS
- COMMAND.COM
- CONFIG.SYS
- AUTOEXEC.BAT

Each file has a different role in the startup process.

---

# FreeDOS and FAT16

FreeDOS stores its files inside a FAT16 filesystem.

For example:

```
Hard Disk

↓

Partition

↓

FAT16

↓

COMMAND.COM

KERNEL.SYS

AUTOEXEC.BAT

CONFIG.SYS
```

Without FAT16, FreeDOS would have no organized method of storing or locating files.

---

# FreeDOS During This Project

Throughout Phase 2, FreeDOS became much more than an operating system.

It served as a practical platform for understanding how IBM PC-compatible computers operate.

Some of the concepts explored included:

- Installing an operating system
- Partitioning a hard disk
- Formatting a partition
- Creating a FAT16 filesystem
- Booting from an IDE hard disk
- Using an ATAPI CD-ROM for installation
- Understanding BIOS startup
- Learning DOS commands

Rather than simply reading about these concepts, I was able to observe each step during the installation process.

---

# Advantages of FreeDOS for Learning

Compared to modern operating systems, FreeDOS offers several educational advantages.

- Small and lightweight
- Easy to understand
- Minimal hardware requirements
- Closely follows the traditional IBM PC boot process
- Excellent for studying classic computer architecture
- Ideal for retro computing and embedded systems education

These characteristics make FreeDOS an excellent choice for learning low-level computer systems.

---

# FreeDOS vs Modern Operating Systems

| FreeDOS | Modern Operating Systems |
|----------|--------------------------|
| Command-line interface | Graphical interface |
| Small codebase | Very large codebase |
| Easy to understand | Much more complex |
| Direct hardware interaction | Hardware abstraction layers |
| Ideal for education | Designed for everyday computing |

Studying FreeDOS first makes it easier to understand the foundations before moving to more complex operating systems.

---

# Common Misconceptions

## "FreeDOS is obsolete."

Although FreeDOS is based on DOS, it remains useful for education, legacy software, embedded applications, and retro computing.

---

## "FreeDOS is just MS-DOS."

Incorrect.

FreeDOS is a separate open-source operating system that aims to be compatible with MS-DOS.

---

## "FreeDOS is only useful for old computers."

FreeDOS is also valuable for learning how personal computers boot and how operating systems interact with hardware.

---

## "Modern operating systems no longer use the concepts learned from FreeDOS."

Although modern systems are much more advanced, many fundamental concepts remain the same.

Examples include:

- Bootloaders
- Filesystems
- Partitioning
- Operating system loading
- Hardware initialization

Understanding FreeDOS provides a strong foundation for learning modern systems.

---

# Questions I Asked During This Phase

## Why didn't we install Windows?

Because the goal was to understand the computer, not simply use it.

FreeDOS exposes low-level concepts that are hidden in modern operating systems.

---

## Why was FreeDOS perfect for a 486 PC?

Because FreeDOS was designed for IBM PC-compatible hardware and works well with classic computer architectures.

---

## Why did we use FAT16 instead of NTFS?

FAT16 matches the capabilities and historical context of DOS systems and is much simpler to understand.

---

## Can FreeDOS still be used today?

Yes.

It remains useful for education, retro computing, legacy software, BIOS updates, and embedded system applications.

---

# Key Takeaways

- FreeDOS is a free and open-source DOS-compatible operating system.
- FreeDOS was chosen because it exposes the fundamentals of PC architecture.
- Installing FreeDOS required partitioning, formatting, and creating a FAT16 filesystem.
- FreeDOS helped demonstrate the complete BIOS-to-operating-system boot process.
- Understanding FreeDOS provides a strong foundation for learning modern operating systems and firmware development.

---

# Connection to Other Topics

FreeDOS brings together every concept studied during Phase 2.

- **86Box.md** – FreeDOS was installed inside the virtual 486 computer.
- **BIOS.md** – BIOS initializes the hardware before loading FreeDOS.
- **CMOS.md** – CMOS stores the BIOS configuration used during startup.
- **Boot-Process.md** – The boot process eventually transfers control to FreeDOS.
- **MBR.md** – The Master Boot Record begins loading the operating system.
- **Partitioning.md** – FreeDOS is installed inside a partition.
- **Formatting.md** – The partition must be formatted before installation.
- **FAT16.md** – FreeDOS stores all of its files inside the FAT16 filesystem.
- **IDE-and-ATAPI.md** – FreeDOS was installed from an ATAPI CD-ROM onto an IDE hard disk.

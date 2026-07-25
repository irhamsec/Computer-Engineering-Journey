# Phase 2 – Building a 486 PC & Installing FreeDOS

> Building a virtual Intel 80486 computer from scratch using **86Box** while learning how a PC boots from power-on to the DOS command prompt.

---

# Overview

Phase 2 focuses on understanding the complete boot process of a classic IBM PC-compatible computer by building a virtual Intel 80486 system inside **86Box** and installing **FreeDOS 1.4**.

Rather than treating the installation as a simple operating system setup, this project explores the engineering concepts that occur before an operating system is even loaded.

Throughout this phase, I learned how firmware initializes hardware, how storage devices are detected, how a hard disk is prepared for use, and how the operating system finally gains control of the computer.

This phase serves as the foundation for future topics including DOS programming, x86 assembly, bootloader development, operating systems, and embedded firmware.

---

# Project Objectives

By the end of this phase, I aimed to understand:

- How an IBM PC-compatible computer starts from power-on
- The responsibilities of the BIOS during system startup
- The purpose of CMOS memory
- The POST (Power-On Self-Test) process
- How BIOS detects IDE hard disks and CD-ROM drives
- Why disks must be partitioned before formatting
- The purpose of the Master Boot Record (MBR)
- How the FAT16 filesystem organizes data
- How the DOS boot process works
- How FreeDOS is installed and started successfully

---

# Hardware Configuration

The following virtual hardware was used throughout this project.

| Component | Configuration |
|-----------|---------------|
| Emulator | 86Box |
| Motherboard | ASUS PVI-486SP3 |
| CPU | Intel 486DX2-66 |
| Memory | 16 MB RAM |
| Graphics | S3 Trio64 |
| Sound Card | Sound Blaster 16 |
| Hard Disk | IDE Hard Disk (~540 MB) |
| CD-ROM | ATAPI CD-ROM |
| Floppy Drive | 3.5" 1.44 MB |
| Operating System | FreeDOS 1.4 |

---

# Software Used

- 86Box Emulator
- FreeDOS 1.4
- 86Box ROM Collection

---

# Learning Journey

During this phase, the learning followed the same sequence as the computer itself.

```text
Power Button

↓

CPU Reset

↓

BIOS

↓

POST

↓

CMOS Configuration

↓

Hardware Detection

↓

Boot Device Selection

↓

Master Boot Record (MBR)

↓

Partition

↓

Filesystem (FAT16)

↓

Bootloader

↓

FreeDOS Kernel

↓

COMMAND.COM

↓

C:\>
```

Understanding each stage of this sequence is the primary objective of this phase.

---

# Engineering Topics Covered

This phase explores the following engineering concepts:

- BIOS
- CMOS
- POST (Power-On Self-Test)
- Boot Process
- Master Boot Record (MBR)
- Partitioning
- Disk Formatting
- FAT16 Filesystem
- IDE Storage
- ATAPI CD-ROM
- FreeDOS
- 86Box Emulator

Detailed explanations for each topic are available in the **Notes** folder.

---

# Repository Structure

```text
Phase-02-486-PC-and-FreeDOS/

├── README.md
├── Notes/
├── Diagrams/
├── Screenshots/
└── Handwritten/ (Planned)
```

### Notes

Detailed engineering explanations written throughout this phase.

### Diagrams

Architecture diagrams and illustrations created to explain concepts visually.

### Screenshots

Important screenshots captured during hardware configuration, installation, and experimentation.

### Handwritten

Handwritten engineering notes created using an iPad. These notes complement the Markdown documentation with sketches, memory maps, and diagrams.

---

# Practical Activities

Throughout this phase, I completed the following practical tasks:

- Configured a complete Intel 80486 virtual computer
- Selected compatible motherboard and hardware
- Configured IDE storage devices
- Installed an ATAPI CD-ROM drive
- Mounted FreeDOS installation media
- Formatted a virtual hard disk using FAT16
- Installed FreeDOS 1.4
- Successfully booted into the DOS command prompt
- Explored BIOS configuration and boot order
- Investigated the relationship between BIOS, MBR, and the operating system

---

# Key Concepts Learned

Some of the most important concepts learned during this phase include:

- BIOS initializes hardware but does not load the entire operating system.
- CMOS stores BIOS configuration settings.
- POST verifies hardware before booting.
- The BIOS executes the boot code stored in the Master Boot Record.
- Partitioning and formatting are different operations.
- Formatting creates a filesystem that organizes files.
- FAT16 tracks files using allocation tables.
- IDE controllers distinguish devices using Master/Slave configuration.
- ATAPI allows CD-ROM drives to communicate over the IDE interface.
- FreeDOS provides a DOS-compatible operating system for legacy x86 systems.

---

# Lessons Learned

Before completing this phase, I viewed operating system installation as simply copying files onto a hard disk.

Through building and configuring a virtual 486 PC, I learned that a successful boot requires many layers working together, including firmware initialization, hardware detection, storage configuration, partitioning, formatting, filesystem creation, bootloader execution, and finally operating system startup.

This project significantly improved my understanding of the lower layers of computer architecture and established a strong foundation for future work in firmware engineering, operating systems, and embedded systems.

---

# Next Phase

The next phase focuses on **DOS Programming**, where the knowledge gained from this phase will be applied by writing and executing programs directly within the FreeDOS environment.

Topics will include:

- DOS commands
- File management
- Batch files
- Program execution
- Memory layout
- Introduction to DOS system calls

---

# References

- FreeDOS Documentation
- 86Box Documentation
- Intel 80486 Programmer's Reference Manual
- Ralf Brown's Interrupt List
- PC System Architecture references

---

**Status:** Completed

**Learning Outcome:** Successfully built, configured, and booted a virtual Intel 80486 computer running FreeDOS while understanding the complete boot process from firmware initialization to the DOS command prompt.

# PC Boot Process

## Introduction

The boot process is the sequence of events that occurs from the moment a computer is powered on until the operating system is ready for use.

Before starting this project, I assumed the BIOS loaded the entire operating system into memory. During Phase 2, I learned that this is incorrect.

The BIOS only initializes the hardware and loads the boot sector from the selected boot device. The bootloader is then responsible for loading the operating system.

Understanding the boot process helped connect many concepts together, including BIOS, CMOS, the Master Boot Record (MBR), partitioning, formatting, and FreeDOS.

---

# Overview

A simplified boot process is shown below.

```
Power On
      │
      ▼
CPU Reset
      │
      ▼
Execute BIOS Firmware
      │
      ▼
POST (Power-On Self-Test)
      │
      ▼
Read CMOS Configuration
      │
      ▼
Detect Hardware
      │
      ▼
Select Boot Device
      │
      ▼
Load Boot Sector (512 bytes)
      │
      ▼
Execute Bootloader
      │
      ▼
Load Operating System
      │
      ▼
DOS Command Prompt
```

---

# Step 1 - Power On

When the computer receives power, every hardware component begins initializing.

The CPU does not immediately start executing an operating system.

Instead, it starts execution from a predefined memory address where the BIOS firmware is stored.

---

# Step 2 - CPU Executes BIOS Firmware

The BIOS (Basic Input/Output System) is firmware stored in ROM or Flash memory on the motherboard.

The CPU immediately begins executing BIOS instructions after reset.

The BIOS becomes the first software that runs on the computer.

Its responsibilities include:

- Initializing hardware
- Performing diagnostic tests
- Detecting storage devices
- Reading CMOS configuration
- Selecting a boot device
- Loading the boot sector

---

# Step 3 - POST (Power-On Self-Test)

Before attempting to boot an operating system, the BIOS verifies that the essential hardware is functioning correctly.

Typical checks include:

- CPU
- RAM
- Keyboard
- Video adapter
- Storage controllers

If a critical problem is detected, the BIOS usually stops the boot process and displays an error message or produces beep codes.

---

# Step 4 - Read CMOS Settings

The BIOS reads configuration data stored inside CMOS memory.

Examples include:

- System date and time
- Boot order
- Hard disk configuration
- Memory settings
- Peripheral configuration

Without CMOS, the BIOS would lose these settings every time the computer lost power.

---

# Step 5 - Detect Hardware

Next, the BIOS searches for installed hardware devices.

Examples include:

- IDE hard drives
- ATAPI CD-ROM drives
- Floppy drives
- Keyboard
- Mouse
- Display adapter

The detected devices are displayed on the POST screen.

---

# Step 6 - Select Boot Device

Using the boot priority stored in CMOS, the BIOS determines which device should be used to start the operating system.

Common boot devices include:

- Floppy Disk
- Hard Disk
- CD-ROM

For this project, I configured the BIOS to boot from the hard disk after installing FreeDOS.

---

# Step 7 - Load the Boot Sector

This was one of the most important concepts I learned.

The BIOS **does not load the entire operating system**.

Instead, it loads only the first sector of the boot device into memory.

For traditional IBM PC compatible systems:

- Size = 512 bytes

This sector contains executable bootloader code.

After loading the boot sector, the BIOS transfers execution to it.

---

# Why Doesn't the BIOS Load the Entire Operating System?

Initially, I assumed the BIOS loaded FreeDOS completely into RAM.

This is incorrect.

Reasons include:

- BIOS is intentionally simple.
- Operating systems can be very large.
- BIOS should remain independent of any operating system.
- Different operating systems use different loading methods.

Instead, the BIOS simply loads a tiny bootloader.

The bootloader understands how to load the operating system correctly.

This design keeps the BIOS generic and compatible with many operating systems.

---

# Step 8 - Bootloader Starts

The bootloader now takes control of the computer.

Its responsibilities include:

- Understanding the filesystem
- Finding operating system files
- Loading them into memory
- Starting the operating system

For FreeDOS, the bootloader eventually loads the DOS system files required for startup.

---

# Step 9 - Operating System Starts

Once the operating system has been loaded into memory, it begins executing.

During FreeDOS startup, files such as:

- CONFIG.SYS
- AUTOEXEC.BAT

are processed before presenting the DOS command prompt.

Example:

```
C:\>
```

At this point, the operating system—not the BIOS—is responsible for running software.

---

# BIOS vs Bootloader vs Operating System

| Component | Responsibility |
|-----------|----------------|
| BIOS | Initialize hardware and load the boot sector |
| Bootloader | Locate and load the operating system |
| Operating System | Manage hardware resources and execute user programs |

Understanding this separation of responsibility was one of the biggest lessons from this phase.

---

# Common Misconceptions

## Misconception 1

**The BIOS loads the operating system.**

Incorrect.

The BIOS only loads the boot sector.

---

## Misconception 2

**The BIOS understands FAT16.**

Not necessarily.

The BIOS simply reads sectors from the storage device.

The bootloader understands the filesystem.

---

## Misconception 3

**The operating system starts immediately after power-on.**

Incorrect.

Several initialization steps occur before the operating system begins executing.

---

# Connection to Other Notes

This document is closely related to:

- BIOS.md
- CMOS.md
- MBR.md
- Partitioning.md
- Formatting.md
- FAT16.md
- FreeDOS.md

---

# Key Takeaways

- Booting begins with the BIOS, not the operating system.
- The BIOS initializes hardware before attempting to boot.
- CMOS stores BIOS configuration settings.
- The BIOS loads only the boot sector (512 bytes).
- The bootloader loads the operating system.
- The operating system finally takes control of the computer.

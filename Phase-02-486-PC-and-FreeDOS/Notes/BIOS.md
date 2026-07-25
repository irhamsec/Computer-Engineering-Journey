# BIOS (Basic Input/Output System)

> The BIOS is firmware stored on the motherboard that initializes the computer's hardware and starts the operating system during the boot process.

---

# Overview

The **Basic Input/Output System (BIOS)** is the first software executed when a traditional IBM PC-compatible computer is powered on.

Unlike an operating system, the BIOS is permanently stored inside a ROM (Read-Only Memory) chip on the motherboard. Its primary responsibility is to initialize the computer's hardware, verify that the system is functioning correctly, and transfer control to a bootable storage device.

Without the BIOS, the CPU would have no instructions to execute after power is applied, making it impossible for the computer to start.

---

# Why Does the BIOS Exist?

When a computer is powered on:

- RAM is empty.
- The operating system has not been loaded.
- Storage devices have not been initialized.
- The CPU requires instructions immediately after reset.

The BIOS solves this problem by providing a permanent set of instructions that the CPU can execute immediately after power-on.

Its job is to prepare the hardware so that an operating system can eventually take control.

---

# Where is the BIOS Stored?

The BIOS is stored inside a non-volatile ROM chip on the motherboard.

Unlike RAM:

| BIOS ROM | RAM |
|-----------|-----|
| Non-volatile | Volatile |
| Keeps contents without power | Loses contents when power is removed |
| Contains firmware | Stores running programs and data |
| Executed immediately after power-on | Used after initialization |

Because the BIOS is stored in ROM, it is always available whenever the computer starts.

---

# BIOS is Firmware

Firmware is software that is permanently stored inside hardware devices.

The BIOS is one example of firmware.

Unlike application software or operating systems, firmware exists to control and initialize hardware before higher-level software begins executing.

Examples of firmware include:

- PC BIOS
- UEFI firmware
- SSD firmware
- Router firmware
- Embedded microcontroller firmware

---

# Responsibilities of the BIOS

The BIOS performs several important tasks during startup.

## 1. Initialize the CPU

After reset, the CPU begins executing BIOS instructions.

The BIOS becomes the first software that controls the computer.

---

## 2. Perform POST (Power-On Self-Test)

The BIOS checks that the essential hardware is functioning correctly.

Typical checks include:

- CPU
- RAM
- Keyboard
- Video adapter
- Storage controllers

If critical hardware fails, the BIOS reports an error using messages or beep codes.

---

## 3. Read CMOS Configuration

The BIOS loads the system configuration stored inside CMOS memory.

These settings include:

- Boot order
- Date and time
- Installed drives
- Hardware configuration

Without CMOS, the BIOS would need to rediscover every configuration every time the computer starts.

---

## 4. Detect Hardware

The BIOS searches for installed hardware such as:

- IDE hard disks
- ATAPI CD-ROM drives
- Floppy drives
- Keyboard
- Video card

The BIOS prepares these devices for later use by the operating system.

---

## 5. Select a Boot Device

Using the configured boot order, the BIOS searches for a bootable device.

For example:

1. Floppy Disk
2. Hard Disk
3. CD-ROM

The first bootable device found will be used.

---

## 6. Load the Master Boot Record (MBR)

If booting from a hard disk, the BIOS reads the first physical sector of the disk.

This sector is called the **Master Boot Record (MBR)**.

The BIOS copies this sector into RAM and transfers execution to its boot code.

From this point onward, the operating system's bootloader takes over.

---

# What the BIOS Does NOT Do

One of the biggest misconceptions is that the BIOS loads the entire operating system.

It does **not**.

The BIOS only loads the first boot sector.

The bootloader stored inside that sector is responsible for loading the operating system.

For example:

```
Power On

↓

BIOS

↓

Reads MBR

↓

Executes Bootloader

↓

Bootloader loads FreeDOS

↓

COMMAND.COM

↓

C:\>
```

The BIOS never loads FreeDOS directly.

---

# BIOS and the Boot Process

The complete boot sequence learned during this project is:

```
Power On

↓

CPU Reset

↓

BIOS Starts

↓

POST

↓

Read CMOS Settings

↓

Detect Hardware

↓

Select Boot Device

↓

Read MBR

↓

Execute Bootloader

↓

Load Operating System

↓

DOS Command Prompt
```

This sequence became much clearer while installing FreeDOS in 86Box.

---

# BIOS During the FreeDOS Installation

During this project, the BIOS performed several visible tasks before FreeDOS started.

These included:

- Detecting the Intel 486DX2 CPU
- Detecting 16 MB of RAM
- Detecting the IDE hard disk
- Detecting the ATAPI CD-ROM
- Checking the configured boot order
- Reading the boot sector
- Starting the FreeDOS installer

These steps were visible every time the virtual machine restarted.

---

# BIOS vs Operating System

| BIOS | Operating System |
|------|------------------|
| Firmware | Software |
| Stored in ROM | Stored on disk |
| Starts immediately after power-on | Loaded after bootloader |
| Initializes hardware | Manages hardware resources |
| Executes before the OS | Executes after BIOS |

The BIOS prepares the computer.

The operating system manages the computer.

---

# Common Misconceptions

## "The BIOS loads Windows or DOS."

Incorrect.

The BIOS loads only the first boot sector.

---

## "The BIOS is the operating system."

Incorrect.

The BIOS exists only to initialize hardware and start the boot process.

---

## "BIOS runs forever."

Incorrect.

After transferring control to the bootloader, the BIOS is no longer responsible for controlling the operating system.

---

# Questions I Asked During This Phase

## Why doesn't the BIOS simply load the whole operating system?

Because operating systems are much larger than a single disk sector.

The BIOS performs only the minimum work necessary to start the bootloader.

The bootloader then loads the operating system in stages.

---

## Why must the BIOS exist in ROM?

Because RAM is empty immediately after power-on.

The CPU requires instructions from a permanent location.

ROM guarantees those instructions are always available.

---

## Why can't the CPU start executing the operating system directly?

Because the operating system is stored on a storage device that has not yet been initialized.

The BIOS initializes the hardware first, allowing the storage device to be accessed.

---

# Key Takeaways

- BIOS is firmware stored in ROM.
- BIOS is the first software executed after power-on.
- BIOS initializes hardware before the operating system starts.
- BIOS performs the POST.
- BIOS reads CMOS configuration settings.
- BIOS detects storage devices.
- BIOS selects a boot device.
- BIOS reads and executes the Master Boot Record.
- BIOS does not load the entire operating system.
- BIOS transfers control to the bootloader, which then loads the operating system.

---

# Related Notes

- CMOS.md
- Boot-Process.md
- MBR.md
- IDE-and-ATAPI.md
- FreeDOS.md

---

# Connection to Other Topics

BIOS is the starting point of the entire Phase 2 learning journey.

Understanding the BIOS makes it easier to understand:

- CMOS (BIOS configuration storage)
- POST (hardware testing)
- MBR (first sector loaded by BIOS)
- Boot Process (overall startup sequence)
- FAT16 (filesystem eventually used by the OS)
- FreeDOS (operating system loaded after the bootloader)

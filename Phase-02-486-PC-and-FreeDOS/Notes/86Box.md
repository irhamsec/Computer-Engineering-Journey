# 86Box

> 86Box is a free and open-source IBM PC emulator that accurately reproduces classic x86 computer hardware. During Phase 2 of this project, 86Box was used to build a virtual Intel 80486 computer and explore the complete boot process from hardware initialization to the FreeDOS operating system.

---

# Introduction

The objective of Phase 2 was not simply to install an operating system.

Instead, the goal was to understand how a classic IBM PC-compatible computer works from the moment power is applied until the operating system takes control.

Rather than using modern virtualization software such as VirtualBox or VMware, I chose **86Box** because it emulates individual hardware components found in historical personal computers.

This made it possible to study hardware, firmware, storage devices, and operating systems in an environment that closely resembles a real 486-era computer.

Throughout this phase, 86Box became the laboratory where every concept-including BIOS, CMOS, the boot process, partitioning, formatting, FAT16, and FreeDOS-could be observed in practice.

---

# What is 86Box?

86Box is an emulator designed to reproduce classic IBM PC-compatible computers.

Unlike a virtual machine, which relies on the host computer's hardware, an emulator recreates the behavior of the original hardware in software.

This allows operating systems and software written for older computers to run as if they were executing on the original machine.

86Box supports computers from the early IBM PC through later Pentium-era systems.

---

# Why is it Called "86Box"?

The name **86Box** comes from the x86 family of processors.

Examples include:

- Intel 8086
- Intel 8088
- Intel 80286
- Intel 80386
- Intel 80486
- Intel Pentium

These processors all belong to the x86 architecture.

The word **"Box"** simply refers to the complete personal computer being emulated.

Rather than emulating only the CPU, 86Box emulates an entire computer system.

---

# Why Did I Choose 86Box?

Several emulators are available for running DOS operating systems.

However, most are designed for different purposes.

I selected 86Box because it provides accurate hardware emulation instead of simply running DOS programs.

Its advantages include:

- Individual motherboard selection
- CPU selection
- BIOS emulation
- CMOS configuration
- IDE controller emulation
- Floppy drives
- Hard disks
- ATAPI CD-ROM drives
- ISA, VLB, and PCI devices
- Sound cards
- Graphics cards

This level of hardware detail makes it ideal for learning computer architecture.

---

# Emulator vs Virtual Machine

One important concept I learned during this phase is the difference between an emulator and a virtual machine.

| Emulator | Virtual Machine |
|----------|-----------------|
| Recreates hardware in software | Shares the host computer's hardware |
| Can emulate different CPU architectures | Normally uses the host CPU architecture |
| Suitable for historical systems | Designed for modern operating systems |
| Focuses on hardware accuracy | Focuses on performance |

Because my objective was to study the architecture of a 486 computer, hardware accuracy was more important than performance.

---

# Hardware Configuration Used

During this project, I built a virtual Intel 80486 computer with the following configuration.

| Component | Configuration |
|-----------|---------------|
| CPU | Intel 80486 DX2-66 |
| RAM | 16 MB |
| Hard Disk | IDE Hard Disk |
| Optical Drive | ATAPI CD-ROM |
| Operating System | FreeDOS |
| Emulator | 86Box |

This configuration closely resembles a typical personal computer from the mid-1990s.

---

# Why an Intel 80486?

The Intel 80486 represents an important stage in the evolution of personal computers.

Compared to modern processors, its architecture is much simpler, making it easier to understand.

Studying a 486 computer allows concepts such as:

- BIOS
- CMOS
- Boot process
- Memory
- Storage
- Interrupts
- DOS

to be explored without the complexity of modern hardware.

This makes it an excellent platform for learning computer engineering fundamentals.

---

# Storage Configuration

Two storage devices were configured.

```
IDE Hard Disk

↓

Stores FreeDOS
```

```
ATAPI CD-ROM

↓

Contains FreeDOS Installation Media
```

The operating system was installed from the CD-ROM onto the IDE hard disk.

After installation, the BIOS booted directly from the hard disk.

---

# BIOS Setup

One of the most valuable features of 86Box is the ability to interact with a traditional BIOS setup utility.

Through the BIOS, I learned how to configure:

- System date and time
- Boot order
- Storage devices
- Hardware configuration

This helped demonstrate the relationship between BIOS firmware and CMOS memory.

---

# What I Learned Using 86Box

Building the virtual computer allowed me to study concepts that are usually hidden by modern operating systems.

Some of the topics explored included:

- BIOS firmware
- CMOS memory
- Power-On Self-Test (POST)
- Boot sequence
- Master Boot Record (MBR)
- Partitioning
- Formatting
- FAT16 filesystem
- IDE hard disks
- ATAPI CD-ROM drives
- FreeDOS installation

Rather than reading about these concepts in isolation, I observed how they worked together inside a complete computer system.

---

# Advantages of Using 86Box

86Box provides several advantages for learning computer engineering.

- Safe environment for experimentation
- No physical hardware required
- Accurate hardware emulation
- Supports many historical PC configurations
- Easy to reinstall operating systems
- Ideal for studying classic PC architecture

These advantages make it an excellent educational tool.

---

# Limitations

Although 86Box accurately emulates classic hardware, it is not intended for modern computing.

Some limitations include:

- Lower performance than modern virtual machines
- Requires BIOS ROM images
- Focused on historical hardware rather than current platforms

For educational purposes, these limitations are acceptable because hardware accuracy is the primary goal.

---

# Common Misconceptions

## "86Box emulates only the CPU."

Incorrect.

86Box emulates an entire computer, including the motherboard, BIOS, storage controllers, graphics hardware, and many peripheral devices.

---

## "86Box is the same as DOSBox."

Incorrect.

DOSBox focuses on running DOS applications and games.

86Box focuses on accurately emulating complete IBM PC-compatible hardware.

---

## "86Box is a virtual machine."

Incorrect.

86Box is a hardware emulator.

It recreates the behavior of historical computer hardware in software.

---

## "Learning an old 486 computer is no longer useful."

Although modern computers are much more advanced, many fundamental concepts remain the same.

Examples include:

- CPU startup
- Firmware
- Bootloaders
- Filesystems
- Storage devices
- Operating systems

Studying a simpler system makes these concepts easier to understand before moving to modern architectures.

---

# Questions I Asked During This Phase

## Why didn't we use VirtualBox?

Because VirtualBox virtualizes modern hardware and hides many low-level details.

86Box exposes the hardware components that were important for learning this project.

---

## Why did we use a 486 instead of a modern computer?

A 486 system is much simpler.

Understanding its architecture provides a strong foundation before studying modern computers.

---

## Why did we install FreeDOS?

FreeDOS exposes the traditional PC boot process and storage organization much more clearly than modern operating systems.

---

## Is 86Box free?

Yes.

86Box is free and open-source software maintained by the community.

---

# Key Takeaways

- 86Box is a hardware emulator for classic IBM PC-compatible computers.
- It emulates an entire computer, not just the CPU.
- Phase 2 used an Intel 80486 DX2-66 virtual computer.
- The emulator provided a safe environment for learning BIOS, CMOS, storage devices, and the boot process.
- Using 86Box made it possible to observe how hardware, firmware, and the operating system interact during startup.

---

# Connection to Other Topics

86Box serves as the practical environment for every concept studied during Phase 2.

- **BIOS.md** – BIOS firmware executed inside the emulated computer.
- **CMOS.md** – BIOS settings were stored in CMOS memory.
- **Boot-Process.md** – The complete startup sequence was observed using 86Box.
- **MBR.md** – The BIOS loaded the MBR from the virtual hard disk.
- **Partitioning.md** – The virtual hard disk was partitioned before installation.
- **Formatting.md** – The partition was formatted with FAT16.
- **FAT16.md** – FreeDOS stored its files within the FAT16 filesystem.
- **IDE-and-ATAPI.md** – IDE and ATAPI devices were configured in the emulator.
- **FreeDOS.md** – FreeDOS was installed and executed inside the virtual machine.

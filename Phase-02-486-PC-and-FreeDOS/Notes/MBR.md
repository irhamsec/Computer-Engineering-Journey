# MBR (Master Boot Record)

> The Master Boot Record (MBR) is the first physical sector of a bootable storage device. It contains executable boot code and the partition table that allow the BIOS to begin loading an operating system.

---

# Overview

The **Master Boot Record (MBR)** is located in the **first physical sector** of a hard disk.

For traditional IBM PC-compatible systems, this sector is always:

- **Sector Number:** 0
- **Size:** 512 bytes

The MBR is one of the most important components of the PC boot process because it acts as the bridge between the BIOS and the operating system.

During Phase 2, understanding the MBR completely changed my understanding of how a computer boots.

Before this project, I assumed the BIOS loaded the operating system directly. In reality, the BIOS only loads the MBR into memory and executes its boot code.

---

# What Does MBR Stand For?

**M** – Master

**B** – Boot

**R** – Record

The name describes its purpose:

- **Master** – The primary boot record for the entire storage device.
- **Boot** – Used during system startup.
- **Record** – A structured block of data stored in the first sector of the disk.

---

# Why Does the MBR Exist?

Imagine a BIOS attempting to boot from a hard disk.

The BIOS knows:

- How to communicate with the storage controller.
- How to read sectors from a disk.

However, the BIOS does **not** know:

- Which partition contains the operating system.
- Where FreeDOS is stored.
- Where files begin or end.
- What FAT16 is.
- What directories or filenames exist.

Instead of understanding every possible filesystem, the BIOS performs one simple task:

1. Read Sector 0.
2. Copy it into RAM.
3. Execute it.

The MBR exists to tell the computer what should happen next.

---

# Where is the MBR Located?

The Master Boot Record is always stored in the first physical sector of the storage device.

```
Hard Disk

+---------------------------+
| Sector 0                  |
| Master Boot Record (MBR)  |
+---------------------------+
| Sector 1                  |
+---------------------------+
| Sector 2                  |
+---------------------------+
| ...                       |
+---------------------------+
```

Whenever the BIOS boots from a hard disk, it reads **Sector 0**.

---

# What Does the MBR Contain?

The 512-byte MBR is divided into several sections.

```
512 Bytes

+-------------------------+
| Boot Code               |
| (~446 Bytes)            |
+-------------------------+
| Partition Table         |
| (64 Bytes)              |
+-------------------------+
| Boot Signature          |
| (2 Bytes)               |
+-------------------------+
```

Each section serves a different purpose.

---

# Boot Code

The first part of the MBR contains executable machine code.

This small program is called the **bootloader** (or the first stage of the bootloader).

Its job is to:

- Read the partition table.
- Locate the active partition.
- Load the partition boot sector.
- Transfer execution to it.

The BIOS does not understand the partition table itself.

Instead, it executes the boot code stored in the MBR.

---

# Partition Table

The partition table describes how the hard disk is divided.

Each partition entry contains information such as:

- Partition type
- Starting sector
- Partition size
- Active (bootable) flag

Without the partition table, the computer would not know which partition should be booted.

---

# Boot Signature

The last two bytes of the MBR contain a special signature.

```
55 AA (Hexadecimal)
```

This signature tells the BIOS that the sector contains valid boot code.

If the signature is missing, the BIOS assumes the disk is not bootable.

---

# MBR During the Boot Process

The sequence is:

```
Power On
      │
      ▼
CPU Reset
      │
      ▼
BIOS
      │
      ▼
POST
      │
      ▼
Read CMOS
      │
      ▼
Detect Hardware
      │
      ▼
Select Boot Device
      │
      ▼
Read Sector 0 (MBR)
      │
      ▼
Execute MBR Boot Code
      │
      ▼
Load Partition Boot Sector
      │
      ▼
Load Operating System
```

The MBR is the first executable code loaded from the hard disk.

---

# MBR During the FreeDOS Installation

During this project, the FreeDOS installer asked whether the Master Boot Record should be written to the hard disk.

At first, I wasn't sure what this meant.

After studying the boot process, I learned that installing the MBR is necessary because:

- A new hard disk contains no boot code.
- Without an MBR, the BIOS has nothing to execute after selecting the hard disk.
- Installing the MBR makes the disk bootable.

This was one of the most important lessons in understanding how operating systems start.

---

# What Happens Without an MBR?

If a hard disk does not contain a valid Master Boot Record:

The BIOS may display errors such as:

```
Missing operating system

Disk boot failure

No bootable device
```

This is because the BIOS cannot find valid boot code to continue the startup process.

---

# MBR vs Filesystem

One misconception I had was thinking the MBR stores the operating system.

It does not.

The MBR only starts the boot process.

The operating system files are stored inside the filesystem.

For example:

```
Hard Disk

Sector 0
│
├── Master Boot Record
│
├── Partition
│
├── FAT16
│
├── FreeDOS System Files
│
├── COMMAND.COM
│
└── User Files
```

The MBR simply helps locate the correct partition.

---

# MBR vs BIOS

| BIOS | MBR |
|------|------|
| Stored in ROM | Stored on the hard disk |
| Firmware | Boot record |
| Initializes hardware | Starts the bootloader |
| Executes first | Executes after BIOS |

The BIOS prepares the hardware.

The MBR continues the boot process.

---

# MBR During This Project

Throughout this project, I encountered several situations involving the MBR.

For example:

- Creating a new partition.
- Writing the MBR during installation.
- Rebooting after partition creation.
- Understanding why a newly created partition was not immediately bootable.
- Learning that the BIOS executes the MBR before the operating system.

These practical experiments made the role of the MBR much easier to understand.

---

# Common Misconceptions

## "The BIOS loads FreeDOS."

Incorrect.

The BIOS loads only the MBR.

---

## "The MBR stores the operating system."

Incorrect.

The MBR stores boot code and the partition table.

The operating system remains inside the filesystem.

---

## "The MBR is the same as a partition."

Incorrect.

The MBR exists before any partition.

It describes the partitions.

---

## "Formatting creates the MBR."

Incorrect.

Partitioning and installing boot code create the MBR.

Formatting creates the filesystem inside a partition.

---

# Questions I Asked During This Phase

## Why does the BIOS execute only the MBR?

Because the BIOS is designed to remain simple and independent of operating systems.

Reading a single sector is enough to begin the boot process.

---

## Why is the MBR stored in Sector 0?

Using a fixed location allows every BIOS to know exactly where to find the initial boot code.

---

## Why doesn't the BIOS understand FAT16?

Because the BIOS only needs to load the first boot sector.

The bootloader is responsible for understanding the filesystem.

---

## Why did the FreeDOS installer ask to overwrite the MBR?

Because installing a new operating system often requires installing new boot code so the BIOS can successfully start the operating system.

---

# Key Takeaways

- MBR stands for **Master Boot Record**.
- The MBR is always stored in Sector 0 of the hard disk.
- The MBR is 512 bytes long.
- The BIOS loads the MBR into RAM and executes it.
- The MBR contains boot code and the partition table.
- The MBR does not contain the operating system.
- The bootloader stored in the MBR continues the boot process.
- Without a valid MBR, the hard disk cannot boot.

---

# Connection to Other Topics

The Master Boot Record connects several concepts studied during Phase 2.

- **BIOS.md** – The BIOS reads and executes the MBR.
- **CMOS.md** – CMOS stores the boot order used by the BIOS to choose which disk's MBR to load.
- **Boot-Process.md** – The MBR is executed after hardware initialization.
- **Partitioning.md** – The MBR contains the partition table.
- **Formatting.md** – Formatting creates a filesystem after partitioning.
- **FAT16.md** – The bootloader eventually loads files from the FAT16 filesystem.
- **FreeDOS.md** – FreeDOS becomes operational only after the MBR and bootloader complete their work.

# Partitioning

> Partitioning is the process of dividing a physical storage device into one or more logical sections called partitions. Each partition behaves like an independent storage area and can contain its own filesystem and operating system.

---

# Introduction

During the FreeDOS installation in Phase 2, one of the first steps was creating a partition on the hard disk.

Initially, I thought partitioning was simply another word for formatting. After studying the installation process, I learned that these are two completely different operations.

Partitioning divides the hard disk into logical sections, while formatting prepares one of those sections with a filesystem.

Without partitioning, an operating system has nowhere to be installed.

Understanding partitioning also helped explain why the Master Boot Record (MBR) contains a partition table and why the BIOS cannot boot directly from an empty hard disk.

---

# What is Partitioning?

A **partition** is a logical division of a physical storage device.

Instead of treating an entire hard disk as one large block of storage, partitioning divides it into separate regions.

Each partition can:

- Have its own filesystem
- Store different files
- Contain an operating system
- Be formatted independently

Although there is only one physical hard disk, the operating system may treat each partition as a separate logical drive.

For example:

```
One Physical Hard Disk

+--------------------------------------+
|                                      |
|              Hard Disk               |
|                                      |
+--------------------------------------+

        Partitioned Into

+----------------+---------------------+
| Partition 1    | Partition 2         |
| (Drive C:)     | (Drive D:)          |
+----------------+---------------------+
```

---

# Why Does Partitioning Exist?

Imagine buying a brand-new hard disk.

Although the hardware is fully functional, the computer has no information about:

- Where files should be stored.
- Which area belongs to the operating system.
- Where user data begins.
- Which partition should be booted.

Partitioning creates this organization.

It divides the disk into clearly defined regions before any filesystem is created.

---

# Physical Disk vs Logical Partition

This distinction was one of the biggest concepts I learned during this project.

A **physical disk** is the actual hardware device.

Examples include:

- IDE Hard Disk
- SATA SSD
- NVMe SSD

A **partition** is only a logical section inside that device.

For example:

```
Physical Hard Disk

+------------------------------------------------+
|                                                |
|                540 MB Hard Disk                |
|                                                |
+------------------------------------------------+

Logical View

+----------------+-------------------------------+
| C:             | D:                            |
| FreeDOS        | Data                          |
+----------------+-------------------------------+
```

There is still only one hard disk.

The partitions simply organize how its storage is used.

---

# What is Stored in a Partition?

A partition normally contains:

- A filesystem (such as FAT16)
- Directories
- Files
- Operating system files
- User data

The partition itself does **not** contain the Master Boot Record.

The MBR exists before the partitions.

---

# Partition Table

The partition table is stored inside the Master Boot Record (MBR).

It records information such as:

- Number of partitions
- Starting sector
- Partition size
- Partition type
- Active (bootable) partition

Without this table, the bootloader would not know where the operating system is located.

---

# Active Partition

One partition can be marked as the **active partition**.

The active partition tells the bootloader which partition should be used to continue the boot process.

For example:

```
Hard Disk

+----------------------+----------------------+
| Partition 1          | Partition 2          |
| Active               | Data                 |
| FreeDOS              | Files                |
+----------------------+----------------------+
```

When the MBR executes, it searches for the active partition.

---

# Partitioning During the FreeDOS Installation

One of the first utilities used during the installation was **FDISK**.

FDISK allowed me to:

- Create a primary partition.
- Mark it as active.
- Prepare the disk for formatting.

At first, this seemed like an unnecessary extra step.

Later, I understood that the operating system cannot be installed until the hard disk has been logically divided into partitions.

---

# Why Can't We Skip Partitioning?

Suppose we have:

- A brand-new hard disk.
- FreeDOS installation media.

Without partitioning:

- No partition exists.
- No partition table exists.
- No active partition exists.
- The installer has nowhere to install the operating system.

Partitioning creates the logical structure that the filesystem and operating system will use.

---

# Partitioning vs Formatting

One of the biggest misconceptions I had during this project was believing these were the same thing.

They are completely different operations.

| Partitioning | Formatting |
|--------------|------------|
| Divides the disk | Creates the filesystem |
| Creates partitions | Creates FAT16 (or another filesystem) |
| Done first | Done after partitioning |
| Changes disk layout | Prepares a partition for storing files |

Think of it like building a house.

Partitioning is deciding where each room will be.

Formatting is furnishing each room so people can actually use it.

---

# Partitioning vs Filesystem

Another misconception was assuming a partition already contains files.

It does not.

A partition is simply a defined region of storage.

Only after formatting does that region receive a filesystem capable of storing files.

```
Hard Disk

Partition

↓

Formatting

↓

FAT16 Filesystem

↓

Files and Directories
```

---

# Boot Process Relationship

Partitioning plays an important role during booting.

```
BIOS

↓

MBR

↓

Partition Table

↓

Active Partition

↓

Partition Boot Sector

↓

Operating System
```

Without a valid partition table, the bootloader cannot locate the operating system.

---

# Common Misconceptions

## "Partitioning and formatting are the same."

Incorrect.

Partitioning creates logical sections.

Formatting creates the filesystem.

---

## "A partition is another physical hard disk."

Incorrect.

A partition is only a logical division inside the same physical disk.

---

## "The operating system is installed directly onto the hard disk."

Not exactly.

The operating system is installed inside a formatted partition.

---

## "The MBR is stored inside a partition."

Incorrect.

The MBR exists before any partition and contains the partition table.

---

# Questions I Asked During This Phase

## Why did the FreeDOS installer ask me to partition the disk first?

Because the operating system needs a logical area where it can be installed.

---

## Why can't formatting create partitions?

Because formatting only creates a filesystem inside an existing partition.

It does not define the layout of the disk.

---

## Why is one partition marked as active?

The active flag tells the bootloader which partition should be used to continue the boot process.

---

## Can a hard disk have multiple partitions?

Yes.

Each partition behaves like an independent logical storage area and may contain a different filesystem or even a different operating system.

---

# Key Takeaways

- Partitioning divides a physical storage device into logical sections.
- Partitions are not physical hardware.
- Each partition can contain its own filesystem.
- The partition table is stored in the Master Boot Record.
- One partition can be marked as active for booting.
- Partitioning must be completed before formatting.
- Operating systems are installed into formatted partitions, not directly onto the raw disk.

---

# Connection to Other Topics

Partitioning connects several concepts studied during Phase 2.

- **BIOS.md** – The BIOS selects the boot device.
- **CMOS.md** – CMOS stores the boot order used by the BIOS.
- **Boot-Process.md** – The partition is used after the MBR is executed.
- **MBR.md** – The MBR contains the partition table.
- **Formatting.md** – Formatting prepares a partition with a filesystem.
- **FAT16.md** – FAT16 is the filesystem created inside a partition.
- **FreeDOS.md** – FreeDOS is installed into a formatted partition.

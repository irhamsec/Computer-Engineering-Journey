# FAT16 (File Allocation Table 16)

> FAT16 (File Allocation Table 16) is a filesystem developed by Microsoft that organizes how files and directories are stored on a storage device. During Phase 2, FreeDOS used FAT16 as the filesystem created after formatting the partition.

---

# Introduction

During the FreeDOS installation, one of the final preparation steps was formatting the partition with the FAT16 filesystem.

Initially, I assumed FAT16 was simply another file format or a way of naming disks.

After studying the installation process, I learned that FAT16 is much more important-it is the **filesystem** that defines how the operating system stores, organizes, and retrieves files.

Without a filesystem such as FAT16, the operating system would have no method of locating files or determining which storage space is available.

Understanding FAT16 also helped explain why formatting is required before installing an operating system.

---

# What Does FAT16 Stand For?

**FAT** = **File Allocation Table**

The **16** refers to the use of **16-bit entries** in the File Allocation Table.

These 16-bit entries allow the filesystem to keep track of where files are stored on the disk.

---

# What is a Filesystem?

A filesystem is a set of rules that defines how data is stored and organized on a storage device.

It allows the operating system to:

- Store files
- Create directories
- Locate files
- Delete files
- Keep track of free space
- Manage storage efficiently

Without a filesystem, a partition is simply a collection of raw sectors with no organization.

---

# Why Does FAT16 Exist?

Imagine saving a file called:

```
REPORT.TXT
```

Without a filesystem, the operating system would not know:

- Where the file begins.
- Where the file ends.
- Which sectors belong to the file.
- Which sectors are still empty.
- Where the filename is stored.

FAT16 solves all of these problems by providing an organized structure for storing information.

---

# FAT16 During Phase 2

During this project, the hard disk was:

```
Partitioned

↓

Formatted

↓

FAT16 Created

↓

FreeDOS Installed
```

After formatting, FreeDOS could finally copy its system files onto the partition because the FAT16 filesystem now existed.

---

# Basic Structure of FAT16

A FAT16 partition is organized into several major sections.

```
+--------------------------------+
| Boot Sector                    |
+--------------------------------+
| File Allocation Table (FAT) #1 |
+--------------------------------+
| File Allocation Table (FAT) #2 |
+--------------------------------+
| Root Directory                 |
+--------------------------------+
| Data Area                      |
+--------------------------------+
```

Each section has a specific purpose.

---

# Boot Sector

The Boot Sector contains information about the filesystem.

Examples include:

- Bytes per sector
- Sectors per cluster
- Number of FAT tables
- Size of each FAT
- Number of root directory entries

It also contains boot code if the partition is bootable.

---

# File Allocation Table (FAT)

The File Allocation Table is the heart of the FAT16 filesystem.

Think of it as a map.

Instead of storing the files themselves, it stores information about where every file is located.

For every cluster on the disk, the FAT records:

- Free
- Used
- End of file
- Next cluster belonging to the same file

This allows files to be stored even when they are spread across different parts of the disk.

---

# Why Are There Two FAT Tables?

You may notice that FAT16 normally stores **two copies** of the File Allocation Table.

```
FAT #1

FAT #2
```

The second table acts as a backup.

If one FAT becomes corrupted, the operating system may still recover information using the second copy.

This improves the reliability of the filesystem.

---

# Root Directory

The Root Directory stores information about files and folders.

For each file, entries include information such as:

- Filename
- File size
- Date
- Time
- File attributes
- Starting cluster

The actual file data is not stored here.

Only information describing the file is stored.

---

# Data Area

The Data Area contains the actual contents of files.

For example:

```
HELLO.TXT

PHOTO.BMP

COMMAND.COM

KERNEL.SYS
```

The Root Directory tells the operating system where a file begins.

The FAT tells it where the rest of the file continues.

The Data Area stores the actual bytes.

---

# What is a Cluster?

A cluster is the smallest unit of storage managed by FAT16.

A cluster may consist of one or more sectors.

For example:

```
Cluster 2

Sector
Sector
Sector
Sector
```

Instead of tracking individual sectors, FAT16 tracks clusters.

This reduces the size of the File Allocation Table.

---

# How FAT16 Stores a File

Suppose a file occupies three clusters.

```
REPORT.TXT

Cluster 5

↓

Cluster 8

↓

Cluster 12

↓

End
```

The Root Directory records:

```
REPORT.TXT

Starts at Cluster 5
```

The FAT contains:

```
Cluster 5 → 8

Cluster 8 → 12

Cluster 12 → End
```

When FreeDOS opens the file, it follows this chain until the end of the file.

---

# Why Doesn't FAT16 Store Files Continuously?

One question I had during this phase was why files sometimes occupy multiple locations on the disk.

The answer is that free space may not always be available in one continuous region.

As files are created and deleted over time, empty clusters become scattered across the disk.

FAT16 allows a file to occupy multiple clusters and uses the File Allocation Table to link them together.

This flexibility allows storage space to be reused efficiently, although it can also lead to **fragmentation**, where a file is split into many non-contiguous clusters.

---

# FAT16 During Boot

FAT16 also plays a role during the boot process.

After:

```
BIOS

↓

MBR

↓

Bootloader
```

The bootloader begins reading the FAT16 filesystem.

It locates important system files such as those required by FreeDOS.

Without FAT16, the bootloader would not know where these files are stored.

---

# Why Was FAT16 Used?

During the era of DOS and early personal computers, FAT16 offered several advantages:

- Simple design
- Fast implementation
- Low memory requirements
- Supported by many operating systems
- Well suited for relatively small hard disks

Because this project emulates a 486-era computer running FreeDOS, FAT16 is historically appropriate.

---

# FAT16 Limitations

Although FAT16 was widely used, it has several limitations.

Examples include:

- Maximum partition size is relatively small compared to modern filesystems.
- Maximum file size is limited.
- Large disks require larger cluster sizes, which can waste storage space.
- Performance decreases when files become heavily fragmented.

These limitations eventually led to newer filesystems such as FAT32, exFAT, NTFS, and others.

---

# Common Misconceptions

## "FAT16 stores the actual files."

Not exactly.

The Data Area stores the actual file contents.

The File Allocation Table stores information about where those contents are located.

---

## "Formatting copies files onto the disk."

Incorrect.

Formatting only creates the FAT16 filesystem.

Files are copied afterwards.

---

## "The FAT is the same as the filesystem."

The File Allocation Table is one important part of the FAT16 filesystem, but the filesystem also includes the Boot Sector, Root Directory, and Data Area.

---

## "The operating system knows where every file is automatically."

Incorrect.

The operating system relies on the FAT16 structures to locate files.

---

# Questions I Asked During This Phase

## Why did FreeDOS require FAT16?

Because FreeDOS needs a filesystem capable of organizing and locating files on the partition.

---

## Why can't the operating system use raw sectors directly?

Because there would be no organized way to store filenames, directories, or free space.

The filesystem provides this organization.

---

## Why are there two File Allocation Tables?

To improve reliability by maintaining a backup copy of the allocation table.

---

## Why is it called FAT16?

Because each File Allocation Table entry uses 16 bits.

---

# Key Takeaways

- FAT16 stands for **File Allocation Table 16**.
- FAT16 is a filesystem, not a file format.
- Formatting creates the FAT16 filesystem.
- FAT16 organizes files, directories, and free space.
- The File Allocation Table records where file data is stored.
- The Root Directory stores information about files.
- The Data Area stores the actual file contents.
- FreeDOS relies on FAT16 to locate and access files.

---

# Connection to Other Topics

FAT16 connects several concepts studied during Phase 2.

- **BIOS.md** – The BIOS begins the boot process.
- **CMOS.md** – CMOS stores the boot configuration used by the BIOS.
- **Boot-Process.md** – The bootloader eventually reads the FAT16 filesystem.
- **MBR.md** – The MBR starts the boot process from the hard disk.
- **Partitioning.md** – FAT16 exists inside a partition.
- **Formatting.md** – Formatting creates the FAT16 filesystem.
- **FreeDOS.md** – FreeDOS stores its system files within the FAT16 filesystem.

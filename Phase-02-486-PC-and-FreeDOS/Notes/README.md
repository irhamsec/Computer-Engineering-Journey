# Phase 2 Engineering Notes

This folder contains the detailed engineering notes written throughout **Phase 2 – Building a 486 PC & Installing FreeDOS**.

Unlike the main Phase 2 documentation, these notes focus on explaining individual concepts in depth. Each document is written based on my own learning process while building and configuring a virtual Intel 80486 computer using **86Box**.

The goal is not simply to install an operating system, but to understand **how a computer starts from power-on and eventually reaches the DOS command prompt**.

---

# Learning Objectives

Throughout Phase 2, I aimed to understand:

- How a PC boots from power-on
- The responsibilities of the BIOS
- The purpose of CMOS memory
- How storage devices are detected
- Why disks must be partitioned and formatted
- How the FAT16 filesystem organizes files
- The role of the Master Boot Record (MBR)
- How the DOS boot process works
- How FreeDOS is installed and boots successfully

---

# Notes Index

| Topic | Description |
|-------|-------------|
| BIOS.md | Understanding the Basic Input/Output System, POST, and hardware initialization. |
| CMOS.md | CMOS memory, BIOS settings, battery backup, and checksum. |
| Boot-Process.md | Complete boot sequence from CPU reset to the DOS command prompt. |
| MBR.md | Master Boot Record structure, boot code, and partition table. |
| Partitioning.md | Why hard disks are partitioned before formatting. |
| Formatting.md | Creating a filesystem and preparing a partition for file storage. |
| FAT16.md | Internal structure of the FAT16 filesystem and file allocation tables. |
| IDE-and-ATAPI.md | Understanding IDE devices, master/slave configuration, and ATAPI CD-ROMs. |
| FreeDOS.md | Installing and booting the FreeDOS operating system. |
| 86Box.md | Hardware configuration and emulator setup used throughout Phase 2. |

---

# Learning Philosophy

These notes are **not copied from textbooks or documentation**.

Instead, they document:

- Concepts learned during experimentation
- Questions asked during the learning process
- Engineering explanations in my own words
- Practical observations while using 86Box
- Lessons learned from mistakes and troubleshooting

The objective is to build a solid understanding of computer architecture rather than simply following installation steps.

---

# Related Resources

Additional materials for this phase can be found in:

- `../Diagrams/` – Architecture diagrams and illustrations
- `../Screenshots/` – Screenshots captured throughout the project
- `../Handwritten/` *(planned)* – Handwritten engineering notes and sketches

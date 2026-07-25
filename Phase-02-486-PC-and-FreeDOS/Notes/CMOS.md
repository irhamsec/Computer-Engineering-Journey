# CMOS (Complementary Metal-Oxide-Semiconductor)

> CMOS is a semiconductor technology widely used in integrated circuits. In traditional IBM PC-compatible computers, the term "CMOS" commonly refers to the small battery-backed memory that stores BIOS configuration settings.

---

# Overview

**Complementary Metal-Oxide-Semiconductor (CMOS)** is a semiconductor manufacturing technology used to build integrated circuits.

Although CMOS technology is used in many modern electronic devices, the term **"CMOS"** in the context of personal computers usually refers to the small amount of low-power memory that stores the computer's BIOS configuration.

This memory preserves important system settings even when the computer is powered off.

During Phase 2 of this project, CMOS became important because the BIOS reads its stored configuration immediately after the computer starts.

---

# What Does CMOS Stand For?

CMOS stands for:

**C** – Complementary

**M** – Metal

**O** – Oxide

**S** – Semiconductor

The name comes from the transistor technology used to manufacture integrated circuits.

CMOS technology became popular because it consumes very little electrical power compared to earlier logic families.

---

# CMOS Technology vs CMOS Memory

One common source of confusion is that the word **CMOS** has two related meanings.

## 1. CMOS Technology

A semiconductor fabrication technology used to manufacture integrated circuits.

Examples include:

- Microprocessors
- Memory chips
- Image sensors
- Logic circuits

This is the original meaning of CMOS.

---

## 2. CMOS Memory

In IBM PC-compatible computers, CMOS usually refers to the small battery-backed memory that stores BIOS configuration settings.

Examples include:

- Boot order
- Date and time
- Installed hard drives
- CPU configuration
- Memory configuration
- Peripheral settings

Throughout this project, the term **CMOS** refers to **CMOS memory**, not the semiconductor manufacturing process.

---

# Why Does CMOS Exist?

The BIOS needs a place to remember the computer's configuration.

For example:

- Which storage device should boot first?
- What is the current date and time?
- Which hardware features are enabled?
- Which IDE devices are installed?

Without CMOS memory, these settings would be lost every time the computer was turned off.

CMOS allows these settings to remain available across power cycles.

---

# Where is CMOS Located?

CMOS memory is located on the motherboard.

It is powered by a small battery, commonly called the **CMOS battery**.

Because of this battery:

- The stored settings remain available even when the computer is unplugged.
- The real-time clock continues running while the computer is turned off.

---

# What Information is Stored in CMOS?

Typical BIOS configuration settings include:

- System date
- System time
- Boot device order
- IDE hard disk configuration
- CD-ROM configuration
- Floppy drive configuration
- CPU settings
- Memory settings
- Integrated peripherals
- Power management options

These values are read by the BIOS every time the computer starts.

---

# CMOS During the Boot Process

One of the first things the BIOS does after completing the initial hardware startup is to read the CMOS memory.

The boot sequence is:

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

Bootloader

↓

Operating System
```

The CMOS provides the BIOS with the configuration needed to continue the boot process correctly.

---

# CMOS Battery

The CMOS memory is powered by a small battery located on the motherboard.

The battery has two important jobs:

1. Keep the CMOS settings stored while the computer is powered off.
2. Keep the real-time clock (RTC) running continuously.

Without this battery:

- BIOS settings would reset.
- System time would be lost.
- The BIOS would return to its default configuration.

---

# CMOS Checksum

During this project, one important topic discussed was the **CMOS checksum**.

The BIOS calculates a checksum based on the CMOS data.

When the computer starts, the BIOS calculates the checksum again and compares it with the stored value.

If they match:

✔ CMOS data is assumed to be valid.

If they do not match:

❌ The BIOS assumes the CMOS data has become corrupted.

This often results in a message such as:

```
CMOS Checksum Error

Defaults Loaded
```

The BIOS then loads its default configuration.

---

# What is a Checksum?

A checksum is a small calculated value used to detect whether stored data has changed unexpectedly.

It helps detect:

- Corrupted settings
- Weak CMOS battery
- Accidental data modification

However, a checksum **cannot repair corrupted data**.

It can only indicate that an error has occurred.

---

# Checksum vs Hamming Code

During Phase 2, we also discussed the difference between a checksum and a Hamming code.

| Checksum | Hamming Code |
|----------|--------------|
| Detects errors | Detects and corrects certain errors |
| Simple calculation | More complex algorithm |
| Cannot repair data | Can repair some corrupted bits |
| Used by BIOS for CMOS validation | Commonly used in ECC memory |

The CMOS checksum is only an error detection mechanism.

---

# CMOS and BIOS

CMOS and BIOS work together but serve different purposes.

| BIOS | CMOS |
|------|------|
| Firmware | Configuration storage |
| Stored in ROM | Battery-backed memory |
| Executes during startup | Stores BIOS settings |
| Initializes hardware | Supplies configuration information |

A simple way to think about them is:

- **BIOS** is the program.
- **CMOS** stores the program's configuration.

---

# CMOS During This Project

While installing FreeDOS inside 86Box, CMOS was responsible for storing information such as:

- Boot order
- IDE hard disk configuration
- ATAPI CD-ROM configuration
- System date and time

Whenever the virtual machine restarted, the BIOS read these settings before continuing the boot process.

---

# Common Misconceptions

## "CMOS is the BIOS."

Incorrect.

The BIOS is firmware.

CMOS stores the BIOS configuration.

---

## "CMOS stores the operating system."

Incorrect.

The operating system is stored on the hard disk.

CMOS only stores configuration settings.

---

## "CMOS and ROM are the same."

Incorrect.

ROM stores firmware.

CMOS stores BIOS settings.

---

# Questions I Asked During This Phase

## Why does the BIOS need CMOS?

Because the BIOS needs a way to remember configuration settings after the computer is powered off.

---

## Why doesn't the BIOS simply remember everything itself?

The BIOS firmware is stored in ROM.

Its contents are permanent.

User-configurable settings need to be stored in writable memory, which is why CMOS exists.

---

## Why does a dead CMOS battery cause BIOS settings to reset?

Because the CMOS memory requires continuous battery power to retain its stored information.

Without power, the settings are lost.

---

## Why does the BIOS check the CMOS checksum?

To verify that the stored configuration has not become corrupted.

If corruption is detected, the BIOS loads default settings instead of using potentially invalid configuration data.

---

# Key Takeaways

- CMOS stands for **Complementary Metal-Oxide-Semiconductor**.
- CMOS originally refers to a semiconductor manufacturing technology.
- In PCs, CMOS commonly refers to battery-backed memory storing BIOS settings.
- BIOS reads CMOS settings during every startup.
- CMOS stores configuration, not programs.
- CMOS uses a battery to preserve settings when power is removed.
- CMOS checksum detects corrupted configuration data.
- A checksum detects errors but cannot repair them.
- CMOS and BIOS work together during the boot process.

---

# Connection to Other Topics

Understanding CMOS helps explain several other concepts covered in Phase 2.

- **BIOS.md** – The BIOS reads CMOS settings during startup.
- **Boot-Process.md** – CMOS is read before hardware detection and boot device selection.
- **MBR.md** – The BIOS uses CMOS settings to determine which device's MBR to load.
- **FreeDOS.md** – FreeDOS boots only after the BIOS has completed initialization using CMOS configuration.

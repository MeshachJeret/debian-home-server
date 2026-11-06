
# Debian Linux Home Server & File Synchronization

## Introduction

This project is part of my journey of learning Linux system administration, networking, and server management using my old desktop PC.

After successfully installing Debian 13 (Trixie) and experimenting with different desktop environments, I decided to take the project further by turning the computer into a personal home server.

Instead of purchasing dedicated server hardware, I wanted to understand how a regular desktop PC could be used to provide services such as file synchronization, storage management, and remote administration.

Through this project, I am gaining hands-on experience configuring Linux services, managing storage devices, troubleshooting network connectivity, and maintaining a server environment.

**Project Status:** Ongoing

## Table of Contents

- [Project Objectives](#project-objectives)
- [Project Architecture](#project-architecture)
- [Hardware Specifications](#hardware-specifications)
- [Storage Configuration](#storage-configuration)
- [Software and Technologies](#software-and-technologies)
- [Layer 1 — File Synchronization](#layer-1--file-synchronization-using-syncthing)
- [Layer 2 — Versioned Archive](#layer-2--versioned-file-archive)
- [Layer 3 — Backup and Data Recovery](#layer-3--backup-and-data-recovery)
- [Troubleshooting and Technical Evidence](#troubleshooting--technical-evidence)


## Project Objectives

- Build a personal home server using Debian 13 (Trixie).
- Synchronize files between Debian Linux and Windows 11.
- Configure remote administration using SSH.
- Organize storage for synchronization, archiving, and backups.
- Learn how to manage Linux services and troubleshoot system issues.
- Develop practical skills in networking and Linux system administration.

## Project Architecture

The home server is designed around three storage layers:

| Layer | Purpose | Status |
|---|---|---|
| Layer 1 — Sync | Synchronize files between Debian and Windows using Syncthing | Completed |
| Layer 2 — Archive | Maintain separate archived versions of selected files | In Progress |
| Layer 3 — Backup | Create additional recoverable copies of important data | Planned |

The system currently operates over a local network, with Debian acting as the home server and Windows 11 as a connected client.

The archive and backup layers are still being developed and tested.


## Hardware Specifications

Instead of purchasing dedicated server hardware, I decided to reuse my old desktop PC to build and experiment with a personal home server.

The system has limited hardware resources, but it provides an opportunity for me to learn Linux server administration, networking, and storage management.

| Component | Specification |
|---|---|
| Processor | Intel Core i3-3220 @ 3.30 GHz |
| RAM | 4 GB |
| System Drive | 500 GB Seagate HDD |
| Secondary Storage | 500 GB Toshiba HDD |
| Operating System | Debian 13 (Trixie) |
| Network Connection | Home Local Area Network (LAN) |
| Wireless Adapter | TP-Link TL-WN722N v2/v3 |

### Storage Configuration

The Debian operating system is installed on the Seagate HDD, while the Toshiba HDD is used as secondary storage for the home server project.

The secondary drive uses the ext4 filesystem and is mounted at:

`/mnt/HomeStorage`

I organized the storage into three main directories:

```text
/mnt/HomeStorage/
├── Sync/
│   ├── Documents/
│   ├── Projects/
│   └── University/
├── Archive/
└── Backups/
```

Each directory has a different purpose:

- **Sync:** Stores files synchronized between connected devices.
- **Archive:** Intended to preserve separate versions of selected files.
- **Backups:** Reserved for future backup implementation.

The directory structure has been created, but the archive and backup features are still being developed.

**Storage Note:** During testing, the secondary Toshiba HDD experienced filesystem input/output errors and SATA communication issues. The storage setup requires further health verification before it can be considered reliable.

---

## Software and Technologies

| Software / Technology | Purpose |
|---|---|
| Debian 13 (Trixie) | Server operating system |
| Syncthing | File synchronization between devices |
| OpenSSH | Remote administration |
| ext4 | Linux storage filesystem |
| rsync | File copying and archive testing |
| systemd | Linux service management |
| Linux CLI | System configuration and troubleshooting |
| Windows 11 | Client device for synchronization testing |

### Why I Chose These Technologies

I chose Debian Linux because I wanted to develop practical experience with Linux administration using an operating system that I was already exploring.

Syncthing allows me to synchronize files between my Debian server and Windows laptop over my local network.

SSH provides a way to remotely access and administer the Debian system without needing to operate directly from its desktop interface.

I also started exploring rsync for the archive layer to understand how file copying and synchronization tools can be used in storage management.


---

## Layer 1 — File Synchronization Using Syncthing

**Status: Completed**

The first layer of my home server project focuses on synchronizing files between my Debian 13 (Trixie) desktop PC and Windows 11 laptop.

I decided to use Syncthing because it allows files to be synchronized directly between devices without relying on a traditional cloud storage provider.

### 1. Installing and Configuring Syncthing

I installed Syncthing on my Debian server and Windows 11 laptop.

After installation, I configured Syncthing and connected both devices using their device IDs.

I also configured the storage location on my Debian server to use the secondary HDD mounted at:

`/mnt/HomeStorage/Sync`

This allowed me to organize synchronized files separately from the Debian operating system.

### 2. Folder Organization

I created several directories for organizing different types of files.

```text
/mnt/HomeStorage/Sync/
├── Documents/
├── Projects/
└── University/
```

These folders help me organize my personal documents, technical projects, and university-related files.

### 3. Connecting Debian and Windows

I configured Syncthing on both devices and established a connection over my local network.

Once the devices were connected, I configured the shared folder settings and tested file synchronization.

The main goal was to ensure that files could be transferred between Debian Linux and Windows 11.

### 4. Testing File Synchronization

After completing the configuration, I performed a file synchronization test.

I created a test file and verified that it was successfully transferred between the connected devices.

Syncthing also displayed the folder status as **Up to Date**, indicating that the synchronized folders had no pending changes at the time of testing.

**Test Results:**

| Test | Result |
|---|---|
| Debian and Windows device pairing | Passed |
| Local network connectivity | Passed |
| File synchronization | Passed |
| Syncthing folder status | Up to Date |

These tests confirmed that the basic synchronization setup was working.

### 5. Service Management and Troubleshooting

During the setup process, I encountered several issues involving Syncthing services and connectivity.

Some of the problems included:

- Syncthing failing to start because of a lock-related error.
- Service startup failures during configuration.
- Initial difficulties connecting the Debian server and Windows laptop.
- Folder synchronization taking longer than expected.

I investigated these issues by checking service status, reviewing configuration settings, and restarting services when necessary.

Eventually, I managed to establish a working synchronization connection between both devices.

### 6. What I Learned

Through this layer, I gained practical experience in:

- Installing and configuring Syncthing on Linux and Windows.
- Connecting devices over a local network.
- Managing Linux services.
- Organizing storage directories.
- Testing file synchronization.
- Troubleshooting connectivity and service startup problems.

### Layer 1 Outcome
Layer 1 was successfully completed, with Syncthing transferring files between my Debian Linux server and Windows 11 laptop over the local network.

However, file synchronization is not the same as a backup. Changes and deletions can also propagate between synchronized devices.

This is why I planned additional archive and backup layers for the home server project.

The completed status refers to my initial functionality tests. The secondary storage drive still requires further reliability checks.

---

## Layer 2 — Versioned File Archive

**Status: In Progress**

After successfully testing file synchronization using Syncthing, I started working on the second layer of my home server project.

The purpose of Layer 2 is to preserve separate copies of selected files from the synchronization directory.

I chose a versioned archive approach because I wanted to learn how file versions could be preserved without depending entirely on Syncthing.

### 1. Archive Design

My home server uses the following storage directories:

```text
/mnt/HomeStorage/
├── Sync/
│   ├── Documents/
│   ├── Projects/
│   └── University/
├── Archive/
└── Backups/
```

The intended workflow is:

1. Syncthing synchronizes files into the `Sync` directory.
2. Selected files are copied into the `Archive` directory.
3. The archive system preserves earlier file versions.
4. Archived files remain separate from normal synchronization operations.

This design is still being implemented and tested.

### 2. Using rsync

I started experimenting with `rsync`, a Linux utility commonly used for copying and synchronizing files.

My goal was to understand how files could be transferred from the synchronization directory into a separate archive location.

During testing, I explored:

- Copying files between directories.
- Comparing source and destination files.
- Running dry-run operations.
- Using Bash scripts to automate repetitive tasks.

A dry run allows me to preview a file operation without actually copying or modifying files.

### 3. Initial Archive Testing

I performed an initial test by copying a sample file from the synchronization directory into the archive directory.

I used `cmp` to compare the source and destination files.

The comparison confirmed that the copied test file matched the original.

I also experimented with `rsync` dry runs to inspect which files would be processed.

These tests helped me understand the basic file-copying workflow.

### 4. Archive Script Development

I began developing a Bash script to automate archive operations.

The script is intended to process selected directories, including:

- Documents
- Projects
- University

I also tested the script in dry-run mode.

During one test, the script completed successfully and reported no files requiring transfer.

However, a successful dry run does not prove that historical file versions are being preserved.

The versioning functionality still requires further implementation and testing.

### 5. Storage Problems Encountered

During development, the secondary Toshiba HDD experienced input/output errors.

Linux also reported ext4 filesystem errors and SATA communication problems.

At one point, the filesystem was remounted as read-only, preventing further write operations.

These problems affected my ability to continue testing the archive system.

I learned that successful file-copying tests are not enough to guarantee storage reliability.

Before relying on the archive system, I need to verify the health and stability of the storage hardware.

### 6. Current Progress

| Component | Status |
|---|---|
| Archive directory structure | Created |
| Initial file-copying test | Passed |
| File comparison using `cmp` | Passed |
| `rsync` dry-run testing | Passed |
| Bash archive script | Under development |
| Historical version preservation | Not yet verified |
| Storage hardware reliability | Requires further investigation |

### 7. What I Learned

Through Layer 2, I gained experience in:

- Understanding file synchronization versus archiving.
- Working with `rsync` and `cmp`.
- Writing and testing Bash scripts.
- Using dry-run operations before modifying files.
- Investigating Linux filesystem and storage errors.
- Recognizing the importance of reliable storage hardware.

### Layer 2 Outcome

Layer 2 is still under development.

I successfully completed initial file-copying and dry-run tests, but I have not yet verified a complete versioned archive workflow.

My next objective is to resolve the storage reliability issues and continue testing historical file preservation.

This experience has helped me understand that building a home server involves more than configuring software. Hardware reliability, testing, and data integrity are equally important.

Layer 1 was successfully completed, with Syncthing transferring files between my Debian Linux server and Windows 11 laptop over the local network.

However, file synchronization is not the same as a backup. Changes and deletions can also propagate between synchronized devices.

This is why I planned additional archive and backup layers for the home server project.

---

## Layer 3 — Backup and Data Recovery

**Status: Planned — Not Yet Implemented**

After working on file synchronization and versioned archiving, the final stage of my home server project will focus on backups and data recovery.

The main objective of Layer 3 is to protect important files against accidental deletion, corruption, and storage hardware failure.

I want to understand how backup systems work and how to verify that stored data can actually be recovered when needed.

### 1. Why I Need a Backup Layer

During the development of Layer 2, my secondary Toshiba HDD experienced input/output errors and filesystem problems.

This helped me understand that storing files on a separate partition or directory does not necessarily protect them from hardware failure.

My current synchronization and archive directories are located on the same physical Toshiba HDD.

If that drive fails, both the synchronized files and archived copies could become unavailable.

Therefore, I plan to introduce a separate backup destination.

### 2. Proposed Backup Architecture

The planned system consists of three layers:

| Layer | Purpose | Implementation |
|---|---|---|
| Layer 1 — Sync | Synchronize files between devices | Syncthing |
| Layer 2 — Archive | Preserve historical versions of selected files | Bash and rsync |
| Layer 3 — Backup | Maintain recoverable copies on separate storage | To be determined |

The intended workflow is:

```text
Windows 11 Laptop
        |
        | Syncthing
        |
Debian 13 Home Server
        |
        +-- Sync/
        |     |
        |     +-- Documents/
        |     +-- Projects/
        |     +-- University/
        |
        +-- Archive/
        |     |
        |     +-- Historical Versions (Planned)
        |
        +-- Backups/
              |
              +-- Local Staging (Planned)

Separate Backup Storage
        |
        +-- Recoverable Backup Copies (Planned)
```

The `Backups` directory on the Toshiba HDD may be used for temporary staging, but it will not be considered an independent backup destination.

### 3. Planned Backup Features

I plan to explore the following features:

- Creating backup copies on a separate physical storage device.
- Preserving older versions of important files.
- Scheduling backup operations.
- Recording backup logs and error messages.
- Verifying backup integrity.
- Testing file restoration.
- Investigating backup encryption and access permissions.

These features are currently planned and have not been implemented.

### 4. Backup Verification

One of my main goals is to learn how to verify that backups are recoverable.

A successful file-copying operation does not automatically guarantee that a backup can be restored.

I plan to test:

1. Creating a backup of sample files.
2. Verifying that the backup contains the expected files.
3. Restoring sample files into a separate test directory.
4. Comparing restored files with their original versions.
5. Recording the results of the restoration test.

I will use test files during development to avoid risking important personal data.

### 5. Future Improvements

Before implementing Layer 3, I need to:

- Investigate the Toshiba HDD storage errors.
- Decide on a suitable independent backup destination.
- Complete and verify the versioned archive workflow.
- Evaluate appropriate Linux backup tools.
- Design a backup schedule and retention policy.
- Test recovery procedures.

### Layer 3 Outcome

Layer 3 remains in the planning stage.

Although the backup system has not yet been implemented, designing this layer has helped me understand the importance of data protection and recovery.

My goal is not only to store files but also to develop a system where important data can be recovered if something goes wrong.

---

## Troubleshooting & Technical Evidence

Throughout this home server project, I encountered several technical problems involving Linux services, networking, storage devices, and filesystem reliability.

These challenges gave me practical experience in identifying problems, examining system behaviour, and testing possible solutions.

### 1. Syncthing Service Startup Problems

**Problem:**

During the initial configuration, Syncthing sometimes failed to start correctly.

I encountered errors including:

- `Failed to acquire lock`
- `Service failed (repeated too quickly)`

These errors interrupted the synchronization setup.

**Investigation and Troubleshooting:**

I investigated the Syncthing process and service status, checked the running instances, and retried the service configuration.

I also tested running Syncthing manually while investigating the startup problem.

**Outcome:**

Syncthing eventually started successfully, and I established file synchronization between my Debian server and Windows 11 laptop.

The service became functional, although I did not establish a definitive root cause for every startup failure.

### 2. SSH Connectivity Problems

**Problem:**

While configuring SSH for remote administration, I encountered connection timeouts and authentication failures.

These issues initially prevented me from reliably accessing the Debian server from another device.

**Investigation and Troubleshooting:**

I checked the connection and authentication behaviour and retried access after restarting the system.

**Outcome:**

SSH connectivity was eventually restored, allowing me to access the Debian system remotely.

This helped me gain experience with remote Linux administration and basic network troubleshooting.

### 3. Toshiba HDD Input/Output Errors

**Problem:**

During archive testing, I encountered an input/output error while attempting to write a file to the secondary Toshiba HDD.

An example of the affected location was:

`/mnt/HomeStorage/Sync/Documents/`

The filesystem subsequently experienced journal-related errors and was remounted as read-only.

**Technical Evidence:**

The Linux kernel logs included messages such as:

```text
ata1.01: failed to resume link
ata1.00: link is slow to respond
limiting SATA link speed to 1.5 Gbps
reset failed, giving up
```

These messages indicated problems communicating with the storage device through the SATA connection.

**Investigation:**

I examined the storage-related errors and attempted to check the drive's health.

A SMART short self-test was unsuccessful and returned an aborted-command error.

The evidence suggested a storage hardware or connection problem, but the exact cause had not been confirmed.

Possible causes requiring further investigation include:

- HDD hardware failure.
- SATA data cable or connector problems.
- SATA power connection issues.
- Storage controller or interface problems.

**Outcome:**

The storage issue remained unresolved during the documented tests.

Because the secondary drive was not behaving reliably, I could not consider the archive system safe for important files.

This experience demonstrated the importance of investigating hardware and filesystem errors before deploying storage services.

### 4. Archive Script Testing

**Problem:**

While developing Layer 2, I needed to verify that my archive script processed the intended directories without accidentally modifying files.

**Testing Approach:**

I used `rsync` dry-run operations to preview file transfers.

The script processed the following directories:

- Documents
- Projects
- University

An example of the test command was:

```bash
bash ~/server-scripts/hybrid-archive.sh
```

The script reported:

```text
Dry run completed successfully.
```

**Outcome:**

The dry-run test completed without reporting an error.

However, the test did not demonstrate that historical file versions were preserved or that the storage device was reliable.

Additional testing is required before enabling actual versioned archive operations.

### 5. Troubleshooting Summary

| Issue | Result |
|---|---|
| Syncthing startup failures | Functionality restored |
| Debian–Windows synchronization | Initial tests passed |
| SSH connectivity failures | Access restored |
| Toshiba HDD input/output errors | Unresolved |
| Archive script dry-run testing | Passed |
| Historical version preservation | Not yet verified |

### Lessons Learned

Through these troubleshooting experiences, I learned:

- How to investigate Linux service failures.
- The importance of checking system logs and error messages.
- How SSH and network connectivity problems can affect remote administration.
- How storage hardware problems can affect filesystem reliability.
- Why dry-run testing is useful before performing file operations.
- The importance of distinguishing successful tests from fully reliable systems.

I also learned that troubleshooting is not always about finding an immediate solution.

Sometimes, understanding the problem, documenting the evidence, and identifying the next investigation steps are equally important.

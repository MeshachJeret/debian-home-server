
# Debian Linux Home Server & File Synchronization

## Introduction

This project is part of my journey of learning Linux system administration, networking, and server management using my old desktop PC.

After successfully installing Debian 13 (Trixie) and experimenting with different desktop environments, I decided to take the project further by turning the computer into a personal home server.

Instead of purchasing dedicated server hardware, I wanted to understand how a regular desktop PC could be used to provide services such as file synchronization, storage management, and remote administration.

Through this project, I am gaining hands-on experience configuring Linux services, managing storage devices, troubleshooting network connectivity, and maintaining a server environment.

**Project Status:** Ongoing

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

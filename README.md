
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

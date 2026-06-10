# Windows Fundamentals

## Windows Editions

### Overview

Microsoft Windows is one of the most widely used operating systems in both personal and corporate environments. Due to its popularity, it has historically been a major target for attackers, malware developers, and cybercriminals.

### Windows Version History

#### Windows XP

* One of Microsoft's most successful operating systems.
* Widely adopted by businesses and home users.
* Remained in use for many years after release.

#### Windows Vista

* Released as a major redesign of Windows.
* Introduced significant interface and security changes.
* Suffered from compatibility and performance issues.
* Was not widely accepted and was quickly replaced.

#### Windows 7

* Released as Vista's successor.
* Became highly popular in enterprise environments.
* Organizations migrated from Windows XP to Windows 7.
* Hardware and software vendors had to ensure compatibility.

#### Windows 8 / 8.1

* Introduced a tablet-oriented interface.
* Had mixed reception among users.
* Short-lived compared to Windows 7 and Windows 10.

#### Windows 10

* Introduced a modernized Start Menu.
* Combined traditional desktop features with newer functionality.
* Became the dominant desktop operating system for many years.

#### Windows 11

* Current desktop operating system.
* Available in:

  * Windows 11 Home
  * Windows 11 Pro

### Windows Server

Server editions are designed for enterprise infrastructure.

Examples:

* Windows Server 2019
* Windows Server 2022
* Windows Server 2025

### Key Points

* Windows dominates both home and enterprise computing.
* Security has improved significantly with each version.
* Older versions eventually reach End-of-Life (EOL) and stop receiving updates.

---

# The Desktop (GUI)

## GUI (Graphical User Interface)

The Windows Desktop is the first screen displayed after a successful login.

Users authenticate using:

* Local account credentials
* Domain credentials (Active Directory)

### Components of the Windows Desktop

1. Desktop
2. Start Menu
3. Search Box (Cortana/Search)
4. Task View
5. Taskbar
6. Toolbars
7. Notification Area

---

## Desktop

The Desktop serves as the primary workspace.

### Uses

* Store files
* Store folders
* Create shortcuts
* Quick access to applications

### Desktop Customization

Right-clicking on the desktop allows you to:

* Change icon size
* Sort icons
* Refresh desktop
* Create new files/folders
* Access display settings
* Access personalization settings

---

## Display Settings

Display Settings allow modification of:

* Screen Resolution
* Display Orientation
* Scaling
* Multiple Monitor Configuration
* Night Light Settings

### Note

Some display options may be disabled during Remote Desktop sessions.

---

## Personalization

Personalization settings allow users to customize:

* Desktop Wallpaper
* Themes
* Fonts
* Colors
* Lock Screen
* Background Images

---

# The Start Menu and Taskbar

## Start Menu

The Start Menu provides centralized access to:

* Applications
* Programs
* Utilities
* System Tools
* Settings

Modern Windows versions use the Windows logo instead of the word "Start".

### Sections of the Start Menu

#### 1. Account and System Actions

Provides shortcuts for:

* User Account Settings
* Documents
* Pictures
* Lock
* Sign Out
* Settings
* Power Options

#### 2. Application List

Displays:

* Recently Added Programs
* Installed Applications
* Programs arranged alphabetically

### Alphabet Navigation

When many programs are installed:

* Clicking a letter heading opens an alphabet grid.
* Allows quick navigation through installed applications.

---

## Tiles

The right side of the Start Menu contains Tiles.

### Tile Features

Tiles can:

* Launch applications
* Be resized
* Be pinned
* Be unpinned
* Display application information

Examples:

* PowerShell
* Event Viewer
* Task Manager
* Control Panel

---

## Taskbar

The Taskbar is located at the bottom of the desktop.

### Functions

Displays:

* Running Applications
* Open Files
* Open Folders
* Pinned Programs

### Taskbar Options

Right-clicking the taskbar provides options such as:

* Toolbars
* Search
* Task View Button
* Task Manager
* Lock Taskbar
* Taskbar Settings

### Preview Feature

Hovering over an application icon displays:

* Thumbnail Preview
* Application Name
* Active Window Information

---

## Notification Area

Located on the bottom-right side of the Taskbar.

Displays:

* Date
* Time
* Network Status
* Volume Controls
* Security Notifications
* Background Application Icons

Users can customize which icons appear in this area.

---

# The File System

## NTFS (New Technology File System)

Modern Windows installations primarily use NTFS.

### Previous Windows File Systems

#### FAT16

File Allocation Table (16-bit)

#### FAT32

File Allocation Table (32-bit)

#### HPFS

High Performance File System

---

## Advantages of NTFS

Compared to FAT systems, NTFS supports:

### Larger Files

Files greater than 4GB can be stored.

### File and Folder Permissions

Granular access control.

### Compression

Built-in file compression support.

### Encryption

Encrypting File System (EFS).

### Reliability

NTFS is a journaling file system.

If a system failure occurs, NTFS can use log information to help recover file system consistency.

---

## NTFS Permissions

Common NTFS permissions include:

### Full Control

Complete access to files and folders.

### Modify

Read, write, and delete permissions.

### Read & Execute

View and run files.

### List Folder Contents

View contents of a directory.

### Read

Open and view files.

### Write

Create and modify files.

---

## Why NTFS Matters in Cybersecurity

Security analysts often investigate:

* File permissions
* Unauthorized file access
* Malware persistence
* Encrypted files
* Alternate Data Streams
* Access control issues

Understanding NTFS is essential for Windows security analysis.

# The Windows\System32 Folder

## Windows Directory

The Windows operating system is typically installed in:

```text
C:\Windows
```

This directory contains the core operating system files required for Windows to function properly.

Although Windows is commonly installed on the C: drive, it can technically be installed on another drive.

---

## Environment Variables

Windows uses environment variables to reference important system locations.

Example:

```text
%windir%
```

`%windir%` points to the Windows installation directory.

### Purpose of Environment Variables

Environment variables store information such as:

* Operating system paths
* Temporary folder locations
* System configuration information
* User-specific locations

---

## System32

One of the most important folders inside the Windows directory is:

```text
C:\Windows\System32
```

### Contents of System32

* Critical operating system files
* DLL files
* Device drivers
* Administrative tools
* Configuration files
* Windows utilities

### Importance

System32 is essential to Windows operation.

Deleting or modifying files inside this directory can:

* Cause application failures
* Prevent Windows from booting
* Corrupt the operating system

### Cybersecurity Relevance

Security analysts frequently investigate System32 because:

* Malware often attempts to hide here.
* Attackers may place malicious files in trusted locations.
* Persistence mechanisms sometimes abuse System32 components.

---

# User Accounts, Profiles, and Permissions

## Types of User Accounts

Windows commonly uses two account types:

### Administrator

Administrators can:

* Add users
* Delete users
* Modify groups
* Change system settings
* Install software
* Manage security settings

### Standard User

Standard Users can:

* Access their own files
* Run applications
* Modify personal settings

Standard users cannot:

* Install many programs
* Modify critical system settings
* Perform administrative actions

---

## Managing User Accounts

User accounts can be viewed through:

```text
Settings → Accounts → Other Users
```

Administrators may:

* Add users
* Remove users
* Change account types

---

## User Profiles

When a user logs in for the first time, Windows creates a user profile.

Profile location:

```text
C:\Users\<username>
```

Example:

```text
C:\Users\Max
```

---

## Common User Profile Folders

Each user profile contains folders such as:

* Desktop
* Documents
* Downloads
* Music
* Pictures
* Videos

These folders store user-specific data.

---

## User Profile Service

When a user signs in for the first time:

* Windows creates the profile.
* User settings are initialized.
* Default folders are generated.

This process is handled by the User Profile Service.

---

## Local Users and Groups Management

Windows provides a management console for user administration.

Run:

```text
lusrmgr.msc
```

This tool allows administrators to:

* View users
* Create users
* Delete users
* Manage groups
* Modify permissions

---

## Cybersecurity Relevance

User account analysis helps identify:

* Unauthorized accounts
* Privilege abuse
* Insider threats
* Misconfigured permissions
* Persistence mechanisms

---

# User Account Control (UAC)

## What is UAC?

User Account Control (UAC) is a security feature designed to prevent unauthorized system changes.

Even if a user belongs to the Administrators group, applications do not automatically receive elevated privileges.

---

## Why UAC Exists

Without UAC:

* Malware would gain administrative privileges immediately.
* System files could be modified more easily.
* Attackers could compromise systems faster.

UAC adds an extra security layer.

---

## How UAC Works

When a program requires elevated privileges:

1. Windows detects the request.
2. A UAC prompt appears.
3. User approval is required.
4. The application runs with elevated permissions.

---

## UAC Prompt

Common actions triggering UAC:

* Installing software
* Modifying system settings
* Changing security configurations
* Editing protected files

---

## UAC Shield Icon

Applications requiring elevated privileges often display a shield icon.

This indicates administrator approval may be required before execution.

---

## Security Benefits

UAC helps:

* Prevent unauthorized changes
* Limit malware execution
* Reduce privilege escalation risks
* Improve overall system security

---

# Settings and Control Panel

## Windows Settings

Settings is the modern configuration interface introduced in newer Windows versions.

Categories include:

### System

* Display
* Sound
* Notifications
* Power

### Devices

* Bluetooth
* Printers
* Mouse

### Network & Internet

* Wi-Fi
* Ethernet
* VPN

### Personalization

* Themes
* Colors
* Backgrounds

### Accounts

* User accounts
* Sign-in options

### Privacy

* Application permissions
* Location settings

### Update & Security

* Windows Update
* Recovery
* Backup

---

## Control Panel

Control Panel is the traditional Windows management interface.

Common categories:

### System and Security

* Security settings
* System information
* Event Viewer

### Network and Internet

* Network configuration
* Sharing settings

### Hardware and Sound

* Devices
* Printers
* Audio configuration

### Programs

* Install programs
* Uninstall programs
* Windows Features

### User Accounts

* Account management
* Credential management

### Appearance and Personalization

* Themes
* Fonts
* Display settings

---

## Programs and Features

Located in:

```text
Control Panel → Programs → Programs and Features
```

Allows users to:

* View installed software
* Remove applications
* Repair programs
* Modify installations

---

## Settings vs Control Panel

| Settings            | Control Panel           |
| ------------------- | ----------------------- |
| Modern Interface    | Traditional Interface   |
| Easier Navigation   | More Advanced Options   |
| Windows 10/11 Focus | Legacy Management Tools |
| Touch Friendly      | Administrative Features |

---

## Searching for Settings

Instead of browsing menus manually, users can search directly from the Start Menu.

Example:

```text
wallpaper
```

Windows will display relevant configuration options.

---

# Task Manager

## Overview

Task Manager is one of the most useful administrative tools in Windows.

It provides information about:

* Running applications
* Background processes
* CPU usage
* Memory usage
* Disk activity
* Network activity

---

## Opening Task Manager

Method 1:

Right-click the Taskbar → Task Manager

Method 2:

```text
Ctrl + Shift + Esc
```

Method 3:

```text
Ctrl + Alt + Delete
```

Then select Task Manager.

---

## Simple View

Initially, Task Manager may open in Simple View.

This displays:

* Running applications
* Basic process information

---

## More Details View

Selecting **More Details** reveals advanced information.

---

## Important Tabs

### Processes

Displays:

* Running applications
* Background processes
* Resource consumption

---

### Performance

Shows:

* CPU utilization
* Memory usage
* Disk activity
* Network usage

Useful for troubleshooting performance issues.

---

### Users

Displays currently logged-in users and resource consumption.

---

### Details

Shows detailed process information including:

* Process IDs (PID)
* Status
* Priority levels

---

### Services

Displays Windows services and their status.

---

## Cybersecurity Importance

Task Manager is frequently used during investigations to:

* Identify suspicious processes
* Detect malware activity
* Analyze resource abuse
* Terminate malicious programs
* Investigate system performance issues

Understanding Task Manager is a fundamental Windows and cybersecurity skill.

---

# Windows Fundamentals Summary

Key topics learned:

* Windows Editions
* Desktop GUI
* Start Menu
* Taskbar
* NTFS File System
* System32
* User Accounts
* User Profiles
* User Account Control (UAC)
* Settings
* Control Panel
* Task Manager

These concepts form the foundation for Windows administration, digital forensics, SOC analysis, incident response, and cybersecurity operations.

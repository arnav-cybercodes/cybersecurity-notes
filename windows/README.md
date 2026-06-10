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

# System Configuration (MSConfig) & Advanced System Settings

## System Configuration (MSConfig)

MSConfig is an advanced troubleshooting utility primarily used to diagnose startup and boot-related issues.

Launch:

```text
msconfig
```

Administrator privileges are required to access this utility.

---

## MSConfig Tabs

### 1. General Tab

Controls what Windows loads during startup.

Startup options:

* Normal Startup
* Diagnostic Startup
* Selective Startup

#### Normal Startup

Loads all device drivers and services.

#### Diagnostic Startup

Loads only basic devices and services.

#### Selective Startup

Allows custom control over startup services and applications.

---

### 2. Boot Tab

Used to configure operating system boot options.

Common options:

* Safe Boot
* No GUI Boot
* Boot Log
* Base Video
* OS Boot Information

Useful for troubleshooting startup issues.

---

### 3. Services Tab

Displays all Windows services regardless of whether they are:

* Running
* Stopped

A service is a background process that performs specific functions for the operating system or applications.

---

### 4. Startup Tab

Modern Windows versions redirect startup management to Task Manager.

MSConfig itself is no longer used to manage startup programs.

Startup items can be viewed through:

```text
Task Manager → Startup
```

or

```text
shell:startup
```

The Startup folder contains programs configured to launch automatically when a user signs in.

---

### 5. Tools Tab

Provides shortcuts to numerous Windows administrative utilities.

Examples:

* About Windows
* Change UAC Settings
* Computer Management
* System Information
* Event Viewer
* Programs and Features
* Internet Options

Each tool includes a description and launch command.

---

# Advanced System Settings

Open:

```text
View advanced system settings
```

This opens the System Properties window.

---

## Performance Settings

Path:

```text
System Properties → Advanced → Performance → Settings
```

Used to configure:

* Visual Effects
* Processor Scheduling
* Memory Usage
* Virtual Memory

---

## Virtual Memory (Page File)

Windows uses a page file when physical RAM becomes full.

Purpose:

* Prevent application crashes
* Improve stability
* Extend available memory

Information available:

* Drive location
* Initial size
* Maximum size
* Automatic management status

---

## Startup and Recovery

Path:

```text
Advanced → Startup and Recovery → Settings
```

Controls:

* Startup behavior
* Recovery options
* Crash dump generation

---

## Crash Dumps

A crash dump is a file created when Windows encounters a critical error (Blue Screen).

Supported dump types:

* Automatic Memory Dump
* Kernel Memory Dump
* Small Memory Dump (256 KB)
* Complete Memory Dump
* None

Crash dumps are useful for forensic analysis and troubleshooting.

---

# Change UAC Settings

## User Account Control (UAC)

UAC helps prevent unauthorized changes to Windows.

Access:

```text
Change UAC Settings
```

---

## UAC Security Levels

### Always Notify

Highest security level.

Windows notifies whenever:

* Applications make changes
* Users make system changes

Desktop is dimmed using Secure Desktop.

---

### Notify Me Only When Apps Try To Make Changes (Default)

* Alerts for application changes
* Does not alert for Windows settings modifications

Default configuration.

---

### Notify Without Dimming

Same as default but Secure Desktop is disabled.

---

### Never Notify

Lowest security level.

No notifications are displayed.

Not recommended.

---

# Computer Management

Launch:

```text
compmgmt.msc
```

Computer Management is divided into three major sections:

1. System Tools
2. Storage
3. Services and Applications

---

# System Tools

## Task Scheduler

Task Scheduler automates tasks on Windows.

Capabilities:

* Run applications
* Execute scripts
* Trigger actions on schedules
* Run tasks at logon/logoff

### Common Triggers

* Daily
* Weekly
* Monthly
* One-Time Events
* System Startup
* User Login

Task Scheduler Library stores all scheduled tasks.

---

## Event Viewer

Event Viewer records system activity and logs.

Used for:

* Troubleshooting
* Security Monitoring
* Incident Investigation
* System Diagnostics

Launch:

```text
eventvwr.msc
```

---

### Event Types

#### Error

Indicates a significant problem.

Example:

* Service startup failure

#### Warning

Potential future issue.

Example:

* Low disk space

#### Information

Successful operation notification.

#### Success Audit

Successful security-related action.

Example:

* Successful login

#### Failure Audit

Failed security-related action.

Example:

* Failed login attempt

---

### Standard Windows Logs

#### Application

Events generated by applications.

#### Security

Authentication and security events.

#### System

Events generated by Windows components.

#### Custom Logs

Application-specific logs.

---

## Shared Folders

Displays shared resources available on the system.

Includes:

* Shares
* Sessions
* Open Files

Useful for identifying network-accessible resources.

---

## Local Users and Groups

Provides management of:

* Local users
* Local groups
* Permissions

Launch:

```text
lusrmgr.msc
```

---

## Performance Monitor (PerfMon)

Launch:

```text
perfmon
```

Used to monitor:

* CPU usage
* Memory usage
* Disk performance
* Network activity

Can collect real-time and historical performance data.

---

## Device Manager

Launch:

```text
devmgmt.msc
```

Used to:

* View hardware devices
* Update drivers
* Disable devices
* Troubleshoot hardware

Examples:

* Network Adapters
* Disk Drives
* Keyboards
* Monitors
* Processors

---

# Storage

## Disk Management

Provides advanced disk administration.

Functions:

* Create partitions
* Extend partitions
* Shrink partitions
* Format volumes
* Assign drive letters

Useful for managing storage devices.

---

# Services and Applications

## Services

Displays all Windows services.

Information shown:

* Service Name
* Display Name
* Status
* Startup Type
* Logon Account

---

### Startup Types

#### Automatic

Starts when Windows boots.

#### Manual

Starts only when required.

#### Disabled

Cannot start.

---

## Windows Management Instrumentation (WMI)

WMI provides a standardized method for accessing management information about Windows systems.

Widely used by:

* Administrators
* Monitoring Tools
* Security Products
* PowerShell Scripts

---

# System Information

Launch:

```text
msinfo32
```

Provides detailed information about:

* Hardware
* Components
* Software Environment

---

## System Summary

Displays:

* OS Name
* Version
* System Model
* Processor
* BIOS Information

---

## Hardware Resources

Contains information about:

* IRQs
* DMA
* Memory
* I/O Resources

Primarily useful for advanced troubleshooting.

---

## Components

Provides detailed information about hardware.

Examples:

* Display
* Sound Devices
* Storage
* USB
* Network Adapters

---

## Software Environment

Provides information about:

* Drivers
* Services
* Running Tasks
* Startup Programs
* Environment Variables
* Network Connections

---

## Environment Variables

Environment variables store system-related information.

Examples:

```text
%windir%
%temp%
%systemroot%
```

Common uses:

* Locating files
* Application configuration
* System automation

---

# Resource Monitor

Launch:

```text
resmon
```

Resource Monitor provides detailed performance monitoring.

Unlike Task Manager, it offers deeper visibility into system resource usage.

---

## Resource Monitor Categories

### CPU

Displays:

* Running Processes
* Services
* Handles
* Modules

---

### Memory

Displays:

* Physical Memory Usage
* Available Memory
* Standby Memory
* Memory Allocation

---

### Disk

Displays:

* Disk Activity
* Read Operations
* Write Operations
* Disk Queue Length

---

### Network

Displays:

* Network Activity
* TCP Connections
* Listening Ports
* Remote Connections

---

## Benefits

Resource Monitor helps:

* Identify bottlenecks
* Diagnose slow systems
* Analyze network activity
* Investigate suspicious processes

---

# Command Prompt

Launch:

```text
cmd
```

Command Prompt is a command-line interface used to interact directly with Windows.

---

## hostname

Displays the computer name.

```cmd
hostname
```

---

## whoami

Displays the currently logged-in user.

```cmd
whoami
```

---

## ipconfig

Displays network configuration.

```cmd
ipconfig
```

Information shown:

* IP Address
* Subnet Mask
* Default Gateway
* DNS Information

---

## Command Help

Most commands support:

```cmd
command /?
```

Example:

```cmd
ipconfig /?
```

Displays available options and syntax.

---

## cls

Clears the command prompt screen.

```cmd
cls
```

---

## netstat

Displays:

* Active TCP Connections
* Listening Ports
* Network Statistics

```cmd
netstat
```

Useful for network troubleshooting and threat hunting.

---

# Registry Editor

Launch:

```text
regedit
```

The Windows Registry is a hierarchical database that stores operating system and application configuration information.

---

## Registry Stores Information About

* User Profiles
* Installed Applications
* File Associations
* Hardware Configuration
* Network Settings
* System Settings

---

## Important Registry Hives

### HKEY_CLASSES_ROOT (HKCR)

File associations and object linking information.

### HKEY_CURRENT_USER (HKCU)

Current user's settings.

### HKEY_LOCAL_MACHINE (HKLM)

System-wide configuration.

### HKEY_USERS (HKU)

All user profiles.

### HKEY_CURRENT_CONFIG (HKCC)

Current hardware profile.

---

## Warning

Improper registry modifications can:

* Break applications
* Cause boot issues
* Corrupt Windows

Always create backups before modifying the registry.

---

## WINDOWS UPDATE
-----------------
Windows Update is a Microsoft service that provides:
• Security updates
• Feature enhancements
• Bug fixes and patches
• Microsoft Defender updates

Patch Tuesday:
• Updates are usually released on the 2nd Tuesday of every month.
• Critical updates may be released earlier if needed.

Important:
• Updates help keep systems secure.
• Many updates require a restart.
• Windows 10/11 updates cannot be postponed forever.

Command:
control /name Microsoft.WindowsUpdate


## WINDOWS SECURITY
-------------------
Windows Security is the central dashboard for managing Windows protection.

Protection Areas:
• Virus & Threat Protection
• Firewall & Network Protection
• App & Browser Control
• Device Security

Status Indicators:
• Green = Protected
• Yellow = Recommendation available
• Red = Immediate action required


## VIRUS & THREAT PROTECTION
----------------------------
Current Threats:
• Shows threat status.
• Displays scan history.
• Shows detected threats.

Scan Types:
• Quick Scan – Checks common malware locations.
• Full Scan – Scans entire system.
• Custom Scan – Scans selected files/folders.

Threat History:
• Last Scan
• Quarantined Threats
• Allowed Threats

Virus & Threat Protection Settings:
• Real-Time Protection – Continuously scans for threats.
• Cloud-Delivered Protection – Uses Microsoft cloud intelligence.
• Automatic Sample Submission – Sends suspicious files to Microsoft.
• Controlled Folder Access – Protects files from ransomware.
• Exclusions – Files/folders ignored by antivirus scans.
• Notifications – Security alerts from Defender.

Warning:
Only allow threats or create exclusions if you are absolutely sure they are safe.


## FIREWALL & NETWORK PROTECTION
--------------------------------
Firewall:
A security feature that controls incoming and outgoing network traffic.

Firewall Profiles:

Domain Profile
• Used on domain networks.

Private Profile
• Used on trusted home/work networks.

Public Profile
• Used on public networks such as airports and cafés.

Functions:
• Turn Firewall On/Off
• Block Incoming Connections
• Allow Apps Through Firewall
• Create Firewall Rules
• Monitor Network Traffic

Command:
wf.msc

Best Practice:
Keep Windows Defender Firewall enabled.


## APP & BROWSER CONTROL
------------------------
Microsoft Defender SmartScreen:
Protects against:
• Malicious websites
• Phishing attacks
• Dangerous downloads
• Unrecognized applications

Modes:
• Block
• Warn
• Off

Exploit Protection:
Built-in security mitigations including:
• Control Flow Guard (CFG)
• Data Execution Prevention (DEP)
• Address Space Layout Randomization (ASLR)


## DEVICE SECURITY
------------------
Provides hardware-based protection.

Core Isolation:
Uses virtualization-based security.

Memory Integrity:
• Prevents malicious code injection into protected processes.

Security Processor:
• Trusted Platform Module (TPM)

TPM Benefits:
• Stores cryptographic keys securely.
• Supports BitLocker encryption.
• Protects sensitive data.
• Detects tampering attempts.


## BITLOCKER
------------
BitLocker is Microsoft's full-disk encryption feature.

Purpose:
• Protects data if a device is lost or stolen.
• Prevents unauthorized access to drives.
• Helps detect system tampering.

Best Protection:
• Use with TPM 1.2 or later.

Advantages:
• Full drive encryption
• Data protection
• Improved system security


## VOLUME SHADOW COPY SERVICE (VSS)
-----------------------------------
VSS creates shadow copies (snapshots) of files and drives.

Uses:
• Create Restore Points
• System Restore
• Restore Previous Versions
• Backup Operations

Stored In:
• System Volume Information folder

Security Note:
Ransomware often deletes shadow copies to prevent recovery.

VSS Functions:
• Create restore points
• Perform system restore
• Configure restore settings
• Delete restore points


QUICK REVISION
--------------
Patch Tuesday = 2nd Tuesday of every month
TPM = Trusted Platform Module
BitLocker = Full disk encryption
SmartScreen = Protection against malicious apps/websites
Firewall = Controls network traffic
Real-Time Protection = Continuous malware monitoring
VSS = Creates snapshots for backup and recovery
Memory Integrity = Prevents code injection attacks
wf.msc = Opens Windows Defender Firewall
control /name Microsoft.WindowsUpdate = Opens Windows Update

operations.

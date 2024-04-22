---
title: 'MacOS fundamentals'
date: 2024-04-21
tags: ["macos", "security"]
TocOpen: true
---


## What is macOS ?

- macOS is the operating system used on Apple computers.
- Widely used in daily home use, business management, graphical design, and arts.

**History Roundup**

- Original start to OS X: Fall 2000, public beta named Kodiak, followed by Mac OS X (10.0) Cheetah and OS X (10.1) Puma.
- Notable releases: OS X (10.2) Jaguar, OS X (10.3) Panther, OS X (10.4) Tiger with Intel support, OS X (10.5) Leopard with Time Machine and Boot Camp, OS X (10.6) Snow Leopard.
- Introduction of iOS in 2007.
- OS X (10.7) Lion brought iOS features to macOS.
- Transition to yearly releases with OS X (10.9) Mavericks, followed by OS X (10.10) Yosemite, OS X (10.11) El Capitan, macOS (10.12) Sierra with Siri and Apple Pay.
- macOS (10.13) High Sierra introduced Apple File System (APFS).
- macOS (10.14) Mojave with Dark Mode and iOS app ports.
- macOS (10.15) Catalina split iTunes and introduced Sidecar.
- macOS 11 Big Sur introduced Apple Silicon support.
- macOS 12 Monterey brought Universal Control and AirPlay changes.
- macOS 13 Ventura introduced Stage Manager and Continuity Camera.

**OS & Architecture Info**

- Kernel: XNU (Mach kernel basis with BSD portions).
- OS Base: Darwin, a FreeBSD derivative open-sourced by Apple.
- Recent shift to support Apple Silicon while still supporting Intel processors.

**Core Components**

- GUI: Aqua provides the graphical interface and visual theme.
- File Manager: Finder manages the desktop and files.
- Application Sandbox: Restricts app access outside necessary resources.
- Cocoa: Application management layer and API, used for built-in apps and development.


## macOS Domains

|Domain|Description|
|---|---|
|Local Domain|Contains resources such as apps local to the computer and shared among all users.|
|System Domain|Contains system software installed by Apple.|
|User Domain|Contains resources specific to users who log in to the system, reflecting their home directory.|
|Network Domain|Contains resources like apps and documents shared among users of a local area network.|

## Standard Directories

|Directory|Description|
|---|---|
|/Applications|Contains applications installed for users, local, and system domains.|
|/Users|User directory containing user-specific applications, files, and resources.|
|/Library|Stores custom data files, caches, configurations, resources, and preferences for applications.|
|/Network|Contains files belonging to the network domain, listing computers in the local area network.|
|/System|Contains system resources required by macOS to run, installed by Apple.|
|/bin|Main storage point for binaries.|
|/dev|Maintains device-id files enabling the use of hardware devices.|
|/etc|Contains system and application configuration files.|
|/sbin|Contains essential administrative binaries.|
|/tmp|Used by the operating system to store temporary files.|
|/usr|Contains libraries and applications such as FTP, SSH, etc.|
|/var|Stores system log files, web server sources, backups, etc.|
|/private|Stores critical system files and caches required for operation.|
|/opt|Storage point for third-party applications or packages.|
|/cores|Contains Core Dumps stored by MacOS for troubleshooting.|
|/home|Subdirectories for each user for storage, including Desktop, Downloads, and Documents folders.|

## File and Directory Permissions

These permissions are shown utilizing the `octal` or Base 8 (0-7) numbering system. They are used to apply the `read`, `write`, and `execute` attributes to the contexts of `User owner`, `Group owner`, and `Others` on a file. These are represented as:

|**Attribute**|**Octal Value**|
|---|---|
|(`r`) - Read|`Octal value of 4`|
|(`w`) - Write|`Octal value of 2`|
|(`x`) - Execute|`Octal value of 1`|

- **chmod**: Change file permissions.
    - Example: `chmod 777 <file>`
- **chown**: Change file ownership.
    - Example: `sudo chown <new_user> <file>`
	- Example: `sudo chown <new_user>:<new_group> <file>`


## Networking 

- **ifconfig**:
    
    - View network interface configurations and statuses.
    - Use `ifconfig <interface>` to focus on specific interfaces.
- **lsof**:
    
    - Check port states and associated files.
    - Example: `lsof -n -i4TCP -P` to view applications bound to TCP/IPv4 addresses.
- **networksetup**:
    
    - Command-line tool to check and configure networking preferences.

| **Command**                                                         | **Description**                                                                                                                                                   |
| ------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| networksetup `-listallnetworkservices`                              | Displays a list of all the network services (device) on the computer’s hardware. This will print out the logical name of the device. (ex. Wi-Fi)                  |
| networksetup `-listnetworkserviceorder`                             | This will print out the network services running and the order in which they are queried for connection. A service at the beginning of the list is checked first. |
| networksetup `-getinfo <devicename>`                                | Get basic info about a networkservice (device) such as the IP address assigned, subnet mask, gateway, and Mac-Address.                                            |
| networksetup `-getcurrentlocation`                                  | Prints out the currently set network location.                                                                                                                    |
| networksetup `-setmanual <networkservice> <ip> <netmask> <Gateway>` | This will manually configure the ip address, network mask, and gateway for the device specified.                                                                  |

#### Tips & Tricks

- **NetworkQuality**:
    
    - Check interface network quality using `networkQuality -I <interface>`.
- **Find Wi-Fi Password**:
    
    - Use `security find-generic-password -wa <SSID>` to retrieve a Wi-Fi password.

#### Bonjour

- **Zero-configuration Networking**:
    - Enables automatic discovery of devices and services on a network.
    - Utilizes mDNSResponder protocol in macOS.
    - Ensure network security and segmentation to prevent unauthorized access.

## Tips 

To show hidden files : 

`Command + Shift + .`



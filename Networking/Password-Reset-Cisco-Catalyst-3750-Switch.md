# Password Reset on a Cisco Catalyst 3750 PoE Switch

## Overview

The default configuration for the switch allows an end user with physical access to
the switch to recover from a lost password by interrupting the boot process during poweron and by entering a new password. These recovery procedures require that you have
physical access to the switch. (Taken directly from Cisco 3750 Config File)

## Required Materials

- Laptop equipped with Cisco Terminal Emulation software (There are plenty of lightweight terminal emulation options. I personally use PuTTY terminal emulation. I used a Windows 11 laptop, but many older Windows versions and certain Linux versions are compatible as well)
- Serial port OR USB to Serial adapter (I used the latter approach)
- Cisco Rollover Cable
- Patch cables (Depending on your setup)
- Cisco Catalyst 3750 PoE Switch
- Permission from relevant network administrators to perform this procedure on the designated switch

NOTE: This procedure resets all configuration settings on the switch. Do NOT perform this procedure without proper authorization from owners or adminstrators of the gear.

## Part I – Powering Off the Switch

### Step 1.) Connect a terminal or PC with terminal-emulation software to the switch console
port. If you are recovering the password to a switch stack, connect to the console port of
the stack master. 

The setup I used was a laptop using PuTTY terminal emulation software. I plugged the USB-A end of a USB to Serial cable into my computer, and then plugged the serial end of the cable into a Cisco Rollover cable. The RJ-45 end of it plugged into a wall jack that led to a panel in the server room I used. I then plugged a standard patch cable into that port, and the other end was plugged into the console port of the Cisco Catalyst 3750

### Step 2.) Set Line Speed

The proper emulation speed for this procedure, and most other procedures involving terminal emulation and this switch is 9600 Baud. When I opened my emulation software, this was the default.




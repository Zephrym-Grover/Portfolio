# Complete Re-Install of Windows Operating System & Windows 11 Drivers

## Background

I was handed a completely blue-screened laptop by a teammate of mine in the dining hall. I asked her about what she had done to troubleshoot, and she said she had tried powering the laptop on and off repeatedly for over an hour, and still nothing had changed. 

## Materials
1 HP Omnibook x flip laptop that was stuck in the recovery screen
1 flash drive with a clean Windows 11 Operating System (Thanks, IT helpdesk)
1 C-Ethernet cable (Once again, thank you IT Helpdesk)
3 pieces of Spearmint gum (Thanks Katie from IT)

## Steps

## I - Initial Diagnostics

### Symptoms:
System booted into the Windows Recovery Environment (WinRE) rather than normally loading Windows.
Recovery environment provided options including PowerShell/Command Prompt, restart, and other recovery utilities.
### Reaction

The main error that I saw on the loading screen was that the laptop was having a boot-related error. I then went into PowerShell and ran the chkdsk utility to see if any piece of the drive was corrupted. The disk came back clean, and I suspected either I would need to reinstall the operating system or that something with the hardware was wrong, possibly the CMOS battery.
## II - Re-Installing Windows
I went to the IT Helpdesk, mainly because they had a flash drive with Windows 11 that I just didn't have at this time. I went into the UEFI, changed the boot order to boot from the flash drive, and turned off Secure Boot. I then booted into the flash drive, which had several different operating system ISO files to choose from. I chose Windows 11, because this user's needs demanded the most up-to-date version of Windows. I booted from the flash drive, and then ran an install from the flash drive to the laptop. This created a proper Windows directory as well as a Windows.old directory. I just left that one, as there wasn't anything important on it, and doing anything with it was more of a headache than it would be worth
## III - Drivers

### Symptoms
Upon recovering/reinstalling Windows, multiple hardware devices were not functioning.
Wi-Fi/network adapter was not available in Windows.
Audio/speakers were not functioning.
Other peripheral devices (microphone/camera/etc.) appeared to have driver issues.
Windows automatic driver detection was unable to locate the required drivers.
### Reaction
Because I did a clean install of Windows 11, a number of drivers were missing from the laptop. The most important of these being the network driver. No network driver, no WiFi. Because this was an AMD laptop, and I didn't know exactly which drivers were missing, I went to AMD and downloaded the Adrenalin Package. That didn't fix much, to be honest. I had Device Manager open to the exact peripherals, and the issue was, in fact, that the drivers were missing. 
I then went to HP's website, and I downloaded the drivers for the specific laptop, one by one. While this was rather tedious, it did end up solving the issue. I eventually got WiFi drivers to work, but that wasn't any good if I couldn't get onto the network.
## IV - Passwords


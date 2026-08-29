# Complete Re-Install of Windows Operating System & Windows 11 Drivers

## Background

I was handed a completely blue-screened laptop by a teammate of mine in the dining hall. I asked her about what she had done to troubleshoot, and she said she had tried powering the laptop on and off repeatedly for over an hour, and still nothing had changed. 

## Steps

## I - Diagnostics

The main error that I saw on the loading screen was that the laptop was having a boot-related error. I then went into PowerShell and ran the chkdsk utility to see if any piece of the drive was corrupted. The disk came back clean, and I suspected either I would need to reinstall the operating system or that something with the hardware was wrong, possibly the CMOS battery.
## II - Re-Installing Windows
I went to the IT Helpdesk, mainly because they had a flash drive with Windows 11 that I just didn't have at this time. I went into the UEFI, changed the boot order to boot from the flash drive, and turned off Secure Boot

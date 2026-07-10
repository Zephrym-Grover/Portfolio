# Deploying DHCP Services via Layer 3 Switch

## Required Materials
- Laptop equipped with Cisco Terminal Emulation software (There are plenty of lightweight terminal emulation options. I personally use PuTTY terminal emulation. I used a Windows 11 laptop, but many older Windows versions and certain Linux versions are compatible as well)
- Test laptop to verify IP assignment via DHCP
- Serial port OR USB to Serial adapter (I used the latter approach)
- Cisco Rollover Cable
- Patch cables (At least 1 is necessary to run from the test laptop to the layer 3 switch. More may be required depending on your setup)
- Cisco Catalyst 3750 PoE Switch
- Permission from relevant network administrators to perform this procedure on the designated switch
- VLANs to deploy DHCP services on set up on the switch (Essentially any configuration of VLANs is acceptable, but this demonstration will use the "Basic VLAN's" setup in the interest of simplicity)
### Step 1.) Verify Setup
show vlan brief

<img width="590" height="81" alt="image" src="https://github.com/user-attachments/assets/a37b8286-1da8-4bee-87b5-3342f9a4b13f" />

Image: The VLAN setup used for this lab, which functions as follows:

<img width="776" height="179" alt="image" src="https://github.com/user-attachments/assets/2bc6ec93-eeea-4aff-81e9-2ca3267a7098" />

- VLAN 3 utilizes ports 3, 4, and 5
- 
  <img width="640" height="125" alt="image" src="https://github.com/user-attachments/assets/73176118-e1c2-46d7-a859-b5a113abd642" />
  
- VLAN 6 utilizes ports 6, 7, and 8
- 
  <img width="659" height="126" alt="image" src="https://github.com/user-attachments/assets/3d2ee01a-56ce-4d86-86ff-273d6272d69e" />
  
- VLAN 9 utilizes ports 9, 10, and 11
  
### Step 2.) 
Type the following commands into the console of the switch
- Switch> enable
- Switch# conf t
- Switch# ip routing

#### VLAN "3"

  

  

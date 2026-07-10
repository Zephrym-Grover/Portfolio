# Spanning Tree Protocol Configuration

## (STP) is a protocol designed to provide a loop free logical topology for networks, and to prevent broadcast storms like those demonstrated here

# Materials Required:
- Laptop equipped with Cisco Terminal Emulation software (There are plenty of lightweight terminal emulation options. I personally use PuTTY terminal emulation. I used a Windows 11 laptop, but many older Windows versions and certain Linux versions are compatible as well)
- Laptop equipped with Wireshark (This may be the same laptop as the laptop with the terminal emulator, but I found it easier to use a second laptop dedicated to running Wireshark in this lab)
- Serial port OR USB to Serial adapter (I used the latter approach)
- Cisco Rollover Cable
- Patch cables (Minimum of three is required for the redundant links between the switches and the Wireshark monitoring. My setup has a patch panel system that requires two extra cables, your setup may vary)
- Two Cisco Catalyst 3750 PoE Switches
- Permission from relevant network administrators to perform this procedure on the designated switch
### Step 1.) Configuring LAN with redundant links: Hardware side
•	Plug USB to Serial cable into computer
•	Connect that Serial connector to the Serial connector on Cisco Rollover cable
•	Plug Cisco Rollover cable into wall jack # (Insert # here)
•	Plug ethernet cable into corresponding port on patch panel
•	Connect that cable to serial port of a switch
•	Find a second valid switch
•	Connect second Ethernet cable between SW1-FA1/0/35 – SW2-Fa1/0/35
•	Connect third Ethernet cable between SW1-FA1/0/36 to SW2-FA1/0/36

- Type into switch 1 <code style="color : orangered">codeword Ronald McDonald</code>
# Lessons Learned

This experiment was completed through a combination of revising, checking problems in my documentation, and thinking on my feet. Using Claude AI (running Opus 4.5) I was led to believe that I needed to configure the redundant link connections, when they were automatic through transparent switching. This is a lesson that AI is not always reliable, and not always capable of understanding the problem at hand, even when provided with screenshots. It is a tool, but it is often incapable of "bringing home the bacon".
\
	I figured this out upon looking at my documentation in class. I borrowed a friend's computer to run Wireshark so that I could have my computer running PuTTY terminal emulation software. I have since acquired another computer for running certain lightweight applications such as PuTTY. If I were to re-run this experiment now, I would use my secondary laptop to run PuTTY, with my primary laptop running Wireshark.
	From here, this experiment went basically as I had planned it in the steps above. Electing a new root bridge was easy. I simply changed the other one to 4096. The switches compared the 4096 to the 32768 that was the default, and the election was over quickly, with the second switch taking over as the root switch.
	The broadcast storm didn’t go exactly as planned. I turned off SPAN on one of the ports when there was no SPAN enabled on either. This kept alternating between both of the switches, creating the broadcast storm before I was prepared for it. WireShark captured this immediately, but my PuTTY was too lagged out to stop it through there.
	Instead, what I had to do was pull both redundant links to stop the broadcast storm. I pulled one at first, and Brian told me that WireShark was still lighting up. I pulled both of them, and then took a moment to get screenshots and figure out exactly what was going on there.
	If I could sum up this lab very quickly, it would be “No plan survives first engagement with the enemy.” As much as the planning I did helped me navigate the challenges of this lab, it still required staying on my toes, instinct, perseverance, and grit to sort out the challenges of Spanning Tree Protocol.
	

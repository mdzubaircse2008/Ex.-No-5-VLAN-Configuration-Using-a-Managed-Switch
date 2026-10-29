## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date:28/10/2026
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/50ee1ebf-c839-45c3-a1e0-47dd8a155e62" />

________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
•	VLAN configuration on switch<br>
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/80366100-6348-420b-8adc-6a6ae75f9852" />

•	PC IP settings<br>
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/d486a050-ff57-451a-a567-85d20647a01d" />
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/df454ba1-9f12-41b1-a8fd-4f68b142fa47" />
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/e7b40a82-10a2-4938-b16e-b9295ce14254" />
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/c0f79a40-b06e-4fcf-b391-4d46a0fe26e4" />



•	Successful ping between PCs in the same VLAN<br>
<img width="672" height="246" alt="image" src="https://github.com/user-attachments/assets/0f1e66dc-3dc0-4b79-ada4-07b04cc583c3" />
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/e821e251-df50-463d-af9c-4a51eb9e00d1" />

•	Failed ping between PCs in different VLANs<br>
<img width="695" height="207" alt="image" src="https://github.com/user-attachments/assets/09e0e3a7-3288-4eec-8ac8-5367ece63051" />
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/5019785c-99f5-43a0-9b03-316c2d4aa0c9" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.


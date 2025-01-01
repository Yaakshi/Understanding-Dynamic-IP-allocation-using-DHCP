## 1. Perform the following steps to capture the DHCP traffic.

### _a. Begin by opening the Windows Command Prompt application. Type “ipconfig /release”._

![image](https://github.com/user-attachments/assets/fc06f518-cdd8-47e5-82be-2b88f51957d2)

### _b. Start up the Wireshark packet sniffer._

### _c. Now go back to the Windows Command Prompt and enter “ipconfig /renew”._

![image](https://github.com/user-attachments/assets/51a7439f-0d02-49ce-afca-95ca0e9d4703)

### _d. Wait until the “ipconfig /renew” has terminated. Then enter the same command “ipconfig /renew” again._

![image](https://github.com/user-attachments/assets/554af374-cb24-417d-8adb-2283f8107e21)

### _e. When the second “ipconfig /renew” terminates, enter the command “ipconfig/release” to release the previously-allocated IP address to your computer._

![image](https://github.com/user-attachments/assets/6646e8c6-ee20-4a1f-b327-f4d8e4422445)

### _f. Finally, enter “ipconfig /renew” to again be allocated an IP address for your computer._

![image](https://github.com/user-attachments/assets/ec2e6e9d-b8c7-4987-ae01-4d5ebebedec3)

### _g. Stop Wireshark packet capture._

![image](https://github.com/user-attachments/assets/c6109e24-9c9e-4fd4-ac1c-b2cef363c159)

## 2. Open the captured traffic file and given pcap file “dhcp” in Wireshark to answer the following questions.

### _a. Are DHCP messages sent over UDP or TCP?_

![image](https://github.com/user-attachments/assets/3f8efda5-ff01-4f54-8328-7c8a22539c9f)
The DHCP messages are sent over UDP.

### _b. Draw a timing datagram illustrating the sequence of the first four-packet Discover/Offer/Request/ACK DHCP exchange between the client and server. For each packet, indicated the source and destination port numbers._

![image](https://github.com/user-attachments/assets/9d8220d7-a941-482c-9afa-4f0fcfed4b3c)

Select all the first four DHCP packets → Go to Statistics tab in the toolbar → Click Flow Graph

![image](https://github.com/user-attachments/assets/ef6afb69-85c1-4ddd-bd76-537e002ad9ec)
![image](https://github.com/user-attachments/assets/ecd9c652-ac73-411f-8828-00e2e34c9108)

### _c. What is the link-layer (e.g., Ethernet) address of your host?_

![image](https://github.com/user-attachments/assets/551a8776-6598-40fd-8c7a-133d745191f8)
The Ethernet address of the host is 00:08:74:4f:36:23

### _d. What values in the DHCP discover message differentiate this message from the DHCP request message?_

![image](https://github.com/user-attachments/assets/7579a0fa-1e62-429a-af4c-517a6464f4cd)
![image](https://github.com/user-attachments/assets/046e658a-ab35-4005-812b-d578857241f6)
The DHCP Message Type field differentiates the discover and request packets.

### _e. What is the value of the Transaction-ID in each of the first four (Discover/Offer/Request/ACK) DHCP messages? What are the values of the Transaction-ID in the second set (Request/ACK) set of DHCP messages? What is the purpose of the Transaction-ID field?_

![image](https://github.com/user-attachments/assets/9472ec82-40b8-48c6-817f-6d22a4210215)
- The Transaction ID of the first set of DHCP messages is 0x3e5e0ce3.
- The Transaction ID of the second set of DHCP messages is 0x3a5df7d9.

If there are two computers entering into the same network, then they need to be assigned
IP address, default gateways, DNS servers, etc. automatically by the DHCP server. These multiple DHCP clients need to communicate with the single DHCP server on the network simultaneously. Transaction ID helps to distinguish these two different sets of DHCP messages. It avoids the mixing of same IP addresses being allocated to two different computers on the network.

### _f. A host uses DHCP to obtain an IP address, among other things. But a host’s IP address is not confirmed until the end of the four-message exchange! If the IP address is not set until the end of the four-message exchange, then what values are used in the IP datagrams in the four-message exchange? For each of the four DHCP messages (Discover/Offer/Request/ACK DHCP), indicate the source and destination IP addresses that are carried in the encapsulating IP datagram._

![image](https://github.com/user-attachments/assets/7860a5b5-69e3-4eeb-87af-e98dae3a9c1d)
![image](https://github.com/user-attachments/assets/b25f48a8-ec44-45b3-85f8-9b4ce3e71ffd)

### _g. What is the IP address of your DHCP server?_

![image](https://github.com/user-attachments/assets/8fa83f97-43b8-45f4-9195-5c269d930678)
The DHCP Offer message is sent by the DHCP server. The IP address of DHCP server is 192.168.1.1

### _h. What IP address is the DHCP server offering to your host in the DHCP Offer message? Indicate which DHCP message contains the offered DHCP address._

![image](https://github.com/user-attachments/assets/d99e40da-1c22-405d-92d7-10a9f179fba6)
The IP address offered to the host by the DHCP server is 192.168.1.101 It is obtained from the Your (client) IP address field.

### _i. In the example screenshot in this assignment, there is no relay agent between the host and the DHCP server. What values in the trace indicate the absence of a relay agent? Is there a relay agent in your experiment? If so, what is the IP address of the agent?_

![image](https://github.com/user-attachments/assets/a7457ed0-54f9-4296-9cd8-1227320707e0)
All the DHCP messages contain a field called Relay agent IP address. The value is 0.0.0.0. This means there is no such relay agent in between.

![image](https://github.com/user-attachments/assets/8b3d8f62-392b-4362-ae40-6891330399a3)

In my experiment also, there is no relay agent. The Relay agent IP address field is 0.0.0.0.

### _j. Explain the purpose of the router and subnet mask lines in the DHCP offer message._

![image](https://github.com/user-attachments/assets/46adb46f-e7e0-4c2c-b85c-84ec8dc476a0)
- The subnet mask field denotes which range of addresses that the client belongs to. This configuration tells the client that it can directly communicate with IP addresses from 192.168.1.0 to 192.168.1.255.
- The router field denotes the default gateway for the client. It is used to connect to other networks and Internet.
- The DHCP Offer message assigns these addresses to the new client added to the network.

### _k. In the DHCP trace file, the DHCP server offers a specific IP address to the client. In the client’s response to the first server OFFER message, does the client accept this IP address? Where in the client’s RESPONSE is the client’s requested address?_

![image](https://github.com/user-attachments/assets/b4a78224-328c-4b3f-8d28-bd827b4467c0)
In the DHCP Offer message, the server offers the IP address 192.168.1.101 to the new client. It accepts the allocated IP address.

![image](https://github.com/user-attachments/assets/29cd2a92-3267-4978-91c4-5fead0a9521c)
In the following DHCP Request message, the client requests for the same IP address 192.168.1.101. It can be viewed in the Requested IP address field.

### _l. Explain the purpose of the lease time. How long is the lease time in your experiment?_

![image](https://github.com/user-attachments/assets/4e16bf89-e10d-4de3-a4aa-844d00310de2)
In the DHCP ACK message, we can find the IP Address Lease Time field. It determines how long the IP address can be used by that client. After the lease time is crossed, new IP address need to be assigned to that client. The lease time for this experiment is 86400 seconds or 1 day.

### _m. What is the purpose of the DHCP release message? Does the DHCP server issue an acknowledgment of receipt of the client’s DHCP request? What would happen if the client’s DHCP release message is lost?_

![image](https://github.com/user-attachments/assets/4be1379f-b965-43c1-9913-ee306c7cdb84)
DHCP Release message will release the IP address of the host back to the DHCP server. The DHCP server does not send acknowledgement for this DHCP release message.

If the client’s DHCP release message is lost, then the client would have released its IP address but the DHCP server would not have received that address back. So, until the lease time of that client expires, the released IP address will not be assigned to any other clients requesting for an IP address.

### _n. Clear the DHCP filter from your Wireshark window. Were any ARP packets sent or received during the DHCP packet-exchange period? If so, explain the purpose of those ARP packets._

![image](https://github.com/user-attachments/assets/d233a240-f179-4f8b-9a9e-6833c945085c)

Yes, several ARP packets can be seen during the DHCP packet exchange period. After the DHCP Discover message, there is an ARP packet. It is a broadcast message sent by DHCP server that checks if 192.168.1.101 is assigned already. 

After the DHCP packet exchange period, the client which was assigned the new IP address 192.168.1.101 sends a broadcast message announcing about its IP address to other clients on the network.
















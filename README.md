<h1>Wireshark Lab</h1>

<h2>Description</h2>
Project consists of simple yet fundamental Wireshark usages/actions. These include the installation of Wireshark on Linux, capturing and saving packets on a detected network, using display filters to detect a certain IP address in a capture, and using conditional filters to locate certain packets in a capture
<br />


<h2>Utilities Used</h2>

- <b>Wireshark</b> 
- <b>Linux</b>

<h2>Environments Used </h2>

- <b>Coursera Cloud Workspace</b> 

<h2>Program walk-through:</h2>

<h3>TASK 1 - Install Wireshark and set up for non-super users belonging to the Wireshark group:</h3>

<p align="center">
Install wireshark - sudo apt install wireshark <br/>
<img src= "https://i.imgur.com/drB6zzq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add user (“rhyme” in this case) to the Wireshark group for packet capture abilities - sudo usermod -aG Wireshark $USER  <br/>
<img src="https://i.imgur.com/aQLMqcq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 2 - Use Wireshark to capture packets on an ethernet port and save the captured data to a file:</h3>

<p align="center">
On the Wireshark application, make sure that “Wired” is checked off as the interfaces shown since the goal is to capture packets on an ethernet port. Also note that “ens5” is selected because it is an ethernet adapter. After that is selected, click on the blue shark fin in the top left corner to start capturing packets. <br/>
<img src= "https://i.imgur.com/DPoO3CO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click the stop button right to the right of the shark fin to pause the packet capture.  <br/>
<img src="https://i.imgur.com/Ulq2X6C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Save the packet capture by clicking on the circled icon on the top of the screen.  <br/>
<img src="https://i.imgur.com/Dc3eeo4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In order to open a packet capture file, click on the circled icon on the top of the screen.  <br/>
<img src="https://i.imgur.com/u7wHUVQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 3 - Use a Wireshark display to detect HTTPS packets:</h3>

<p align="center">
Utilizing the instructions from TASK 2, I started a packet capture, loaded duckduckgo.com, then stopped the capture. Afterwards I saved this packet capture. <br/>
<br />
<br />
In order to filter the display of the packet capture to show only HTTPS packets, type “tcp.port == 443” in the display filter and then on the right side click the circled enter button.  <br/>
<img src="https://i.imgur.com/N8PFF0j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Note: The “Client Hello” (circled) is the client initiating a TLS handshake with the server.  <br/>
<img src="https://i.imgur.com/ON7txFo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 4 - Start a Wireshark capture, visit a web page and detect its IP address using a display filter:</h3>

<p align="center">
Utilizing the instructions from TASK 2, I started a packet capture, loaded google.com, then stopped the capture. Afterwards I saved this packet capture. <br/>
<br />
<br />
Using the display filter (ask shown in TASK 3), I filtered the packet capture to only display HTTPS packets. <br/>
<br />
<br />
The IP address of google.com is 172.253.115.104 as is shown in this screenshot. Notice the “Client Hello” circled. <br/>
<img src="https://i.imgur.com/EzlnEgB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Note: To see only TLS handshakes and analyze what website was visited within a packet list, type “tls.handshake.type == 1” into the display filter. <br/>
<img src="https://i.imgur.com/82GR7k9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Note: To only display information about a specific IP address, type in “ip.addr == *IP Address* into the display filter. <br/>
<img src="https://i.imgur.com/5S4JTLW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 5 - Start a capture, visit multiple websites, stop the capture, and eliminate packets from one IP address from the display:</h3>

<p align="center">
Utilizing the instructions from TASK 2, I started a packet capture, loaded google.com and duckduckgo.com (separately) then stopped the capture. Afterwards I saved this packet capture. <br/>
<br />
<br />
Now, to view all of the packets containing Client Hello TLS handshakes I inputed “tls.handshake.type == 1” (as performed in TASK 4). <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now, in this project, the first Client Hello TLS handshake that came up was referring to google.com (172.253.63.105). In order to use the display filter in such a way that 172.253.63.105 will not be displayed but HTTPS traffic in general will be displayed, the following was inputed into the display filter: !(ip.addr == 172.253.63.105) and (tcp.port == 443) *note that the “!” in the beginning means “not”. *also note that parentheses help with order of execution. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

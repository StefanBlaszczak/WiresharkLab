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
<img width="771" alt="Screen Shot 2023-11-14 at 12 33 03 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/ee0c2d91-0ccd-4d69-ae5a-956484438aa4">
<br />
<br />
Add user (“rhyme” in this case) to the Wireshark group for packet capture abilities - sudo usermod -aG Wireshark $USER  <br/>
<img width="746" alt="Screen Shot 2023-11-14 at 12 39 17 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/b374812b-493b-4662-a9d6-3fe9bdd13ea8">
<br />
<br />

<h3>TASK 2 - Use Wireshark to capture packets on an ethernet port and save the captured data to a file:</h3>

<p align="center">
On the Wireshark application, make sure that “Wired” is checked off as the interfaces shown since the goal is to capture packets on an ethernet port. Also note that “ens5” is selected because it is an ethernet adapter. After that is selected, click on the blue shark fin in the top left corner to start capturing packets. <br/>
<img width="993" alt="Screen Shot 2023-11-14 at 12 47 50 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/a0fdb2c5-0d44-4d0d-b383-e106dfff8a01">
<br />
<br />
Click the stop button right to the right of the shark fin to pause the packet capture.  <br/>
<img width="678" alt="Screen Shot 2023-11-14 at 1 07 42 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/b767edf2-51a9-41f6-808d-6efc510ceecb">
<br />
<br />
Save the packet capture by clicking on the circled icon on the top of the screen.  <br/>
<img width="904" alt="Screen Shot 2023-11-14 at 1 10 53 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/5de608f7-2344-461f-bb27-b5f634243c64">
<br />
<br />
In order to open a packet capture file, click on the circled icon on the top of the screen.  <br/>
<img width="859" alt="Screen Shot 2023-11-14 at 1 13 49 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/17ada402-27ef-4032-aa53-02ee97f815f7">
<br />
<br />

<h3>TASK 3 - Use a Wireshark display to detect HTTPS packets:</h3>

<p align="center">
Utilizing the instructions from TASK 2, I started a packet capture, loaded duckduckgo.com, then stopped the capture. Afterwards I saved this packet capture. <br/>
<br />
<br />
In order to filter the display of the packet capture to show only HTTPS packets, type “tcp.port == 443” in the display filter and then on the right side click the circled enter button.  <br/>
<img width="816" alt="Screen Shot 2023-11-14 at 1 30 10 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/32819eb0-078e-48dd-ac51-f8b2f24250bc">
<br />
<br />
Note: The “Client Hello” (circled) is the client initiating a TLS handshake with the server.  <br/>
<img width="976" alt="Screen Shot 2023-11-14 at 1 37 54 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/97916c1e-cf32-4f07-ada4-3393e4c9b925">
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
<img width="850" alt="Screen Shot 2023-11-14 at 2 12 28 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/cc5b71d4-2dc6-406b-a3cb-a89df29f2ddd">
<br />
<br />
Note: To see only TLS handshakes and analyze what website was visited within a packet list, type “tls.handshake.type == 1” into the display filter. <br/>
<img width="693" alt="Screen Shot 2023-11-14 at 3 16 23 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/d305c8f6-6547-436b-93a1-e4183d85bfda">
<br />
<br />
Note: To only display information about a specific IP address, type in “ip.addr == *IP Address* into the display filter. <br/>
<img width="691" alt="Screen Shot 2023-11-14 at 3 19 02 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/5c3a687f-1b8c-4133-bbb3-ad803ebd6d9c">
<br />
<br />

<h3>TASK 5 - Start a capture, visit multiple websites, stop the capture, and eliminate packets from one IP address from the display:</h3>

<p align="center">
Utilizing the instructions from TASK 2, I started a packet capture, loaded google.com and duckduckgo.com (separately) then stopped the capture. Afterwards I saved this packet capture. <br/>
<br />
<br />
Now, to view all of the packets containing Client Hello TLS handshakes I inputed “tls.handshake.type == 1” (as performed in TASK 4). <br/>
<img width="633" alt="Screen Shot 2023-11-14 at 4 01 41 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/5b7144a0-b804-4eb0-9c82-a50660adc5b6">
<br />
<br />
Now, in this project, the first Client Hello TLS handshake that came up was referring to google.com (172.253.63.105). In order to use the display filter in such a way that 172.253.63.105 will not be displayed but HTTPS traffic in general will be displayed, the following was inputed into the display filter: !(ip.addr == 172.253.63.105) and (tcp.port == 443) *note that the “!” in the beginning means “not”. *also note that parentheses help with order of execution. <br/>
<img width="634" alt="Screen Shot 2023-11-14 at 4 11 24 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/5d391a55-3c53-4e43-acc8-79b3b5dcd875">
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

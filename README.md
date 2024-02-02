<h1> HawkEye </h1>

<h2>Description</h2>
An accountant at your organization received an email regarding an invoice with a download link. Suspicious network traffic was observed shortly after opening the email. As a SOC analyst, investigate the network trace and analyze exfiltration attempts.
<br />


<h2>Tools Used</h2>

- <b> WireShark </b> 
- <b> Base64 Decoder </b>
- <b> Virus Total </b>
- <b> IP Geolocation (https://www.iplocation.net) </b>
- <b> CyberDefenders </b>


<h2>Environments Used </h2>

- <b>Orcale Virtual Box </b>
- <b>Windows 10</b> 

<h2>Walk-through</h2>

<p align="left">

  <h3>Question #1</h3>
How many packets does the capture have? <br/>
<br/>
<img src="https://i.imgur.com/FolXXUK.png" height="80%" width="80%" alt="question 1"/>
<br/> 
<br/>
If We look at the bottom right in Wireshark we can see the Tool Packets Captured 
<br/>
<br/>
<img src="https://i.imgur.com/BqXJIp4.png" height="80%" width="80%" alt="Answer 1"/>

<br />
<br />

<h3>Question #2</h3>
At what time was the first packet captured? <br/>
<br/>
<img src="https://i.imgur.com/gY1540F.png" height="80%" width="80%" alt="Question 2"/>
<br/>
We will need to navigate to the first packet in the capture, and then pull up the date from the "Frame" tab
<br/>
<br/>
<img src="https://i.imgur.com/eTpZ5Lg.png" height="80%" width="80%" alt="Answer 2"/>
<br />
<br />

<h3>Question #3</h3>
What is the duration of the capture? <br/>
<br/>
<img src="https://i.imgur.com/GM2i1Qu.png" height="80%" width="80%" alt="Question 3"/>
<br />
<br />
We Can get this information from the packet statistics. We get that using Statistics > Capture File Properties. We can get that  <br/>
<br/>
<img src="https://i.imgur.com/ZVNsSUx.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #4</h3>
What is the most active computer at the link level?  <br/>
<br/>
<img src="https://i.imgur.com/y3btvJA.png" height="80%" width="80%" alt="Question 4"/>
<br />
<br />
To obtain the most active computer, we can retrieve this information by examining the packet statistics within the PCAP file, accessible through the "Statistics" menu, specifically under "IPv4 Statistics" and "All Addresses." where we can see the computer with the most packets. <br/>
<br/>
<img src="https://i.imgur.com/Ohsar85.png" height="80%" width="80%" alt="Answer 4"/>
<img src="https://i.imgur.com/xTNG77a.png" height="80%" width="80%" alt="Answer 4"/>
<br/>
<br/>

<h3>Question #5</h3>
Manufacturer of the NIC of the most active system at the link level? <br/>
<br/>
<img src="https://i.imgur.com/yJtXyu2.png" height="80%" width="80%" alt="Question 4"/>
<br />
<br />
From the identical log, it is evident that WireShark successfully resolved the MAC address to HewlettP_1c:47:ae. After a quick Google search, we can see the company is Hewlett-Packard   <br/>
<br/>
<img src="https://i.imgur.com/8WUaYFV.png" height="80%" width="80%" alt="Answer 4"/>
<img src="https://i.imgur.com/USRCbKo.png" height="80%" width="80%" alt="Answer 4"/>
<img src="https://i.imgur.com/1wq68VW.png" height="80%" width="80%" alt="Answer 4"/>
<br/>
<br/>

<h3>Question #6</h3>
Where is the headquarters of the company that manufactured the NIC of the most active computer at the link level? <br/>
<br/>
<img src="https://i.imgur.com/CGTiddo.png" height="80%" width="80%" alt="Question 3"/>
In the previous Google Search, we can see the answer listed <br/>
<br/>
<br/>
<br/>

<h3>Question #7</h3>
The organization works with private addressing and netmask /24. How many computers in the organization are involved in the capture? <br/>
<br/>
<img src="https://i.imgur.com/16t1a4O.png" height="80%" width="80%" alt="Question 3"/>
<br />
<br />
We can observe all the IPv4 addresses participating in the network capture by navigating to Statistics > IPv4 Statistics > All Addresses. 
<br/> There are four addresses in the 10.4.10.x range. However, since one is 10.4.10.255, designated as a broadcast address unsuitable for assignment to any specific computer, we only  have three assignable addresses.  <br/>
<br/>
<img src="https://i.imgur.com/SRNxHfr.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #8</h3>
What is the name of the most active computer at the network level? <br/>
<br/>
<img src="https://i.imgur.com/lX56HkV.png" height="80%" width="80%" alt="Question 3"/>
<br />

With Brim, we can see the presence of DHCP traffic in this capture. 
<br/> Upon searching for DHCP packets in Wireshark, we can locate a DHCPINFORM packet. After inspecting the packet, we can ascertain that the client included the Host Name option, allowing us to extract the hostname of the computer.  <br/>
<br/>
<img src="https://i.imgur.com/lX56HkV.png" height="80%" width="80%" alt="Answer 3"/>
<img src="https://i.imgur.com/BC26QDR.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #9</h3>
What is the IP of the organization's DNS server?<br/>
<br/>
<img src="https://i.imgur.com/JZA0gFn.png" height="80%" width="80%" alt="Question 3"/>
<br />

With Brim, we can see the presence of DHCP traffic in this capture. 
<br/> Upon searching for DHCP packets in Wireshark, we can locate a DHCPINFORM packet. After inspecting the packet, we can ascertain that the client included the Host Name option, allowing us to extract the hostname of the computer.  <br/>
<br/>
<img src="https://i.imgur.com/lX56HkV.png" height="80%" width="80%" alt="Answer 3"/>
<img src="https://i.imgur.com/BC26QDR.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #10</h3>
What domain is the victim asking about in packet 204? <br/>
<br/>
<img src="https://i.imgur.com/ZYV2Iuv.png" height="80%" width="80%" alt="Question 3"/>
<br />
<br />
We can go ahead and pull up packet 204 and locate the DNS Query field, where we can find the domain <br/>
<br/>
<img src="https://i.imgur.com/bhYGM9C.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #11 </h3>
What is the IP of the domain in the previous question? <br/>
<br/>
<img src="https://i.imgur.com/RXUBxrk.png" height="80%" width="80%" alt="Question 3"/>
<br />
<br />
If We Check the details of the previous packet, we can see that there is a destination IP address <br/>
<br/>
<img src="https://i.imgur.com/pFrOrpY.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #12 </h3>
 Indicate the country to which the IP in the previous section belongs. <br/>
<br/>
<img src="https://i.imgur.com/6LLHBiS.png" height="80%" width="80%" alt="Question 3"/>
<br />
<br />
We can use IP Geolocation to get the location of the IP<br/>
<br/>
<img src="https://i.imgur.com/9kbhryd.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #13 </h3>
Q13: What operating system does the victim’s computer run? <br/>
<br/>
<img src="https://i.imgur.com/6LLHBiS.png" height="80%" width="80%" alt="Question 3"/>
<br />
By examining the HTTP User-Agent of the computer, we can initiate the operating system on the system. <br/>
Among several HTTP logs in this capture, only the one originating from the browser at proforma-invoices.com appears relevant. <br/>
Consequently, we can determine the operating system running on the machine based on the information in the mentioned header. It appears that our target is using Windows NT 6.1.<br/>
<br/>

<h3>Question #14 </h3>
What is the name of the malicious file downloaded by the accountant? <br/>
<br/>
<img src="https://i.imgur.com/CkZbkwU.png" height="80%" width="80%" alt="Question 3"/>
<br />
<br />
We will need to extract the information needed, Hence, File > Export Objects > HTTP to get the objects. <br/>
<br/>
<img src="https://i.imgur.com/qU4Fatx.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #15 </h3>
What is the md5 hash of the downloaded file? <br/>
<br/>
<img src="https://i.imgur.com/gd1ViW3.png" height="80%" width="80%" alt="Question 3"/>
<br />
<br />
Once we extract the Http above, we can use Virus total to get the MD5 Hash <br/>
<br/>
<img src="https://i.imgur.com/XWwyevn.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #16 </h3>
What software runs the webserver that hosts the malware?? <br/>
<br/>
<img src="https://i.imgur.com/XB6E11k.png" height="80%" width="80%" alt="Question 3"/>
<br />
Choosing the malicious file from the HTTP object list will simultaneously highlight the packet indicating the commencement of the HTTP stream. <br/>
Utilizing the Follow > HTTP Stream option allows us to capture the entire stream. <br/>
Analyzing the followed HTTP headers data enables us to identify the web server operating on the server. <br/>
<br/>
<img src="https://i.imgur.com/O4KwKzN.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>

<h3>Question #17 </h3>
What is the md5 hash of the downloaded file? <br/>
<br/>
<img src="https://i.imgur.com/gd1ViW3.png" height="80%" width="80%" alt="Question 3"/>
<br />
Examining the HTTP object list reveals communication with another site named bot[.]whatismyipaddress[.]com, a recognized service for obtaining a computer's Public IP Address. <br/>
Choosing the HTTP object record will also highlight the packet signifying the initiation of the HTTP stream. By utilizing Follow > HTTP Stream, <br/> 
we can capture the complete stream. Analyzing the following HTTP headers data lets us retrieve the public IP address. <br/>
<br/>
<img src="https://i.imgur.com/U7t50AZ.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/>


<h3>Question #18 </h3>
What is the md5 hash of the downloaded file? <br/>
<br/>
<img src="https://i.imgur.com/gd1ViW3.png" height="80%" width="80%" alt="Question 3"/>
<br />
Examining the HTTP object list reveals communication with another site named bot[.]whatismyipaddress[.]com, a recognized service for obtaining a computer's Public IP Address. <br/>
Choosing the HTTP object record will also highlight the packet signifying the initiation of the HTTP stream. By utilizing Follow > HTTP Stream, <br/> 
we can capture the complete stream. Analyzing the following HTTP headers data lets us retrieve the public IP address. <br/>
<br/>
<img src="https://i.imgur.com/U7t50AZ.png" height="80%" width="80%" alt="Answer 3"/>
<br/>
<br/



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>



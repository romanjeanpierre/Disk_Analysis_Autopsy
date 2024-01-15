<h1>Disk Image Analysis with Autopsy</h1>

<h2>Brief Description</h2>
<p>This project involves conducting a disk analysis using Autopsy, a digital forensics tool. The goal is to answer specific questions related to an ongoing investigation by examining the disk image named "Craig Tucker.EO1" using Autopsy.</p>

<h2>Project Walk-Through</h2>
<br/>
<h3>To start a Disk Image analysis with Autopsy </h3>
Select Host > Disk Image > Data source path > Select modules to ingest.
<br/>
<br/>
<img src="https://imgur.com/Zwvit9J.png" height="80%" width="80%" alt="Project Overview Image">
<img src="https://imgur.com/esKcmJu.png" height="80%" width="80%" alt="Project Overview Image">
<img src="https://imgur.com/cz3T0PS.png" height="80%" width="80%" alt="Project Overview Image">
<img src="https://imgur.com/e547pmR.png" height="80%" width="80%" alt="Project Overview Image">
<br/>
<br/>
Command => <code>python vol.py -f /home/ubuntu/Desktop/Volatility\ Exercise/memdump1.mem image info</code>
<br/>
<br/>
<img src="https://imgur.com/C3Qo3mE.png" height="80%" width="80%" alt="Project Overview Image">
<h3> Results:</h3>
<oL>
<li>Suggested Profile: Win7SP1x64</li> 
<li>KDGB address value: 0xf80002bfa0a0L</li>
</oL>
<br/>
<h3>Find the list of processes</h3>
<br/>
<p> Command => <code>python vol.py -f /home/ubuntu/Desktop/Volatility\ Exercise/memdump1.mem --profile=Win7SP1x64 pslist</code></p>
<br/>
<img src="https://imgur.com/T07ndUW.png" height="80%" width="80%" alt="FTK Imager Memory Capture">

<h3>Display processes in Parent and Child Representation</h3>
<br/>
Use the Parent-child relationship to detect unusual processes.
<br/>
<p> Command => <code>python vol.py -f /home/ubuntu/Desktop/Volatility\ Exercise/memdump1.mem --profile=Win7SP1x64 pstree </code></p>
<br/>
<img src="https://imgur.com/td5uSbc.png" height="80%" width="80%">

<img src="https://imgur.com/UZnmFcg.png" height="80%" width="80%">
<br/>
svchost.exe process creates a cmd.exe child process, where the ping command is used, because we can see the ping.exe process being this will be considered unusual activity. 
<br/>
<br/>
<h3> Filtering processes with sum count </h3>
<p>Finding how many processes with the name "svchost.exe" were running in the system</p>
Command => <code> python vol.py -f /home/ubuntu/Desktop/Volatility\ Exercise/memdump1.mem --profile=Win7SP1x64 pslist | grep “svchost.exe” | wc -l </code>
<br/>
<br/>
<img src="https://imgur.com/ZOcBykp.png" height="80%" width="80%" alt="PID Results Output">

<h3> Finding command lines with associated PIDs </h3>
Command => <code> python vol.py -f /home/ubuntu/Desktop/Volatility\ Exercise/memdump1.mem --profile=Win7SP1x64 cmdline -p 2352 </code>
<br/>
<br/>
<img src="https://imgur.com/LsRVX6r.png" height="80%" width="80%" alt="ProcDump Memory Dump">
<h3>Filtering Malicious Network Connections</h3>
A machine suspected to be infected by some type of malware. We need to identify the harmful IP related to the malware.
<br/>
Command => <code>python vol.py -f /home/ubuntu/Desktop/Volatility\ Exercise/memdump2.mem --profile=Win7SP1x64 netscan</code>
<br/>
<br/>
<img src="https://imgur.com/cVl6nkP.png" height="80%" width="80%" alt="FTK Imager Disk Image Creation">
<br/>
WINWORD.EXE (Microsoft Word) was communicating to the Foreign IP 65[.]111[.]166[.]58 on port 80 (HTTP). Based on knowledge of phishing attacks, this is very likely to be a malicious Word document macro that is downloading malicious software from the mentioned IP address over HTTP.
<br/>
<br/>
<h3> Dump specific process and calculate MD5 Hash</h3>
Filter process ID 2940 information and output to a directory path
<br/>
Command => <code>python vol.py -f /home/ubuntu/Desktop/Volatility\ Exercise/memdump2.mem --profile=Win7SP1x64 procdump -p 2940 -D /home/ubuntu/Desktop</code>
<br/>
<img src="https://imgur.com/kXUvhpb.png" height="80%" width="80%" alt="Drive Input Selection">
<br/>
Calculate MD5 Hash
<img src="https://imgur.com/tINj1d6.png" height="80%" width="80%">
<br/>
<br/>

<h2>Conclusion</h2>
<p>In conclusion, by leveraging Volatility we can successfully identify and analyze potential security incidents, malware infections, and suspicious activities within memory dump data.</p>


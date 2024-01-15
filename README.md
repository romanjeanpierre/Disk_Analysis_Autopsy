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
<h3> Identify operating system & Hostname</h3>
Data Artifacts > Operating System Information
<br/>
<br/>
<img src="https://imgur.com/xHuOUMm.png" height="80%" width="80%" alt="Project Overview Image">
<h3> Results:</h3>
<oL> 
<li> Operating System: Windows 8 </li> 
<li> Hostname: WIN-BK3J6TFMHLL </li>
</oL>
<br/>
<h3>Identify file that was downloaded at 2013-12-18 03:02:50 & URL</h3>
Data Artifacts > Web Downloads
<br/>
<br/>
<img src="https://imgur.com/JHKz4Wn.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<h3>Identify the path of "Pier.jpg"</h3>
Data Artifacts > Recent Documents
<br/>
<br/>
<img src="https://imgur.com/1wFAOLU.png" height="80%" width="80%">
<h3> Identify File size of "lib" directory</h3>
Program Files > GIMP 2 > Click on largest partition
<img src="https://imgur.com/gq22YpL.png" height="80%" width="80%">
<h3> Investigate when was Administrator account last accessed </h3>
Navigate > OS Accounts
<br/>
<img src="https://imgur.com/9gCLCyy.png" height="80%" width="80%" alt="Drive Input Selection">

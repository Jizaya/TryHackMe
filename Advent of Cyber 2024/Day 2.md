<h1>Learning Objectives</h1>
<li>Learn to identify and analyze false positives in security alerts.</li>
<li>Learn methods to prioritize and reduce false positives in monitoring.</li>
<li>Understand how to differentiate between genuine events and benign events.</li>


<p align="center"><img src="https://github.com/user-attachments/assets/aa936231-7825-4f66-948c-5283bdf2bbac" width="150"/></p>
<p>Similar to every SOC, the analysts in the Wareville SOC also need to differentiate TPs from FPs. This becomes especially difficult for them near Christmas when the analysts face alert fatigue.
High chances of misclassification of TPs into FPs and vice versa are present in such times. The analysts, therefore, appreciate any help they could get from us in this crucial time.</p>
<p>To make matters worse, the office of the Mayor has sent the analysts an alert informing them of multiple encoded powershell commands run on their systems. Perhaps we can help with that.</p>
<p>According to the alert sent by the Mayor's office, the activity occurred on Dec 1st, 2024, between 0900 and 0930.</p> 
<h2>Q1: What is the name of the account causing all the failed login attempts?</h2>

<details>
<summary>Q1 Walkthrough</summary>
  <p>Change timeframe to around the time the activity occurred</p>
  <img src="https://github.com/user-attachments/assets/b5564f3b-96f6-48fd-ac5a-5d1002273d63"/>
  <p>Apply column filters that will assist in answering the question</p>
  <img src="https://github.com/user-attachments/assets/61563756-c473-4e6a-aa67-330e328a4a5b"/>

<p>Filter the event.outcome for failures to find the answer</p>
<img src="https://github.com/user-attachments/assets/04a91d0c-c5ab-4eb8-9270-dbf6d4957235"/>
<details>
  <summary>Q1 Answer</summary>
  <p><b>service_admin</b></p>
  <p><img src="https://github.com/user-attachments/assets/53212c03-40b0-4374-8815-5737cc388d39"/></p></details>
</details>


<p><h2>Q2: How many failed logon attempts were observed?</h2></p>

<details>
  <summary>Q2 Walkthrough</summary>
<p>Filter for failed on login attempts within timeframe</p>
<img src="https://github.com/user-attachments/assets/956d247c-7756-4152-90be-73e19ccf974e" width="100%" height="100%"/>
 <details> 
  <summary>Q2 Answer</summary>
   <p><b>6791</b>
    <p><img src="https://github.com/user-attachments/assets/134d31b7-ce92-4962-b889-3dfecb933d73" width="650"/></details>
</details>


<p><h2>Q3: What is the IP address of Glitch?</h2></p>

<details>
  <summary>Q3 Walkthrough</summary>
<p>Check the chart for any spikes in activity</p>
<img src="https://github.com/user-attachments/assets/ccbc2ca7-01cb-4df7-ae87-358bc33795d7" width="100%" height="100%"/>
  <p>Investigate the time when the spike in acitivity started</p>
<img src="https://github.com/user-attachments/assets/5f392e90-b423-4322-a31f-75a267434521" width="100%" height="100%"/>
  <p><img src="https://github.com/user-attachments/assets/ecac7def-3e1c-4458-990d-9840f3c56da4" width="100%" height="100%"/></p>
 <details> 
  <summary>Q3 Answer</summary>
   <p><b>10.0.255.1</b>
    <p><img src="https://github.com/user-attachments/assets/eff4f176-867b-4a89-b152-0e40fa7a14b3" width="650"/></details>
</details>


<p><h2>Q4: When did Glitch successfully logon to ADM-01? Format: MMM D, YYY HH:MM:SS.SSS</h2></p>

<details>
  <summary>Q4 Walkthrough</summary>
<p>Filter events by "ADM-01" host.hostname and find the first successful authentication login</p>
<img src="https://github.com/user-attachments/assets/f5f06f9d-a887-45ec-9854-c5421b6d2b09" width="100%" height="100%"/>
 <details> 
  <summary>Q4 Answer</summary>
   <p><b>Dec 1, 2024 08:54:39.000</b>
    <p><img src="https://github.com/user-attachments/assets/e3f38962-ff68-42ea-b91a-935503d8a567" width="650"/></details>
</details>


<p><h2>Q5: What is the decoded command executed by Glitch to fix the systems of Wareville?</h2></p>

<details>
  <summary>Q5 Walkthrough</summary>
<p>Filter events by "process" in event.category and find processes where a PowerShell command was executed</p>
<img src="https://github.com/user-attachments/assets/9acfeb43-7ac4-4d11-bd20-ab592cec9c84" width="100%" height="100%"/>
  <p>Decode the encoded command using a site such as <a href="https://gchq.github.io/CyberChef/"> CyberChef</a> <i>PowerShell commands are usually encoded with Base64</i></p>
  <img src="https://github.com/user-attachments/assets/08af5de6-52fc-417a-af68-1424f6ed67db"/>
 <details> 
  <summary>Q5 Answer</summary>
   <p><b>Install-WindowsUpdate -AcceptAll -AutoReboot</b>
    <p><img src="https://github.com/user-attachments/assets/d4182100-bbfc-43e6-9dff-4ced6be0204f" width="650"/></details>
</details>

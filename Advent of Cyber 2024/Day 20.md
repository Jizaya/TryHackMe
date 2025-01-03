<h1>Learning Objectives</h1>
<li>Investigate network traffic using Wireshark.</li>
<li>Identify indicators of compromise (IOCs) in captured network traffic.</li>
<li>Understand how C2 servers operate and communicate with compromised systems.</li>


<p align="center"><img src="https://github.com/user-attachments/assets/5bbf4a4e-eb35-40a1-b6b3-065752a1e893" height="350"/>

<p align="center"><i>Glitch snuck through the shadows, swift as a breeze,</p>
<p align="center">He captured the traffic with delicate ease.</p>
<p align="center">A PCAP file from a system gone bad,</p>
<p align="center">Mayor Malware's tricks made everything mad!</i></p> 


<p><h2>Q1: What was the first message the payload sent to Mayor Malware’s C2?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Open the C2_Traffic_Analysis.pcap in Wireshark </p>
      <img src="https://github.com/user-attachments/assets/0ae19b1b-7d4c-4411-9d71-6fc58717ea6f" width="650"/>
    <p>Enter "ip.src == 10.10.229.217" to filter for traffic from Marta May Ware's machine</p>
      <img src="https://github.com/user-attachments/assets/f40edae0-31c5-4850-a15d-c1cf21ce2c77"/>
    <p>Inspect packets for suspicious activity</p>
      <img src="https://github.com/user-attachments/assets/a15dc045-9cf8-4114-b0f1-672900bb776e"/>
 <details> 
  <summary>Q1 Answer</summary>
   <p><b>I am in Mayor!</b>
    <p><img src="https://github.com/user-attachments/assets/6fb69d5e-d207-4292-97fa-3dcabafdc051"/></details>
</details>


<p><h2>Q2: What was the IP address of the C2 server?</h2></p>

<details>
  <summary>Q2 Walkthrough</summary>
    <p>Analyze the destination of the suspicious packets</p>
      <img src="https://github.com/user-attachments/assets/b4b8a344-2689-42a9-8a51-a84dd705ed83"/>
 <details> 
  <summary>Q2 Answer</summary>
   <p><b>10.10.123.224</b>
    <p><img src="https://github.com/user-attachments/assets/48efc7c3-fad4-4d7f-a635-a2e6d66063ce"/></details>
</details>


<p><h2>Q3: What was the command sent by the C2 server to the target machine?</h2></p>

<details>
  <summary>Q3 Walkthrough</summary>
    <p>Filter for HTTP GET method to view requests from the server</p>
      <img src="https://github.com/user-attachments/assets/8f7ca829-381a-4307-81c1-ee08e1f01669"/>
    <p>View the HTTP Stream to see content in the way the application layer sees it</p>
      <img src="https://github.com/user-attachments/assets/f8a1bf5b-bcca-469b-977b-1c362fe19bd7"/>
 <details> 
  <summary>Q3 Answer</summary>
   <p><b>whoami</b>
    <p><img src="https://github.com/user-attachments/assets/dc2e1f47-3549-4477-92fc-f4c2caf6cf71"/></details>
</details>


<p><h2>Q4: What was the filename of the critical file exfiltrated by the C2 server?</h2></p>

<details>
  <summary>Q4 Walkthrough</summary>
    <p>Filter for HTTP POST method to data sent to the server</p>
      <img src="https://github.com/user-attachments/assets/0f84f6f5-7401-4910-bb9c-8fa856428758"/>
    <p>View the HTTP Stream to see content in the way the application layer sees it</p>
      <img src="https://github.com/user-attachments/assets/80f7907f-69a4-4dae-a0cc-af3aafad78a5"/>
 <details> 
  <summary>Q4 Answer</summary>
   <p><b>credentials.txt</b>
    <p><img src="https://github.com/user-attachments/assets/a8f3eabd-e529-4553-a716-165750bbb726"/></details>
</details>


<p><h2>Q5: What secret message was sent back to the C2 in an encrypted format through beacons?</h2></p>

<details>
  <summary>Q5 Walkthrough</summary>
    <p>Investigate the HTTP Stream of the POST method request containing the file that was exfiltrated for a key</p>
      <img src="https://github.com/user-attachments/assets/3f1f22b3-4a88-4a3c-a1fa-37d715707609"/>
    <p>Investigate other suspicious POST method request packets for the encrypted message</p>
      <img src="https://github.com/user-attachments/assets/c5f35e9e-ae41-44ec-9261-d990888766af"/>
      <img src="https://github.com/user-attachments/assets/a1797247-5e5f-4251-8e01-ddf6b49f3486"/>
    <p>Navigate to <a href="https://cyberchef.org/"/>Cyber Chef</a> to unencrypt the secret message using the clues from the packets</p>
      <img src="https://github.com/user-attachments/assets/6d1b4097-928c-44f6-8194-5a2184ea7552"/>
 <details> 
  <summary>Q5 Answer</summary>
   <p><b>THM_Secret_101</b>
    <p><img src="https://github.com/user-attachments/assets/a645f7c6-d0c1-49b3-b82b-c00b7768931d"/></details>
</details>

<h1>Learning Objectives</h1>
<li>Understand how phishing attacks work.</li>
<li>Discover how macros in documents can be used and abused.</li>
<li>Learn how to carry out a phishing attack with a macro.</li>

<p align="center"><i>Mayor Malware had one, just one SOC-mas wish:
<p align="center">The SOC organiser would fall for his phish!
<p align="center">Well on top of this, he wanted as well,
<p align="center">Once the email opened, to gain a rev shell.</i></p>

<p align="center"><img src="https://github.com/user-attachments/assets/162dafc0-b792-4b23-a6a6-d3771b7938b3"  width="450"/> 

<p>Marta May Ware is surprised that her system was compromised even after following tight security, but McSkidy thinks she traced the attacker, and he got in. It’s none other than Mayor Malware who got into the system. This time, the Mayor used phishing to get his victim. McSkidy’s quick incident response prevented significant damage.</p>

<p>In this task, you will run a security assessment against Marta May Ware. The purpose would be to improve her security and raise her cyber security awareness against future attacks.</p>


<p><h2>Q1: What is the flag value inside the flag.txt file that’s located on the Administrator’s desktop?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Open terminal window and run msfconsole and set payload related to creating a document with a Microsoft Word macro</p>
      <img src="https://github.com/user-attachments/assets/afe0cac1-0bc0-4796-ad2c-6072354e6051"/>
    <p>Set LHOST to IP address of attacking system and set LPORT to 8888 for the port you will listen on for incoming connections on the attacking system</p>
      <img src="https://github.com/user-attachments/assets/71670173-c16d-4ec9-b09a-d364f0f02ed3"/>
    <p>Confirm proper configuration options and run exploit to generate a macro and embed it in a document (Take note of wear document is saved)</p>
      <img src="https://github.com/user-attachments/assets/5540f5a6-46af-415c-beac-3832f49065a1" width="650"/>
    <p>Open terminal window and run msfconsole and set payload that works with the payload used when creating the malicious macro</p>
      <img src="https://github.com/user-attachments/assets/50b1d67e-889f-4b1c-bdb6-a8d62a08ae58"/>
    <p>Set LHOST to IP address of attacking system and set LPORT to 8888 for the port you will listen on for incoming connections on the attacking system</p>
      <img src="https://github.com/user-attachments/assets/16ec86d0-31f9-4f6a-b907-ae6384c894bd"/>
    <p>Confirm proper configuration options and run exploit to listen for incoming connections</p>
      <img src="https://github.com/user-attachments/assets/b7edb74b-9147-4633-8cfb-c133c3be809f" width="650"/>
    <p>Change name of malicious file to something a user would click on without investigating further</p>
      <img src="https://github.com/user-attachments/assets/5f94f91d-d202-4459-9c72-f28866d6d408"/>
    <p>Log into email account and write phishing email to user</p>
      <img src="https://github.com/user-attachments/assets/39456b04-8abe-4872-9506-053e63287e23"/>
      <img src="https://github.com/user-attachments/assets/be9a076c-0270-4c52-92a1-a7cd234f172b"/>
    <p>Verify account and connect to shell</p>
      <img src="https://github.com/user-attachments/assets/761c56fe-fabf-48f7-bd21-7258975d100c"/>
    <p>Navigate to desktop and retrieve flag</p>
      <img src="https://github.com/user-attachments/assets/783cda5b-6ee1-4cab-ab41-c17a13ff303b"/>
      <img src="https://github.com/user-attachments/assets/4a6de5ad-0863-4f02-b2cf-7ac7e436fd3e"/>

       

 <details> 
  <summary>Q1 Answer</summary>
   <p><b>THM{PHISHING_CHRISTMAS}</b>
    <p><img src="https://github.com/user-attachments/assets/8b354f43-431e-4997-934f-aefdcff61c7d"/></details>
</details>

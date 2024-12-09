<h1>Learning Objectives</h1>
<li>Learn how to identify malicious techniques using the MITRE ATT&CK framework.</li>
<li>Learn about how to use Atomic Red Team tests to conduct attack simulations.</li>
<li>Understand how to create alerting and detection rules from the attack tests.</li>
  
  
<p align="center"><img src="https://github.com/user-attachments/assets/accfac41-4c2a-435e-8050-4661d7d4207c"/></p>

<p>As Glitch continues to prepare for SOC-mas and fortifies Wareville's security, he decides to conduct an attack simulation that would mimic a ransomware attack across the environment. He is unsure of the correct detection metrics to implement for this test and asks you for help. Your task is to identify the correct atomic test to run that will take advantage of a <b>command and scripting interpreter</b>, conduct the test, and extract valuable artefacts that would be used to craft a detection rule.</p>


<p><h2>Q1: What was the flag found in the .txt file that is found in the same directory as the PhishingAttachment.xslm artefact?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Open Event Viewer and navigate to Applications and Services => Microsoft => Windows => Sysmon => Operational to view Operational logs.</p>
      <img src="https://github.com/user-attachments/assets/105f3ec9-74cf-4e1b-85ae-f7454f0753d1"/>
    <p>Run AtomicTest command and refresh Operational logs for new events. Investigate logs for pertinent information.</p>
      <img src="https://github.com/user-attachments/assets/c91481fd-27d6-427e-bb6d-92a4267daaef"/>
    <p>Navigate to directory in log and open txt file for answer.</p>
      <img src="https://github.com/user-attachments/assets/92887c5d-0ffa-4619-a226-dbe01845a38b"/>
      <img src="https://github.com/user-attachments/assets/e1815462-3bf9-41f9-b15a-c66fa087b8f6"/>

 <details> 
  <summary>Q1 Answer</summary>
   <p><b>THM{GlitchTestingForSpearphishing}</b>
    <p><img src="https://github.com/user-attachments/assets/bf636781-1398-459b-9f4f-70655ca755f3"/></details>
    
</details>


<p><h2>Q2: What ATT&CK technique ID would be our point of interest?</h2></p>
<details>
  <summary>Q2 Walkthrough</summary>
  <p>Navigate to <a href="https://attack.mitre.org/">MITRE ATT&CK</a> website and search "Command and Scripting Interpreter" for answer</p>
    <img src="https://github.com/user-attachments/assets/bb14fdfb-faf4-4352-b9fb-8b2118a44c1f"/>
  <details>
  <summary>Q2 Answer</summary>
  <p><b>T1059</b></p>
    <img src="https://github.com/user-attachments/assets/7ada91d8-05db-4906-aa8c-e60fe2b770b6"/></p></details>
  </details>


<p><h2>Q3: What ATT&CK subtechnique ID focuses on the Windows Command Shell?</h2></p>
<details>
  <summary>Q3 Walkthrough</summary>
  <p>Navigate to <a href="https://attack.mitre.org/">MITRE ATT&CK</a> website and search "Windows Command Shell" for answer</p>
    <img src="https://github.com/user-attachments/assets/eebbe472-0897-4476-86d2-8b7ecabba002"/>
  <details>
  <summary>Q3 Answer</summary>
  <p><b>T1059.003</b></p>
    <img src="https://github.com/user-attachments/assets/dfca25d2-d6bb-4cbc-a051-87ec302c071a"/></p></details>
  </details>



<p><h2>Q4: What is the name of the Atomic Test to be simulated?</h2></p>
<details>
  <summary>Q3 Walkthrough</summary>
  <p>Open PowerShell and run "invoke-atomictest t1059.003 -showdetails" for answer</p>
    <img src="https://github.com/user-attachments/assets/ab86d64f-2127-4ae2-b2c5-95141d5fb21d"/>
  <details>
  <summary>Q3 Answer</summary>
  <p><b>Simulate BlackByte Ransomware Print Bombing</b></p>
    <img src="https://github.com/user-attachments/assets/04acaaca-d953-46a2-8968-7f996ce3d525"/></p></details>
  </details>




<p><h2>Q5: What is the name of the file used in the test?</h2></p>
<details>
  <summary>Q5 Walkthrough</summary>
  <p>Open PowerShell and run "invoke-atomictest t1059.003 -showdetails" and find the Atomic Test 4 from previous question</p>
    <img src="https://github.com/user-attachments/assets/dc8fcad4-9b7c-4400-9c1d-5544fde50ce3"/>
  <p>Look through the commands and dependencies for the answer</p>
    <img src="https://github.com/user-attachments/assets/295d4b9f-f545-420f-b64b-cfd9af4a4cb2"/>   
  <details>
  <summary>Q5 Answer</summary>
  <p><b>Wareville_Ransomware.txt</b></p>
    <img src="https://github.com/user-attachments/assets/9c3598d9-9390-4913-b091-5a707e9eb664"></p></details>
  </details>




<p><h2>Q6: What is the flag found from this Atomic Test?</h2></p>
<details>
  <summary>Q6 Walkthrough</summary>
  <p>Navigate to the directory of the file used in the test found from the last question</p>
    <img src="https://github.com/user-attachments/assets/a77b6e82-eddf-4452-8aee-f4f6bdee1bcf">
  <details>
  <summary>Q6 Answer</summary>
  <p><b>THM{R2xpdGNoIGlzIG5vdCB0aGUgZW5lbXk=}</b></p>
    <img src="https://github.com/user-attachments/assets/e335e1a1-8c87-42f8-9e3f-51fb80a3fbb2"></p></details>
  </details>

<h1>Learning Objectives</h1>
<li>Analyze malware behaviour using sandbox tools.</li>
<li>Explore how to use YARA rules to detect malicious patterns.</li>
<li>Learn about various malware evasion techniques.</li>
<li>Implement an evasion technique to bypass YARA rule detection.</li></p>
  
  
<p align="center"><i>His malware, it seemed, wasn't quite ready for town.</p>
<p align="center">"There are watchers and scanners and rules by the ton!</p>
<p align="center">If I'm not careful, they'll catch all my fun!"</i></p>

<p align="center"><img src="https://github.com/user-attachments/assets/34a2795a-36ca-4b8f-ac1f-df3441689c76" width="350"/></p>

<p>Mayor Malware leaned back, tapping his fingers thoughtfully on the table. All of this research had revealed an unsettling truth: his malware, as cunning as it was, wasn't yet ready for the wild. There were too many tools and too many vigilant eyes—analysts armed with YARA rules, Sysmon, and a host of detection techniques that could expose his creation before it even had a chance to spread.</p>


<p><h2>Q1: What is the flag displayed in the popup window after the EDR detects the malware?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Open PowerShell, navigate to C:\Tools directory, and run JingleBells script</p>
      <img src="https://github.com/user-attachments/assets/19bf7e6d-1c39-4436-9c84-8d9bca9f2f00"/>
    <p>Run JingleBells.ps1 script to start EDR</p>
      <img src="https://github.com/user-attachments/assets/ae76be25-2caa-41c5-a4f3-e15180f752f1"/>
    <p>Navigate to C:\Tools\Malware directory and run MerryChristmas.exe for answer to popup</p>
      <img src="https://github.com/user-attachments/assets/85fe0362-dfc1-4e9c-bf6c-c732dbadafd6"/>
 <details> 
  <summary>Q1 Answer</summary>
   <p><b>THM{GlitchWasHere}</b>
    <p><img src="https://github.com/user-attachments/assets/ca3785dc-615c-4934-8da1-547ed78acd56"/></details>
</details>


<p><h2>Q2: What is the flag found in the malstrings.txt document after running floss.exe, and opening the file in a text editor?</h2></p>

<details>
  <summary>Q2 Walkthrough</summary>
    <p>Open PowerShell, navigate to "C:\Tools\FLOSS" directory, and run "floss.exe C:\Tools\Malware\MerryChristmas.exe |Out-File C:\tools\malstrings.txt" to scan for strings in the MerryChristmas.exe and save the results to a file called malstrings.txt</p>
      <img src="https://github.com/user-attachments/assets/22db891f-5ef6-4bf5-9b48-610f0826b9f9"/>
    <p>Navigate to previous directory and list files to ensure text file was created</p>
      <img src="https://github.com/user-attachments/assets/61bfa2fd-2ac8-4de8-8f90-5da6ca5754ad"/>
    <p>Run "ii malstrings.txt" to open the text file and find the flag within the file</p>
      <img src="https://github.com/user-attachments/assets/fab101dc-82f9-4e1e-aab9-9855bb550d69"/>
 <details> 
  <summary>Q2 Answer</summary>
  <p><b>THM{HiddenClue}</b></p>
    <img src="https://github.com/user-attachments/assets/4758453e-725a-4c2e-8c02-983bbdda0f96"/></p></details>
  </details>

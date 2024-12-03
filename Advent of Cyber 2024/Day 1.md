<h1>Learning Objectives</h1>
<li>Learn how to investigate malicious link files.</li>
<li>Learn about OPSEC and OPSEC mistakes.</li>
<li>Understand how to track and attribute digital identities in cyber investigations.</li>
  
  
  <p align="center"><img src="https://github.com/user-attachments/assets/cf51aa40-b86f-49db-81f1-5dfa71f446a5" width="350"></p>

  <p align="center"><i>McSkidy dug deeper, her mind sharp and quick,</p>
<p align="center">But something felt off, a peculiar trick.</p>
<p align="center">The pieces she’d gathered just didn’t align,</p>
<p align="center">A puzzle with gaps, a tangled design.</i></p>


<p>As McSkidy continued digging, a pattern emerged that didn't fit the persona she was piecing together. A different handle appeared in obscure places, buried deep in the details: "MM."</p>
<p>"Who's MM?" McSkidy muttered, the mystery deepening.</p>
<p>Even though all signs on the website seemed to point to Glitch as the author, it became clear that someone had gone to great lengths to ensure Glitch's name appeared everywhere. Yet, the scattered traces left by MM suggested a deliberate effort to shift the blame.</p>


<p><h2>Q1: Looks like the song.mp3 file is not what we expected! Run "exiftool song.mp3" in your terminal to find out the author of the song. Who is the author?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
<p>Open web browser and navigate to x.x.x.x to convert video to mp3.</p>
<img src="https://github.com/user-attachments/assets/c801389f-5c74-4410-a047-1926a76a7e10" width="650"/>
<p>Extract files and navigate to path of unzipped files.</p>
<p>Run "exiftool song.mp3" for answer</p>
<img src="https://github.com/user-attachments/assets/d63f1a5f-d824-4e3f-a920-65f5a528f513" width="650"/>
 <details> 
  <summary>Q1 Answer</summary>
   <p><b>Tyler Ramsbey</b>
    <p><img src="https://github.com/user-attachments/assets/469d4bc5-a4ac-48c9-afc5-5d197a5c67c3" width="650"/></details>
</details>


<p><h2>Q2: The malicious PowerShell script sends stolen info to a C2 server. What is the URL of this C2 server?</h2></p>
<details>
  <summary>Q2 Walkthrough</summary>
  <p>Run "exiftool somg.mp3" and navigate to URL of file that will be downloaded through PowerShell command
  <p><img src="https://github.com/user-attachments/assets/997703c9-89dc-41c1-9bad-8c19ee7fa98f" width="1250">
    <p>Search for the command that states where the stolen info will be sent</p>
  <p><img src="https://github.com/user-attachments/assets/179f5b5a-035f-4f3d-96d6-de2f459545b5"/>
</p>
</p>
  <details>
  <summary>Q2 Answer</summary>
  <p><b>http://papash3ll.thm/data</b></p>
  <p><img src="https://github.com/user-attachments/assets/28f5b8c7-3e66-4400-8b11-4d7ee140ecaa" width="650"></p></details>
  </details>


<p><h2>Q3: Who is M.M? Maybe his Github profile page would provide clues?</h2></p>
<details>
  <summary>Q3 Walkthrough</summary>
<p>Find a clue of who created the PowerShell command within the URL found within the PowerShell command</p>
<img src="https://github.com/user-attachments/assets/bf4a9ccf-c406-4b98-afaf-919bbd932815" width="650"/>
<p>Search the web or GitHub for the code</p>
  <p><img src="https://github.com/user-attachments/assets/d522e29a-69af-4515-a6dc-c4b9ef786ab9"/> <img src="https://github.com/user-attachments/assets/e18cd2ba-aaec-4137-b1b7-a5c454a1dd7a"/>
<p>Explore the GitHub profile for the answer</p>
<img src="https://github.com/user-attachments/assets/3371e440-c7a0-49ea-a499-12dc57754dd9" width="650"/>
 <details> 
  <summary>Q3 Answer</summary>
   <p><b>Mayor Malware</b>
    <p><img src="https://github.com/user-attachments/assets/514f7602-1713-4bd7-9c1d-589ffb84be04" width="650"/></details>
</details>


<p><h2>Q4: What is the number of commits on the GitHub repo where the issue was raised?</h2></p>
<details>
  <summary>Q4 Walkthrough</summary>
<p>Backtrack to how it was discovered who created the PowerShell code</p>
<p><img src="https://github.com/user-attachments/assets/d522e29a-69af-4515-a6dc-c4b9ef786ab9"/> <img src="https://github.com/user-attachments/assets/e18cd2ba-aaec-4137-b1b7-a5c454a1dd7a"/>
<p>Check the insights for the answer</p>
  <p><img src="https://github.com/user-attachments/assets/569a2ac3-640c-4705-90fa-d2d948890f1d"/> 
 <details> 
  <summary>Q4 Answer</summary>
   <p><b>1</b>
    <p><img src="https://github.com/user-attachments/assets/20c0e0e9-7e45-4885-9c29-3476ff63d55a" width="650"/></details>
</details>

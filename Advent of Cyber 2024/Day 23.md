<h1>Learning Objectives</h1>
<li>Understand what hash functions and hash values are.</li>
<li>Learn how to save hashed passwords.</li>
<li>Learn about cracking hashes.</li>
<li>Explore how to find the password of a password-protected document.</li>

<p align="center"><img src="https://github.com/user-attachments/assets/f89a3f70-85f3-4e4d-9f57-63e761696dd5"  width="650"/> 

<p align="center"><i>As time went on by, something seemed funny:
<p align="center">Mayor Malware and the source of his money!
<p align="center">SOC-mas grew closer, so The Glitch better move it.
<p align="center">Gain access to the wallet so that he could prove it!</i>

<p>Glitch has been investigating how Mayor Malware funds his shady operations for quite some time. Recently, the Mayor disposed of various old electronic equipment; one was an old tablet with a cracked screen. Being an avid connoisseur of active and passive reconnaissance who does not mind “dumpster diving” for the greater good, Glitch quickly picked it up before the garbage truck. Surprisingly, despite being in a terrible condition with a cracked and hazy screen, the tablet still turns on. Browsing through the various files, one PDF file that caught his attention was password-protected. It is time you work with Glitch to discover the password and uncover any evidence lurking there.</p>


<p><h2>Q1: Crack the hash value stored in hash1.txt. What was the password?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Navigate to directory containing hash1.txt and copy the hash within the file</p>
      <img src="https://github.com/user-attachments/assets/35f94c55-0233-48e0-8761-2e93df0a24bc"/>
    <p>Run python hash identification script to find what kind of hash it is</p>
      <img src="https://github.com/user-attachments/assets/8b12ff07-65e7-4059-a285-fe559020754c"/>
    <p>Use John the Ripper to crack the hash</p>
      <img src="https://github.com/user-attachments/assets/56eea549-0a27-4252-82f7-bd3d4a547a9c"/>
 <details> 
  <summary>Q1 Answer</summary>
   <p><b>fluffycat12</b>
    <p><img src="https://github.com/user-attachments/assets/5d0f45af-843b-4123-97eb-78b4a81976ab"/></details>
</details>


<p><h2>Q2: What is the flag at the top of the private.pdf file?</h2></p>

<details>
  <summary>Q2 Walkthrough</summary>
    <p>Create hash of private.pdf using pdf2john</p>
      <img src="https://github.com/user-attachments/assets/c085e9c9-e500-40b6-8289-30770ad2a450"/>
    <p>Use wordlist in directory to crack the hash with John the Ripper</p>
      <img src="https://github.com/user-attachments/assets/daa3d7c0-39a9-4b1d-85ee-601f99844dae"/>
    <p>Convert the pdf to a text file to view in the CLI using the password</p>
      <img src="https://github.com/user-attachments/assets/9d1cd11d-067e-465a-9973-585e45efd1e5"/>  
    <p>Run head private.txt to view the first few lines of the pdf for the flag</p>
      <img src="https://github.com/user-attachments/assets/d298acd8-9264-42cc-b23d-a7e7684f55a6"/>

 <details> 
  <summary>Q2 Answer</summary>
   <p><b>THM{do_not_GET_CAUGHT}</b>
    <p><img src="https://github.com/user-attachments/assets/4fcde807-fce6-4da4-baa2-2da5086375c5"/>
</details>

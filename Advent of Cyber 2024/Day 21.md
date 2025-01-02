<h1>Learning Objectives</h1>
<li>Understanding the structure of a binary file.</li>
<li>The difference between Disassembly vs Decompiling.</li>
<li>Familiarity with multi-stage binaries.</li>
<li>Practically reversing a  multi-stage binary.</li>


<p align="center"><img src="https://github.com/user-attachments/assets/7a9c7940-ac42-4f0d-8b5e-0a8e3c03cf58"/>


<p>Join McSkidy and help investigate the alerts coming from the file WarevilleApp.exe. Put on your reverse engineering hat and help decipher the mystery behind this suspicious binary.</p>


<p><h2>Q1: What is the function name that downloads and executes files in the WarevilleApp.exe?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Open the WarevilleApp.exe in ILSpy</p>
      <img src="https://github.com/user-attachments/assets/87239ac7-658f-4249-b7ca-fb13673c1679"/>
    <p>Sift through the decompiled code of the WarevilleApp for code that downloads and executes files</p>
      <img src="https://github.com/user-attachments/assets/0e2d0f39-807c-4aa7-9087-189d1002d723"/>
 <details> 
  <summary>Q1 Answer</summary>
   <p><b>DownloadAndExecuteFile</b>
    <p><img src="https://github.com/user-attachments/assets/4392f59e-33dc-4e5b-99df-cdaa5c240563"/></details>
</details>


<p><h2>Q2: Once you execute the WarevilleApp.exe, it downloads another binary to the Downloads folder. What is the name of the binary?</h2></p>

<details>
  <summary>Q2 Walkthrough</summary>
    <p>Analyze the decompiled code for the binary that downloads into the Downloads folder</p>
      <img src="https://github.com/user-attachments/assets/23a553ef-1969-479c-83cf-9387cbd1cc51"/>
 <details> 
  <summary>Q2 Answer</summary>
   <p><b>explorer.exe</b>
    <p><img src="https://github.com/user-attachments/assets/afbad655-e186-40e9-81a6-b54ef74f318b"/></details>
</details>


<p><h2>Q3: What domain name is the one from where the file is downloaded after running WarevilleApp.exe?</h2></p>

<details>
  <summary>Q3 Walkthrough</summary>
    <p>Analyze the decompiled code for any domain names</p>
      <img src="https://github.com/user-attachments/assets/21223acf-f390-4f92-a27d-acf8c7e4b27f"/>
 <details> 
  <summary>Q3 Answer</summary>
   <p><b>mayorc2.thm</b>
    <p><img src="https://github.com/user-attachments/assets/2e6338a2-5e6f-4f4d-a81c-3ec388b7e4dc"/></details>
</details>


<p><h2>Q4: The stage 2 binary is executed automatically and creates a zip file comprising the victim's computer data; what is the name of the zip file?</h2></p>

<details>
  <summary>Q4 Walkthrough</summary>
    <p>Run the Wareville App in a sandbox environment and press "Submit"</p>
      <img src="https://github.com/user-attachments/assets/3f66811f-e08e-4ab3-b655-59ce745f25b1"/>
    <p>Open the downloaded application in ILSpy</p>
      <img src="https://github.com/user-attachments/assets/192f8d26-38b1-4728-a478-8a9d1a15e5f2"/>
    <p>Analyze the decompiled code for the code that creates a zip file</p>
      <img src="https://github.com/user-attachments/assets/4116aea2-73cf-4767-9255-c0675d82923c"/>
 <details> 
  <summary>Q4 Answer</summary>
   <p><b>CollectedFiles.zip</b>
    <p><img src="https://github.com/user-attachments/assets/7cf67457-b36f-4ce3-99e6-9a37608caa99"/></details>
</details>


<p><h2>Q5: What is the name of the C2 server where the stage 2 binary tries to upload files?</h2></p>

<details>
  <summary>Q5 Walkthrough</summary>
    <p>Analyze the decompiled code for files uploaded to a server</p>
      <img src="https://github.com/user-attachments/assets/0ba2e81f-aefb-4e81-aaca-8c074afb1822"/>
 <details> 
  <summary>Q5 Answer</summary>
   <p><b>anonymousc2.thm</b>
    <p><img src="https://github.com/user-attachments/assets/5eb6273d-6324-42eb-9620-af10c04988f3"/></details>
</details>

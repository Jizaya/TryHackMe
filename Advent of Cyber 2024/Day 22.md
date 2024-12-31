<h1>Learning Objectives</h1>
<li>Learn about Kubernetes, what it is and why it is used.</li>
<li>Learn about DFIR, and the challenges that come with DFIR in an ephemeral environment.</li>
<li>Learn how DFIR can be done in a Kubernetes environment using log analysis.</li>
  
  
<p align="center"><img src="https://github.com/user-attachments/assets/90574c54-d6fe-4fed-aa65-5b2f0212a7ca" width="350"></p>

<p>We will help McSkidy and the Glitch become digital forensics analysts and retrace the malicious actor's steps. We will especially focus on collecting evidence and artefacts to uncover the perpetrator and present our analysis to Wareville townspeople.</p>


<p><h2>Q1: What is the name of the webshell that was used by Mayor Malware?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Spin up a Kubernetes cluster and verify all the pods are running</p>
      <img src="https://github.com/user-attachments/assets/ab2419d1-d486-4f60-aa8f-465d4cfe41cb"/>
    <p>Connect to the pod of the compromised web application and search for any suspicious logs</p>
      <img src="https://github.com/user-attachments/assets/fa845508-0c66-4037-80be-142672ea2064"/>
  
 <details> 
  <summary>Q1 Answer</summary>
    <p><b>shelly.php</b></p>
      <img src="https://github.com/user-attachments/assets/f9877333-d291-4880-8521-877cc488d394"/></details>
</details>


<p><h2>Q2: What file did Mayor Malware read from the pod?</h2></p>

<details>
  <summary>Q2 Walkthrough</summary>
    <p>Navigate to the backup directory at /home/ubuntu/dfir_artefacts</p>
      <img src="https://github.com/user-attachments/assets/eff67614-dbbc-4b83-bc2d-43b27b1b91f9"/>
    <p>Search for command within the pod_apache2_access log that displays the contents of a file</p>
      <img src="https://github.com/user-attachments/assets/6e21e18c-4cdf-4ebc-ae87-762be3a91f47"/>

<details>
  <summary>Q2 Answer</summary>
    <p><b>db.php</b></p>
      <p><img src="https://github.com/user-attachments/assets/f729fc05-7b75-4932-8891-7db1397aaaf8"></p></details>
  </details>


<p><h2>Q3: What tool did Mayor Malware search for that could be used to create a remote connection from the pod?</h2></p>

<details>
  <summary>Q3 Walkthrough</summary>
    <p>Search for any suspicious activity within the pod_apache2_access log</p>
      <img src="https://github.com/user-attachments/assets/6e21e18c-4cdf-4ebc-ae87-762be3a91f47"/>

<details>
  <summary>Q3 Answer</summary>
    <p><b>nc</b></p>
      <p><img src="https://github.com/user-attachments/assets/8f00a014-e080-466f-840c-12479daa9db7"></p></details>
  </details>


<p><h2>Q4: What IP connected to the docker registry that was unexpected?</h2></p>

<details>
  <summary>Q4 Walkthrough</summary>
    <p>Use the following command to filter for lines containing the word HEAD and extracting the first word from each line to isolate the IP addresses in the file</p>
      <img src="https://github.com/user-attachments/assets/253625d5-9c56-4375-a585-f976227c0e5e"/>
 
  <details> 
    <summary>Q4 Answer</summary>
     <p><b>10.10.130.253</b>
      <p><img src="https://github.com/user-attachments/assets/3097074b-5e78-47bd-8749-d320c9a71a1c"/></details>
</details>


<p><h2>Q5: At what time is the first connection made from this IP to the docker registry?</h2></p>

<details>
  <summary>Q5 Walkthrough</summary>
    <p>Use following command to filter for every log containing the suspicious IP address</p>
      <img src="https://github.com/user-attachments/assets/15cf2235-de78-43e8-b950-0b48e551926a"/>

 <details> 
  <summary>Q5 Answer</summary>
   <p><b>29/Oct/2024:10:06:33 +0000</b>
    <p><img src="https://github.com/user-attachments/assets/c90bf630-5446-460c-82f4-62d9dcfe6732"/></details>
</details>


<p><h2>Q6: At what time is the updated malicious image pushed to the registry?</h2></p>

<details>
  <summary>Q6 Walkthrough</summary>
    <p>Use the following command to filter for every log containing the suspicious IP where a new image was pushed</p>
      <img src="https://github.com/user-attachments/assets/0b6097af-c5c2-4218-b825-b04b931f963a"/>

  <details> 
  <summary>Q6 Answer</summary>
   <p><b>29/Oct/2024:12:34:28 +0000</b>
    <p><img src="https://github.com/user-attachments/assets/36bb6e8e-a1ed-4c5a-aa78-ca545addba15"/></details>
</details>


<p><h2>Q7: What is the value stored in the "pull-creds" secret?</h2></p>

<details>
  <summary>Q7 Walkthrough</summary>
<p>Use the following command to retrieve the kubernetes secret from wareville container and decode it into plain text</p>
<p><img src="https://github.com/user-attachments/assets/8e4f77f4-1365-4e04-802f-3086b8328ca8"/> 

 <details> 
  <summary>Q7 Answer</summary>
   <p><b>{"auths":{"http://docker-registry.nicetown.loc:5000":{"username":"mr.nice","password":"Mr.N4ughty","auth":"bXIubmljZTpNci5ONHVnaHR5"}}}</b>
    <p><img src="https://github.com/user-attachments/assets/204cac09-9dc0-4305-a788-75b9121f6b1a"/></details>
</details>

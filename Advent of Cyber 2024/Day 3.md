<h1>Learning Objectives</h1>
<li>Learn about Log analysis and tools like ELK.</li>
<li>Learn about KQL and how it can be used to investigate logs using ELK.</li>
<li>Learn about RCE (Remote Code Execution), and how this can be done via insecure file upload.</li>
  
  
<p align="center"><img src="https://github.com/user-attachments/assets/4f5b6715-ee6c-4335-8845-4627f8b379d2" width="350"></p>

<p align="center"><i>Late one Christmas evening the Glitch had a feeling, Something forgotten as he stared at the ceiling. He got up out of bed and decided to check, A note on his wall: ”Two days! InsnowSec”.</p>
<p align="center">With a click and a type he got his hotel and tickets, And sank off to sleep to the sound of some crickets. Luggage in hand, he had arrived at Frosty Pines, “To get to the conference, just follow the signs”.</p>
<p align="center">Just as he was ready the Glitch got a fright, An RCE vulnerability on their website ?!? He exploited it quick and made a report, But before he could send arrived his transport.</p>
<p align="center">In the Frosty Pines SOC they saw an alert, This looked quite bad, they called an expert. The request came from a room, but they couldn’t tell which, The logs saved the day, it was the room of…the Glitch.</i></p>

<p>Thanks to our extensive intrusion detection capabilities, our systems alerted the SOC team to a web shell being uploaded to the WareVille Rails booking platform on Oct 1, 2024. Our task is to review the web server logs to determine how the attacker achieved this.</p>


<p><h2>Q1: Where was the web shell uploaded to? Format: /directory/directory/directory/filename.php</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
<p>Change start time to October 3, 2024 11:30:00 and end time to October 3, 2024 12:00:00</p>
  <img src="https://github.com/user-attachments/assets/44615614-3ca6-4335-989a-eca4c901b4c8"/>
  <p>Investigate logs for any that standout. Search (message: "shell.php") to query all entries of "shell.php" in the message field of logs</p>
  <img src="https://github.com/user-attachments/assets/bfe5b22c-8c31-4fe1-9e61-b2672527ce8e"/>
 <details> 
  <summary>Q1 Answer</summary>
   <p><b>/media/images/rooms/shell.php</b>
    <p><img src="https://github.com/user-attachments/assets/c65e5f12-685f-43de-ba75-031b74089544"/></details>
</details>


<p><h2>Q2: What IP address accessed the web shell?</h2></p>
<details>
  <summary>Q2 Walkthrough</summary>
  <p>Inspect the logs where the message contents consist of "shell.php" for suspicious activity</p>
    <img src="https://github.com/user-attachments/assets/67f552e0-01d6-464c-be51-f778f1e9cadc">
  <details>
  <summary>Q2 Answer</summary>
  <p><b>10.11.83.34</b></p>
    <img src="https://github.com/user-attachments/assets/909d91cb-52ae-4576-a5c3-915e7860b786"></p></details>
  </details>


<p><h2>Q3: What is the contents of the flag.txt</h2></p>
<details>
  <summary>Q3 Walkthrough</summary>
  <p>Create malicious file</p>
    <img src="https://github.com/user-attachments/assets/b5a98141-72da-4f7f-986d-e35cc7db4399"/> 
    <p><img src="https://github.com/user-attachments/assets/dc9697fe-1d56-47ec-a59f-101ed62b5e97"/></p>
  <p> Per TryHackMe, "Please note, to access http://frostypines.thm, you will need to reference it within your hosts file. On the AttackBox, this can be done by executing the following command in a terminal: echo "<i>MACHINE IP</i> frostypines.thm" >> /etc/hosts"</p>
  <p>Access admin page using following credentials. <i>Password = admin</i></p>
    <img src="https://github.com/user-attachments/assets/f3f49869-2e8d-465d-be78-8fd23d55d02c"/>
  <p>Navigate to "Add new Room" page and upload created file to room image</p>
    <img src="https://github.com/user-attachments/assets/dd9f3ab0-b1e2-4d34-85aa-2dc40e94c64d"/>
  <p>Open image in new tab to find directory where maliciuous file is now stored and navigate to directory of malicious file</p>
    <img src="https://github.com/user-attachments/assets/16979c95-1e20-408a-954c-703f4686c23c"/> 
    <img src="https://github.com/user-attachments/assets/9c4e4c19-6605-4c36-abf0-cf187862128c"/>
  <p>Execute "ls" command to list files in the directory</p>
    <img src="https://github.com/user-attachments/assets/6ece9ae4-cc06-4370-bd5e-557699be42b7"/>
  <p>Execute "cat" command for flag.txt to read the contents of the file
    <img src="https://github.com/user-attachments/assets/a5b6793e-c450-46bd-905f-d14d0aa61d8a"/>
 <details> 
  <summary>Q3 Answer</summary>
   <p><b>THM{Glitch_Was_H3r3}</b></p>
    <img src="https://github.com/user-attachments/assets/805985c1-bcf1-4f1c-91e0-f38c68ca2a1f"/></details>
</details>

